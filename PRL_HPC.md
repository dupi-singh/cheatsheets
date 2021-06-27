Interact with HPC Cluster at PRL using SSH and SCP
-------------------------------------------------


### Login to Cluster
```bash
ssh username@clusteraddress
```
e.g. 
```bash
ssh dupinder@vikram-100.lan.prl.res.in
```
Login with X11 forwarding (For running application with GUI)
```bash
ssh -X username@clusteraddress
```
For MAC, make sure to install XQuartz which include X11.
To test if X11 forwarding is working, try running the following:
```bash
xclock 
```
You can also try the following GUI applications
| Application | Use
|--|--|
| xeyes | Animated eyes that follow cursor
| gedit | Text editor
| nautilus | File browser
  
to know the display for current SSH session:
```bash
echo $DISPLAY
```

------------------------------------------------------------------------------------------


### SCP commands
Copy Folder from PC to Cluster
```bash
scp -r path_to_local_directory destination_path
```
e.g.
```bash
scp -r /Volumes/NPDF_DS/SWARM/MAGx_LR/SAT_A/MDR_MAG_LR/ dupinder@vikram-100.lan.prl.res.in:~/Data/SWARM//SAT_A/  
```
copy single file from PC to Cluster
```bash
scp path_to_local_file destination_path
```
------------------------------------------------------------------------------------------

### Module Commands
Command | Usage
|--|--|
| module avail | List of available modules on cluster
| module load module_name | Load a module 
| module add module_name | Add a particular version of software to your environment 
| module rm module_name | Remove a particular version of software from your environment
| module purge | Remove all software from your environment
| module switch modulev1 modulev2 | Switch between particular versions of software
| module show modulename | Display paths and other environment variables a module uses

------------------------------------------------------------------------------------------

### Paths and environment variable associated with a software
'module show' can be used to display the paths and environment variable associated with a software. Following example shows the paths and environment variable associated with default MATLAB on cluster
```bash
$ module show matlab-client
-------------------------------------------------------------------
/shared/modulefiles/toolkits/matlab-client:

module-whatis	 adds MATLAB to your environment variables 
prepend-path	 PATH /shared/matlab/r2019b-client/bin 
prepend-path	 LD_LIBRARY_PATH /shared/matlab/r2019b-client/runtime/glnxa64 
prepend-path	 LD_LIBRARY_PATH /shared/matlab/r2019b-client/bin/glnxa64 
prepend-path	 LD_LIBRARY_PATH /shared/matlab/r2019b-client/sys/os/glnxa64 
prepend-path	 LD_LIBRARY_PATH /shared/matlab/r2019b-client/sys/opengl/lib/glnxa64 
-------------------------------------------------------------------
```



### Submitting Jobs in batch mode using LSF 
Submit using bsub command line
```bash
bsub -J jobname -oo outfile.%J -eo errorfile.%J myprog
```
Submit using LSF Script
```bash
bsub < jobfile
```
where jobfile is a script containing the job instructions. An example of script for submitting a Parallel shared memory MATALAB job is as follows
```bash
#!/bin/sh
# LSF options to bsub - start with #BSUB
#BSUB -J jobname                    # job name (optional)
#BSUB -q hpc                        # queue (optional)
#BSUB -R "rusage[mem=2GB]"          # -- specify that we need 2GB of memory per core/slot -- 
#BSUB -B                            # -- Notify me by email when execution begins --
#BSUB -N                            # -- Notify me by email when execution ends   --
##BSUB -u your_email_address        # receive e-mail notifications on a non-default address
#BSUB -oo Output_%J.txt             # -- Output File --  (optional) %J suffix the job number with file name
#BSUB -eo Error_%J.txt              # -- Error File --   (optional) 
#BSUB -W 04:00                      # -- estimated wall clock time (execution time): hh:mm -- 
#BSUB -n 24                         # -- Number of cores requested -- 
#BSUB -R "span[hosts=1]"            # -- Specify the distribution of the cores: on a single node --
# -- end of LSF options -- 

# -- commands to execute -- 
# 
module load matlab_client
matlab -batch mfilename -logfile logfilename
```
Note that -batch option is used while calling MATALB. -batch is convenient than -r for the non-interactive jobs because 
1. implicitly sets up the -nosplash and -nodisplay options. For -r, these options have to be set explicitly.
2. removes the startup banner
3. ensures the MATLAB process exits (with an exit code) even if your statement throws an error

------------------------------------------------------------------------------------------

### Basic LSF Commands
| Command            | Description |
|---|---|
| bjobs | Shows a list of your running jobs |
| bjobs -l JOBID | Shows detailed information about your job (JOBID = job number) |
| bqueues | Shows a list of available queues including jobs and slots |
| bhosts | Displays hosts and their static and dynamic resources |
| bkill JOBID | Kill job specified with JOBID |
| bkill 0 | Kill all of your running jobs |
| lsload | Displays load information for hosts |
------------------------------------------------------------------------------------------

### Current status of Cluster
```bash
vikram-100-stat
```
------------------------------------------------------------------------------------------

### Populate .bashrc
It is a good idea to populate the $HOME/.bashrc with neccessary stuff that you have to do every time. Every time you log into the cluster or submit a job, the commands in your $HOME/.bashrc file will be executed. bashrc can be edited by directly exporting to it or using gedit:
```bash
gedit ~/.bashrc
```
Lets add the line to load matlab module
```bash
module load matlab-client
```
save file. Now every time you login into ssh, matlab module will be loaded into memory automatically. You can also set environment variables in bashrc for example add paths.

------------------------------------------------------------------------------------------


