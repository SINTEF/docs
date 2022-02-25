# What are the best filesystems for your infrastructure?

Sometimes one has to choose a filesystem. The default filesystem of your operating system is usually the best choice. But in rare cases, one might want to use a different filesystem.

## Ext4 or XFS

Ext4 and XFS are both good filesystems for Linux servers and desktops. Choosing one or the other does not have a significant impact. They have technical differences, but they are minor for a system administrator. The performances are almost the same between ext4 and XFS.

I usually go with XFS when I write my choice in a configuration file. I like the dynamically allocated inodes feature in XFS, though I may never need it. If the system already uses ext4, I do not bother switching to XFS.

## ZFS or Btrfs

ZFS and Btrfs are a lot fancier than Ext4 and XFS. They have many cool features such as RAID support, copy on write, automatic compression, and snapshots.

They are also more complex and slower on average than Ext4 and XFS, and I would not use these filesystems for my servers' root partition. They are perfect for data storage.

ZFS is not in the Linux Kernel because of its license, but it is easy to use on Linux nowadays. Btrfs is in the Linux Kernel and does not require any package and particular configuration to use.

ZFS supports encryption, while Btrfs does not. However, you can use encryption below the filesystem, which is not as convenient.

Btrfs was presented to the public a bit too early in its development. People lost data which gave him a bad reputation. It is now a stable filesystem that is safe to use.

I recommend ZFS because it supports encryption. But if you want to use the other fancy features on your root partition, you should use Btrfs unless you like challenges.

## N2FS

N2FS is a filesystem designed for flash storage, like smartphones and SD cards. I would not use it in other cases. Some people find it fast on SSDs, but my tests have shown that it is not always true.

## Should you use the Logical Volume Manager (LVM)?

The Linux Logical Volume Manager gives you more flexibility in your disks and partitions. It is cool, but I never had a use for it, so I don't use it anymore. It adds a layer of complexity. If you need a feature provided by LVM, such as quick partition resizing, you should use it.

I would rather keep it simple and use ZFS and classic Raid.

## If you use Windows or Mac, keep the defaults.

Windows use NTFS, it's not very good, but you don't have a choice. If you are doing software development, you should consider enabling WSL2 and developing using it. WSL2 uses an ext4 partition and is much faster than NTFS. It's highly noticeable if you do NodeJS development.

On Mac, you use APFS.