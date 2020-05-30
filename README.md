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

See [`/cache/apparmor`](cache/apparmor.md)

## `/cache/certs`

See [`/cache/certs`](cache/certs.md)

## `/cache/ldconfig`

See [`/cache/ldconfig`](cache/ldconfig.md)
