# /cache

## Purpose

`/cache` contains variable Operating System data files.

It must be available during early boot, at it can be used by
init. Thus it should reside on the root filesystem or be mounted from
the initrd.

It is assumed to be mounted read-write. It can be mounted read-only,
but then it must be available for read-write during application of
configuration updates or system updates.

It is not guaranteed to be sharable, but it can be, if the
configuration of the shared systems is compatible.

Applications may add directories to the top level of `/cache`, but not
individual files. Consultation with the
[FHS-discuss](https://lists.linuxfoundation.org/mailman/listinfo/fhs-discuss
"FHS discuss mailing list") mailing list is nonetheless advised, to
ensure cooperation across software providing or consuming similar
data.

## Requirements

There are no required directories in `/cache`. `/cache` may contain
directories, or symbolic links to directories. `/cache` can also be
empty, if none of the subsystems that use `/cache` are installed.

## Specific Options

The following directories, or symbolic links to directories, may be in
`/cache`, if the corresponding subsystem is installed and in-use:

| Directory   	     | Description
|---	             |---
| `/cache/apparmor`  | AppArmor LSM binary compiled profiles
| `/cache/certs`     | X.509 public CA certificates bundles
| `/cache/ldconfig`  | `ld.so` dynamic linker cache files
| `/cache/insserv`   | dependencies cache of LSB init.d scripts
| `/cache/swap`      | Linux Swap files

## `/cache/apparmor`

The directory `/cache/apparmor` should be used to store AppArmor
precompiled binary profiles.

The profiles are compiled from their textual representation, and
stored in subdirectories orgnazied by kernel features. The textual
representations are normally shipped in the directories under `/etc`
and `/usr`.

The directories `/etc/apparmor.d/cache.d` and `/var/cache/apparmor`
were previously used for this data and are now deprecated. For
backwards compatibility the deprecated directories may be replaced
with symbolic links to `/cache/apparmor`.

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
