# Disk
[Adaptec hardware RAID controller](https://docs.hetzner.com/robot/dedicated-server/raid/adaptec-raid-controller/)

Status of the drives:
```sh
arcconf getconfig 1 pd|egrep "Device #|State\>|Reported Location|Reported Channel|S.M.A.R.T. warnings|Model|Serial number"
```
Full status of the drives:
```sh
arcconf getconfig 1
```

------------

**Software RAID**
Storage device information:
```sh
lsblk
```
Create RAID:
```sh
mdadm --create --verbose /dev/md2 --level=1 --raid-devices=2 /dev/nvme2n1 /dev/nvme3n1
```
RAID status:
```sh
cat /proc/mdstat
```
***Troubleshooting***

After the server is restarted, the raid status is as follows: `md127 : active (auto-read-only) raid1`
```sh
mdadm -Es
```
Added ARRAY to file (without a name):
```sh
nano /etc/mdadm/mdadm.conf
update-initramfs -u
```
Reboot server

------------

**Disk replacement in software RAID**

Storage device information:
```sh
cat /proc/mdstat
lshw -class disk -class storage
lsblk
smartctl -a /dev/nvme0n1
```
Сopy the markup from the working disk to a new one:
```sh
sfdisk -d /dev/nvme1n1 | sfdisk /dev/nvme0n1
```
Integrate a new disk, by partition
```sh
mdadm /dev/md0 -a /dev/nvme0n1p1
mdadm /dev/md1 -a /dev/nvme0n1p2
```
