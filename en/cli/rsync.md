
# Rsync

**Command:** `vagrant rsync`

This command forces a resync of any [rsync synced folders][synced-folders].

Note that if you change any settings within the rsync synced folders such as exclude paths, you'll need to `vagrant reload` before this command will pick up those changes.

[synced-folders]: https://docs.vagrantup.com/v2/synced-folders/rsync.html