# cccp0 - Multiple Context Bypass Droid

# Bypasses
```
URL Encoding
URL Double Encoding
UTF-8 Unicode Encoding
UTF-16 Unicode Encoding
Cyrillic Language Unicode Encoding
Hex
Octal
HTML Entity Encoding
CRLF %0D %0A Bypasses
Read the Manual F*cK Bypasses
```

# Whats happening
```
1. We send a payload to the server with the crafted unicode characters which take CR/LF as the last byte and ecnode it in UTF-8. 
2. Server receives the request but does not detect any malicious characters
3. Server decodes the input and removes out-of-range characters.
4. The output then contains clean CR/LF characters.

Original form                    U+560A

Input Value(UTF-8 Encoded)       E5 98 8A

Decoded Value                    56 0A

Output Value                     56 0A  

```

# Cool Examples
```
CR/LF

Unicode CR/LF  -  (U+560A, %56%0a)
UTF-8 Unicode CR/LF - (%E5%98%8A , == U+560A, == %56%0A)

Payload
  Cookie: %E5%98%8A%E5%98%8DSet-Cookie:%20test
```







# References
```
blog.innerht.ml
```
