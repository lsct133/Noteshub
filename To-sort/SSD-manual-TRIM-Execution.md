SSD manual TRIM Execution

  Manual TRIM using these cmds.

# Trim a specific mount point
sudo fstrim -v /home
sudo fstrim -v /
# Trim all supported filesystems
sudo fstrim -av

