Renaming scripts

  ✅ RENAME BASH SCRIPT:

 1. Convert filenames to lowercase
 2. Replace underscores (_), hyphens (-), and dashes (– and —) with a space

--------------------------------------------------------------------------------


📜 BASH SCRIPT: RENAME_CLEAN.SH

#!/bin/bash

# Loop through all files in the current directory
for file in *; do
  # Skip if not a regular file
  [ -f "$file" ] || continue

  # Convert filename to lowercase and replace underscores/hyphens/dashes with space
  newname=$(echo "$file" | tr '[:upper:]' '[:lower:]' | sed 's/[_\-–—]/ /g')

  # Only rename if name actually changes
  if [[ "$file" != "$newname" ]]; then
    echo "Renaming: '$file' → '$newname'"
    mv -i -- "$file" "$newname"
  fi
done

--------------------------------------------------------------------------------


📌 HOW TO USE

 1. Save the script:
    
    nano rename_clean.sh
    
    Paste the script, save with CTRL+O, then CTRL+X.
 2. Make it executable:
    
    chmod +x rename_clean.sh

 3. Run it in a folder:
    
    ./rename_clean.sh

--------------------------------------------------------------------------------


📝 NOTES:

 * It works only on regular files in the current directory.
 * It will not recurse into subdirectories.
 * It uses mv -i to prompt before overwriting files.
 * If your filenames contain special characters or spaces, this script handles
   them safely.

Would you like a version that processes subdirectories too?

--------------------------------------------------------------------------------


✅ RECURSIVE RENAME BASH SCRIPT:

Here’s an updated version of the `Rename Bash Script` that:

✅ Converts filenames (in all subdirectories) to lowercase
✅ Replaces underscores, hyphens, en-dashes (–), and em-dashes (—) with spaces
✅ Works recursively

--------------------------------------------------------------------------------


📜 RECURSIVE BASH SCRIPT: RENAME_CLEAN_RECURSIVE.SH

#!/bin/bash

# Function to rename a file
rename_file() {
  local filepath="$1"
  local dir=$(dirname "$filepath")
  local base=$(basename "$filepath")

  # Convert to lowercase and replace underscores/dashes with space
  local newbase=$(echo "$base" | tr '[:upper:]' '[:lower:]' | sed 's/[_\-–—]/ /g')
  local newpath="$dir/$newbase"

  # Only rename if different
  if [[ "$filepath" != "$newpath" ]]; then
    echo "Renaming: '$filepath' → '$newpath'"
    mv -i -- "$filepath" "$newpath"
  fi
}

export -f rename_file

# Use find to get all regular files (not directories) and process them
find . -type f -exec bash -c 'rename_file "$0"' {} \;

--------------------------------------------------------------------------------


📌 HOW TO USE:

 1. Save the script: replace nano with micro
    
    nano rename_clean_recursive.sh
    
    Paste the script, then save (CTRL+O, CTRL+X).
 2. Make it executable:
    
    chmod +x rename_clean_recursive.sh

 3. Run it from the top-level directory:
    
    ./rename_clean_recursive.sh

--------------------------------------------------------------------------------


🔒 SAFETY NOTES:

 * mv -i ensures you are prompted if there's a name conflict.
 * It will skip directories; only renames regular files.
 * Make sure filenames don’t collide when normalized (e.g., File_A.txt and
   file-a.txt → file a.txt could conflict).

--------------------------------------------------------------------------------

Would you like to also rename directories recursively with the same rules?

Perfect — here's a full recursive script that:


✅ RENAMES BOTH BASH SCRIPT:

 * All files
 * All directories

...so that:
 1. Names are lowercase
 2. Underscores, hyphens, en-dashes (–), and em-dashes (—) are replaced with
    spaces
 3. It works safely and recursively

--------------------------------------------------------------------------------


💡 WHY SPECIAL CARE FOR DIRECTORIES?

Directories need to be renamed after their contents are processed (bottom-up),
to avoid breaking paths. This script handles that.

