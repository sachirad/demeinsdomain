---
icon: hard-drive
---

# Configure Local Storage

### Practice Questions: "Configure Local Storage" (RHCSA v9)

Based on official RHCSA objectives and practical exam-style tasks, here are questions covering all key points of the "Configure local storage" section including partitioning, LVM, mounting, and non-destructive storage changes[^1]:

***

## <mark style="color:green;">Questions</mark>

#### List, create, delete partitions on MBR and GPT disks

* List all partitions and disks on the system, showing details such as size and type.
* Create a new GPT partition of 500MB on `/dev/sdb` using `parted` or `fdisk`.
* Delete an existing partition `/dev/sdb1` safely without affecting other partitions.

#### Create and remove physical volumes

* Create physical volumes on `/dev/sdb1` and `/dev/sdc1`.
* Remove a physical volume from the system without deleting data on the underlying device.

#### Assign physical volumes to volume groups

* Create a volume group named `datastore` using the physical volumes `/dev/sdb1` and `/dev/sdc1`.
* Extend an existing volume group by adding a new physical volume `/dev/sdd1`.

#### Create and delete logical volumes

* Create a logical volume named `accounting_lv` of size 150MB in the `datastore` volume group.
* Format the logical volume as `ext4` and mount it at `/datastore/accounting`.
* Delete the logical volume `accounting_lv` safely.

#### Configure systems to mount file systems at boot by UUID or label

* Find the UUID and label of the logical volume `/dev/datastore/accounting_lv`.
* Configure `/etc/fstab` to mount the logical volume persistently at `/datastore/accounting` using its UUID.
* Change the mount configuration to use the filesystem label instead of UUID.

#### Add new partitions and logical volumes, and swap to a system non-destructively

* Add a new partition of 100MB to `/dev/sdb` without deleting existing partitions.
* Create a new logical volume of 100MB in the `datastore` volume group and format it as `xfs`.
* Configure a new swap partition on `/dev/sdb2` and enable it without rebooting.
* Extend the size of an existing logical volume by 50MB and resize the filesystem accordingly.

***

#### Sample Practical Scenario (combining multiple objectives)

* You have two new disks `/dev/sdb` and `/dev/sdc`.
* Partition `/dev/sdb` with one primary partition and `/dev/sdc` with two partitions.
* Create physical volumes on all partitions.
* Create a volume group `vg_data` with all physical volumes.
* Create two logical volumes: `lv_data1` (200MB) and `lv_data2` (300MB).
* Format both logical volumes with `xfs` and mount them persistently at `/data1` and `/data2` respectively using UUIDs in `/etc/fstab`.
* Add a swap partition on `/dev/sdb2` and activate it immediately.
* Extend `lv_data1` by 100MB without unmounting it and resize the filesystem.

***

## <mark style="color:red;">Answers</mark>

#### List, create, delete partitions on MBR and GPT disks

* df -Th or lsblk -ft
* parted&#x20;
  * sudo parted /dev/sda
  * mktable GPT
  * mkpart
* rm 1

#### Create and remove physical volumes

* pvcreate /dev/sda1 /dev/sda2
* pvmove /dev/sda1
* vgreduce vg\_group /dev/sda1
* sudo pvremove /dev/sda1

#### Assign physical volumes to volume groups

* vgcreate datastore /dev/sda1&#x20;
* vgextend datastore /dev/sda2

#### Create and delete logical volumes

* &#x20;lvcreate -n accounting\_lv -L 150MB datastore
* mkfs.ext4 /dev/datastore/accounting\_lv&#x20;
* mkdir -p /datastore/accounting
* mount /dev/datastore/accounting\_lv /datastore/accounting/
* sudo umount /datastore/accounting
* sudo lvremove /dev/datastore/accounting\_lv

#### Configure systems to mount file systems at boot by UUID or label

* blkid /dev/mapper/datastore-accounting\_lv or blkid
* vim fstab and enter the UUID and mount point file system rest are defualt
* vim fstab and enter the label and mount point file system rest are defualt

#### Add new partitions and logical volumes, and swap to a system non-destructively

* parted /dev/sda
* mkpart&#x20;
* mkswap /dev/sda2&#x20;
* swapon /dev/sda2
* lvextend -L +50MB /dev/datastore/accounting\_lv
* resize2ft /dev/datastore/accounting\_lv    ( This is for ext file systems only)
* xfs\_growfs /dev/datastore/accounting\_lv      ( This is for xfs file systems only)

⁂

[^1]: https://qtechbabble.wordpress.com/2024/02/25/rhcsa-9-exam-study-points-configure-local-storage/
