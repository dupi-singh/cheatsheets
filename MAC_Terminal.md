MAC Terminal Commands
------------------

### Files and directories

| Command | Usage
|--|--|
| ls | List files and folders in the current folder
| ls -l | List files and folders along with their attributes
| ls -lh | Human readable version of ls -l 

### Compilers and Xcode related
| Command | Usage
|--|--|
| gcc -version | Gives the gcc version and configuration executable in path
| xcode-select --install | Install command line tools and add the /usr/include folder. This folder includes all the header files. If in case you get any error like ‘stdio.h not found’, make sure that this folder exists. If this folder does not exist, reinstall the command line tools.
| xcode-select --print-path | Show xcode path
| Which gfortran | Show the gfortran path
| gfortran --version | Version of gfortran
| Open . | Open current folder in finder

### Text Files
| Command | Usage
|--|--|
cat filename | To print small text files
less filename | a pager to print long text files
less -FX filename | behave as cat on small files otherwise similar to 'less'

### Shell related
| Command | Usage
|--|--|
$0 | Current shell
$SHELL | Default shell
sudo purge | Purging cache memory
unset | Delete a variable in bash

### Tricks
Trick | Example
|--|--|
make aliases to include flags with commands | alias aliasname='less -FX'
Space around = | Not allowed in bash (A = 3 is invalid). Allowed in cs shell.
