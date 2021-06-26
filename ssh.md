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
Login with X forwarding
```bash
ssh -X username@clusteraddress
```
To test if X forwarding is working, try running the following
```bash
xclock 
```
or
```bash
xeyes
```


### Copy Folder from PC to Cluster
```bash
scp -r path_to_local_file destination_path_with_username
```
e.g.
```bash
scp -r /Volumes/NPDF_DS/SWARM/MAGx_LR/SAT_A/MDR_MAG_LR/ dupinder@vikram-100.lan.prl.res.in:~/Data/SWARM//SAT_A/  
```

### Module Commands
```bash
module avail                 # List of available modules on cluster
module load module_name      # Load a module 
```

### Job submission
```bash
bsub -J jobname -oo outfile.%J -eo errorfile.%J myprog
```

### Running a MATLAB job
---
Jobs are submitted using 'bsub' command. bsub submits the job to Load Sharing Facility (LSF) by running the specified command and its arguments. bsub syntax is as follows
```bash
bsub [options] command [arguments]
```
An example scrpt file to submit Parallel shared memory Job
```bash
#!/bin/sh
# LSF options to bsub - start with #BSUB
#BSUB -J jobname                    # job name (optional)
#BSUB -q hpc                        # queue (optional)
#BSUB -R "rusage[mem=2GB]"          # -- specify that we need 2GB of memory per core/slot -- 
#BSUB -B                            # -- Notify me by email when execution begins --
#BSUB -N                            # -- Notify me by email when execution ends   --
##BSUB -u your_email_address        # receive e-mail notifications on a non-default address
#BSUB -o Output_%J.txt              # -- Output File --  (optional)
#BSUB -e Error_%J.txt               # -- Error File --   (optional) 
#BSUB -W 04:00                      # -- estimated wall clock time (execution time): hh:mm -- 
#BSUB -n 24                         # -- Number of cores requested -- 
#BSUB -R "span[hosts=1]"            # -- Specify the distribution of the cores: on a single node --
# -- end of LSF options -- 

# -- commands to execute -- 
# 
# module load matlab/R2021a         # For specific version
matlab -nodisplay -r filename -logfile MySharedMatlabOut
```

### Basic LSF Commands
----
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




