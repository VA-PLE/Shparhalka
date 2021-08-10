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
