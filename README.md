# /cache

## Purpose

`/cache` contains Operating System managed, variable, binary data;
symbolic link farms and state.

It must be available during early boot to be used by init.

It should reside on the root filesystem or be mounted from the initrd.

It is assumed to be mounted read-write. It can be mounted read-only,
but then it must be available for read-write during application of
configuration updates and system updates.

It is not guaranteed to be shareable, but it can be, if the
configuration of the shared systems is compatible.

In particular, this directory attempts to clean up existing abuse of
`/etc`. The intention is to keep `/etc` for only human readable and
human modifiable configuration, additions and overrides. And move all
cached and generated data out of the way. This should provide a
clearer separation of the Operating System provided defaults (`/lib`
and `/usr`), versus system administrator changes (`/etc`), versus the
combined state of the two (`/cache`). It also enables easier usage of
immutable, shared rootfs, and smaller `/etc`.

Applications may add directories to the top level of `/cache`, but not
individual files. Consultation with the
[FHS-discuss](https://lists.linuxfoundation.org/mailman/listinfo/fhs-discuss
"FHS discuss mailing list") mailing list is nonetheless advised, to
ensure cooperation across software providing or consuming similar
data.

## Requirements

There are no required directories in `/cache`.

`/cache` may contain directories, or symbolic links to directories.

`/cache` can also be empty, if none of the subsystems that use
`/cache` are installed or adopted its use.

Distributions may choose to optionally support and use `/cache` only in
certain configurations.

## Specific Options

The following directories, or symbolic links to directories, may be in
`/cache`, if the corresponding subsystem is installed and in-use:

| Directory   	     | Description
|---	             |---
| `/cache/apparmor`  | AppArmor LSM binary compiled profiles
| `/cache/certs`     | X.509 public CA certificates bundles
| `/cache/ldconfig`  | `ld.so` dynamic linker cache files
| `/cache/rcd`       | LSB `init.d` script symbolic link farms and dependencies
| `/cache/swap`      | Linux Swap files

## `/cache/apparmor`

See [`/cache/apparmor`](apparmor.md)

## `/cache/certs`

See [`/cache/certs`](certs.md)

## `/cache/ldconfig`

See [`/cache/ldconfig`](ldconfig.md)

## `/cache/rcd`

See [`/cache/rcd`](rcd.md)

## `/cache/swap`

See [`/cache/swap`](swap.md)
