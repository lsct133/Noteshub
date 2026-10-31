fstab backup June 9/25

  Location: /etc/fstab

Use 'blkid' to print the universally unique identifier for a device; this may be
used with UUID= as a more robust way to name devices that works even if disks
are added and removed. See fstab(5).

# &lt;file system&gt;             &lt;mount point&gt;  &lt;type&gt;  &lt;options&gt;  &lt;dump&gt;  &lt;pass&gt;
UUID=0BC3-E44F                            /boot/efi      vfat    defaults,umask=0077 0 2
UUID=2b18a072-d211-4d26-8401-374c096aa807 /home          ext4    defaults   0 2
UUID=2afbfe66-daf1-4113-b3fe-db5aa0b6007e /              ext4    defaults   0 1
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0

UUID=26dd3e5e-4ab7-46ab-8d1a-9bc6dbc67699 /mnt ext4 defaults,nofail,user,x-gvfs-show,noatime,nosuid,noexec 0 2

