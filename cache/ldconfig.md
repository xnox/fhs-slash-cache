## `/cache/ldconfig`

The directory `/cache/ldconfig` should be used to store `ldconfig`
generated cache files.

#### Deprecated locations

| Deprecates                | Reason
|---                        |---
| `/etc/ld.so.cache`        | Not a human editable configuration file

The previous location `/etc/ld.so.cache` is now deprecated, and may be
replaced with a symbolic link to `/cache/ldconfig/ld.so.cache`.
