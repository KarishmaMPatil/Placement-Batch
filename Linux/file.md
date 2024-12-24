# Disk Partitioning and File Systems in Linux

## 1. What is a Partition?
A **partition** is a contiguous set of blocks on a drive, treated as an independent disk.

---

## 2. What is Partitioning?
**Partitioning** involves dividing a single hard drive into multiple logical drives.

---

## 3. Why Have Multiple Partitions?
- **Data Encapsulation:** Limits file system corruption to a single partition, protecting data.
- **Disk Space Efficiency:** Allows formatting with different block sizes, reducing disk wastage.
- **Data Growth Management:** Enables disk quotas to control and limit data growth.

---

## 4. Structure of a Disk Partition
- The first sector of the disk contains the **Master Boot Record (MBR)** (512 bytes).
  - **Initial Program Loader (IPL):** 446 bytes, contains the Secondary Boot Loader for booting the OS.
  - **Partition Table Information (PTI):** Stores details about the number, size, and types of partitions.

---

## 5. Disk Partition Criteria
- A disk can have a maximum of **4 partitions**:
  - **3 Primary Partitions**
  - **1 Extended Partition** (further divided into logical partitions).
- **Primary Partition:** Used for MBR and OS installation.
- **Extended Partition:** Allows creating additional logical partitions.

---

## 6. Disk Identification in Linux
Disks are identified using different naming conventions:
- **IDE Drives:** `/dev/hda`, `/dev/hdb`, `/dev/hdc`, etc. (Partitions: `/dev/hda1`, `/dev/hda2`, etc.)
- **iSCSI/SCSI/SATA Drives:** `/dev/sda`, `/dev/sdb`, `/dev/sdc`, etc. (Partitions: `/dev/sda1`, `/dev/sda2`, etc.)
- **Virtual Drives:** `/dev/vda`, `/dev/vdb`, `/dev/vdc`, etc. (Partitions: `/dev/vda1`, `/dev/vda2`, etc.)

### Abbreviations:
- **IDE:** Integrated Drive Electronics
- **SCSI:** Small Computer System Interface
- **iSCSI:** Internet Small Computer System Interface

---

## 7. What is a File System?
A **file system** organizes and stores data on the disk. Every partition (except MBR and Extended partitions) must have a file system assigned for data storage. File systems are applied by formatting the partition.

---

## 8. Types of File Systems in Linux
### Commonly Supported File Systems:
- **ext2**, **ext3**, **ext4:** Widely used in RHEL-6.
- **xfs:** Introduced in RHEL-7.
- **vfat:** Provides compatibility between Linux and Windows.
- **cdfs:** Used for mounting CD-ROMs.
- **hdfs:** Used for mounting DVDs.
- **iso9660:** Reads CD/DVD `.iso` image files.

# Disk Partitioning and File Systems in Linux

## 8. What are the different types of file systems supported in Linux?
The Linux-supported file systems are ext2, ext3, ext4, xfs, vfat, cdfs, hdfs, iso9660, etc.

- **ext2, ext3, ext4**: Widely used in RHEL-6.
- **xfs**: Introduced in RHEL-7.
- **vfat**: Maintains common storage between Linux and Windows.
- **cdfs**: Used to mount CD-ROMs.
- **hdfs**: Used to mount DVDs.
- **iso9660**: Reads CD/DVD `.iso` image format files in Linux.

## 9. What is mounting, and how many types of mounting are there?
Mounting refers to attaching a directory to the file system to access a partition and its file system. Generally, subdirectories under `/mnt` are the mount points. There are two types of mountings:

- **Temporary Mounting**:
  - Mount lasts only until the system is rebooted.
  - Example: `# mount <options> <device name> <directory name>`

- **Permanent Mounting**:
  - Requires an entry in `/etc/fstab` for persistence across reboots.
  - Example entry: `<device name> <mount point> <file system type> <mount options> <backup option> <fsck value>`
  - Example command: `# mount -a` (mount partitions without reboot).

## 10. Differences between ext2, ext3, ext4, and xfs file systems

