# cccp0 - Multiple Context Bypass Droid

# Bypasses
```
URL Encoding
Double URL Encoding
UTF-8 Unicode Encoding
UTF-16 Unicode Encoding
Cyrillic Language Unicode Encoding
Hex
Octal
HTML Entity Encoding
CRLF %0D %0A Bypasses
RFC Misimplementation bypasses
Read the Manual Bypasses

Camel Casing Bypasses
Using Comments as Spaces
Dynamic Query Execution ( 'SEL'||'ECT') , CHAR(83)+CHAR(69)+CHAR(76) , HEX(0x53454c45435) )
Null Bytes Bypass
Nested Expressions Bypass
Truncation Bypass

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

# Types of Input Filters
```
Block any of the following (Keywords, individual characters, whitespaces)
Modify the input to make it safe (Encoding, escaping  key chars, or stripping away offending items and processing as normal)
Create a whitelist of acceptable character ranges
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
https://www.youtube.com/watch?v=HhIEDWmQS3w
```
