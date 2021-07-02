# Most used OpenSSL Commands

A list of most used Openssl Commands

- Ich bin davon genervt jedes mal nach einem openssl Befehl zu Suchen. Hier eine Sammlung der häufigsten verwendeten Befehle
- Alle getestet
- Bonus link zu OPENSSL Manual
- Input Feld hinzufügen
- Für jeden Befehl die Eingabe und Ausgabe Felder kommentieren

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

##  1. <a name='TableofContent'></a>Table of Content





##  2. <a name='Information'></a>Information

####  2.1. <a name='GetOpenSSLVersion'></a> Get OpenSSL Version

```shellscript
openssl version
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

####  4.3. <a name='ConvertaPKCS12file.pfx.p12includingtheprivatekeyandcertificatetoPEM'></a>Convert a PKCS#12 file (.pfx .p12) including the private key and certificate to PEM

```shellscript
openssl pkcs12 -in keyStore.p12 -out keyStore.pem -nodes
```

*Output:*

```shellscript
bar
```

####  4.4. <a name='Convertpublickey'></a>Convert public key

```shellscript
bar
```

*Output:*

```shellscript
bar
```

####  4.5. <a name='foo'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
```

####  4.6. <a name='foo-1'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
```

####  4.7. <a name='foo-1'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
```

####  4.8. <a name='foo-1'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
```

####  4.9. <a name='foo-1'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
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

##  5. <a name='Validating'></a>Validating
openssl req -out CSR.csr -pubkey -new -keyout privateKey.key -config .shareopenssl.cmf
@TODO
- Validate CSR with public key
- Validate CSR with private key
- Validate public Key with private key
- Validate CRT with private key
- Validate CRT with CA certificate
- Validate SSL settings
####  5.1. <a name='foo-1'></a>foo

```shellscript
bar
```

*Output:*

```shellscript
bar
```
