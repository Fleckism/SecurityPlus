---
tags: [Implementation]
---
# EXAM OBJECTIVES COVERED

2.3 Summarize secure application development, deployment, and automation concepts

3.2 Given a scenario, implement host or application security solutions

While you may not be taking on direct development duties on major projects, you will often be called upon to make updates to scripts, or make a quick judgment whether a script could be vulnerable and should be evaluated more closely for weaknesses. Being able to summarize secure coding practices will help you to work effectively as part of a [[DevSecOps]] team.
# SECURE CODING TECHNIQUES 

The security considerations for new programming technologies should be well understood and tested before deployment. One of the challenges of application development is that the pressure to release a solution often trumps any requirement to ensure that the application is secure. A legacy software design process might be heavily focused on highly visible elements, such as functionality, performance, and cost. Modern development practices use a security development life cycle running in parallel or integrated with the focus on software functionality and usability. Examples include Microsoft's SDL ([microsoft.com/en-us/securityengineering/sdl](https://www.microsoft.com/en-us/securityengineering/sdl)) and the [[OWASP]] Software Assurance Maturity Model ([owasp.org/www-project-samm](https://owasp.org/www-project-samm/)) and Security Knowledge Framework ([owasp.org/www-project-security-knowledge-framework](https://owasp.org/www-project-security-knowledge-framework/)). OWASP also collates descriptions of specific vulnerabilities, exploits, and mitigation techniques, such as the OWASP Top 10 ([owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/)).

**Some of the most important coding practices are input validation, output encoding, and error handling**.

### Input Validation

A primary vector for attacking applications is to exploit faulty input validation. Input could include user data entered into a form or URL passed by another application as a URL or HTTP header. Malicious input could be crafted to perform an overflow attack or some type of script or SQL injection attack. To mitigate this risk, all input methods should be documented with a view to reducing the potential attack surface exposed by the application. There must be routines to **check user input**, and anything that does not conform to what is required must be rejected.

### Normalization and Output Encoding

Where an application accepts string input, the input should be subjected to normalization procedures before being accepted. Normalization means that a string is stripped of illegal characters or substrings and converted to the accepted character set. This ensures that the string is in a format that can be processed correctly by the input validation routines.

When user-generated strings are passed through different contexts in a web application—between HTTP, JavaScript, PHP, and SQL for instance—each with potentially different [[canonicalization]] schemes, it is extremely difficult to ensure that characters that would facilitate script injection by [[XSS]] have been rendered safe. Output encoding means that the string is re-encoded safely for the context in which it is being used. For example, a web form might perform input validation at the client, but when it reaches the server, a PHP function performs **output encoding before composing an SQL statement**. Similarly, when a string is delivered from a database using SQL, a JavaScript function would perform output encoding to render the string using safe HTML entities ([cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)).
# SERVER-SIDE VERSUS CLIENT-SIDE VALIDATION

A web application (or any other client-server application) can be designed to perform code execution and input validation locally (on the client) or remotely (on the server). An example of client-side execution is a document object model ([[DOM]]) script to render the page using dynamic elements from user input. Applications may use both techniques for different functions. The main issue with **client-side validation** is that the client will always be **more vulnerable** to some sort of malware interfering with the validation process. The **main issue with server-side validation** is that it can be **time-consuming**, as it may involve multiple transactions between the server and client. Consequently, client-side validation is usually restricted to informing the user that there is some sort of problem with the input before submitting it to the server. Even after passing client-side validation, the input will still undergo server-side validation before it can be posted (accepted). Relying on client-side validation only is poor programming practice.
# WEB APPLICATION SECURITY

With web applications, special attention must be paid to secure cookies and options for HTTP response header security.

### Secure Cookies

Cookies can be a vector for session hijacking and data exposure if not configured correctly ([developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)). Some of the key parameters for the SetCookie header are:

