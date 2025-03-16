---
{"dg-publish":true,"permalink":"/homelab/true-nas-scale-pool-migration/"}
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
*Step 13*. Sanity test the server and applications with new pool. 
*Step 14*. When satisfied, import the temp pool, then detach and select "DESTROY" to purge the drives.

(Research how to set up those drives as a backup - Maybe attach the 12TB to the Legion and do a remote backup and enable off-site)

---

Apps have been partially initialized on 'Brunhilda' pool but it is missing 
'Brunhilda/ix-applications/k3s/kubelet, 
Brunhilda/ix-applications/default_volumes, 
Brunhilda/ix-applications/catalogs, 
Brunhilda/ix-applications/releases, 
Brunhilda/ix-applications/k3s' datasets. 

Specify force to override this and let system re-initialize applications.

---
Apps have been partially initialized on 'Brunhilda' pool but it is missing 
'Brunhilda/ix-applications/releases, 
Brunhilda/ix-applications/catalogs, 
Brunhilda/ix-applications/default_volumes, 
Brunhilda/ix-applications/k3s, 
Brunhilda/ix-applications/k3s/kubelet' 

datasets.

---
List of Datasets to Move:

* Config
* HASS
* Lidarr
* Melissa
* Michael
* Melissa
* *Overseer*
* Prowlarr
* Radarr
* NextCloud
* Sonarr
* Scripts
* Tautulli

zfs send

---

*Converting a RAID0 to a RAID1 in Proxmox*
Oneway would be to install it in ZFS RAID 0 mode on the smaller disk first. Then once the system is up and running, follow the "Changing a failed bootable device" [procedure in the Proxmox VE Admin guide](https://pve.proxmox.com/pve-docs/pve-admin-guide.html#chapter_zfs)  
  
The only difference! Instead of `zpool replace`, you use the `zpool attach rpool <already installed disk> <new disk>`.  
  
You can get the list of the currently used disk with `zpool status`. When you attach the disk, choose it via the /dev/disk/by-id path. There it will also be exposed via the manufacturer, model and serial number. Having them in the ZFS status output can speed up the process of figuring out which disk has an issue a lot.  
  
In the end you should have a mirrored rpool and the bootloader on both disks, so the system will boot if one fails.