# Video Commands:
apt install cifs-utils
mkdir /mnt/truenas
nano /etc/samba/.smbcreds 

add creds to file format:

username=[username]
passwprd=[pswrd]
exit nano

chmod 400 /etc/samba/.smbcreds

mount -t cifs -o rw,vers=3.0,credentials=/etc/samba/.smbcreds,uid=34,gid=34 //10.0.0.20/data /mnt/truenas

nano /etc/fstab
 
add this line to end:- 
//10.0.0.20 /mnt/truenas cifs vers=3.0,credentials=/etc/samba/.smbcreds,uid=34,gid=34,defaults 0 0
