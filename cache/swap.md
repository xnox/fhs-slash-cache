## `/cache/swap`

The directory `/cache/swap` may be used to store Linux Swap files.

If needed, filesystem specific tuning must be applied to this
directory. For example journaling, copy-on-write, striping, and
snapshotting can be disabled for this directory.

The directory `/cache/swap` might be empty, yet available for dynamic
creation of swapfiles. Instead of having large swapfiles during normal
operation, this directly can be used to dynamically create and grow
swapfiles during high memory preassure. Also this directory maybe used
to create a large hybernation file, if the system was requested to
hybernate dispite usually not requiring to do so. This directory gives
the flexibility to use differnt swapfiles, for different purposes, as
needed, without wasting the disk space all the time.

Now, `/cache` was mentioned that it can be mounted read-only, however
for Linux Swap files to work this directory needs to be read-write. If
read-only `/cache` is in use during initial boot, the init system can
be configured to remount `/cache/swap` read-write during bootup. This
has been done before for '/' and '/usr'. If `/cache/swap` remains
read-only, it will obviously be unusable for swapfiles.

This directory supperseeds simply using `/swapfile`, when possible.
