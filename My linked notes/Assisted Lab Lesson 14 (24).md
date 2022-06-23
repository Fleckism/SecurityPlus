# Assisted Lab 24: Identifying a Browser Attack

## Scenario

An interception proxy is software that sits between a client and server (a Man-in-the-Middle or On-Path attack) and allows requests from the client and responses from the server to be analyzed and modified. In this activity, you will use the interception proxy Burp Suite ([portswigger.net](https://portswigger.net/)) to probe a web application for weaknesses and show how allowing a simple script to run can compromise browser security. Next, you will see the steps behind intercepting an email password reset attempt.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objective:

-   1.3 Given a scenario, analyze potential indicators associated with application attacks.

## Configure interception proxy

In the first part of this activity, you will see how XSS attacks take advantage of web applications that process user input to form the HTML output in some way. There are usually two sources of inputs:

-   User typed input through a form or control.
    
-   Parsing (interpreting) parameters from a URL.
    

XSS vulnerability testing on a website will consequently focus primarily on script-based pages (such as PHP) and on forms. You will use Burp Suite to probe a user form for XSS vulnerabilities. The form is hosted on Mutillidae, which is an intentionally vulnerable web application created by OWASP ([github.com](https://github.com/webpwnized/mutillidae)).

> Mutillidae contains pages with language that some may find offensive. If you are offended by bad language, please skip this activity.

To configure the browser to use Burp Suite as an interception proxy, complete the following steps.

> Recall that you cannot use the automatic Type Text feature with Linux virtual machines and that all commands and input in Linux are case-sensitive. Linux commands will be displayed by using the monospace font: hostname

1.  Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/13852b9f-a5cc-43e9-bf9f-e922efa46acf?rc=10#) VM. Log on with the credentials root and Paw0rd
    
2.  Open **Firefox ESR**.
    
3.  In the browser bar, enter about:preferences#advanced
    
4.  Scroll to the bottom of the configuration page, and then, under _Network Settings_, select the **Settings** button.
    
5.  Select the **Manual proxy configuration** radio button.
    
6.  In the HTTP Proxy box, type 127.0.0.1
    
7.  In the Port box, type 8080
    
8.  Check the **Use this proxy server for all protocols** box.
    
    Network settings![Network settings](https://labondemand.blob.core.windows.net/content/lab84056/Screen%20Shot%202020-11-08%20at%209.30.30%20AM.png)
    
9.  Select **OK**.
    
10.  Minimize Firefox.





## Run interception proxy

Start Burp Suite and configure the proxy to intercept requests.

1.  Open the **burpsuite** desktop shortcut.
    
2.  Accept the license, and then select **Next** through the rest of the setup wizard to use the default settings. Do not be concerned with any warnings about Burp Suite being out of date - select **OK**.
    
3.  With the temporary project open, select the **Proxy** tab, and ensure that the **Intercept is on** button is active. (If it says Intercept is on it's ACTIVE)
    
4.  Arrange the Firefox and Burp Suite windows so that you can use them both together easily.
    
5.  In the browser address bar, enter the following URL, taking care to type the address correctly:
    
    ```nocopy-nocode
    http://10.1.0.10/mutillidae/?page=add-to-your-blog.php
    ```
    
    The web page will not load. This is expected, because Burp Suite is intercepting the browser request.
    
    Note the page's file extension. PHP (PHP Hypertext Preprocessor) is a scripting language widely used to create web applications.
    
6.  In Burp Suite, note the content of what the browser is sending to the server—a simple page request along with some information about itself. Select the **Forward** button.
    
7.  Note that the browser has made another request (for a JPEG icon). Select the **Forward** button to let this through, too.
    
8.  In the browser, type a message into the box then select the **Save Blog Entry** button. Note that, again, nothing will happen.
    
9.  In Burp Suite, analyze the contents of the new request. This is a POST request (compared to the previous GET) and contains the text you typed plus the control used. Note that the application has also set a session cookie. Select the **Forward** button.
    
10.  In the browser, observe that the message you typed is posted to the blog entries table.
    
11.  In Burp Suite, select the **Intercept is On** button to switch it off.


## Test injection vulnerability

If you want to probe this site for injection vulnerabilities, a basic test is to try to use some JavaScript to show an alert.

1.  In Burp Suite, select the **HTTP history** tab. Locate the **POST** record then right-click it and select **Send to Repeater**.
    
2.  Select the **Repeater** tab. In the Request panel, select the **Params** tab.
    
3.  In the **blog_entry** box, add the following code to whatever you typed then press **ENTER**:
    
    ```nocopy-nocode
    <script>alert ("Gotcha!")</script>
    ```
    
    The alert![alert](https://labondemand.blob.core.windows.net/content/lab84056/Screen%20Shot%202020-11-08%20at%209.37.42%20AM.png)
    
4.  Right-click the **blog_entry** line and select **Request in browser > In original session**. Select the **Copy** button.
    
5.  Switch to the browser and paste the copied URL into the address bar. Press **ENTER**.
    
    The _Gotcha!_ alert is displayed.
    
    The Gotcha! alert![Gotcha](https://labondemand.blob.core.windows.net/content/lab84056/Screen%20Shot%202020-11-08%20at%209.40.27%20AM.png)
    
    The _Gotcha!_ alert appears when a user visits the page. This is an example of a Cross Site Scripting attack (XSS) where the the site allows messages posted as blog entries to execute embedded scripts.
    
6.  Select **OK** to close the alert.
    
7.  Scroll down the web page and note the duplicate blog entry that was created when you reran the request in Burp Suite.
    
8.  Return to Burp Suite, right-click the **blog_entry** again, and then select **Save Item**. Save the entry with the script to the /root directory as a file named script.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
9.  Confirm that the /root/script file exists.
    
    Script file

## Test URL interception vulnerability

In this task, you will intercept a mock email password reset attempt. Imagine a user has submitted a password reset form for the email account _jan@515web.net_. The reset mechanism submits the user's alternative email address (_jsmith@email.foo_) as a parameter in the URL.

1.  If necessary, select **Firefox**.
    
2.  Enter the following URL to generate a simulated password reset request for a user named Jan Smith, and then press **ENTER**:
    
    ```nocopy-nocode
    http://pwd-reset.515web.net/resetpassword.php?username=janh&altemail=jsmith%40email.foo
    ```
    
    The URL contains a reset request to be sent to jsmith@email.foo for jan@515web.net.
    
    The page does not load. This is expected as we are not actually simulating the reset site in this example.
    
3.  In Burp Suite, select the **Proxy** tab, and then select the **HTTP history** tab.
    
4.  Locate the **GET** record that corresponds to the email reset attempt (it is probably the final entry at the bottom of the list).
    
5.  Right-click the **GET** record and then select **Send to Repeater**.
    
6.  Select the **Repeater** tab. In the Request panel, select the **Params** tab.
    
7.  In the **altemail** _Value_ field, replace the existing address with mal%40evil.foo and then press **ENTER**.
    
    Changing the destination email![change the email](https://labondemand.blob.core.windows.net/content/lab84056/Screen%20Shot%202020-11-08%20at%209.46.21%20AM.png)
    
8.  Right-click the **altemail** line and select **Request in browser > In original session**. Select the **Copy** button.
    
9.  Switch to Firefox and paste the copied URL into the address bar. Press **ENTER**.
    
    The page will fail to load. The goal was to simulate how a password reset could be intercepted and modified by a man-in-the-middle or on-path attack.
    
10.  Return to Burp, select **Proxy**, and then select **HTTP history**.
    
11.  Display final host connection, select the **Params** tab, and use the information to answer the following question.
    
12.  What email Value is displayed for the altemail Name?
    
    jan@515web.net
    
    jan@email.foo
    
    mal@515web.net
    
    mal@evil.foo
    
    jsmith@515web.net
    
    jsmith@email.foo
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
13.  Right-click the line containing the Name altemail and the corresponding value. Select **Save Item**.
    
    Save the entry with the value to the /root directory as a file named altemail.
    
14.  Confirm that the /root/altemail file exists.
    
    Altemail file
    
    > Password reset utilities such as the one depicted in this scenario should not be designed in a way that lets client-side code or parameters be injected.



## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following answers best explains why the URL is vulnerable?
    
    It can be intercepted, edited, and forwarded on
    
2.   Which of the following answers best describes the process of the URL injection attack against Jan Smith's email password reset attempt?

	Attacker intercepted and edited the password reset URL, and then forwarded it on to the email service with changed information.