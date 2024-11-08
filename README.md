# Assignment 2: Shell Scripting

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
3. `complete-setup-script` bash script file
4. `packages.txt` text file
5. Configuration files under the `bin/`, `config/`, and `home/` directories provided for the packages

### About Scripts

In the project 1 folder, you will find scripts that will help streamline the setup process for new systems:
1. The `package-install-script` file will install the desired packages listed in the `packages.txt` file. This script will install the `kakoune` and `tmux` packages listed.
* `kakoune` is a modal text editor for Linux that is inspired from Vim. https://wiki.archlinux.org/title/Kakoune
* `tmux` is a terminal multiplexer: it enables a number of terminals, each able to run a separate program which can be controlled and accessed from a single screen. https://wiki.archlinux.org/title/Tmux

>[!TIP]
> If the user would like to download more scripts, they can use a text editor like `vim` or `nano` to edit the `packages.txt` file and append more package names separated by each line.

2. The `symlink-setup-script` file will create symbolic links pointing to the provided configuration files located in the `main_configs` directory from your user home directory. For example, this script creates the `/home/<user-name>/bin` directory and provides a symbolic link to files located in `/main_configs/bin`.

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

>[!CAUTION]
> Please refer to the documentation for the various dependencies and packages if you are unfamiliar with using them

### Usage and Examples

It is recommended to run **only** the `main-script` file to install packages and/or set up the symbolic links. The main script requires the user to run with `sudo` privileges or as `root` user because the script can install packages.

This is what the usage guide built into the `main-script` looks like that gives the valid options and syntax:
```bash
  Usage: sudo ./main-script -a | -p | -l | -h"
  Syntax: sudo ./main-script [OPTION]"
  Options:"
  -a, ALL | calls both package-install-script and symlink-setup-script"
  -p, PACKAGE | calls the package-install-script"
  -l, LINK | calls the symlink-setup-script"
  -h, HELP | show syntax and options for usage"
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
# Command to only run the file to create symbolic links
sudo ./main-script -l
```

```bash
# Command to view the usage guide and syntax
sudo ./main-script -h
```

## Project 2: New User Script