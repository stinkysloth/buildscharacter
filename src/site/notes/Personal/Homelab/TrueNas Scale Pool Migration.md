---
{"dg-publish":true,"permalink":"/personal/homelab/true-nas-scale-pool-migration/"}
---


*Step 1*. Install new disks. 
*Step 2*. Create pool with desired RAID configuration. 
*Step 3*. Scrub primary pool. 
*Step 4*. Shut off all apps that are running. 
*Step 5*. Create a backup of server configuration. 
*Step 6*. Create a snapshot of the primary pool. Ensure 'recursive' is selected. 
*Step 7*. Execute a replication task from primary pool to temp pool. 
*Step 8*. Detach both pools from TrueNas. DO NOT CHOOSE TO DESTROY THE POOLS. 
*Step 9*. Via SSH, import and rename both pools. This will pull the pools back in with swapped names. 
	a. zpool import primary temp
	b. zpool import temp primary
*Step 10*. Via SSH, export the pools. 
	a. zpool export temp
	b. zpool export primary
*Step 11*. Using GUI, import the volume tab. 
*Step 12*. Restore configuration of shares from Step 5 server config backup. 
Step 13. Sanity test the server and applications with new pool. 
Step 14. When satisfied, import the temp pool, then detach and select "DESTROY" to purge the drives.

(Research how to set up those drives as a backup - Maybe attach the 12TB to the Legion and do a remote backup and enable off-site)