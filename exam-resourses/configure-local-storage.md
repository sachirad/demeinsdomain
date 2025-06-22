---
icon: hard-drive
---

# Configure Local Storage

### Practice Questions: "Configure Local Storage" (RHCSA v9)

Based on official RHCSA objectives and practical exam-style tasks, here are questions covering all key points of the "Configure local storage" section including partitioning, LVM, mounting, and non-destructive storage changes[^1]:

***

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
* Remove a physical volume from a volume group after migrating data off it.

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

#### Tips

* Always verify changes with `lsblk`, `pvs`, `vgs`, `lvs`, and `blkid`.
* Use `mount -a` to test `/etc/fstab` entries without reboot.
* Practice non-destructive modifications carefully to avoid data loss.
* Reboot after storage configuration to confirm persistence[^2].

These questions and scenarios will help you comprehensively practice the "Configure local storage" objective for the RHCSA v9 exam[^1].

⁂

[^1]: https://qtechbabble.wordpress.com/2024/02/25/rhcsa-9-exam-study-points-configure-local-storage/

[^2]: https://learn.redhat.com/t5/Platform-Linux/Why-am-I-failing-my-RHCSA-V9-exam/td-p/35520
