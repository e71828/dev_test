# static_ip

The ip of TX2 is assigned to be `192.168.0.22`  
To test in the `miwifi`, add another ip: `192.168.31.22`  

## achievement
```bash
nmcli con show
nmcli con edit Wired\ connection\ 1
> set ipv4.address 192.168.31.22
> go ipv4.address
> add 192.168.0.22/24
> back
> back
> set connection.id single
> save
> quit
```