--------------------------------------------------------------------------------


📜 FULL SCRIPT: RENAME_ALL_RECURSIVE.SH

#!/bin/bash

# Function to rename a file or directory
rename_path() {
  local oldpath="$1"
  local dir=$(dirname "$oldpath")
  local base=$(basename "$oldpath")

  # Convert to lowercase and replace special characters
  local newbase=$(echo "$base" | tr '[:upper:]' '[:lower:]' | sed 's/[_\-–—]/ /g')
  local newpath="$dir/$newbase"

  # Rename only if changed
  if [[ "$oldpath" != "$newpath" ]]; then
    echo "Renaming: '$oldpath' → '$newpath'"
    mv -i -- "$oldpath" "$newpath"
  fi
}

export -f rename_path

# 1. Rename files (top-down)
find . -type f -exec bash -c 'rename_path "$0"' {} \;

# 2. Rename directories (bottom-up to avoid path breakage)
find . -depth -type d -exec bash -c 'rename_path "$0"' {} \;


--------------------------------------------------------------------------------


🧪 EXAMPLE:

Given:

./My_Folder/Sub-Folder/File_NAME—Example.txt

It becomes:

./my folder/sub folder/file name example.txt

--------------------------------------------------------------------------------


📌 HOW TO USE:

 1. Save it:
    
    nano rename_all_recursive.sh

 2. Make it executable:
    
    chmod +x rename_all_recursive.sh

 3. Run in the directory you want to clean:
    
    ./rename_all_recursive.sh

--------------------------------------------------------------------------------


⚠️ CAUTION:

 * If multiple names collapse into the same final name (e.g., File_A.txt and
   file-a.txt), mv -i will prompt.
 * Backup first if you're doing this in important directories.

--------------------------------------------------------------------------------

Would you like this to support dry run mode (show what would happen without
renaming)?

--------------------------------------------------------------------------------


✅ RENAME RECURSIVE (DRY-RUN SUPPORT)

This version supports:
 * ✅ Renaming files and directories recursively
 * ✅ Lowercase conversion + replacing _, -, –, — with spaces
 * ✅ Dry-run mode: see what would be renamed without making changes

--------------------------------------------------------------------------------


🧾 USAGE

./rename_all_recursive.sh        # Real rename
./rename_all_recursive.sh --dry  # Dry run (just preview)

--------------------------------------------------------------------------------

#!/bin/bash

DRY_RUN=false

# Check for --dry argument
if [[ "$1" == "--dry" ]]; then
  DRY_RUN=true
  echo "🔍 Dry run enabled — no changes will be made."
  echo
fi

# Function to rename a file or directory
rename_path() {
  local oldpath="$1"
  local dir
  local base
  local newbase
  local newpath

  dir=$(dirname "$oldpath")
  base=$(basename "$oldpath")

  # Convert to lowercase and replace underscores/dashes with spaces
  newbase=$(echo "$base" | tr '[:upper:]' '[:lower:]' | sed 's/[_\-–—]/ /g')
  newpath="$dir/$newbase"

  if [[ "$oldpath" != "$newpath" ]]; then
    if $DRY_RUN; then
      echo "[Dry run] Would rename: '$oldpath' → '$newpath'"
    else
      echo "Renaming: '$oldpath' → '$newpath'"
      mv -i -- "$oldpath" "$newpath"
    fi
  fi
}

export -f rename_path
export DRY_RUN

# Step 1: Rename files (top-down)
find . -type f -exec bash -c 'rename_path "$0"' {} \;

# Step 2: Rename directories (bottom-up)
find . -depth -type d -exec bash -c 'rename_path "$0"' {} \;

--------------------------------------------------------------------------------


💡 TIPS

 * This script avoids breaking paths by renaming directories after their
   contents.
 * You can also use this in CI/CD scripts with --dry to log name problems
   without changing anything.
 * Works with complex filenames and deeply nested structures.

--------------------------------------------------------------------------------

Would you like an enhancement that logs all changes to a file for undo/reference
later?

