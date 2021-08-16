1. Backup the partition table: `sfdisk -d /dev/sda > /partition_bak.dmp`
2. Adjust the ending of the partition, dry run: `growpart -N /dev/sda 3` ( / is /dev/sda3)
3. Really adjust it: `growpart /dev/sda 3`
4. Resize the filesystem (ext4 since kernel 2.6 supports online resizing): `resize2fs /dev/sda3` (by default expand it to boundary)
5. Force fsck at next reboot: `touch /forcefsck`
6. Done. Reboot is not usually necessary.
