## `/cache/rcd`

The directory `/cache/rcd` should be used to store LSB `init.d`
scripts runlevel directories managed by `update-rc.d` as well as
`insserv` dependency information.

This deprecates `/etc/rc*.d/` and `/etc/.depend.*` locations.

For backwards compatibility the deprecated `/etc/rc*.d` directories
can be replaced with symbolic links to `/cache/rc*.d/` directories
instead. The deprecated `/etc/.depend.*` files can be replaced with
symbolic links, to non-hidden `/cache/depend.*` files.

Normally the `rc*.d` directories are pure symbolic link farms. And for
correct integration with the update software, often enough, removing
symbolic links is not a valid configuration override and instead
symbolic links have to be renamed to `K` names instead.

By moving `/etc/rc*.d` under `/cache`, it is possible to achieve goals
of immutable root filesystem and empty-`/etc`. For example, system
default LSB `init.d` scripts can now be shipped in `/lib/init.d` or
`/usr/libexec/init.d` making `/etc` empty. System administrator can
then supply additional `init.d` scripts, or overrides, in `/etc` which
would then be preferred over stock ones.

Whilst `/cache/rcd` can be recreated from the data in `/etc/init.d`,
`/lib/init.d`, `/usr/libexec/init.d`, it may loose some state. For
example, system administrator can use `update-rc.d` to manipulate
state in `/cache/rcd` to rename symbolic links to force disable or
force enable certain scripts, without storing this in the overridden
LSB headers in `/etc/init.d`. If ability to destroy and recreate
`/cache/rcd` is desired, changes to the default start and stop
runlevels should be encoded in the LSB header in `/etc/init.d` instead
of simply manipulating the symbolic link farm state.
