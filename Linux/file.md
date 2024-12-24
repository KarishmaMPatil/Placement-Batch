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
