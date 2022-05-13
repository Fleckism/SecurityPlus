Smart-card authentication means programming cryptographic information onto a card equipped with a secure processing chip. **The chip stores the user's** 
- digital certificate, the 
- private key associated with the certificate, and a 
- personal identification number (PIN) used to activate the card. 

For Kerberos authentication, smart-card logon works as follows: 

1.  The user presents the smart card to a reader and is prompted to enter a PIN.
2.  Inputting the correct PIN authorizes the smart card's cryptoprocessor to use its private key to create a Ticket Granting Ticket (TGT) request, which is transmitted to the authentication server (AS). 
3.  The AS is able to decrypt the request because it has a matching public key and trusts the user's certificate, either because it was issued by a local certification authority or by a third-party CA that is a trusted root CA.
4.  The AS responds with the TGT and Ticket Granting Service (TGS) session key.