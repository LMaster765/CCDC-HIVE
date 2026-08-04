# HIVE Host Setup

Full host setup instructions are not yet written. For now, this page hosts instructions for small portions of setup.

## Increasing Host Disk Size

If you decide that you need to give the host more disk space, there are a few steps you need to take:

1. If your host is a VM on a range, increase the disk size through the UI.

    - In proxmox, this involves going to Hardware > Hard Disk > Disk Action > Resize and specifying how much you want to increase it by.

2. Verify the host has more storage by running `lsblk`. The size of the top level partition (e.g. "sda") should be more than the sum of the sizes of its subpartitions.

3. Run `fdisk -l /dev/sda` (or whatever your partition is named) and take note of what partition number pve is under.

4. Run `growpart /dev/sda 3`. If the command is not installed, run `apt install cloud-guest-utils`.

5. Resize the LVM volumne by running `pvresize /dev/sda3`.

6. Verify that the volume group has more free space now by running `vgs` (look under "VFree").

7. Find the name of the thin pool by running `lvs`. It will probably be "data".

8. Extend the thin pool's storage with `lvextend -l +<amount>%FREE /dev/pve/data`. Replace amount with the amount you increased the disk size by in gigabytes, for example `+100%FREE` for 100GB.

9. Verify that this worked by running `pvesm status` and `lsblk`.