---
title: "Adding Storage ToLinux"
date: 2023-04-06T15:54:49-03:00
draft: true
---

To mount a new disk in Linux, you can follow these steps:

1. Connect the disk to your Linux machine (either physical or virtual)
2. Use the `lsblk` command to find the device name of the disk. For example, the disk may be listed as `/dev/sdb`.
3. Use the `fdisk` command to create a GPT partition table on the disk. Run the following command, replacing `/dev/sdb` with the device name of your disk:

``` shell
sudo fdisk /dev/sdb
```

> Help inside `fdisk` can be found with `m` (some think of it as `m` for Menu)

Inside the `fdisk` utility prompt,  prompt, enter `g` to create a new GPT partition table.

4. Use the `n` command to create a new partition on the disk. You will need to specify the partition number, starting sector, and ending sector:

``` shell
Command (m for help): n
Partition number (1-128, default 1): 1
First sector (2048-41943039, default 2048): 
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-41943039, default 41943039): 
```

5. Use the `t` command to set the partition type to Linux filesystem:

``` shell
Command (m for help): t
Selected partition 1
Partition type (type L to list all types): 83
```

6. Use the `n`` command again to create a second partition on the disk. Repeat steps 4 and 5 to create a new partition with a different partition number and type.

7. Use the `mkfs` command to format the first partition as xfs. Run the following command, replacing `/dev/sdb1` with the device name of your partition:

``` bash
sudo mkfs.xfs /dev/sdb1
```

8. Use the `mkfs` command to format the second partition as ext4. Run the following command, replacing `/dev/sdb2` with the device name of your partition:

``` shell
sudo mkfs.ext4 /dev/sdb2
```


9. Create a directory where you want to mount the partitions. For example:

bash

sudo mkdir /mnt/xfs
sudo mkdir /mnt/ext4

    Use the blkid command to find the UUID of each partition. Run the following commands, replacing /dev/sdb1 and /dev/sdb2 with the device names of your partitions:

bash

sudo blkid /dev/sdb1
sudo blkid /dev/sdb2

The output will include a line similar to the following:

bash

/dev/sdb1: UUID="some-uuid-here" TYPE="xfs"

Copy the UUID value for each partition.

    Edit the /etc/fstab file to add permanent mount points for the partitions. Run the following command to open the file in a text editor:

bash

sudo nano /etc/fstab

Add the following lines to the end of the file, replacing the UUID values and mount points with your own:

bash

UUID=some-uuid-here /mnt/xfs xfs defaults 0 0
UUID=some-other-uuid-here /mnt/ext4 ext4 defaults 0 0

    Save and close the file.

    Use the mount command to mount the partitions. Run the following commands:

css

sudo mount -a
sudo mount

The output of the mount command should include lines similar to the following:

bash

/dev/sdb1 on /mnt/xfs type xfs (rw,relatime,attr2,inode64
