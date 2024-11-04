# Assignment 2: Shell Scripting

## Project 1: Configuration Scripts

### Folder Contents

1. `package-install-script` bash script file
2. `symlink-setup-script` bash script file
3. `complete-setup-script` bash script file
4. `packages.txt` text file
5. Configuration files under the `bin/`, `config/`, and `home/` directories provided for the packages to be installed

### About Scripts

In the project 1 folder, you will find scripts that will help streamline the setup process for new systems:
1. The `package-install-script` will download the desired packages listed in the `packages.txt` file. In our example we will download the `kakoune` and `tmux` packages.
* `kakoune` is a modal text editor for Linux that is inspired from Vim.
* `tmux` is a terminal multiplexer: it enables a number of terminals, each able to run a separate program which can be controlled and accessed from a single screen.
2. The `symlink-setup-script` ...
3. The `complete-setup-script` ...

### Requirements

>[!NOTE]
> The material and contents are written under and intended for the Arch Linux environment as it uses Arch Linux's distinguished package manager `pacman`.

You will need to download **all** contents in the project 1 folder. To run these scripts you will need to have `root` user access or have `sudo` user privileges.

## Project 2: New User Script