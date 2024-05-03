# Set Hostname
> iptables -A INPUT -p icmp -j ACCEPT

sudo nano /etc/hostname
> Change the Hostname: Replace the current hostname with "intranet" in the file. Delete the existing hostname and type "intranet". Save the changes and exit the text editor.

sudo nano /etc/hosts
> Edit the Hosts File: Find the line that starts with `127.0.0.1` and contains the existing hostname. Replace the existing hostname with "intranet". Additionally, if there's a line with the server's IP address and its current hostname, replace the hostname with "intranet" on that line as well. Save the changes and exit the text editor.

sudo hostnamectl set-hostname intranet
(sudo reboot)

# SSH Key Authentication
> iptables -A INPUT -s 192.168.1.251/32 -p tcp -m tcp --dport 22 -j ACCEPT
## Management
ssh-keygen -t rsa
ssh-copy-id user@intranet_ip
ssh user@intranet_ip
## Intranet
sudo nano /etc/ssh/sshd_config
	PubkeyAuthentication yes
	PasswordAuthentication no
sudo systemctl restart sshd
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

# Install webserver on extranet server
>iptables -A INPUT -p tcp --dport 443 -j ACCEPT

1. [apt](https://www.server-world.info/en/command/html/apt.html) -y install apache2
2. nano /etc/apache2/conf-enabled/security.conf
	- Line 12: change
		- ServerTokens Prod
3. nano /etc/apache2/mods-enabled/dir.conf
	- Add file name that it can access only with directory's name
		- DirectoryIndex index.html index.htm
4. nano /etc/apache2/apache2.conf
	- Line 70: add to specify server name
		- ServerName hq.company.com
5. nano /etc/apache2/sites-enabled/000-default.conf
	- line 11 : change to webmaster's email
		- ServerAdmin extranet@hq.company.com
6. systemctl reload apache2

# Install PHP
1. [apt](https://www.server-world.info/en/command/html/apt.html) -y install php-fpm
2. nano /etc/apache2/sites-available/default-ssl.conf
	- add into ```<VirtualHost> - </VirtualHost>```
```
<FilesMatch \.php$>
	SetHandler "proxy:unix:/var/run/php/php8.2-fpm.sock|fcgi://localhost/"
</FilesMatch>
```
3. a2enmod proxy_fcgi setenvif
> Considering dependency proxy for proxy_fcgi:
	Enabling module proxy.
	Enabling module proxy_fcgi.
	Module setenvif already enabled
	To activate the new configuration, you need to run:
	systemctl restart apache2
4. a2enconf php8.2-fpm
> Enabling conf php8.1-fpm.
	To activate the new configuration, you need to run:
	  systemctl reload apache2
5. [systemctl](https://www.server-world.info/en/command/html/systemctl.html) restart php8.2-fpm apache2

# Install Filesharing role on intranet server
> iptables -A INPUT -p tcp -m tcp --dport 445 -j ACCEPT
> iptables -A INPUT -p tcp -m tcp --dport 139 -j ACCEPT


1. [apt](https://www.server-world.info/en/command/html/apt.html) -y install samba
2. [mkdir](https://www.server-world.info/en/command/html/mkdir.html) /home/share
3. [chmod](https://www.server-world.info/en/command/html/chmod.html) 777 /home/share
4. [vi](https://www.server-world.info/en/command/html/vi.html) /etc/samba/smb.conf
```
[global]
   # line 25 : add (set charset)
   unix charset = UTF-8

   # line 37 : uncomment and add network you allow to access
   interfaces = 127.0.0.0/8 10.0.0.0/24

   # line 98 : confirm (no authentication)
   map to guest = bad user

.....
.....

# add to the end
# any Share name you like
[Share]
   # specify shared directory
   path = /home/share
   # allow writing
   writable = yes
   read only = no
   browseable = yes
   # allow guest user (nobody)
   guest ok = yes
   # looks all as guest user
   guest only = yes
   # set permission [777] when file created
   force create mode = 777
   # set permission [777] when folder created
   force directory mode = 777
```
5. [systemctl](https://www.server-world.info/en/command/html/systemctl.html) restart smbd

# Install database server on extranet
1. [apt](https://www.server-world.info/en/command/html/apt.html) -y install mariadb-server
2. nano /etc/mysql/mariadb.conf.d/50-server.cnf
```
# line 95 : confirm default charset  
# if use 4 bytes UTF-8, specify [utf8mb4]
character-set-server  = utf8mb4
collation-server      = utf8mb4_general_ci
```
3. [systemctl](https://www.server-world.info/en/command/html/systemctl.html) restart mariadb
4. mysql_secure_installation
```
NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user. If you've just installed MariaDB, and
haven't set the root password yet, you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password or using the unix_socket ensures that nobody
can log into the MariaDB root user without the proper authorisation.

You already have your root account protected, so you can safely answer 'n'.

# Switch to [unix_socket] authentication or not
# [unix_socket] auth is enabled for root user by default even if you select [No]
Switch to unix_socket authentication [Y/n] n
 ... skipping.

You already have your root account protected, so you can safely answer 'n'.

# set MariaDB root password or not
# [unix_socket] authentication is enabled by default, but
# if you set root password, it's also possible to login with password authentication.
# if not set root password, only OS root user can login as MariaDB root user
Change the root password? [Y/n] n
 ... skipping.

By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

# remove anonymous users
Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

# disallow root login remotely
Disallow root login remotely? [Y/n] y
 ... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

# remove test database
Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

# reload privilege tables
Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!

# connect to MariaDB

  
root@www:~# 

mysql

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 37
Server version: 10.11.3-MariaDB-1 Debian 12

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

# [Unix_Socket] authentication is enabled by default
MariaDB [(none)]> show grants for root@localhost; 
+-----------------------------------------------------------------------------------------------------------------------------------------+
| Grants for root@localhost                                                                                                               |
+-----------------------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO `root`@`localhost` IDENTIFIED VIA mysql_native_password USING 'invalid' OR unix_socket WITH GRANT OPTION |
| GRANT PROXY ON ''@'%' TO 'root'@'localhost' WITH GRANT OPTION                                                                           |
+-----------------------------------------------------------------------------------------------------------------------------------------+
2 rows in set (0.000 sec)

# show user list
MariaDB [(none)]> select user,host,password from mysql.user; 
+-------------+-----------+----------+
| User        | Host      | Password |
+-------------+-----------+----------+
| mariadb.sys | localhost |          |
| root        | localhost | invalid  |
| mysql       | localhost | invalid  |
+-------------+-----------+----------+
3 rows in set (0.001 sec)

# show database list
MariaDB [(none)]> show databases; 
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.000 sec)

# create test database
MariaDB [(none)]> create database test_database; 
Query OK, 1 row affected (0.000 sec)

# create test table on test database
MariaDB [(none)]> create table test_database.test_table (id int, name varchar(50), address varchar(50), primary key (id)); 
Query OK, 0 rows affected (0.108 sec)

# insert data to test table
MariaDB [(none)]> insert into test_database.test_table(id, name, address) values("001", "Debian", "Hiroshima"); 
Query OK, 1 row affected (0.036 sec)

# show test table
MariaDB [(none)]> select * from test_database.test_table; 
+----+--------+-----------+
| id | name   | address   |
+----+--------+-----------+
|  1 | Debian | Hiroshima |
+----+--------+-----------+
1 row in set (0.000 sec)

# delete test database
MariaDB [(none)]> drop database test_database; 
Query OK, 1 row affected (0.111 sec)

MariaDB [(none)]> exit
Bye
```
# Configure database backup
1. [apt](https://www.server-world.info/en/command/html/apt.html) -y install mariadb-backup
2. [mkdir](https://www.server-world.info/en/command/html/mkdir.html) /home/mariadb_backup
3. mariabackup --backup --target-dir /home/mariadb_backup -u root
```
.....
.....

[01] 2023-07-04 19:06:33 Copying /var/lib/mysql//aria_log.00000001 to /home/mariadb_backup/aria_log.00000001
[01] 2023-07-04 19:06:33         ...done
[00] 2023-07-04 19:06:33 Waiting for log copy thread to read lsn 49898
[00] 2023-07-04 19:06:33 Executing FLUSH NO_WRITE_TO_BINLOG ENGINE LOGS...
[00] 2023-07-04 19:06:33 mariabackup: The latest check point (for incremental): '49882'
mariabackup: Stopping log copying thread
[00] 2023-07-04 19:06:33 Executing BACKUP STAGE END
[00] 2023-07-04 19:06:33 All tables unlocked
[00] 2023-07-04 19:06:33 Backup created in directory '/home/mariadb_backup/'
[00] 2023-07-04 19:06:33 Writing backup-my.cnf
[00] 2023-07-04 19:06:33         ...done
[00] 2023-07-04 19:06:33 Writing xtrabackup_info
[00] 2023-07-04 19:06:33         ...done
[00] 2023-07-04 19:06:33 Redo log (from LSN 49882 to 49898) was copied.
[00] 2023-07-04 19:06:33 completed OK!
```
4. [ll](https://www.server-world.info/en/command/html/ls.html) /home/mariadb_backup
```
total 12752
-rw-r----- 1 root root   417792 Jul  4 19:06 aria_log.00000001
-rw-r----- 1 root root       52 Jul  4 19:06 aria_log_control
-rw-r----- 1 root root      475 Jul  4 19:06 backup-my.cnf
-rw-r----- 1 root root 12582912 Jul  4 19:06 ibdata1
-rw-r----- 1 root root    12304 Jul  4 19:06 ib_logfile0
drwx------ 2 root root     4096 Jul  4 19:06 mysql
drwx------ 2 root root     4096 Jul  4 19:06 performance_schema
drwx------ 2 root root    12288 Jul  4 19:06 sys
drwx------ 2 root root     4096 Jul  4 19:06 test_database
-rw-r----- 1 root root       73 Jul  4 19:06 xtrabackup_checkpoints
-rw-r----- 1 root root      434 Jul  4 19:06 xtrabackup_info
```
5. [systemctl](https://www.server-world.info/en/command/html/systemctl.html) stop mariadb
6. [rm](https://www.server-world.info/en/command/html/rm.html) -rf /var/lib/mysql/*
7. [ll](https://www.server-world.info/en/command/html/ls.html) mariadb_backup.tar.gz
```
-rw-r--r-- 1 debian debian 704177 Jul 4 19:07 mariadb_backup.tar.gz
```
8. [tar](https://www.server-world.info/en/command/html/tar.html) zxvf mariadb_backup.tar.gz
9. mariabackup --prepare --target-dir /root/mariadb_backup
```
mariabackup based on MariaDB server 10.11.3-MariaDB debian-linux-gnu (x86_64)
[00] 2023-07-04 19:15:31 cd to /root/mariadb_backup/
[00] 2023-07-04 19:15:31 open files limit requested 0, set to 1024
[00] 2023-07-04 19:15:31 Loading plugins from provider_bzip2=provider_bzip2;provider_lz4=provider_lz4;provider_lzma=provider_lzma;provider_lzo=provider_lzo;provider_snappy=provider_snappy
[00] 2023-07-04 19:15:31 Loading plugins
[00] 2023-07-04 19:15:31         Plugin parameter :  '--plugin_load=provider_bzip2=provider_bzip2;provider_lz4=provider_lz4;provider_lzma=provider_lzma;provider_lzo=provider_lzo;provider_snappy=provider_snappy'
[00] 2023-07-04 19:15:31         Plugin parameter :  '--prepare'
[00] 2023-07-04 19:15:31         Plugin parameter :  '--target-dir'
[00] 2023-07-04 19:15:31         Plugin parameter :  '/root/mariadb_backup'
[00] 2023-07-04 19:15:31 This target seems to be not prepared yet.
[00] 2023-07-04 19:15:31 mariabackup: using the following InnoDB configuration for recovery:
[00] 2023-07-04 19:15:31 innodb_data_home_dir = .
[00] 2023-07-04 19:15:31 innodb_data_file_path = ibdata1:12M:autoextend
[00] 2023-07-04 19:15:31 innodb_log_group_home_dir = .
[00] 2023-07-04 19:15:31 InnoDB: Using liburing
[00] 2023-07-04 19:15:31 Starting InnoDB instance for recovery.
[00] 2023-07-04 19:15:31 mariabackup: Using 104857600 bytes for buffer pool (set by --use-memory parameter)
2023-07-04 19:15:31 0 [Note] InnoDB: Compressed tables use zlib 1.2.13
2023-07-04 19:15:31 0 [Note] InnoDB: Number of transaction pools: 1
2023-07-04 19:15:31 0 [Note] InnoDB: Using crc32 + pclmulqdq instructions
2023-07-04 19:15:31 0 [Note] InnoDB: Using liburing
2023-07-04 19:15:31 0 [Note] InnoDB: Initializing buffer pool, total size = 100.000MiB, chunk size = 100.000MiB
2023-07-04 19:15:31 0 [Note] InnoDB: Completed initialization of buffer pool
2023-07-04 19:15:31 0 [Note] InnoDB: Buffered log writes (block size=512 bytes)
[00] 2023-07-04 19:15:31 Last binlog file , position 0
[00] 2023-07-04 19:15:31 completed OK!

# run restore
  
root@node01:~# 

mariabackup --copy-back --target-dir /root/mariadb_backup


[01] 2023-07-04 19:16:04 Copying ./sys/x@0024ps_schema_table_statistics_io.frm to /var/lib/mysql/sys/x@0024ps_schema_table_statistics_io.frm
[01] 2023-07-04 19:16:04         ...done
[01] 2023-07-04 19:16:04 Copying ./sys/sys_config.MAI to /var/lib/mysql/sys/sys_config.MAI
[01] 2023-07-04 19:16:04         ...done
[01] 2023-07-04 19:16:04 Copying ./sys/x@0024user_summary_by_file_io.frm to /var/lib/mysql/sys/x@0024user_summary_by_file_io.frm
[01] 2023-07-04 19:16:04         ...done
[01] 2023-07-04 19:16:04 Copying ./sys/x@0024ps_digest_avg_latency_distribution.frm to /var/lib/mysql/sys/x@0024ps_digest_avg_latency_distribution.frm
[01] 2023-07-04 19:16:04         ...done
[00] 2023-07-04 19:16:04 completed OK!
```
10. [chown](https://www.server-world.info/en/command/html/chown.html) -R mysql:mysql /var/lib/mysql
11. systemctl start mariadb
12. crontab -e
13. 0 ** * * * tar -zcf /var/backups/home.tgz /home/
> every hour
![[Pasted image 20240428151925.png]]
# Install Wordpress on extranet server
> iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT

1. sudo apt-get install php8.2 php8.2-cli php8.2-common php8.2-imap php8.2-redis php8.2-snmp php8.2-xml php8.2-mysqli php8.2-zip php8.2-mbstring php8.2-curl libapache2-mod-php -y
2. php -v
```
root@host:~# php -v
Created directory: /var/lib/snmp/cert_indexes
PHP 8.2.7 (cli) (built: Jun  9 2023 19:37:27) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.2.7, Copyright (c) Zend Technologies
    with Zend OPcache v8.2.7, Copyright (c), by Zend Technologies
```
3. sudo systemctl start mariadb && sudo systemctl enable mariadb
4. sudo systemctl status mariadb
5. mariadb
```
 CREATE USER 'wordpress'@'localhost' IDENTIFIED BY 'YourStrongPasswordHere';
 CREATE DATABASE wordpress;
 GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress'@'localhost';
 FLUSH PRIVILEGES;
 EXIT;
```
6. cd /var/www/html
7. wget https://wordpress.org/latest.zip
8. unzip latest.zip
9. rm latest.zip
10. chown -R www-data:www-data wordpress/
11. cd wordpress/
12. find . -type d -exec chmod 755 {} \;
13. find . -type f -exec chmod 644 {} \;
14. mv wp-config-sample.php wp-config.php
15. nano wp-config.php
```
// ** Database settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', 'wordpress' );

/** Database username */
define( 'DB_USER', 'wordpress' );

/** Database password */
define( 'DB_PASSWORD', 'YourStrongPasswordHere' );
```
16. cd /etc/apache2/sites-available/
17. touch wordpress.conf
18. nano wordpress.conf
```
<VirtualHost *:80>
ServerName **yourdomain.com**
DocumentRoot /var/www/html/wordpress

<Directory /var/www/html/wordpress>
AllowOverride All
</Directory>

ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```
19. sudo a2enmod rewrite
20. sudo a2ensite wordpress.conf
21. apachectl -t
22. systemctl reload apache2
# Install and configure NTP as client
## Windows
1. net stop w32time 
2. w32tm /config /syncfromflags:manual /manualpeerlist:"0.nl.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.nl.pool.ntp.org"
3. w32tm /config /reliable:yes 
4. net start w32time
5. w32tm /query /configuration 
6. w32tm /resync
## Debian
1. sudo apt-get update
2. sudo apt-get install ntp
3. sudo nano /etc/ntpsec/ntp.conf
4. server 192.168.1.2 iburst
5. sudo sytemctl restart ntp
6. sudu systemctl enable ntp
7. sudo systemctl status ntp
8. ntpq -p
# Configure PAM login with AD
> iptables -A INPUT -p tcp -m tcp --dport 5985 -j ACCEPT
> iptables -A INPUT -p tcp -m tcp --dport 5986 -j ACCEPT

1. apt install realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit
2. nano /etc/resolv.conf
```
domain hq.company.com
search hq.company.com
nameserver 192.168.1.2
```
3. realm discover hq.company.com
4. realm join hq.company.com
5. id Administrator@hq.company.com
6. nano /etc/pam.d/common-session
```
# add to the end : create Home Dir automatically when initial login
session optional        pam_mkhomedir.so skel=/etc/skel umask=077
```
7. exit
8. Administrator@hq.company.com
```
root@intranet:~# cat /etc/sssd/sssd.conf

[sssd]
domains = hq.company.com
config_file_version = 2
services = nss, pam

[domain/hq.company.com]
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = hq.company.com
realmd_tags = manages-system joined-with-adcli
id_provider = ad
fallback_homedir = /home/%u@%d
ad_domain = hq.company.com
use_fully_qualified_names = False
ldap_id_mapping = True
access_provider = ad
```
# Enable AD users integration in SAMBA Fileshares
1. apt -y install winbind libpam-winbind libnss-winbind krb5-config samba-dsdb-modules samba-vfs-modules
2. mv /etc/samba/smb.conf /etc/samba/smb.conf.org
3. nano /etc/samba/smb.conf
```
[global]
   kerberos method = secrets and keytab
   realm = HQ.COMPANY.COM
   workgroup = HQ
   security = ads
   template shell = /bin/bash
   winbind enum groups = Yes
   winbind enum users = Yes
   winbind separator = +
   idmap config * : rangesize = 1000000
   idmap config * : range = 1000000-19999999
   idmap config * : backend = autorid
   winbind use default domain = no
   password server = *
   interface = 127.0.0.0/8 192.168.1.0/24
   map to guest = bad user
   unix charset = UTF-8

[share]
   path = /home/share
   browseable = yes
   read only = no
   writable = yes
   force create mode = 777
   force directory mode = 777
   guest ok = yes
   guest only = yes
```
4. nano /etc/nsswitch.conf
```
# line 7 : confirm
passwd:         files systemd winbind
group:          files systemd winbind
```
5. nano /etc/pam.d/common-session
```
# add to the end if you need (auto create a home directory at initial login)
session optional        pam_mkhomedir.so skel=/etc/skel umask=077
```
6. nano /etc/resolv.conf
```
domain hq.company.com
search hq.company.com
nameserver 192.168.1.2
```
7. systemctl restart winbind
8. net ads info
9. log on with username@hq.company.com
# Install BIND DNS Server on intranet
> iptables -A INPUT -p tcp -m tcp --dport 138 -j ACCEPT
> iptables -A INPUT -p tcp -m tcp --dport 53 -j ACCEPT

1. apt -y install bind9 bind9utils
2. nano /etc/bind/named.conf
```
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
# add
include "/etc/bind/named.conf.internal-zones";
```
3. nano /etc/bind/named.conf.options
```
acl internal-network {
        192.168.1.0/24;
        localhost;
        localnets;
};
options {
        allow-query { internal-network; };
        # network range you allow to transfer zone files to clients
        # add secondary DNS servers if it exist
        # allow-transfer { localhost; };
        # add : allow recursion
        recursion yes;
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                192.168.1.2;
                192.168.1.3;
        };
        forward only;
        auth-nxdomain no;    # conform to RFC1035

        # dnssec-enable yes;
        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        # dnssec-validation yes;

        listen-on-v6 { any; };
};
```
4. nano /etc/bind/named.conf.internal-zones
```
zone "hq.company.com" IN {
        type master;
        file "/etc/bind/hq.company.com.lan";
        allow-update { none; };
};
zone "1.168.192.in-addr.arpa" IN {
        type master;
        file "/etc/bind/1.168.192.db";
        allow-update { none; };
};
```
5. nano /etc/default/named
```
#
# run resolvconf?
RESOLVCONF=no

# startup options for the server
OPTIONS="-u bind"
#OPTIONS="-u bind -4
```
6. nano /etc/bind/hq.company.com.lan
```
$TTL 86400
@   IN  SOA     intranet.hq.company.com. admin.hq.company.com. (
        2023061501  ;Serial
        3600        ;Refresh
        1800        ;Retry
        604800      ;Expire
        86400       ;Minimum TTL
)

; Define Name Servers
@   IN  NS      intranet.hq.company.com.

; Define Name Server's IP address
intranet.hq.company.com.  IN  A  192.168.1.252

; Define other hosts
management     IN  A       192.168.1.251
extranet       IN  A       192.168.1.253

```
7. nano /etc/bind/1.168.192.db
```
$TTL    604800
@       IN      SOA     intranet.hq.company.com. admin.hq.company.com. (
                        2022040901 ; Serial
                        604800     ; Refresh
                        86400      ; Retry
                        2419200    ; Expire
                        604800 )   ; Negative Cache TTL
;
@       IN      NS      intranet.hq.company.com.

31       IN      PTR     management.hq.company.com.
30       IN      PTR     intranet.hq.company.com.
32     IN      PTR     extranet.hq.company.com.
```
8. systemctl restart named
9. dig intranet.hq.company.com
### On windows DC
1. Server manager -> tools -> DHCP -> dc1 -> ipv4 -> server options -> DNS servers
2. add ip of intranet as dns server and remove ip of dc's
# Install DHCP server on intranet server
> iptables -A INPUT -p udp -m udp --sport 68 --dport 67 -j ACCEPT
> iptables -A OUTPUT -p udp -m udp --sport 67 --dport 68 -j ACCEPT

1. apt -y install isc-dhcp-server
2. nano /etc/default/isc-dhcp-server
```
# Defaults for isc-dhcp-server (sourced by /etc/init.d/isc-dhcp-server)

# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
#DHCPDv4_CONF=/etc/dhcp/dhcpd.conf
#DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf

# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
DHCPDv4_PID=/var/run/dhcpd.pid
#DHCPDv6_PID=/var/run/dhcpd6.pid

# Additional options to start dhcpd with.
#       Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=""

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACESv4="ens192"
#INTERFACESv6=""
```
3. nano /etc/dhcp/dhcpd.conf
```
option domain-name "hq.company.com";
option domain-name-servers 192.168.1.252;

default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
    option routers 192.168.1.1;
    option subnet-mask 255.255.255.0;
    range dynamic-bootp 192.168.1.101 192.168.1.199;
    option domain-name-servers 192.168.1.252;
    option ntp-servers 192.168.1.252;
}
```
4. systemctl restart isc-dhcp-server
5. ls -l /var/lib/dhcp
6. cat /var/lib/dhcp/dhcpd.leases
### On Windows DC
1. Server manager -> Tools -> DHCP -> DC -> ipv4 -> Right click "Scope" -> Deactivate
# Install NTP server on intranet server
> iptables -A OUTPUT -p udp -m udp --dport 123 -j ACCEPT

1. apt -y install ntpsec
2. nano /etc/ntpsec/ntp.conf
```
# pool.ntp.org maps to about 1000 low-stratum NTP servers.  Your server will
# pick a different set every time it starts up.  Please consider joining the
# pool: <https://www.pool.ntp.org/join.html>
# pool 0.debian.pool.ntp.org iburst
# pool 1.debian.pool.ntp.org iburst
# pool 2.debian.pool.ntp.org iburst
# pool 3.debian.pool.ntp.org iburst
#server 192.168.1.2 iburst
pool ntp.nict.jp iburst
```
3. systemctl restart ntpsec
4. ntpq -p
### [Debian NTP server with Chrony](https://leho-howest.instructure.com/courses/21019/modules/items/819696 "Debian NTP server with Chrony")
1. apt -y install chrony
2. nano /etc/chrony/chrony.conf
```
# line 8 : comment out default settings and add NTP Servers for your timezone
#pool 2.debian.pool.ntp.org iburst
pool ntp.nict.jp iburst 

# add to the end : network range you allow to receive time syncing requests from clients
allow 192.168.1.0/24
```
3. systemctl restart chrony
4. chronyc sources
# Replace ISC-DHCPD With ISC-KEA on Intranet Server
1. apt install curl apt-transport-https -y
2. curl -1sLf 'https://dl.cloudsmith.io/public/isc/kea-2-2/setup.deb.sh' | sudo -E bash
3. apt install isc-kea-dhcp4-server -y
4. cd /etc/kea
5. mv kea-dhcp4.conf kea-dhcp4.conf.bak
6. nano kea-dhcp4.conf
```
{
"Dhcp4": {
    "interfaces-config": {
        "interfaces": ["ens192"]
    },

    "lease-database": {
        "type": "memfile",
        "persist": true,
        "name": "/var/lib/kea/kea-leases4.csv",
        "lfc-interval": 3600
    },

    "renew-timer": 15840,
    "rebind-timer": 27720,
    "valid-lifetime": 31680,

    "option-data": [
        {
            "name": "domain-name-servers",
            "data": "192.168.1.252"
        },

        {
            "name": "domain-search",
            "data": "hq.company.com"
        }
    ],

    "subnet4": [
        {
            "subnet": "192.168.1.0/24",
            "pools": [ { "pool": "192.168.1.110 - 192.168.1.199" } ],
            "option-data": [
                {
                    "name": "routers",
                    "data": "192.168.1.1"
                }
            ],

            "reservations": [
                // MAC address reservation
                {
                    "hw-address": "00:50:56:9C:D3:11",
                    "ip-address": "192.168.1.101",
                    "hostname": "win11"
                },]
        }

        // Add subnets here
    ]
}
```
7. `chown _kea:root kea-dhcp4.conf`
8. systemctl restart isc-kea-dhcp4-server
9. more /var/lib/kea/kea-leases4.csv
### Stork
https://stork.readthedocs.io/en/v1.16.0/install.html#installing-on-debian-ubuntu
https://www.pgsclusters.com/blog/install-postgresql-on-debian
1. sudo apt install postgresql postgresql-contrib
2. sudo -u postgres psql -c "ALTER USER postgres PASSWORD 'postgres';"
3. stork-tool db-create --db-name stork --db-user stork
4. stork-tool db-init
5. stork-tool db-up
6. curl -1sLf 'https://dl.cloudsmith.io/public/isc/stork/cfg/setup/bash.deb.sh' | sudo bash
7. sudo apt install isc-stork-server
8. nano /etc/stork/server.env
```
STORK_DATABASE_PASSWORD=stork
```
9. sudo systemctl enable isc-stork-server
10. sudo systemctl start isc-stork-server
11. sudo systemctl status isc-stork-server
#### Andere server voor Stork agent (extranet/management)
1. sudo apt install isc-stork-agent
2. sudo dnf install isc-stork-agent
3. sudo systemctl enable isc-stork-agent
4. sudo systemctl start isc-stork-agent
5. sudo systemctl status isc-stork-agent
6. su stork-agent -s /bin/sh -c 'stork-agent register -u http://stork.example.org:8080'
# HAProxy on Debian (extranet)
> iptables -A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT
> iptables -A INPUT -p tcp -m tcp --dport 8083 -j ACCEPT

1. apt -y install haproxy
2. nano /etc/haproxy/haproxy.cfg
```
global
        log /dev/log    local0
        log /dev/log    local1 notice
        chroot /var/lib/haproxy
        stats socket /run/haproxy/admin.sock mode 660 level admin
        stats timeout 30s
        user haproxy
        group haproxy
        daemon

        # Default SSL material locations
        ca-base /etc/ssl/certs
        crt-base /etc/ssl/private

        # See: https://ssl-config.mozilla.org/#server=haproxy&server-version=2.0.3&config=intermediate
        ssl-default-bind-ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256->
        ssl-default-bind-ciphersuites TLS_AES_128_GCM_SHA256:TLS_AES_256_GCM_SHA384:TLS_CHACHA20_POLY1305_SHA2>
        ssl-default-bind-options ssl-min-ver TLSv1.2 no-tls-tickets

defaults
        log     global
        mode    http
        option  httplog
        option  dontlognull
        timeout connect 5000
        timeout client  50000
        timeout server  50000
        errorfile 400 /etc/haproxy/errors/400.http
        errorfile 403 /etc/haproxy/errors/403.http
        errorfile 408 /etc/haproxy/errors/408.http
        errorfile 500 /etc/haproxy/errors/500.http
        errorfile 502 /etc/haproxy/errors/502.http
        errorfile 503 /etc/haproxy/errors/503.http
        errorfile 504 /etc/haproxy/errors/504.http

frontend http-in
        # listen on 8083 port
        bind *:8083
        # set default backend
        default_backend    backend_servers
        # send X-Forwarded-For header
        option             forwardfor

# define backend
backend backend_servers
        # balance with roundrobin
        balance            roundrobin
        # define backend servers
        server             node01 192.168.1.252:8080 check
```
3. systemctl restart haproxy
# Firewall
## Intranet
iptables -P INPUT DROP
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -s 192.168.1.251/32 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 445 -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 445 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 139 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 138 -j ACCEPT
iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -p udp -m udp --sport 68 --dport 67 -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 123 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 5985 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 5986 -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 53 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 53 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT
iptables -A OUTPUT -p udp -m udp --sport 67 --dport 68 -j ACCEPT
iptables -A OUTPUT -p udp -m udp --dport 123 -j ACCEPT
iptables -A OUTPUT -p udp -m udp --sport 53 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --sport 53 -j ACCEPT

iptables-save > /etc/iptables/rules.v4
## Extranet
iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -s 192.168.1.251/32 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport 8083 -j ACCEPT

iptables-save > /etc/iptables/rules.v4
