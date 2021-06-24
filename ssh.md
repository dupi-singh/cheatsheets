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

### Copy Folder from client to Cluster
```bash
scp -r path_to_local_file destination_path_with_username
```
e.g.
```bash
scp -r /Volumes/NPDF_DS/SWARM/MAGx_LR/SAT_A/MDR_MAG_LR/ dupinder@vikram-100.lan.prl.res.in:~/Data/SWARM//SAT_A/  
```

### List of modules installed on cluster
```bash
module avail
```

### Job submission
```bash
bsub -J jobname -oo outfile.%J -eo errorfile.%J myprog
```



