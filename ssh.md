Interact with Cluster using SSH and SCP
---------------------------------------


### Login to Cluster
'''ssh username@clusteraddress'''
e.g. 
'''ssh dupinder@vikram-100.lan.prl.res.in'''

### Copy Folder from client to Cluster
scp -r path_to_local_file destination_path_with_username
e.g. scp -r /Volumes/NPDF_DS/SWARM/MAGx_LR/SAT_A/MDR_MAG_LR/ dupinder@vikram-100.lan.prl.res.in:~/Data/SWARM//SAT_A/       

###List of modules installed on cluster
module avail

###Job submission



