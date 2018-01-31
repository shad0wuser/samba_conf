# Configure simple Samba Server

Update & install `samba`
```bash
apt-get update
apt-get install samba
```
Downlaod configuration file
```bash
git clone https://github.com/shad0wuser/samba_conf.git
cp samba_conf/smb.conf /etc/samba/
```
Create 3 folders: `smb-full`, `smb-read`, `smb-vary`
```bash
mkdir -p /exports/smb-{full,read,vary}
```
Set password for root to allow connect on smb server
```bash
smbpasswd -a root
```

## Verify connetction on client
Install smbclient
```bash
apt-get install smbclient
```
Verify smb connection (replace **ip_address** with your SMB Server IP)
```bash
smbclient -L ip_address
```
Connect to shared folder
```bash
smbclient //ip_address/smb-vary
```
or login with root user
```bash
smbclient //ip_address/smb-vary -U root
```
