 Canonicalization refers to the way the server converts between the different methods by which a resource (such as a file path or URL) may be represented and submitted to the simplest (or canonical) method used by the server to process the input. Examples of encoding schemes include HTML entities and character set percent encoding (ASCII and Unicode). An attacker might be able to exploit [[vulnerability|vulnerabilities]] in the canonicalization process to perform code injection or facilitate directory traversal. For example, to perform a directory traversal attack, the attacker might submit a URL such as:

http://victim.foo/?show=../../../../etc/config

A limited input validation routine would prevent the use of the string ../ and refuse the request. If the attacker submitted the URL using the encoded version of the characters, he or she might be able to circumvent the validation routine: