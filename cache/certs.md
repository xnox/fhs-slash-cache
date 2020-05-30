## `/cache/certs`

The directory `/cache/certs` should be used to store certificates
trusted by the operating system and the system administrator.

They certificates should be organised in sub-directories by format and
purpose.

The sub-directories may contain certificate bundles or symbolic links
to files in other locations.

For compatibility with previously used locations, symbolic links may be
added to provide bundles under previously used names.

Example sub-directories:

| Directory   	          | Description
|---	                  |---
| `/cache/certs/csca`     | Country Signing Certificate Authority (CSCA) public key certificates
| `/cache/certs/edk2`     | EDK2 file format
| `/cache/certs/java`     | Java KeyStore file
| `/cache/certs/openssl`  | OpenSSL `rehash` symbolic links or bundles
| `/cache/certs/smime`    | PEM format CA bundles for S/MIME communication
| `/cache/certs/tls`      | PEM format CA bundles for TLS communication
| `/cache/certs/tpm`      | TPM vendor root and intermediate certificates

For example, `/cache/certs/openssl` may contain by-hash symbolic links to
certificates in `/etc/` or `/usr`.

The intention is that system administrator can add and remove
certificates that are generated in `/cache` with configuration in
`/etc`. For example to add site-local Certificate Authority
certificates, or distrust public ones.

The structure of `/cache/certs/` directory and sub-directories should
be compatible to replace existing usage of similar directories such as
`/usr/lib/ssl/certs`, `/etc/ssl/certs`,
`/etc/pki/ca-trust/extracted`.

This layout is particularly of interest to systems with transactional
updates that desire immutable `/usr` and empty-`/etc` by default. Yet
want the system administrator to have the ability to distrust or add
additional certificates by creating configuration in `/etc`.