| S.No. | Feature                       | ext2                       | ext3                      | ext4                      | xfs                      |
|-------|-------------------------------|----------------------------|---------------------------|---------------------------|--------------------------|
| 1     | Stands for                   | Second Extended File System | Third Extended File System | Fourth Extended File System | Extended File System    |
| 2     | Journaling Feature          | No                         | Yes                       | Yes                       | Yes                      |
| 3     | Max. File Size              | 16 GB to 2 TB              | 16 GB to 2 TB             | 16 GB to 16 TB            | 16 GB to 8 EB            |
| 4     | Max. File System Size       | 2 TB to 32 TB              | 2 TB to 32 TB             | 2 TB to 1 EB              | 2 TB to 16 EB            |
| 5     | Conversion                  | Cannot convert to ext2     | Convert ext2 to ext3      | Convert any ext to ext4   | Requires unmount/remount |

## 11. Files related to mounting in Linux
- **/etc/mtab**: Stores information on currently mounted file systems (dynamic).
- **/etc/fstab**: Stores permanent mount points.
  - Entry format: `<device name> <mount point> <file system type> <mount options> <backup> <fsck value>`

## 12. How to create different types of partitions
```bash
# fdisk -l
# fdisk /dev/sdc
Command (m for help): n (create new partition)
(p - primary, e - extended): p
First cylinder: (Enter for default)
Last cylinder: +<size in KB/MB/GB/TB>
Command (m for help): t (change partition ID, e.g., 8e for LVM)
Command (m for help): w (save changes)
# partprobe /dev/sdc1 (update partition table)
```

## 13. How to create a file system in Linux
```bash
# mkfs.<file system type> <device name>
Example: # mkfs.ext4 /dev/sdc1
```

## 14. How to mount file systems
- **Temporary Mount**:
  ```bash
  # mkdir /mnt/oracle
  # mount /dev/sdc1 /mnt/oracle
  ```
- **Permanent Mount**:
  ```bash
  # vim /etc/fstab
  /dev/sdc1 /mnt/oracle xfs defaults 0 0
  # mount -a
  ```

## 15. How to delete a partition
```bash
# fdisk /dev/sdc
Command (m for help): d (delete partition)
Partition number: (specify partition number)
Command (m for help): w (save changes)
# partprobe /dev/sdc1 (update partition table)
```

## 16. Partitions not mounting despite entries in /etc/fstab
1. Check for incorrect entries in `/etc/fstab`.
2. Unmount all partitions: `# umount -a`.
3. Mount all partitions: `# mount -a`.

## 17. Troubleshooting unmount issues
Reasons a directory cannot unmount:
1. Current directory is the mount point (`# pwd`).
2. Files in use:
   ```bash
   # fuser -cu <device>
   # lsof <device>
   # fuser -ck <file path>
   ```
   After resolving, unmount: `# umount <mount point>`.

## 18. View usage of mounted partitions
```bash
# df -hT
```

## 19. View size of files or directories
```bash
# du -h <file/directory>
# du . | sort -nr | head -n10
# ncdu (requires ncdu package)
```

## 20. Assign a label to a partition
```bash
# e2label <device> <label>
Example: # e2label /dev/sdb1 oradisk
# mount -l (view labels of mounted partitions)
```
**21. How to mount a partition temporarily or permanently using label?**
# mount LABEL=<label name> <mount point>
Example: # mount LABEL=oradisk /mnt/oracle (to mount the oradisk label on /mnt/oracle directory)
# vim /etc/fstab
LABEL=oradisk /mnt/oracle ext4 defaults 0 0
Esc+:+wq! (to save and exit the file)
# mount -a (to mount the partitions)
# mount (to verify whether it is mounted or not)

**22. How to mount the partition permanently using block id (UUID)?**
# blkid <partition name or disk name> (to see the UUID or block id of that partition)
Example: # blkid /dev/sdb2 (to see the UUID or block id of the /dev/sdb2 partition)
Copy that UUID with mouse and paste it in /etc/fstab file and make an entry about that.
Example: # vim /etc/fstab
UUID="{.......................}" /mnt/oracle ext4 defaults 0 0
Esc+:+wq! (to save and exit)

