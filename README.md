#Systems Integration
##Assignment 1 - Custom Shell
###Author: Rudolf B Suguitan - C13460538

##Introduction
Networking shell is developed for the purpose of having a custom shell
for particular users of a system. This shell has limited functionalities 
and options which restricts these users to do what they can normally do 
when using a normal shell like bash, the Ubuntu default shell. Users will 
not be able to use commands that are not in this custom shell.

This shell is developed using bash script. The script provides limited 
commands for the users and are run by using abbreviation. For example, 
when the user entered the custom shell command "ifc", the default shell
command "ifconfig" will be ran and the data will be display on the terminal.

##Installation
Installing this shell for a user is quite simple and can be done by following
the steps bellow:

**1 - Clone Repository**
- This is the most recommended way to install this custom shell and is done following the steps bellow:
	- Open terminal and enter command: sudo su
	- After entering your password, enter command: cd /
		- This will bring you to your main directory
		- Though, you can use your chosen directory for the repository
	- Then enter: git clone "https://github.com/RudolfBSuguitan/SystemsIntegration.git"
	- This repository will be cloned into the directory you are in.
	- This repository should contain a file named customShell which is the script for the custom shell
	- To update, go to the repo folder and enter the command: git pull
	- You must be logged in as root in order to update.

**2.1 - Creating Users**
- *If there are users avaible to set-up the custom shell, you can skip this step but 
look at the following step (2.2) to make sure you have the right configuration.	
- To create a new user, enter the following commands:
	- useradd -m username
		- e.g. useradd -m rv
		- Flag -m will create and set a home directory for the use and named as the user.
	- passwd username
		- e.g. passwd rv
		- This will create a password for that user.
- To switch user, enter the command: su username
	- e.g. su rv

**2.2 - User Shell Configuration**
- This step will change the default shell to custom shell of a user.
	- Enter command: usermod -s /DirectoryOfClone/SystemsIntegration/customShell username	
		- e.g. usermod -s /SystemsIntegration/customShell rv
		- This will configure your shell.
	- Alternatively, you can do this by accessing /etc/passwd using nano and as root.
	- Then, find the user and at the end of the line of that user, enter the direcotory as above.

##How It Works
- The custom shell is ran when the particular user logs in. To start, that user should enter the command
**how** which is similar to default **help** bash command. This will display all the commands (abbreviations)
and the description or what these commands does. Tails or flags information are also included.

- It is developed that when the user logs in, the current directory will automatically switch to that user's 
home directory. This way, that user will have no access to other user accounts that can be found in /home/ directory.

- When the user entered a command, the shell checks whether that command does or doesnt have a tail. If no tail 
is provided, it will go through the case statement to run that command or call a function to run that command. 
If the command contains tail(s), it will also go throught the case statement then call the fucntion which runs 
that command after checking for any errors.

- Users can log out of their system or the custom shell by entering the command: **close**. Then the user will
see a logging out message and what that user have done or accesed within its account will not be seen by other users.

- This shell also has error checking feature that displays warnings if what has been entered is unknown or
unrecognized by the shell.
