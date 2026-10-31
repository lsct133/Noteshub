Timeshift include / exclude files

  In Timeshift, a system restore tool for Linux, you can include or exclude
specific files or directories from backups (snapshots) using its GUI or by
editing configuration files.

--------------------------------------------------------------------------------


🔧 1. USING THE GUI (GRAPHICAL USER INTERFACE)


🪟 TO INCLUDE/EXCLUDE FILES OR DIRECTORIES:

 1. Open Timeshift (you may need root privileges).
 2. Click Settings (gear icon or from the menu).
 3. Go to the Filters or Users tab depending on what you want to exclude:

📁 FILTERS TAB (FOR SYSTEM FILES):

 * You’ll see a list of filters (like /home, /var, etc.).
 * Click Add to include or exclude a path.
 * Prefix rules with:
   * + to include
   * - to exclude
 * Example:
   * - /home/yourusername/Downloads → Excludes Downloads folder
   * + /etc/custom-config → Includes a custom config folder

👤 USERS TAB (FOR USER HOME DIRECTORIES):

 * You can select which user home directories are included in snapshots.
 * Toggle the checkbox for the user.
 * You can choose to exclude hidden files, non-hidden files, or both.

--------------------------------------------------------------------------------


📝 2. USING THE CONFIGURATION FILE

Edit the file:

/etc/timeshift.json

Or, for filters:

/etc/timeshift/filters.json

You can define include/exclude rules directly here.


EXAMPLE FILTER:

[
  {
    "exclude": true,
    "path": "/home/yourusername/Downloads"
  },
  {
    "exclude": false,
    "path": "/etc/custom-config"
  }
]


--------------------------------------------------------------------------------


📌 TIPS:

 * Timeshift is mainly designed to back up system files, not user data. It
   excludes /home by default unless you change that in settings.
 * If you want to back up user files, consider tools like Déjà Dup or rsync.