## `/cache/certs`

The directory `/cache/certs` should be used to store certficates
trusted by the operating system and the system administrator.

They certficates should be organized in subdirectories by format and
purpose.

The subdirectories may contain certificate bundles or symbolic links
to files in other locations.

For compatibility with previously used locations, symlinks may be
added to provide bundles under previously used names.

Example subdirectories:

| Directory   	          | Description
|---	                  |---
| `/cache/certs/csca`     | Country Signing Certificate Authority (CSCA) public key certificates
| `/cache/certs/edk2`     | EDK2 file format
| `/cache/certs/java`     | Java KeyStore file
| `/cache/certs/openssl`  | OpenSSL `rehash` symlinks or bundles
| `/cache/certs/smime`    | PEM format CA bundles for S/MIME communication
| `/cache/certs/tls`      | PEM format CA bundles for TLS communication
| `/cache/certs/tpm`      | TPM vendor root and intermediate certificates

For example, `/cache/certs/openssl` may contain by-hash symlinks to
certificates in `/etc/` or `/usr`.

The intention is that system administrator can add and remove
certificates that are generated in `/cache` with configuration in
`/etc`. For example to add site-local Certificate Authority
certficates, or distrust public ones.

The structure of `/cache/certs/` directory and subdirectories should
be compatible to replace existing usage of similar directories such as
`/usr/lib/ssl/certs`, `/etc/ssl/certs`,
`/etc/pki/ca-trust/extracted`.

This layout is particularly of interest to systems with transactional
updates that desire immutable `/usr` and empty-`/etc` by default. Yet
want the system administrator to have the ability to distrust or add
additional certificates by creating configuration in `/etc`.
