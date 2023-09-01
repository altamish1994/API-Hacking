
### Brute Force
Check if application allows enumeration of users
Check if brute force is possible

FFuF
Add FUZZ to the parameter you want to fuzz

ffuf -request req.txt -request-proto http -w /path/to/wordlist -mc 200

-----------

### Authentication Token Strength

Send the response that give token to sequencer
Configure and highlight the token
Then start live capture
If the token is base64 encoded then in analysis option select base64 decode


-------------

JWT Tokens

Has three sections : Header, Payload and secret; all are base64 encoded
Can be identified in request with header Authorization Bearer

![[Pasted image 20230902025819.png]]

jwt.io Website to modify jwt tokens

Hashcat can  be used to crack jwt tokens

hashcat -a 0 -m 16500 jwt_token /path/to/rockyou --show

jwt_tool can be used to scan common jwt related issues

jwt_tool -t http://url_that/uses/token -rh 'Authorization: Bearer jwt_token' -M at

JWT Editor extention of burp can also be used to perform attacks