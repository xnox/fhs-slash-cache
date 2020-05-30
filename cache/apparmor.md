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
