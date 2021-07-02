# Most used OpenSSL Commands

A list of most used Openssl Commands

<!--- Ich bin davon genervt jedes mal nach einem openssl Befehl zu Suchen. Hier eine Sammlung der häufigsten verwendeten Befehle
- Alle getestet
- Bonus link zu OPENSSL Manual
- Input Feld hinzufügen
- Für jeden Befehl die Eingabe und Ausgabe Felder kommentieren
-->
<!-- vscode-markdown-toc -->
* 1. [Table of Content](#TableofContent)
* 2. [Information](#Information)
		* 2.1. [Get OpenSSL Version](#GetOpenSSLVersion)
* 3. [Generating](#Generating)
	* 3.1. [Blub](#Blub)
		* 3.1.1. [Generate new private key](#Generatenewprivatekey)
		* 3.1.2. [Generate encrypted private key with Password](#GenerateencryptedprivatekeywithPassword)
		* 3.1.3. [Generate the public key from private key](#Generatethepublickeyfromprivatekey)
		* 3.1.4. [Generate a Certificate Singning Request (CSR) for an existing private key](#GenerateaCertificateSingningRequestCSRforanexistingprivatekey)
		* 3.1.5. [Generate a Self-Signed Certificate](#GenerateaSelf-SignedCertificate)
		* 3.1.6. [Create a PKCS#12 (.p12, .pfx) container with private key and certificate](#CreateaPKCS12.p12.pfxcontainerwithprivatekeyandcertificate)
		* 3.1.7. [Create a PKCS#12 (.p12, .pfx) container private Key, certificate and CA certificate](#CreateaPKCS12.p12.pfxcontainerprivateKeycertificateandCAcertificate)
		* 3.1.8. [Create a PKCS#12 (.p12, .pfx) container only with private key](#CreateaPKCS12.p12.pfxcontaineronlywithprivatekey)
		* 3.1.9. [Create a PKCS#12 (.p12, .pfx) container only with certificates](#CreateaPKCS12.p12.pfxcontaineronlywithcertificates)
		* 3.1.10. [Remove password from a private key](#Removepasswordfromaprivatekey)
* 4. [Converting](#Converting)
		* 4.1. [Convert a DER Binary Format (.der, .cer) file to PEM (.crt, .pem, .cer)](#ConvertaDERBinaryFormat.der.cerfiletoPEM.crt.pem.cer)
		* 4.2. [Convert a PEM (.crt, .pem, .cer) file to DER (.der, .cer)](#ConvertaPEM.crt.pem.cerfiletoDER.der.cer)
		* 4.3. [Convert a PKCS#12 file (.pfx .p12) including the private key and certificate to PEM](#ConvertaPKCS12file.pfx.p12includingtheprivatekeyandcertificatetoPEM)
		* 4.4. [Convert public key](#Convertpublickey)
		* 4.5. [foo](#foo)
		* 4.6. [foo](#foo-1)
* 5. [Validating](#Validating)
		* 5.1. [foo](#foo-1)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

<!-- Input Template
#### foo

```shellscript
bar
```
*Input:*
```shellscript
bar
```

*Output:*

```shellscript
bar
```
!-->


##  1. <a name='TableofContent'></a>Table of Content





##  2. <a name='Information'></a>Information

####  2.1. <a name='GetOpenSSLVersion'></a> Get OpenSSL Version

```shellscript
openssl version
```

#### GET OCSP Adress from certificate

```shellscript
openssl x509 -noout -ocsp_uri -in github-com.crt
```
*Input:*
```shellscript
-----BEGIN CERTIFICATE-----
MIIFBjCCBK2gAwIBAgIQDovzdw2S0Zbwu2H5PEFmvjAKBggqhkjOPQQDAjBnMQsw
CQYDVQQGEwJVUzEXMBUGA1UEChMORGlnaUNlcnQsIEluYy4xPzA9BgNVBAMTNkRp
Z2lDZXJ0IEhpZ2ggQXNzdXJhbmNlIFRMUyBIeWJyaWQgRUNDIFNIQTI1NiAyMDIw
...
-----END CERTIFICATE-----
```

*Output:*

```shellscript
http://ocsp.digicert.com
```

##  3. <a name='Generating'></a>Generating

####  3.1.1. <a name='Generatenewprivatekey'></a> Generate new private key

```shellscript
openssl genrsa -out private-key.pem 4096
```

*Output:*

```shellscript
-----BEGIN RSA PRIVATE KEY-----
MIIJKQIBAAKCAgEAz07dxYumJ8ehkWiCwBX25QR89+sunjytiHokNph/CTb+JQ1H
LISO8UTuWBLHTPZzr9zJzav/VHOR0bYtktl7hxEw5xDxf+AjILbfuIl1/X9UHma0
A7N4aL5sOjJhP9WAWEr4nqIwkE2sch3yyP1yn8cZ9WUyJu1qKC+FAl9dfggrcqhR
tQtfMclMh6MjA6Fa1FMzAmvShNRlnqyogQlbTkW91EIxi1a6+RCH8ZBKOlNaQSdK
VuaTrZCzSnO8TMn2BahmTgArXNKCDzUptWKJ0Tr2IcTiNKkaxMeKsshW8x/3XfQk
ZcPvlZe7LgS+cFj/mzzS+qpOEhsdm1KhDTemm5nmv2xEXmBKun5XFIxo9u+2oOvZ
....
-----END RSA PRIVATE KEY-----
```


####  3.1.2. <a name='GenerateencryptedprivatekeywithPassword'></a> Generate encrypted private key with Password

```shellscript
openssl genrsa -aes256 -out private-key.pem 4096
```

*Output:*

```shellscript
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-256-CBC,EA6FFC06DA689C8EF13818E6CCA8F559

h+os980FwiK90m1bJjhxDEzcjvEWVB5nTipu3stS7F2fwqjbLWnI0o3ONy3oTUIi
aEGHD6Fyk5F7z+/FFIC96ALRRvG4WzQmuP7o2/VEaiY5Cak4fq3BwTvEE4bLkIti
XpqcZvV1Fq9puam0ULGkm2APIGIurUCJ/e2UafnXXbEuUhml6wOVpmGZoIaoU/a9
......
-----END RSA PRIVATE KEY-----
```

####  3.1.3. <a name='Generatethepublickeyfromprivatekey'></a>Generate the public key from private key

```shellscript
openssl rsa -in private-key.pem -pubout -outform PEM -out public-key.pem
```

*Output:*
```shellscript

-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAl58SlffmOQbx7xSnhvu0
V51Ov7nCkbFdVmqsPWB8aR7+uwqoFOGgOL9XdfAX65eANUas0jpQ8sB8nINFA5mI
Gf2WbKkS+1Jivp+GJ5eTXgDUQcG1A52AldycPCk5s2ZXezZnTlKg+yBi5U4SohXp
....
-----END PUBLIC KEY-----
```

####  3.1.4. <a name='GenerateaCertificateSingningRequestCSRforanexistingprivatekey'></a>Generate a Certificate Singning Request (CSR) for an existing private key

```shellscript
openssl req -out my-csr.csr -key private-key.pem -new
```

*Output:*

```shellscript
-----BEGIN CERTIFICATE REQUEST-----
MIIEhzCCAm8CAQAwQjELMAkGA1UEBhMCREUxFTATBgNVBAcMDERlZmF1bHQgQ2l0
eTEcMBoGA1UECgwTRGVmYXVsdCBDb21wYW55IEx0ZDCCAiIwDQYJKoZIhvcNAQEB
BQADggIPADCCAgoCggIBAM9O3cWLpifHoZFogsAV9uUEfPfrLp48rYh6JDaYfwk2
...
-----END CERTIFICATE REQUEST-----
```

####  3.1.5. <a name='GenerateaSelf-SignedCertificate'></a>Generate a Self-Signed Certificate

```shellscript
openssl req -new -x509 -key private-key.pem -out mycertificate.crt -days 365
```

*Output:*

```shellscript
-----BEGIN CERTIFICATE-----
MIIFhTCCA22gAwIBAgIUTZro+2uPIRzLw7J/2JcPyfVL7KQwDQYJKoZIhvcNAQEL
BQAwUjELMAkGA1UEBhMCREUxFTATBgNVBAcMDERlZmF1bHQgQ2l0eTEcMBoGA1UE
CgwTRGVmYXVsdCBDb21wYW55IEx0ZDEOMAwGA1UEAwwFSGVsbG8wHhcNMjEwNzAx
...
-----END CERTIFICATE-----
```

####  3.1.6. <a name='CreateaPKCS12.p12.pfxcontainerwithprivatekeyandcertificate'></a>Create a PKCS#12 (.p12, .pfx) container with private key and certificate
`-name`: is the alias of the certificate in .p12 file
```shellscript
openssl pkcs12 -export -name mycert -inkey private-key.pem -in mycertificate.crt -out mycontainer.p12
```

####  3.1.7. <a name='CreateaPKCS12.p12.pfxcontainerprivateKeycertificateandCAcertificate'></a>Create a PKCS#12 (.p12, .pfx) container private Key, certificate and CA certificate

`-name` is the alias of the certificate in .p12 file
`-certfile` filename of the CAFile which has signed the certificate. Be aware that the file must be in PEM Format and NOT DER. Check below for a command to convert from DER to PEM

```shellscript
openssl pkcs12 -export -name mycert -inkey clientCert-mtls-E2EBankSign.prv.key -in mycertificate.crt -certfile CAFile.pem.crt -out mycontainer.p12
```

####  3.1.8. <a name='CreateaPKCS12.p12.pfxcontaineronlywithprivatekey'></a>Create a PKCS#12 (.p12, .pfx) container only with private key

`-name`: is the alias of the certificate in .p12 file

`-nocerts`: no certificate is imported to the .p12 file

```shellscript
openssl pkcs12 -export -name mykey -nocerts -inkey private-key.pem -out mycontainer.p12
```

####  3.1.9. <a name='CreateaPKCS12.p12.pfxcontaineronlywithcertificates'></a>Create a PKCS#12 (.p12, .pfx) container only with certificates

`-name` is the alias of the certificate in .p12 file

`-nokeys` no private key is imported to the .p12 file

```shellscript
openssl pkcs12 -export  -name mycert -nokeys -in mycertificate.crt -out mycontainer.p12
```

####  3.1.10. <a name='Removepasswordfromaprivatekey'></a>Remove password from a private key

```shellscript
openssl rsa -in private-key.pem -out new-private-key.pem
```

##  4. <a name='Converting'></a>Converting

####  4.1. <a name='ConvertaDERBinaryFormat.der.cerfiletoPEM.crt.pem.cer'></a>Convert a DER Binary Format (.der, .cer) file to PEM (.crt, .pem, .cer)

```shellscript
openssl x509 -inform der -in certificate.der -out certificate.pem.crt
```

####  4.2. <a name='ConvertaPEM.crt.pem.cerfiletoDER.der.cer'></a>Convert a PEM (.crt, .pem, .cer) file to DER (.der, .cer)

```shellscript
openssl x509 -outform der -in certificate.pem.crt -out certificate.der 
```

*Output:*

```shellscript
-----BEGIN CERTIFICATE-----
MIIFhTCCA22gAwIBAgIUTZro+2uPIRzLw7J/2JcPyfVL7KQwDQYJKoZIhvcNAQEL
BQAwUjELMAkGA1UEBhMCREUxFTATBgNVBAcMDERlZmF1bHQgQ2l0eTEcMBoGA1UE
CgwTRGVmYXVsdCBDb21wYW55IEx0ZDEOMAwGA1UEAwwFSGVsbG8wHhcNMjEwNzAx
...
-----END CERTIFICATE-----
```

####  Convert a PKCS#12 file (.pfx .p12) including the private key and certificate to **encrypted** PEM
```shellscript
openssl pkcs12 -in mycontainer.p12 -out keyStore.pem
```

*Output:*

```shellscript
Bag Attributes
    friendlyName: mycert
    localKeyID: 32 FA B3 80 22 13 3D A3 9D 08 11 8A B2 7E 7A 9C 6D 0C DB 26
subject=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

issuer=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

-----BEGIN CERTIFICATE-----
MIIFazCCA1OgAwIBAgIURZdcNOt396gxUYEWeWS7NXGrGeswDQYJKoZIhvcNAQEL
BQAwRTELMAkGA1UEBhMCREUxEzARBgNVBAgMClNvbWUtU3RhdGUxITAfBgNVBAoM
GEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZDAeFw0yMTA3MDIxNDExMThaFw0yMjA3
...
-----END CERTIFICATE-----
Bag Attributes
    friendlyName: mycert
    localKeyID: 32 FA B3 80 22 13 3D A3 9D 08 11 8A B2 7E 7A 9C 6D 0C DB 26
Key Attributes: <No Attributes>
-----BEGIN ENCRYPTED PRIVATE KEY-----
MIIJnDBOBgkqhkiG9w0BBQ0wQTApBgkqhkiG9w0BBQwwHAQIllxy3lyvHUsCAggA
MAwGCCqGSIb3DQIJBQAwFAYIKoZIhvcNAwcECM9EzWTCWm0aBIIJSO9oB86osKEC
3pMP/L8wivg1531Vnz/t1WXWz3F6Ezs5q2j3IRVVep+h1ASQbG/5sXDqfQR1GkUj
...
-----END ENCRYPTED PRIVATE KEY-----
```

####  Convert a PKCS#12 file (.pfx .p12) including the private key and certificate to **unencrypted** PEM

```shellscript
openssl pkcs12 -in mycontainer.p12 -out keyStore.pem -nodes
```

*Output:*

```shellscript
Bag Attributes
    friendlyName: mycert
    localKeyID: 32 FA B3 80 22 13 3D A3 9D 08 11 8A B2 7E 7A 9C 6D 0C DB 26
subject=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

issuer=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

-----BEGIN CERTIFICATE-----
MIIFazCCA1OgAwIBAgIURZdcNOt396gxUYEWeWS7NXGrGeswDQYJKoZIhvcNAQEL
BQAwRTELMAkGA1UEBhMCREUxEzARBgNVBAgMClNvbWUtU3RhdGUxITAfBgNVBAoM
GEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZDAeFw0yMTA3MDIxNDExMThaFw0yMjA3
...
Bag Attributes
    friendlyName: mycert
    localKeyID: 32 FA B3 80 22 13 3D A3 9D 08 11 8A B2 7E 7A 9C 6D 0C DB 26
Key Attributes: <No Attributes>
-----BEGIN PRIVATE KEY-----
MIIJQwIBADANBgkqhkiG9w0BAQEFAASCCS0wggkpAgEAAoICAQCzRzFB1RuUCmrV
9jK7wUMvWxmFQjq7+MAjO+WFKimcMzyGhiT4NiE25jJP06L1iWS0cBqpKvtysXc+
ttSBXPHjkBQ+ak79mNlrfvzm9h7wsS7Uciny4DSUSylY/pYMqE3DvBjVMTyLC6zI
...
-----END PRIVATE KEY-----
```

####  Export only private key + client certificate (not CA certificates). from a PKCS#12 file (.pfx .p12) 

```shellscript
openssl pkcs12 -in mycontainer.p12 -clcerts -out file.pem -nodes
```

*Output:*

```shellscript
Bag Attributes
    friendlyName: mycert
    localKeyID: 32 FA B3 80 22 13 3D A3 9D 08 11 8A B2 7E 7A 9C 6D 0C DB 26
subject=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

issuer=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

-----BEGIN CERTIFICATE-----
MIIFazCCA1OgAwIBAgIURZdcNOt396gxUYEWeWS7NXGrGeswDQYJKoZIhvcNAQEL
BQAwRTELMAkGA1UEBhMCREUxEzARBgNVBAgMClNvbWUtU3RhdGUxITAfBgNVBAoM
GEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZDAeFw0yMTA3MDIxNDExMThaFw0yMjA3
...
Bag Attributes
    friendlyName: mycert
    localKeyID: 32 FA B3 80 22 13 3D A3 9D 08 11 8A B2 7E 7A 9C 6D 0C DB 26
Key Attributes: <No Attributes>
-----BEGIN PRIVATE KEY-----
MIIJQwIBADANBgkqhkiG9w0BAQEFAASCCS0wggkpAgEAAoICAQCzRzFB1RuUCmrV
9jK7wUMvWxmFQjq7+MAjO+WFKimcMzyGhiT4NiE25jJP06L1iWS0cBqpKvtysXc+
ttSBXPHjkBQ+ak79mNlrfvzm9h7wsS7Uciny4DSUSylY/pYMqE3DvBjVMTyLC6zI
...
-----END PRIVATE KEY-----
```

#### Export only client certificate from a PKCS#12 file (.pfx .p12) 

```shellscript
openssl pkcs12 -in mycontainer.p12 -nokeys -out file.pem -nodes
```

*Output:*

```shellscript
Bag Attributes
    friendlyName: mycert
    localKeyID: 32 FA B3 80 22 13 3D A3 9D 08 11 8A B2 7E 7A 9C 6D 0C DB 26
subject=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

issuer=C = DE, ST = Some-State, O = Internet Widgits Pty Ltd

-----BEGIN CERTIFICATE-----
MIIFazCCA1OgAwIBAgIURZdcNOt396gxUYEWeWS7NXGrGeswDQYJKoZIhvcNAQEL
BQAwRTELMAkGA1UEBhMCREUxEzARBgNVBAgMClNvbWUtU3RhdGUxITAfBgNVBAoM
GEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZDAeFw0yMTA3MDIxNDExMThaFw0yMjA3
...
```


##  5. <a name='Validating'></a>Validating
<!--
@TODO
- Validate CRT with CA certificate
- Validate CRT with OCSP request
- Validate CRT with CRL request
-->
#### Verify a Certificate Signing Request (CSR)

```shellscript
openssl req -text -verify -in my-csr.csr -noout
```

*Output:*

```shellscript
verify OK
Certificate Request:
    Data:
        Version: 1 (0x0)
        Subject: C = DE, ST = Some-State, O = Internet Widgits Pty Ltd
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                RSA Public-Key: (4096 bit)
                Modulus:
                    00:b3:47:31:41:d5:1b:94:0a:6a:d5:f6:32:bb:c1:
....
```

#### Verify a private key

```shellscript
openssl rsa -in private-key.pem -check -noout
```

*Output:*

```shellscript
RSA key ok
```

#### Verify a certificate

```shellscript
openssl x509 -in mycertificate.crt -text -noout
```

*Output:*

```shellscript
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            45:97:5c:34:eb:77:f7:a8:31:51:81:16:79:64:bb:35:71:ab:19:eb
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C = DE, ST = Some-State, O = Internet Widgits Pty Ltd
        Validity
            Not Before: Jul  2 14:11:18 2021 GMT
            Not After : Jul  2 14:11:18 2022 GMT
        Subject: C = DE, ST = Some-State, O = Internet Widgits Pty Ltd
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                RSA Public-Key: (4096 bit)
                Modulus:
                    00:b3:47:31:41:d5:1b:94:0a:6a:d5:f6:32:bb:c1:
...
```

#### Check a PKCS#12 (.pfx, .p12) file

```shellscript
openssl pkcs12 -info -in mycontainer.p12
```

*Output:*

```shellscript
MAC: sha1, Iteration 2048
MAC length: 20, salt length: 8
PKCS7 Encrypted data: pbeWithSHA1And40BitRC2-CBC, Iteration 2048
Certificate bag
PKCS7 Data
Shrouded Keybag: pbeWithSHA1And3-KeyTripleDES-CBC, Iteration 2048
```

#### Verify if private key / public key / certificate / certificate request matches

```shellscript
openssl rsa -noout -modulus -in private-key.pem | openssl md5       #MD5 of private key

openssl rsa -noout -modulus -pubin -in public-key.pem | openssl md5 #MD5 of public key

openssl x509 -noout -modulus -in mycertificate.crt | openssl md5    #MD5 of certificate

openssl req -noout -modulus -in my-csr.csr | openssl md5		    #MD5 of certificate signing request .csr

```

*Output:*

```shellscript
(stdin)= c0976d5a10463452c539ea2ff0c4c166

(stdin)= c0976d5a10463452c539ea2ff0c4c166

(stdin)= c0976d5a10463452c539ea2ff0c4c166

(stdin)= c0976d5a10463452c539ea2ff0c4c166
```

## TLS Checks

####  4.6. <a name='foo-1'></a>foo

```shellscript
openssl s_client -connect github.com:443
```

*Output:*

```shellscript
CONNECTED(00000003)
depth=2 C = US, O = DigiCert Inc, OU = www.digicert.com, CN = DigiCert High Assurance EV Root CA
verify return:1
depth=1 C = US, O = "DigiCert, Inc.", CN = DigiCert High Assurance TLS Hybrid ECC SHA256 2020 CA1
verify return:1
depth=0 C = US, ST = California, L = San Francisco, O = "GitHub, Inc.", CN = github.com
verify return:1
---
Certificate chain
 0 s:C = US, ST = California, L = San Francisco, O = "GitHub, Inc.", CN = github.com
   i:C = US, O = "DigiCert, Inc.", CN = DigiCert High Assurance TLS Hybrid ECC SHA256 2020 CA1
 1 s:C = US, O = "DigiCert, Inc.", CN = DigiCert High Assurance TLS Hybrid ECC SHA256 2020 CA1
   i:C = US, O = DigiCert Inc, OU = www.digicert.com, CN = DigiCert High Assurance EV Root CA
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBjCCBK2gAwIBAgIQDovzdw2S0Zbwu2H5PEFmvjAKBggqhkjOPQQDAjBnMQsw
CQYDVQQGEwJVUzEXMBUGA1UEChMORGlnaUNlcnQsIEluYy4xPzA9BgNVBAMTNkRp
Z2lDZXJ0IEhpZ2ggQXNzdXJhbmNlIFRMUyBIeWJyaWQgRUNDIFNIQTI1NiAyMDIw
...
-----END CERTIFICATE-----
subject=C = US, ST = California, L = San Francisco, O = "GitHub, Inc.", CN = github.com

issuer=C = US, O = "DigiCert, Inc.", CN = DigiCert High Assurance TLS Hybrid ECC SHA256 2020 CA1

---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: ECDSA
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2709 bytes and written 366 bytes
Verification: OK
---
New, TLSv1.3, Cipher is TLS_AES_128_GCM_SHA256
Server public key is 256 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_128_GCM_SHA256
    Session-ID: D2D63C36E461B88D457C4EEC6D28C7034B036883A95C6B3F16F90FAC3BB84348
    Session-ID-ctx:
    Resumption PSK: 7E5EFE2B4AFC07C8A6434159539BBD3F2A05F6465E2E2FF90012EFC80C9D9CE8
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 36 4f e4 40 76 15 d7 56-ab 28 10 4f 7d 52 77 72   6O.@v..V.(.O}Rwr
    0010 - 78 02 e8 cc 6c 60 3d ee-87 27 c3 c5 36 93 f9 da   x...l`=..'..6...

    Start Time: 1625237698
    Timeout   : 7200 (sec)
    Verify return code: 0 (ok)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_128_GCM_SHA256
    Session-ID: 47B48F9A66F777DE35CD6C350744C5F1A4505C0055D3193BA8E6FE37671F8E44
    Session-ID-ctx:
    Resumption PSK: D5F3EBBF7FDDB0FF3BE2C0110407B7E3165154729D06D5AFE6476B2CC70AECB5
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 8b 03 4b ce 8d 26 49 f1-0b 98 e8 01 28 88 90 bb   ..K..&I.....(...
    0010 - 71 42 85 b7 6c 64 8b 0f-a4 4f 6d da 3e 8d c5 e9   qB..ld...Om.>...

    Start Time: 1625237698
    Timeout   : 7200 (sec)
    Verify return code: 0 (ok)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
closed
```

####  Check TLS connection with custom Certificate Authority

```shellscript
openssl s_client -connect github.com:443 -CAfile CA.crt
```

####  Connect HTTPS Only with TLS 1, 1.1, 1.2, 1.3

```shellscript
openssl s_client -connect github.com:443 -tls1
openssl s_client -connect github.com:443 -tls1_1
openssl s_client -connect github.com:443 -tls1_2
openssl s_client -connect github.com:443 -tls1_3
```

####  Connect HTTPS in debug mode


```shellscript
openssl s_client -connect github.com:443 -tlsextdebug
```

####  4.10. <a name='foo-1'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
```

####  4.11. <a name='foo-1'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
```
