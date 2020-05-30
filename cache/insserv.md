## `/cache/insserv`

The directory `/cache/insserv` should be used to store LSB `init.d`
scripts dependency information.

#### Deprecated locations

| Deprecates           | Reason
|---                   |---
| `/etc/.depend.boot`  | Not a human editable configuration file
| `/etc/.depend.start` | Not a human editable configuration file
| `/etc/.depend.stop`  | Not a human editable configuration file

For backwards compatibility the deprecated files can be replaced with
symlinks to `/cache/insserv/depend.boot` and similar.
