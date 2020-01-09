# cccp0 - Multiple Context Bypass Droid

# Bypasses
```
URL Encoding                        %22
Double URL Encoding                 %2522
Escaping Characters                 \"
Native Javascript Encoding          \x22
UTF-8 Unicode Encoding              
UTF-16 Unicode Encoding
Cyrillic Language Unicode Encoding
Hex                                 22
Octal
HTML Entity Encoding                &quot;
CRLF %0D %0A Bypasses
RFC Misimplementation bypasses
Read the Manual Bypasses

Camel Casing Bypasses               (<SeLeCt>)
Using Comments as Spaces            (select/**/all/**/from)
Dynamic Query Execution             ( 'SEL'||'ECT') , CHAR(83)+CHAR(69)+CHAR(76) , HEX(0x53454c45435) )
Null Bytes Bypass                   (%00)
Nested Expressions Bypass           (<sel<select>ect>)
Truncation Bypass 
Custom Filter Bypasses              (%0ASYS, S%FFS, "SYS", <<FOO>>)
Non-Standard Entry Points Bypass    (Adding arbritrary parameter names to requests, headers fields)

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
