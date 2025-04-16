---
toc: false
layout: post
comments: true
description: tls ssl certificate for HTTPS
categories: [markdown, tech]
title: TLS Certificate
---

## Introduction
TLS (Transport Layer Security) is a cryptographic protocol designed to provide secure communication over a computer network. It is widely used to secure web traffic, email, and other forms of data transmission. TLS is the successor to SSL (Secure Sockets Layer), and while the terms are often used interchangeably, TLS is the more modern and secure protocol.
TLS certificates are digital certificates that authenticate the identity of a website and enable an encrypted connection. They are issued by trusted Certificate Authorities (CAs) and contain information about the certificate holder, including the public key, the CA's digital signature, and the certificate's expiration date.

When a user connects to a website using HTTPS (HTTP over TLS), the server presents its TLS certificate to the user's browser. The browser verifies the certificate's authenticity and establishes a secure connection if the certificate is valid.
TLS certificates are essential for ensuring the security and privacy of online communications. They help protect sensitive information, such as login credentials, credit card numbers, and personal data, from eavesdropping and tampering by malicious actors.

## How to enable TLS certificate
1. **Choose a Certificate Authority (CA)**: Select a trusted CA to issue your TLS certificate. Some popular CAs include Let's Encrypt, DigiCert, and GlobalSign.
2. **Generate a Certificate Signing Request (CSR)**: Create a CSR on your server, which includes your public key and information about your organization. This request will be sent to the CA for validation.
3. **Submit the CSR to the CA**: Provide the CSR to the CA along with any required documentation to verify your identity and domain ownership.
4. **Receive and install the TLS certificate**: Once the CA validates your request, they will issue your TLS certificate. Install it on your server, along with any intermediate certificates provided by the CA.
5. **Configure your web server**: Update your web server configuration to use the new TLS certificate. This typically involves specifying the certificate file paths and enabling HTTPS.
6. **Test your configuration**: Use online tools like SSL Labs' SSL Test to check your server's TLS configuration and ensure that it is secure and properly set up.
7. **Renew your certificate**: TLS certificates have expiration dates, so be sure to renew them before they expire to maintain secure connections.


## Add/Renew TLS/SSL certificate

Files required for securing TLS/SSL cert:

1. private key
    1. a pem file `key.pem` starting with BEGIN PRIVATE KEY
2. cert file
    1.  a pem file `chain.pem` starting with BEGIN CERTIFICATE

## Adding TLS/SSL to website
```
  # NOTE: A signed cert must be supplied if an SSL server is used
  # At the very least, a self-signed cert is required.
  $ TLS_DIR=.certs
  $ sudo openssl req -x509 -sha256 -nodes -newkey rsa:2048 -keyout ${TLS_DIR}/key.pem -out ${TLS_DIR}/chain.pem
```

This will generate 2 files: 1 private key key.pem and a certificate chain.pem

* generate them and copy them to ./.cert 
* check docker-compose file
* docker compose -f docker-compose.prod.yml up

Open website, and you should be able to see self-signed HTTPS


### Authority signed TLS/SSL

Choose a CA Server

In order to get TLS/SSL cert issued by CA Server


We still need to provide 2 files: private key `key.pem` and cert file `chain.pem` to web server

Difference is: use chain.pem downloaded from  CA server instead of self-signed one

1. Use the self-generated key.pem 

2. Generate a CSR(Cert Request) from key.pem

* openssl req -new -key key.pem -out key.csr

3. Submit the CSR to CA server

4. Download chain.pem to replace local self-signed chain.pem

5. docker compose -f docker-compose.prod.yml up

