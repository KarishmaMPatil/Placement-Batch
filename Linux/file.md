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
