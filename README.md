# Assignment 2: Shell Scripting

# Table of Contents

1. [About Repository](#about-repository)
2. [Project 1: Configuration Scripts](#project-1-configuration-scripts)
    - [Folder Contents](#folder-contents)
    - [About Scripts](#about-scripts)
    - [Requirements](#requirements)
        - [Dependencies](#dependencies)
    - [Usage and Examples](#usage-and-examples)
3. [Project 2: New User Script](#project-2-new-user-script)
    - [Folder Contents](#folder-contents-1)
    - [About Script](#about-script)
    - [Requirements](#requirements-1)
    - [Usage and Examples](#usage-and-examples-1)
    - [Troubleshooting](#troubleshooting)


## About Repository

This repository holds 2 projects involving shell scripting which is an essential skill for software engineers and system administrators.

1. Configuration Scripts

This project (`project1`) holds several small scripts that help automate the installation of several essential packages as well as creating the symbolic links to provided configuration files. These scripts will help streamline and facilitate the initialization process of setting up for new systems and establish an efficient method to managing configuration files.

2. User Creation Script

This project (`project2`) holds a script that will automate the process of creating new users to a system. This script includes password setup, establishing preliminary group memberships, creating the user's home directory, and configuring the user's shell.

## Project 1: Configuration Scripts

### Folder Contents

1. `package-install-script` bash script file
2. `symlink-setup-script` bash script file
3. `main-script` bash script file
4. `packages.txt` text file
5. Configuration files under the `bin/`, `config/`, and `home/` directories provided for the packages

### About Scripts

In the project 1 folder, you will find scripts that will help streamline the setup process for new systems:
1. The `package-install-script` file will install the desired packages listed in the `packages.txt` file. This script will install the `kakoune` and `tmux` packages listed.
* `kakoune` is a modal text editor for Linux that is inspired from Vim.[^4]
* `tmux` is a terminal multiplexer: it enables a number of terminals, each able to run a separate program which can be controlled and accessed from a single screen. [^5]

>[!TIP]
> If the user would like to download more scripts, they can use a text editor like `vim` or `nano` to edit the `packages.txt` file and append more package names separated by each line.

2. The `symlink-setup-script` file will create symbolic links pointing to the provided configuration files located in the `main_configs` directory from your user home directory. A **symbolic link** is essentially a **shortcut**, it's a special kind of file that directs the system to look at the original file. For example, this script creates the `/home/<user-name>/bin` directory and provides a symbolic link to files located in `/main_configs/bin`.

3. The `main-script` file is the main script that can help run both the `package-install-script` and `symlink-setup-script` for a quicker installation process.

>[!NOTE]
> The `main-script` file has a usage guide and requires to be run with several options. Please refer to the usage guide built within the script for more information by running the script.

### Requirements

To make use of the configuration scripts you will need:

* a Linux-based system running the Arch Linux distribution since the scripts are making use of the package manager `pacman`.
* internet connection to download packages and to prevent `pacman` from failing.
* to have `root` user access or have `sudo` user privileges with proper executable permissions in order to run the scripts
* the user must clone the whole repository and download **all** contents to their user home directory. For example, after cloning, the path to the project 1 directory should be: `home/<username>/acit2420-as2/project1`.

>[!CAUTION]
> In order for the system setup to go smoothly, there should be **no changes** done to the file names of the scripts and directories as they are case-sensitive and hard coded into the scripts.

Copy and run the command below to clone this repository:
```bash
git clone https://github.com/jse-h/acit2420-as2.git
```

Keep in mind this will install both `project1` and `project2` directories.

* the scripts requires execute permissions.
Copy and run the command below to make the scripts in the project1 directory executable for users:
```bash
sudo chmod u+x ./main-script ./symlink-setup-script ./package-install-script
```

#### Dependencies

This project requires a few dependencies on top of the requirements.

* `fzf` is a general-purpose command fuzzy finder. The command `fzf` is used in the `bashrc` file located in the `/main_configs/home` directory that is part of our `symlink-setup-script` file
Copy and run the command below to install the `fzf` package:
```bash
sudo pacman -Syu fzf
```
* `vim`, `nvim`, or `nano` are popular text editors. You may want to use these text editors if you would like to add more packages to the `packages.txt` file.
The command below is an example how to install the `nvim` package:
```bash
sudo pacman -Syu neovim
```
* `git` is a distributed version control system that tracks versions of files. In our project, we will be mainly concerned of only using `git` to clone this repository to grab the necessary files.
Copy and run the command below to install the `git` package:
```bash
sudo pacman -Syu git
```

>[!CAUTION]
> Please refer to the documentation for the various dependencies and packages if you are unfamiliar with using them

### Usage and Examples

It is recommended to run **only** the `main-script` file to install packages and/or set up the symbolic links. The main script requires the user to run with `sudo` privileges or as `root` user because the script can install packages.

This is what the usage guide built into the `main-script` looks like that gives the valid options and syntax:
```
  Usage: sudo ./main-script -a | -p | -l | -h
  Syntax: sudo ./main-script [OPTION]
  Options:
  -a, ALL | calls both package-install-script and symlink-setup-script
  -p, PACKAGE | calls the package-install-script
  -l, LINK | calls the symlink-setup-script
  -h, HELP | show syntax and options for usage
```

Refer to the commands below for example usage of the script
```bash
# Command to run both package-install-script and symlink-setup-script files
sudo ./main-script -a
```

```bash
# Command to only run the package installer
sudo ./main-script -p
```

```bash
# Command to only run the symbolic link creator
sudo ./main-script -l
```

```bash
# Command to view the usage guide and syntax
sudo ./main-script -h
```

## Project 2: New User Script

### Folder Contents

In this project, there is one script file that helps create new users for your Linux system

1. The `create_user` script file

### About Script

The `create_user` script file creates new users and have options to allow them to add the user to new groups or existing groups. 

### Requirements

* The script must be run as root user or with sudo privileges
* An `/etc/skel` folder in your `/etc` directory to be copied and used as base files for your new user

### Usage and Examples

This is what the usage guide built into the `create_user` script looks like that gives the valid options and syntax:
```
Usage: create_user -u | -g | -h | -s | -i 
Syntax: create_user [OPTION...] [ARGUMENTS...]
 -u USERNAME,     specify the username desired of the new user
 -g GROUPS,       specify the new groups or existing groups to add to the user, 
                  can take a string of one or more groups

 -h HOME,         specify the path to the user's home directory
 -s SHELL,        specify the path to the user's shell
 -i INFO,         display the usage guide and syntax with options
```

>[!NOTE]
> The script does not ask the user to set a user id (`uid`) or group id (`gid`), instead it automatically assigns the next highest and unique `uid` and `gid` value.

Refer to the commands below for example usage of the script
```bash
# Command making a new user "John" using the -u, -g, and -i flags
sudo ./create_user -u "John" -g "group1" -i "Cloud User"
```

```bash
# Command making a new user "Jane" and adding them to multiple groups
# The script will make any new groups and add user to existing to groups
sudo ./create_user -u "John" -g "group1 group2 group3"
```

### Troubleshooting

The script has built-in error handling for if there are existing usernames or groups already exising in your Linux system.

This script will add an entry to the files below: 
* `/etc/passwd`, the user entry is appended that displays the username, user ID, group ID, user's home directory, and user's shell.
* `/etc/shadow`, the encrypted password file for the user is reflected in this file.
* `/etc/group`, new group entries is appended and displays the groupname and corresponding group ID

To successfully check that the user has been created you can view those files above that have been changed by using a text editor to view the file or using the `cat` command. [^3]

Copy and run the commands below to look at the various files:

```bash
# View contents of the passwd file
cat /etc/passwd
```

```bash
# View contents of the shadow file
sudo cat /etc/passwd
```

```bash
# View contents of the group file
cat /etc/group
```

When testing the script, you may want to delete certain test groups, users, and/or directories created.

After viewing the files you may use the `userdel`[^1] or `groupdel`[^2] utility that will help you remove test users and groups respectively.

Below are examples of using each utility:

```bash
# Requires root user or sudo privileges, this command removes the user john from the system.
sudo userdel -r john # The -r option removes john's home directory as well

# Note: This does not remove other files elsewhere owned by user 'john'
```

>[!NOTE]
> The `userdel` utility removes the user's entry from the `/etc/passwd` and `/etc/shadow` files.

```bash
# Requires root user or sudo privileges, this command deletes the group `group1`
sudo groupdel group1

# Note: This does not delete files owned by the group
```

[^1]: https://man7.org/linux/man-pages/man8/userdel.8.html
[^2]: https://man7.org/linux/man-pages/man8/groupdel.8.html
[^3]: https://man7.org/linux/man-pages/man1/cat.1.html
[^4]: https://wiki.archlinux.org/title/Kakoune
[^5]: https://wiki.archlinux.org/title/Tmux