#Attack is an deliberate unauthorized action on a system or asset.
- Attack can be classified as active and passive attack.
- An attack will have a motive and will follow a method when opportunity arise.

[[Attack surface]] is all the points at which a malicious [[threat actor]] could try to exploit a vulnerability. Potential **[[attack vector]]s**.

[[attack vector]] is the path that a [[threat actor]] uses to gain access to a secure system. In the majority of cases, gaining access means being able to run malicious code on the target.

-   **Direct access**—this is a type of physical or local attack. 
-   **Removable media**—the attacker conceals malware on a USB thumb drive or memory card.
-   [[Email]]—the attacker sends a malicious file attachment via email, or via any other communications system that allows attachments. The attacker needs to use social engineering techniques to persuade or trick the user into opening the attachment.
-   **Remote and wireless**—the attacker either ==obtains credentials== for a remote access or wireless connection to the network or <mark style="background: #FFB8EBA6;">cracks the security protocols used for authentication</mark> .
-   **Supply chain**—rather than attack the target directly, a [[threat actor]] may seek ways to infiltrate it via companies in its supply chain. <mark style="background: #FFB8EBA6;">aka smart thermostat, HVAC</mark> 
-   **Web and social media**—malware may be concealed in files attached to posts or presented as downloads. An attacker may also be able to compromise a site so that it automatically infects vulnerable browser software (**a drive-by download**). Social media may also be used more subtly, to reinforce a social engineering campaign and drive the adoption of Trojans.
-   **Cloud**—many companies now run part or all of their network services via Internet-accessible clouds. **The attacker only needs to find one account, service, or host with weak credentials to gain access.** The attacker is likely to target the accounts used to develop services in the cloud or manage cloud systems. They may also try to attack the cloud service provider (CSP) as a way of accessing the victim system.
_________________________________________________
- **Network**
	- **Improper credential management** continues to be one of the most fruitful vectors for network attacks. 

Types of attacks
- [[DoS]] 
- [[MITM]]
- chosen ciphertext
- padding oracle
- downgrade attack
- brute force
	- horizontal 
	
		- ![[Pasted image 20220510102929.png]]
- dictionary attack
- birthday 
- Domain hijacking 
- DNS poisoning
- [[ARP]] poisoning
- [[REPLAY ATTACKS]]
- disassociation attack exploits the lack of encryption in management frame traffic to send spoofed frames.
- Covert channel:   A attack that subverts network security systems and policies to transfer data without authorization or detection

[[malware]] is a #tool that can be used in an attack



**A downgrade attack can be used to facilitate a man-in-the-middle attack by requesting that the server use a lower specification protocol with weaker ciphers and key lengths. For example, rather than use TLS 1.3, as the server might prefer, the client requests the use of SSL. It then becomes easier for Mallory to forge the signature of a certificate authority that Alice trusts and have Alice trust Mallory's public key.**

# Birthday attack
A <mark style="background: #FFB8EBA6;">birthday attack is a type of brute force attack aimed at exploiting collisions in hash functions</mark> . A collision is where a function produces the same hash value for two different plaintexts. This type of attack can be used for the purpose of forging a digital signature. 

A salt is an additional value stored with the hashed data field. The purpose of salt is to frustrate attempts to crack the hashes of passwords in this case. This will protect against birthday attacks.

Key stretching takes a key that is generated from a user password, and repeatedly converts it to a longer and more random key. The initial key is put through thousands of rounds of hashing to slow down attackers.

Securely authenticating public keys, such as associating the keys with certificates, helps protect against man-in-the-middle attacks.

Blockchain is a concept in which an expanding list of transactional records is secured using cryptography. Each record is referred to as a block and is run through a hash function.

# Downgrade attack
A downgrade attack can be used to facilitate a man-in-the-middle attack by requesting that the server use a lower specification protocol with weaker ciphers and key lengths, making it easier for a malicious actor to forge the trusted certificate authority’s signature.

Credential harvesting is a campaign specifically designed to steal account credentials.

Key stretching takes a key that is generated from a user password and repeatedly converts it to a longer and more random key, adding extra layers of processing to a potential attacker’s task.

Phishing is a combination of social engineering and spoofing. It persuades or tricks the target into interacting with a malicious resource disguised as a trusted one, traditionally using email as the vector.
# STRUCTURED QUERY LANGUAGE INJECTION ATTACKS

Attacks such as session replay, CSRF, and [[DOM]]-based [[XSS]] are [[client-side]] [[attack]]s. This means that they execute arbitrary code on the browser. A [[server-side attack]] causes the server to do some processing or run a script or query in a way that is not authorized by the application design. Most server-side attacks depend on some kind of injection attack.

**Where an overflow attack works against the way a process performs memory management**, an **injection attack exploits some unsecure way in which the application processes requests and queries**. For example, an application might allow a user to view his or her profile with a database query that should return the single record for that one user's profile. An application vulnerable to an injection attack might allow a [[threat actor]] to return the records for all users, or to change fields in the record when they are only supposed to be able to read them.

A web application is likely to use Structured Query Language ([[SQL]]) to read and write information from a database. The main database operations are performed by SQL statements for selecting data (SELECT), inserting data (INSERT), deleting data (DELETE), and updating data (UPDATE). In a SQL injection attack, the [[threat actor]] modifies one or more of these four basic functions by adding code to some input accepted by the app, causing it to execute the attacker's own set of SQL queries or parameters. If successful, this could allow the attacker to extract or insert information into the database or execute arbitrary code on the remote system using the same privileges as the database application

# Dump
[[5C Cryptographic Use Cases and Weaknesses]]

# Questions
1.  How are different attacks triggered?
2. **chosen ciphertext attack**
3. 