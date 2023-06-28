# disk-partition-and-mounting
```
[ec2-user@ip-172-31-2-117 ~]$ sudo fdisk /dev/xvdf

Welcome to fdisk (util-linux 2.37.4).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0xe648821c.

Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1):
First sector (2048-209715199, default 2048):
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-209715199, default 209715199): +20G

Created a new partition 1 of type 'Linux' and of size 20 GiB.

Command (m for help): p
Disk /dev/xvdf: 100 GiB, 107374182400 bytes, 209715200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe648821c

Device     Boot Start      End  Sectors Size Id Type
/dev/xvdf1       2048 41945087 41943040  20G 83 Linux

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.
```
#### Check that it is created
```
 lsblk
NAME      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
xvda      202:0    0    8G  0 disk
├─xvda1   202:1    0    8G  0 part /
├─xvda127 259:0    0    1M  0 part
└─xvda128 259:1    0   10M  0 part
xvdf      202:80   0  100G  0 disk
└─xvdf1   202:81   0   20G  0 part
```
####  Create a directory
#### mount it 
```
sudo mount /dev/xvdf1 yannick/
[ec2-user@ip-172-31-2-117 ~]$ lsblk
NAME      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
xvda      202:0    0    8G  0 disk
├─xvda1   202:1    0    8G  0 part /
├─xvda127 259:0    0    1M  0 part
└─xvda128 259:1    0   10M  0 part
xvdf      202:80   0  100G  0 disk
└─xvdf1   202:81   0   20G  0 part /home/ec2-user/yannick
```
