Krename: add prefix to images

  Renaming-lots-of-files asks: I am trying to add a prefix to a bunch of image
files. Is there a tool for doing this?

DistroWatch answers: Yes, there is. In fact, I am happy to report there are
several tools for renaming large groups of files. The Krename desktop
application is probably the easiest way to go. It has a wizard that walks you
through some questions about which files to operate on and how to change their
names. It even offers an undo function in case you mangle the new filenames.

You may also be able to use the command line rename program as follows:

rename 's/^/prefix-/' *.jp

he rename command uses regular expressions to adjust the names of files, or
parts of the names. The above instruction tells rename to substitute (s) the
beginning of each name (^) with the word "prefix-". This will be done to all
JPEG files (*.jpg). In other words, a file called 1.jpg would be renamed to
prefix-1.jpg. The HowtoForge website has some simple examples showing how to get
started with the rename command.

Another alternative is to use built-in shell features. Each command line shell
offers the ability to rename groups of files too, though the syntax is a little
tricky. In Bash, the following example would use a for loop to rename all of the
JPEG files in a directory, adding the word "prefix-" to the start of each
filename. It builds a new filename ($newname) out of the original filename
($myfile) and then uses the move (mv) command to perform the name change.

for myfile in *.jpeg ; do $newname="prefix-$myfile"; mv "$myfile" "$newname"; done

For most people, I suggest starting with Krename, or a similar utility like
Xfce's Bulk Rename program as they offer relatively easy point-n-click
interfaces.
