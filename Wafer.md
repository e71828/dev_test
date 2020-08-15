# share folders

We assign the disk `D` as the public disk, which meanss everyone in the `LAN` can fetch or push files. More cconvenient than `Git.`

## how to achievement
1. Rename the disk `本地磁盘(D:)` to`Share`.
1. Right click on the disk `Share(D:)`> `Properties`> `Security`> `Edit`> `Add`> `Advanced...`> `Find Now`> select `Everyone` and click `OK`.
2. Right click on the disk `Share(D:)`> `Properties`> `Share`> `Advanced Sharing...`> tick `Share this folder`, `Settings`--`Share name`: `智能平台处理中心`, `Permissions`> tick `Allow` on `Full Control`> `OK` 
3. Right click on the disk `Share(D:)`> `Properties`> `Share`> `OK` >`Password Protection`--`Network Sharing Center`> `ALL Networks`> `Turn off password protected sharing`> `Save changes`.
4. Access the disk/folders from another `LAN` computer .

# static ipv4.address
The ip of Wafer is assigned to be `192.168.0.20`.  
To test in the miwifi, add another ip: `192.168.31.20`

## how to achievement
1. Open `Change adapter options`, view `Control Panel\Network and Internet\Network Connections`;
2. Rename the connection `.. I211 ...` to `智能平台`；
3. Rename the connection `.. I219-LM` to `DSP`；
4. Right click on `智能平台`> `Properties`> `TCP/IPV4`> `Use the following IP address`, IP address: `192.168.0.20`, Subnet mask: `255.255.255.0`;
5. After last input, click `Advanced..`> in `IP address` area, click `ADD`> IP address: `192.168.31.20`, Subnet mask  : `255.255.255.0` and click `Add` to confirm> `OK`.
6. Open Windows Powershell, `ping 192.168.31.163`, if OK will reply with some time delay.
7. Rename the computer to `Sense-Center` and we can `ping` from anywhere else in `LAN` with `ping sense-center`.
