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
5. Configuration files under the `bin/`, `config/`, and `home/` directories provided for the packages to be installed

### About Scripts

In the project 1 folder, you will find scripts that will help streamline the setup process for new systems:
1. The `package-install-script` will download the desired packages listed in the `packages.txt` file. This script will download the `kakoune` and `tmux` packages listed.
* `kakoune` is a modal text editor for Linux that is inspired from Vim. https://wiki.archlinux.org/title/Kakoune
* `tmux` is a terminal multiplexer: it enables a number of terminals, each able to run a separate program which can be controlled and accessed from a single screen. https://wiki.archlinux.org/title/Tmux

>[!TIP]
> If the user would like to download more scripts, they can use a text editor to edit the `packages.txt` file and append more package names separated by each line.

2. The `symlink-setup-script` will create symbolic links pointing from the provided configuration files located in `main_configs` to links created in your user home directory. For example, this script creates the `~/bin` directory and provides a symbolic link to files located in `/main_configs/bin`.
3. The `complete-setup-script` ...

### Requirements

To make use of the configuration scripts you will need:

* a Linux-based system running the Arch Linux distribution since the scripts are making use of the package manager `pacman`.
* internet connection to download packages and to prevent `pacman` from failing.
* to have `root` user access or have `sudo` user privileges with proper executable permissions in order to run the scripts
* the user must clone the whole repository and download **all** contents to their user home directory. For example, after cloning, the path to the project 1 directory should be: `~/acit2420-as2/project1`.

## Project 2: New User Script