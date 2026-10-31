Time saving terminal tricks

  1. RUN PREV CMD WITH SUDO

We’ve all been there. You type a command, hit Enter, and get a “Permission
denied” message. You realize that you forgot to prefix it with sudo
[https://www.howtogeek.com/447906/how-to-control-sudo-access-on-linux/]. Instead
of retyping the whole thing, you can use a neat little trick:

sudo !!


This tells the shell to rerun your last command, but this time, with sudo. The
!! symbol is part of Bash history expansion. It expands to the entire previous
command. So, if your last command was apt update, typing !! would effectively
run apt update. And sudo !! becomes:

sudo apt update

![Using !! (double exclamation) with sudo to run the previous command with elevated privileges.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/using-double-exclamation-with-sudo-to-run-the-previous-command-with-elevated-privileges.png)

It’s a real time-saver, especially when you're deep into a workflow and forget
to elevate privileges.

2. RUN CMDS WITH NO HISTORY ENTRY

Here's an example of my command history.

![An example of running Linux commands that get saved in the history.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/an-example-of-running-linux-commands-that-get-saved-in-the-history.png)

Now, after running a command starting with a space, it won't get added to the
history.

![An example of using space before a command prevents it from being saved in history.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/an-example-of-using-space-before-a-command-prevents-it-from-being-saved-in-history.png)


As you can see, that last echo command
[https://www.howtogeek.com/446071/how-to-use-the-echo-command-on-linux/] is not
to be found. This trick relies on a Bash feature called HISTCONTROL. By default,
many systems have HISTCONTROL set to either ignorespace or ignoreboth. These
settings tell Bash to ignore commands that start with a space when writing
history.

Ever typed out a long file name, then needed to use it again in the next
command? Instead of copying and pasting (or retyping,) just hit Alt+period (.)
and it will insert the last argument from the previous command right where your
cursor is. It works in most Bash shells, and it’s especially handy for commands
that work on the same file or directory over and over.

For example, you might issue this command:

mkdir really_long_directory_name_with_underscores


Then you could type cd and hit Alt+. to change directories to the one you just
made.

Another common situation where you may use this is when you extract a archive
file and want to remove it. If you ran this command:

tar -xvf archive_name.tar.gz


You could just type rm and press Alt+. to delete the archive. You can press this
shortcut multiple times to cycle through previous arguments from earlier
commands.

[![Linux mascot on a desk next to a laptop.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2024/06/linux-mascot-on-a-desk-next-to-a-laptop.jpg)](https://www.howtogeek.com/types-of-linux-terminal-programs-do-you-know-them-all/)


Related

3. REPLACE WORD WITH ANOTHER IN PREVIOUS CMD

^wrong^right


This replaces the first occurrence of "wrong" in your previous command with
"right," and runs the updated command immediately. Let’s say you meant to ping
google.com, but typed ping goggle.com mistakenly. Just do:

^goggle^google


Bash will run:

ping google.com


![Replacing a word of the previous command with another one.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/replacing-a-word-of-the-previous-command-with-another-one.png)


This can be useful when you have a quick typo to fix, and it occurred only once.

4. SWAP CHARACTERS BEFORE AND AFTER CURSOR

If you're a fast typist, you've probably mashed the wrong keys and typed
something like:

sl


When you actually wanted to type:

ls


Yes, that’s such a common typo that there’s literally a command-line joke tool
[https://www.howtogeek.com/fun-linux-commands/] called sl that shows a train
chugging across your screen.

grpe file.txt


You meant grep. Just place the cursor on the p, hit Ctrl+T, and it becomes:

grep file.txt


It’s a tiny trick that feels minor until you catch yourself using it 20 times a
day.

5. USING ALIASES

Let’s face it. Some Linux commands are just long. And when you're running them
often, typing the same flags or full paths gets irritating. Not to mention
error-prone. That’s where aliases
[https://www.howtogeek.com/why-you-should-be-using-aliases-in-the-linux-terminal/]
come in. They allow you to create your own command shortcuts, using simple names
for more complex or frequently used commands.

Creating an alias is as simple as:

alias shortname=&amp;apos;actual command here&amp;apos;


Let’s say you’re always running:

ls -lah --color=auto


You can quickly create an alias like this:

alias ll=&amp;apos;ls -lah --color=auto&amp;apos;


![An example of using command aliases on Linux.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/an-example-of-using-command-aliases-on-linux.png)


6. FORMAT YOUR OUTPUT IN COLUMNS

On Linux, we often need to work with data in the command line. Sometimes, the
output can be quite messy. Luckily, we have the column command. It can turn that
chaos into clean, readable tables of data. The column command formats text into
neat columns, aligning things nicely based on whitespace or a custom delimiter.
It's perfect when you're dealing with data like lists, CSV, colon-separated
data, etc.

Let's see a common example. We can normally list the processes on Linux with:

ps aux


We can format it further using the column command:

ps aux | head -10 | column -t


![An example of using the column command to format Linux command output.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/an-example-of-using-the-column-command-to-format-linux-command-output.png)


7. RUN MULTI CMDS CONSECUTIVELY

Sometimes you want to run several commands back to back. Instead of typing them
one at a time and waiting, you can chain them together on a single line. Then,
control whether they run unconditionally or only if the previous one succeeds.

The semicolon (;) lets you chain commands so they run one after the other,
regardless of success or failure.

echo &amp;quot;Updating...&amp;quot; ; sudo apt update ; echo &amp;quot;Done!&amp;quot;


![Running multiple Linux commands seperated by semicolons.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/running-multiple-linux-commands-seperated-by-semicolons.png)


In this example, even if apt update fails, the final echo "Done!" still runs.

sudo apt update &amp;amp;&amp;amp; sudo apt upgrade


The command after &amp;&amp; will only run if the command before it runs
successfully. The opposite of &amp;&amp; is the || (two vertical bars) operator.
When two commands are combined using this symbol, the command on the right will
execute only if the command on the left fails. Using &amp;&amp; and || helps you
debug issues with your Bash scripts
[https://www.howtogeek.com/808593/bash-script-examples/].

[![A hand using a laptop and Linux mascot coming out of the screen with a gear and some files behind.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2024/07/a-hand-using-a-laptop-and-linux-mascot-coming-out-of-the-screen-with-a-gear-and-some-files-behind.jpg)](https://www.howtogeek.com/ways-to-configure-linux-command-line-tools/)


Related

5 WAYS TO MAKE LINUX CMDS WORK THE WAY YOU WANT
[https://www.howtogeek.com/ways-to-configure-linux-command-line-tools/]

You don't really know the full power of Linux until you can tweak your toolset.

8. GO TO PREV DIR YOU WERE IN

I often find myself jumping back and forth between two directories. Typing the
full path repeatedly is annoying. So this neat little trick was a lifesaver for
me:

cd -


This command sends you to the previous working directory, just like a back
button in your Linux file system
[https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/].
Let’s say you start in:

/home/user/projects/website


![Using the cd - command to jump between two directories.](https://static1.howtogeekimages.com/wordpress/wp-content/uploads/2025/05/using-the-cd-command-to-jump-between-two-directories.png)


#Aliases #Terminal