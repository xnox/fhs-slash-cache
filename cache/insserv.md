## `/cache/insserv`
The directory `/cache/insserv` should be used to store LSB `init.d`
scripts dependency information.

#### Deprecated locations

For backwards compatibility the deprecated locations
`/etc/.depend.boot`, `/etc/.depend.start`, `/etc/.depend.stop` can be
replaced with symlinks to `/cache/insserv/depend.boot`,
`/cache/insserv/depend.start`, `/cache/insserv/depend.stop`.
