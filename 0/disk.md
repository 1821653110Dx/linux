# format a  dev to fat32 format and 1 partition in total
	sudo fdisk <dev>	// not partition !!!
		n
		p
		keep enter
		w
	mkfs.vfat -F 32 {partition}

> if reformat a dev, you need to del all old partitions first : d
> 
> if you just want to reformat a partition to fat32 format, use : mkfs.vfat -F 32 {partition}
> 
> if the dev itself(not partition) has a signature, do the cmd first, which will rm all signatures: sudo wipefs --all --force \<dev\>

# rename a partition
> make sure the partition unmounted first
## for ntfs ext2/3/4 exfat
    {cmd} {dev} {name}
    # cmd
    ## for NTFS = ntfsprogs  
    ## for ext2, ext3, ext4 = e2label  
    ## for exfat = exfatlabel  # makesure you've install exfat-utils
## for fat32
	sudo fatlabel /dev/sda1 “my_label”
	//OR//
	# makesure you've installed mtools
	mlabel -i {partition} ::{name}
	
# list partitions and the format of partitions
## mounted partitions
df -Th
## unformated partitions 
```bash
parted -l
# can also be used to find unformated disk
```
## all partitions
lsblk -f
## specified partition
file -s partition
# disk usage
## display the size of each file
du -a  --apparent-size
## display the total size
du -s  --apparent-size
## check the size of lv.0 directory
du -d 0 path --apparent-size 
	
# check io
## check io volume every 2 s
	iostat -d -m 2 
> -m means mb, if want kb, use -k
## check io processes
	iotop
# mount
## temporary
- non-root user
	- mount to defalut path
		- udiskctl mount -b /dev/\<partition>
	- mount to customed path
		- sudo mount /dev/\<partition> <mount_point> -o uid=<user's_uid>
> usually uid = 1000
>
> check the uid: id
- root
	- mount to defalut path
		- udiskctl mount -b /dev/\<partition>
	- mount to customed path
		- mount /dev/\<partition> <mount_point>
## pernanent
```bash
step1  
	check UUID of the specified disk:	blkid
	(check uid and gid = id user_name)
step2  
	vim /etc/fstab  
step3  
	UUID=\<UUID\> \<where to mount\> \<the format of the disk\> defaults 0 0  
	//or//  
	UUID=\<UUID\> \<where to mount\> \<the format of the disk\> defaults,utf8,uid=\<uid\>,gid=\<gid\> 0 0  
```

# umount
## non-disk
	gio mount -u mountpoint
	umount /dev/partition 
	umount  mountpoint
## disk 
	udiskctl unmount -b partition
# eject
## non-disk
	gio mount -e mountpoint
	eject partition
## disk
	udiskctl power-off -b partition 

# process
## identify the process using the dev
	fuser -m -v [dev]
## kill the process using the dev
- kill all without asking
	- fuser -km [dev]
- kill one by one with asking
	- fuser -m -k -i -v [dev]

# check errors of unmounted dev
	sudo fsck [dev]