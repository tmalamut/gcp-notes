# Secret Manager

### Definitions
* Stores API keys, passwords, certificates, and other sensitive data as binary blobs or text strings. With the appropriate permissions, you can view the contents of the secret.
* A key management system, such as Cloud KMS, allows you to manage cryptographic keys and to use them to encrypt or decrypt data. However, you cannot view, extract, or export the key material itself.
* A secret is a project-global object that contains a collection of metadata and secret versions. The metadata can include replication locations, labels, annotations, and permissions. The secret versions store the actual secret data, such as an API key or credential.
* A secret version stores the actual secret data, such as API keys, passwords, or certificates.
* You can rotate a secret by adding a new secret version to the secret.