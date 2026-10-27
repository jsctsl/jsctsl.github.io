```
apt install --no-install-recommends -y vsftpd/stable
apt install --no-install-recommends -y db-util/stable

nano /etc/vsftpd_virtual_users.txt
admin
admn1290
mason
masn1290
jason
jasn1290
matt
mat!1290

db_load -T -t hash -f /etc/vsftpd_virtual_users.txt /etc/vsftpd_virtual_users.db
chmod 600 /etc/vsftpd_virtual_users.*


nano /etc/pam.d/vsftpd_virtual
auth    required        pam_userdb.so    db=/etc/vsftpd_virtual_users
account required        pam_userdb.so    db=/etc/vsftpd_virtual_users


nano /etc/vsftpd.conf
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=007
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd_virtual
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
utf8_filesystem=YES
guest_enable=YES
guest_username=ftp
virtual_use_local_privs=YES
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=50000
log_ftp_protocol=YES
user_config_dir=/etc/vsftpd.d
allow_writeable_chroot=YES

nano /etc/vsftpd.d/jason
local_root=/srv/ftp/sales
cmds_denied=DELE,RMD,RNFR,RNTO,MKD
#cmds_allowed=ABOR,CWD,LIST,MDTM,NLST,PASS,PASV,PORT,PWD,QUIT,RETR,SIZE,STOR,TYPE,USER

nano /etc/vsftpd.d/admin
local_root=/srv/ftp
```

