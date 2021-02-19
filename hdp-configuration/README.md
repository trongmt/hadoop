Running the YARN Utility Script
=================

# This section describes how to use the yarn-utils-py script to calculate YARN, MapReduce, Hive, and Tez memory allocation settings based on the node hardware specifications. The yarn-utils-py script is included in the HDP companion files

# To run the yarn-utils-py script, execute the following command from the folder containing the script yarn-utils-py options, where options are as follows:

    Option 						Description
----------------------------------------------------------------------------
    -c CORES 		The number of cores on each host
	-m MEMORY 		The amount of memory on each host, in gigabytes
	-d DISKS 		The number of disks on each host
	-k HBASE 		"True" if HBase is installed; "False" if not

# Example:
	python yarn-utils.py -c 16 -m 64 -d 4 -k True

# Returns:

	Using cores=16 memory=64GB disks=4 hbase=True
	Profile: cores=16 memory=49152MB reserved=16GB usableMem=48GB disks=4 
	Num Container=8
	Container Ram=6144MB 
	Used Ram=48GB
	Unused Ram=16GB

	yarn.scheduler.minimum-allocation-mb=6144 
	yarn.scheduler.maximum-allocation-mb=49152 
	yarn.nodemanager.resource.memory-mb=49152 

	mapreduce.map.memory.mb=6144 
	mapreduce.map.java.opts=-Xmx4096m 
	mapreduce.reduce.memory.mb=6144 
	mapreduce.reduce.java.opts=-Xmx4096m
	mapreduce.task.io.sort.mb=1792

	yarn.app.mapreduce.am.resource.mb=6144 
	yarn.app.mapreduce.am.command-opts=-Xmx4096m

	tez.am.resource.memory.mb=6144 
	tez.am.launch.cmd-opts =-Xmx4096m

	hive.tez.container.size=6144 
	hive.tez.java.opts=-Xmx4096m

link: https://docs.cloudera.com/HDPDocuments/HDP2/HDP-2.5.6/bk_command-line-installation/content/determine-hdp-memory-config.html