-   Avoid using persistent cookies for session authentication. **Always use a new cookie** when the user reauthenticates.
-   **Set the Secure attribute** to prevent a cookie being sent over unencrypted HTTP.
-   **Set the HttpOnly** attribute to make the cookie inaccessible to document object model/client-side scripting.
-   **Use the SameSite** attribute to control from where a cookie may be sent, mitigating request forgery attacks.

### Response Headers 

A number of security options can be set in the response header **returned by the server to the client** ([owasp.org/www-project-secure-headers](https://owasp.org/www-project-secure-headers/)). While it should seem like a straightforward case of enabling all these, developers are often constrained by compatibility and implementation considerations between different client browser and server software types and versions. Some of the most important security-relevant header options are:

-   HTTP Strict Transport Security ([[HSTS]])—forces browser to connect using HTTPS only, mitigating downgrade attacks, such as SSL stripping.
-   Content Security Policy ([[CSP]])—mitigates clickjacking, script injection, and other client-side attacks. Note that X-Frame-Options and X-XSS-Protection provide mitigation for older browser versions, but are now deprecated in favor of CSP.
-   **Cache-Control**—sets whether the browser can cache responses. Preventing caching of data protects confidential and personal information where the client device might be shared by multiple users.
# DATA EXPOSURE AND MEMORY MANAGEMENT

Data exposure is a fault that allows privileged information (such as a token, password, or personal data) to be read without being subject to the appropriate access controls. Applications must only transmit such data between authenticated hosts, using cryptography to protect the session. When incorporating encryption in your code, it's important to use encryption algorithms and techniques that are known to be strong, rather than creating your own.

### Error Handling

A well-written application must be able to handle errors and exceptions gracefully. This means that the application performs in a controlled way when something unpredictable happens. An error or exception could be caused by invalid user input, a loss of network connectivity, another server or process failing, and so on. Ideally, the programmer will have written a structured exception handler ([[SEH]]) to dictate what the application should then do. Each procedure can have multiple exception handlers.

Some handlers will deal with anticipated errors and exceptions; there should also be a catchall handler that will deal with the unexpected. The main goal must be for the application not to fail in a way that allows the attacker to execute code or perform some sort of injection attack. One infamous example of a poorly written exception handler is the Apple GoTo bug ([nakedsecurity.sophos.com/2014/02/24/anatomy-of-a-goto-fail-apples-ssl-bug-explained-plus-an-unofficial-patch](https://nakedsecurity.sophos.com/2014/02/24/anatomy-of-a-goto-fail-apples-ssl-bug-explained-plus-an-unofficial-patch/)).

Another issue is that an application's interpreter may default to a standard handler and display default error messages when something goes wrong. These may reveal platform information and the inner workings of code to an attacker. It is better for an application to use **custom error handlers** so that the developer can choose the amount of information shown when an error is caused.

**Technically, an error is a condition that the process cannot recover from**, such as the system running out of memory. **An exception is a type of error that can be handled by a block of code without the process crashing.** Note that exceptions are still described as generating error codes/messages, however.

### Memory Management

**Many arbitrary code attacks depend on the target application having faulty memory management procedures.** This allows the attacker to execute his or her own code in the space marked out by the target application. **There are known unsecure practices for memory management that should be avoided and checks for processing untrusted input, such as strings, to ensure that it cannot overwrite areas of memory.**
# SECURE CODE USAGE

Developing code to perform some function is hard work, so developers will often look to see if someone else has done that work already. A program may make use of existing code in the following ways:

-   **Code reuse**—using a block of code from elsewhere in the same application or from another application to perform a different function (or perform the same function in a different context). The risk here is that the copy and paste approach causes the developer to overlook potential vulnerabilities (perhaps the function's input parameters are no longer validated in the new context).
-   **Third-party library**—using a **binary package** (such as a dynamic link library) that implements some sort of standard functionality, such as establishing a network connection or performing cryptography. Each library must be monitored for vulnerabilities and patched promptly.
-   **Software development kit** (SDK)—using sample code or libraries of pre-built functions from the programming environment used to create the software or interact with a third party API. As with other third party libraries or code, it is imperative to monitor for vulnerabilities.
-   **Stored procedures**—using a pre-built function to perform a database query. A stored procedure is a part of a database that executes a custom query. The procedure is supplied an input by the calling program and returns a predefined output for matched records. This can provide a more secure means of querying the database. Any stored procedures that are part of the database but not required by the application should be disabled.
# OTHER SECURE CODING PRACTICES

Input and error handling plus secure reuse of existing code cover some of the main security-related development practices that you should be aware of. There are a few other issues that can arise during the development and deployment of application code.

### Unreachable Code and Dead Code

Unreachable code is a part of application source code that can never be executed. For example, there may be a routine within a logic statement (If ... Then) that can never be called because the conditions that would call it can never be met. Dead code is executed but has no effect on the program flow. For example, there may be code to perform a calculation, but the result is never stored as a variable or used to evaluate a condition.

This type of code may be introduced through carelessly reused code, or when a block of code is rewritten or changed. Unreachable and dead code should be removed from the application to forestall the possibility that it could be misused in some way. The presence of unreachable/dead code can indicate that the application is not being well maintained.

### Obfuscation/Camouflage 

It is important that code be well-documented, to assist the efforts of multiple programmers working on the same project. **Well-documented code is also easier to analyze, however, which may assist the development of attack**s. Code can be made difficult to analyze by using an **obfuscator**, which is software that randomizes the names of variables, constants, functions, and procedures, removes comments and white space, and performs other operations to make the compiled code physically and mentally difficult to read and follow. This sort of technique might be used to make reverse engineering an application more difficult and as a way of disguising malware code.
# STATIC CODE ANALYSIS 

Development is only one stage in the software life cycle. A new release of an application or automation script should be audited to ensure that it meets the goals of [[confidentiality]], [[integrity]], and [[availability]] critical to any secure computer system.

Static code analysis (or source code analysis) is performed against the application code before it is packaged as an executable process. The analysis software must support the programming language used by the source code. The software will scan the source code for signatures of known issues, such as [[OWASP]] Top 10 Most Critical Web Application Security Risks or injection vulnerabilities generally. NIST maintains a list of source code analyzers and their key features ([samate.nist.gov/index.php/Source_Code_Security_Analyzers.html](https://samate.nist.gov/index.php/Source_Code_Security_Analyzers.html)).

Human analysis of software source code is described as a manual code review. It is important that the code be reviewed by developers (peers) other than the original coders to try to identify oversights, mistaken assumptions, or a lack of knowledge or experience. It is important to establish a collaborative environment in which reviews can take place effectively.
# DYNAMIC CODE ANALYSIS

Static code review techniques will not reveal vulnerabilities that might exist in the runtime environment, such as exposure to race conditions or unexpected user input. Dynamic analysis means that the application is tested under "real world" conditions using a staging environment.

**Fuzzing is a means of testing that an application's input validation routines work well.** Fuzzing means that the test or vulnerability scanner generates large amounts of deliberately invalid and/or random input and records the responses made by the application. This is a form of "stress testing" that can reveal how robust the application is. There are generally three types of fuzzers, representing different ways of injecting manipulated input into the application:

-   **Application** UI—identify input streams accepted by the application, such as input boxes, command line switches, or import/export functions.
-   **Protocol**—transmit manipulated packets to the application, perhaps using unexpected values in the headers or payload.
-   **File format**—attempt to open files whose format has been manipulated, perhaps manipulating specific features of the file.

Fuzzers are also distinguished by the way in which they craft each input (or test case). The fuzzer may use semi-random input (dumb fuzzer) or might craft specific input based around known exploit vectors, such as escaped command sequences or character literals, or by mutating intercepted inputs.

Associated with fuzzing is the concept of stress testing an application to see how an application performs under extreme performance or usage scenarios.

Finally, the fuzzer needs some means of detecting an application crash and recording which input sequence generated the crash. 

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3717-1599771809526.png)

Loading a list of strings for the payload of a fuzzing test in Burp Suite. (Screenshot Burp Suite [portswigger.net/burp](https://portswigger.net/burp).)
