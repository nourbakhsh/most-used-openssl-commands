# Most used OpenSSL Commands

A list of most used Openssl Commands

## Information

#### Get OpenSSL Version
`openssl version`

## Generating

#### Generate a new private key and public key

Generate private key:

```shellscript
$> openssl genrsa -out private-key.pem 4096
```

Generate encrypted private key with Password:
```shellscript
$> openssl genrsa -aes256 -out private-key.pem 4096`
```

Generate the corresponding public key:
```shellscript
$> openssl rsa -in private-key.pem -pubout -out public-key.pem`
```
#### Generate a new private key and CSR


## Converting


## Validating
openssl req -out CSR.csr -pubkey -new -keyout privateKey.key -config .shareopenssl.cmf