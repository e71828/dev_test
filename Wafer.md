# Remote Desktop
**Allow remote connections to this computer!**  
**Allow remote connections to this computer!**  
**Allow remote connections to this computer!**  

# share folders

We assign the disk `D` as the public disk, which meanss everyone in the `LAN` can fetch or push files. More convenient than `Git.`

## how to achievement
1. Rename the disk `本地磁盘(D:)` to`Share`.
1. Right click on the disk `Share(D:)`> `Properties`> `Security`> `Edit`> `Add`> `Advanced...`> `Find Now`> select `Everyone` and click `OK`.
2. Right click on the disk `Share(D:)`> `Properties`> `Share`> `Advanced Sharing...`> tick `Share this folder`, `Settings`--`Share name`: `智能平台处理中心`, `Permissions`> tick `Allow` on `Full Control`> `OK` 
3. Right click on the disk `Share(D:)`> `Properties`> `Share`> `OK` >`Password Protection`--`Network Sharing Center`> `ALL Networks`> `Turn off password protected sharing`> `Save changes`.
4. Access the disk/folders from another `LAN` computer .

# static ipv4.address
The ip of Wafer is assigned to be `192.168.0.20`.  
To test in the miwifi, add another ip: `192.168.31.20`

## Mac Address
- 1号机
    - 00-18-7D-CA-B2-22
    - 00-18-7D-CA-B2-21
- 0号机
    - 00-18-7D-CA-B2-0E
    - 00-18-7D-CA-B2-0D
  
  We can enable `Wake-on-LAN` on the two System through ethernet. Generally, wo need both supports of the BIOS and driver.

## how to achievement
1. Open `Change adapter options`, view `Control Panel\Network and Internet\Network Connections`;
2. Rename the connection `.. I211 ...` to `智能平台`；
3. Rename the connection `.. I219-LM` to `DSP`；
4. Right click on `智能平台`> `Properties`> `TCP/IPV4`> `Use the following IP address`, IP address: `192.168.0.20`, Subnet mask: `255.255.255.0`;
5. After last input, click `Advanced..`> in `IP address` area, click `ADD`> IP address: `192.168.31.20`, Subnet mask  : `255.255.255.0` and click `Add` to confirm> `OK`.
5. Right click on `DSP`> `Properties`> `TCP/IPV4`> `Use the following IP address`, IP address: `192.168.1.10`, Subnet mask: `255.255.255.0`;
6. Open Windows Powershell, `ping 192.168.31.163`, if OK will reply with some time delay.
7. Rename the computer to `Sense-Center` and we can `ping` from anywhere else in `LAN` with `ping sense-center`.

# Problem: CredSSP encryption oracle remediation
This security update addresses the vulnerability by correcting how CredSSP validates requests during the authentication process. [more](https://support.microsoft.com/en-us/help/4093492/credssp-updates-for-cve-2018-0886-march-13-2018)
## solution
- best but not needed: update both client and server
- recommended: config your client, open Windows Powershell(`win` + `X`, `A`);  
  `REG ADD HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters\ /v AllowEncryptionOracle /t REG_DWORD /d 2`


# Autologin
To use Registry Editor to turn on automatic logon, follow these steps:

1. Click **Start**, and then click **Run**.
1. In the **Open** box, type Regedt32.exe, and then press Enter.
1. Locate the following subkey in the registry:   
    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon**
1. Double-click the **DefaultUserName** entry, type your user name, and then click **OK**.
1. Double-click the **DefaultPassword** entry, type your password, and then click **OK**.

    #### Note If the DefaultPassword value does not exist, it must be added. To add the value, follow these steps:
 
    1. On the **Edit** menu, click **New**, and then point to **String Value**.
    1. Type DefaultPassword, and then press Enter.
    1. Double-click **DefaultPassword**.
    1. In the Edit String dialog, type your password and then click **OK**.
    
    #### Note If no DefaultPassword string is specified, Windows automatically changes the value of the AutoAdminLogon key from 1 (true) to 0 (false), disabling the AutoAdminLogon feature.
 
1. On the **Edit** menu, click **New**, and then point to **String Value**.
1. Type AutoAdminLogon, and then press Enter.
1. Double-click **AutoAdminLogon**.
1. In the **Edit String** dialog box, type 1 and then click **OK**.
1. If you have joined the computer to a domain, you should add the **DefaultDomain** value, and the data for the value should be set as the fully qualified domain name (FQDN) of the domain.
1. Exit Registry Editor.
2. Click **Start**, click **Restart**.
4. Restart your computer. You can now log on automatically.

## Config Autologin with cmd(admin)
```Powershell
REG ADD "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName /t REG_SZ /d Administrator
REG ADD "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword /t REG_SZ /d admin
REG ADD "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon /t REG_SZ /d 1
```

