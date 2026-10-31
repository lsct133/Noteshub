Script to auto-run a cmd on login

  > I want this cmd restart xfce panel to run automatically 5 seconds after login.

You achieve this by creating a script and adding it to your session startup
applications.

Here’s how to do it:


STEP 1: CREATE A SCRIPT

 1. Open a terminal.
 2. Create a new script file. You can name it something like restart_panel.sh
    
    micro ~/restart_panel.sh

 3. Add the following lines to the script:
    
    #!/bin/bash
    sleep 5  # Wait for 5 seconds
    xfce4-panel -r
    
    This script will wait for 5 seconds after login and then run the command.
 4. Save the file and exit the editor
 5. Make the script executable:
    
    chmod +x ~/restart_pa
    
    You can also right click on the script and manually make it executable.Now
    move the script in a location of your choice.


STEP 2: ADD THE SCRIPT TO STARTUP APPLICATIONS

 1. Open the XFCE Settings Manager.
 2. Go to Session and Startup.
 3. Click on the Application Autostart tab.
 4. Click the Add button.
 5. Fill in the details:
    * Name: Restart XFCE Panel
    * Description: Runs xfce4-panel -r after login
    * Command: /location/of/script/your_username/restart_panel.sh (replace
      your_username with your actual username)
 6. Click OK to save.


STEP 3: TEST IT

Log out and log back in to see if the command runs automatically after a few
seconds.

This setup will ensure that the xfce4-panel -r command runs automatically a few
seconds after you log in to your XFCE session. Adjust the sleep duration in the
script if you need more or less time before the command executes.

