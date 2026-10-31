Rclone webdav mount shadowdrive.sh

  #!/bin/bash

# Function to handle errors
error_exit() {
  echo "$1" 1&gt;&amp;2
  exit 1
}

# Log the start of the process
echo "Starting rclone mount..."

# Attempt to mount with error handling
rclone mount Shadow: ~/ShadowDrive --vfs-cache-mode writes &amp;

# Check if the rclone command was successful
if [ $? -ne 0 ]; then
  error_exit "rclone failed to start the mount."
fi

echo "rclone mount started successfully."
