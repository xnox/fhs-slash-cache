## `/cache/rcd`

The directory `/cache/rcd` should be used to store LSB `init.d`
scripts runlevel directories managed by `update-rc.d`.

This deprecates `/etc/rc*.d/` locations.

For backwards compatibility the deprecated directories can be replaced
with symlinks to `/cache/rc*.d/` directories instead.

Normally these directories are pure symlink farms. And for correct
integration with the update software, often enough, removing symlinks
is not a valid configuration override and instead symlinks have to be
renamed to `K` names instead.

By moving `/etc/rc*.d` under `/cache`, it is possible to achieve goals
of immutable rootfs and empty-`/etc`. For example, system default LSB
`init.d` scripts can now be shipped in `/lib/init.d` or
`/usr/libexec/init.d` making `/etc` empty. System administrator can
then supply additional `init.d` scripts, or overrides, in `/etc` which
would then be preffered over stock ones.