**23. What is the basic rule for swap size?**
(i) If the size of the RAM is less than or equal to 2GB, then the size of the swap = 2 x RAM size.
(ii) If the size of the RAM is more than 2GB, then the size of the swap = 2GB + RAM size.

**24. How to create a swap partition and mount it permanently?**
# free -m (to see the present swap size)
# swapon -s (to see the swap usage)
# fdisk <disk name> (to make a partition)
Example: # fdisk /dev/sdb
Command (m for help): n (to create a new partition)
First cylinder: (press Enter to take as default value)
Last cylinder: +2048M (to create 2GB partition)
Command (m for help): t (to change the partition id)
Enter the partition No.: 2 (to change the /dev/sdb2 partition id)
Enter the id: 82 (to change the partition id Linux to Linux Swap)

Command (m for help): w (to save the changes into the disk)
# partprobe /dev/sdb (to update the partition table information)
# mkswap <device or partition name> (to format the partition with swap file system)
Example: # mkswap /dev/sdb2 (to format the /dev/sdb2 partition with swap file system)
# swapon <device or partition name> (to activate the swap space)
Example: # swapon /dev/sdb2 (to activate /dev/sdb2 swap space)
# free -m (to see the swap size)
# vim /etc/fstab (to make an entry to permanently mount the swap partition)
/dev/sdb2 swap swap defaults 0 0
Esc+:+wq! (to save and exit)

**25. What are the attributes of the file system?**
(i) Inode number
(ii) File name
(iii) Data block

**26. What is inode number and what is the use of it?**
Inode numbers are the objects the Linux O/S uses to record the information about the file.
Generally, an inode number contains two parts:
(a) Inode first part contains information about the file, owner, its size, and its permissions.
(b) Inode second part contains a pointer to data blocks associated with the file content.
That's why using the inode number we can get the file information quickly.

**27. How to check the integrity of a file system or consistency of the file system?**
By running the **# fsck <device or partition name>** command we can check the integrity of the file system.
But before running the **fsck** command, first unmount that partition and then run the **fsck** command.

**28. What is fsck check or what are the phases of the fsck?**
(a) First it checks blocks and sizes of the file system
(b) Second it checks file system path names
(c) Third it checks file system connectivity
(d) Fourth it checks file system reference counts (nothing but inode numbers)
(e) Finally it checks file system occupied cylindrical groups

**29. Why should the file system be unmounted before running the fsck command?**
If we run **fsck** on mounted file systems, it leaves the file systems in an unusable state and also deletes the data.
So, before running the **fsck** command the file system should be unmounted.

**30. Which type of file system problems do you face?**
(i) File system full
(ii) File system corrupted

**31. How to extend the root file system which is not on LVM?**
By using the **# gparted** command we can extend the root partition; otherwise, we cannot extend the file systems which are not on LVM.

**32. How to unmount a file system forcefully?**
# umount -f <mount point>
# fuser -ck <mount point>

**33. How to know the file system type?**
# df -hT (command gives the file system type information)

**34. How to know which file system occupies more space and the top 10 file systems?**
# df -h <device or partition name> | sort -r | head -10

**35. What is the command to know the mounted file systems?**
# mount or # cat /etc/mtab

**36. How to know whether the file system is corrupted or not?**
First unmount the file systems and then run the **fsck** command on that file system.

**37. How to recover if a file system is corrupted or crashed?**
If the normal or not related to O/S file system is corrupted, first unmount that file system and run the **fsck** command on that file system. If the O/S related file system is corrupted, then boot the system with CDROM in single-user mode and run the **fsck** command.
If the normal or not related to O/S file system is crashed, then restore it from the recent backup. If the O/S related file system is crashed, then boot the system with CDROM in single-user mode and restore it from the recent backup.

**38. How to create a file with a particular size?**
# dd if=/dev/zero of=/orafile bs=1MB count=500 (to create 500MB size /orafile with 4KB block size)

**39. How to find how many disks are attached to the system?**
# fdisk -l (to see how many disks are attached to the system)

**40. What is journaling?**
It is a dedicated area in the file system where all the changes are tracked when the system crashes. So the possibility of the file system corruption or crashes is less because of this journaling feature.
