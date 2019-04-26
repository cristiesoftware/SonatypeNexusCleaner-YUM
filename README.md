# Sonatype Nexus - Old Package Remover (YUM Repositories)

This script removes old unused packages from yum repositories by reading the yum repo XML and comparing the file names.  

The reason we have to use the repo XML is because Nexus only returns the full path and stripping RPM names out of file names is risky.    

This will stop the ability of a yum downgrade but frees space on Nexus.  

You will need to "Compact" any blob stores affected to regain space.  

_Example_  

>Before Clean:  
>noarch/  
>noarch/testrpm-2.7-5984.noarch.rpm  
>noarch/testrpm-2.7-5985.noarch.rpm  
>noarch/testrpm-2.7-5986.noarch.rpm  
>
>python NexusYumCleaner.py  
>  
>Cleaning up alpha  
>Downloading Repo XML...  
>Writing Packages to list...  
>Comparing versions...  
>Querying the Nexus API...  
>Removing files...  
>noarch/testrpm-2.7-5984.noarch.rpm  
>Deleted! Status: 204  
>noarch/testrpm-2.7-5985.noarch.rpm  
>Deleted! Status: 204  
>
>After:  
>noarch/   
>noarch/testrpm-2.7-5986.noarch.rpm  
>

# !!!! CAUTION !!!!  
This script is destructive.  
Use at your own risk  
Author: RobWasley 25/09/2018
