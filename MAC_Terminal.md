MAC Terminal Commands
------------------

### File Query

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
