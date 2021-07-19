ssh -i id_rsa_scs scslin@40.71.213.26

sudo su

Content

/var/www/html: The actual web content, which by default only consists of the default Nginx page you saw earlier, is served out of the /var/www/html directory. This can be changed by altering Nginx configuration files.


Server Configuration
/etc/nginx: The Nginx configuration directory. All of the Nginx configuration files reside here.
/etc/nginx/nginx.conf: The main Nginx configuration file. This can be modified to make changes to the Nginx global configuration.
/etc/nginx/sites-available/: The directory where per-site server blocks can be stored. Nginx will not use the configuration files found in this directory unless they are linked to the sites-enabled directory. Typically, all server block configuration is done in this directory, and then enabled by linking to the other directory.
/etc/nginx/sites-enabled/: The directory where enabled per-site server blocks are stored. Typically, these are created by linking to configuration files found in the sites-available directory.
/etc/nginx/snippets: This directory contains configuration fragments that can be included elsewhere in the Nginx configuration. Potentially repeatable configuration segments are good candidates for refactoring into snippets.
Server Logs
/var/log/nginx/access.log: Every request to your web server is recorded in this log file unless Nginx is configured to do otherwise.
/var/log/nginx/error.log: Any Nginx errors will be recorded in this log.

cd /etc/nginx/sites-available/

vi default

Next, test to make sure that there are no syntax errors in any of your Nginx files:

sudo nginx -t
Save and close the file when you are finished.

If there aren’t any problems, restart Nginx to enable your changes:

sudo systemctl restart nginx
Nginx should now be serving your domain name. You can test this by navigating to http://example.com, where you should see something like this:


https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04

sudo certbot --nginx -d zoom.shreemaycommunity.org -d www.shreemaycommunity.org

Certificate Update :

https://www.digitalocean.com/community/questions/let-s-encrypt-acmev1-protocol-you-should-upgrade-to-an-acmev2

root@scslin:/home/scslin# sudo apt install --only-upgrade certbot

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-filesystem1.58.0 libboost-program-options1.58.0
  libboost-system1.58.0 libboost-thread1.58.0 libgoogle-perftools4
  libpcrecpp0v5 libsnappy1v5 libtcmalloc-minimal4 libv8-3.14.5
  libyaml-cpp0.5v5 linux-azure-cloud-tools-4.15.0-1037
  linux-azure-cloud-tools-4.15.0-1039 linux-azure-cloud-tools-4.15.0-1040
  linux-azure-cloud-tools-4.15.0-1041 linux-azure-cloud-tools-4.15.0-1045
  linux-azure-cloud-tools-4.15.0-1046 linux-azure-cloud-tools-4.15.0-1047
  linux-azure-cloud-tools-4.15.0-1049 linux-azure-cloud-tools-4.15.0-1050
  linux-azure-cloud-tools-4.15.0-1051 linux-azure-cloud-tools-4.15.0-1052
  linux-azure-cloud-tools-4.15.0-1055 linux-azure-cloud-tools-4.15.0-1056
  linux-azure-cloud-tools-4.15.0-1057 linux-azure-cloud-tools-4.15.0-1059
  linux-azure-cloud-tools-4.15.0-1060 linux-azure-cloud-tools-4.15.0-1061
  linux-azure-cloud-tools-4.15.0-1063 linux-azure-cloud-tools-4.15.0-1064
  linux-azure-cloud-tools-4.15.0-1066 linux-azure-cloud-tools-4.15.0-1067
  linux-azure-cloud-tools-4.15.0-1069 linux-azure-cloud-tools-4.15.0-1071
  linux-azure-cloud-tools-4.15.0-1075 linux-azure-cloud-tools-4.15.0-1077
  linux-azure-cloud-tools-4.15.0-1082 linux-azure-cloud-tools-4.15.0-1083
  linux-azure-cloud-tools-4.15.0-1089 linux-azure-cloud-tools-4.15.0-1091
  linux-azure-cloud-tools-4.15.0-1092 linux-azure-cloud-tools-4.15.0-1093
  linux-azure-cloud-tools-4.15.0-1095 linux-azure-cloud-tools-4.15.0-1096
  linux-azure-cloud-tools-4.15.0-1098 linux-azure-cloud-tools-4.15.0-1100
  linux-azure-cloud-tools-4.15.0-1102 linux-azure-cloud-tools-4.15.0-1103
  linux-azure-cloud-tools-4.15.0-1106 linux-azure-cloud-tools-4.15.0-1108
  linux-azure-cloud-tools-4.15.0-1109 linux-azure-cloud-tools-4.15.0-1110
  linux-azure-cloud-tools-4.15.0-1111 linux-azure-headers-4.13.0-1011
  linux-azure-headers-4.13.0-1014 linux-azure-headers-4.13.0-1018
  linux-azure-headers-4.15.0-1013 linux-azure-headers-4.15.0-1014
  linux-azure-headers-4.15.0-1018 linux-azure-headers-4.15.0-1019
  linux-azure-headers-4.15.0-1021 linux-azure-headers-4.15.0-1022
  linux-azure-headers-4.15.0-1023 linux-azure-headers-4.15.0-1025
  linux-azure-headers-4.15.0-1031 linux-azure-headers-4.15.0-1032
  linux-azure-headers-4.15.0-1035 linux-azure-headers-4.15.0-1036
  linux-azure-headers-4.15.0-1037 linux-azure-headers-4.15.0-1039
  linux-azure-headers-4.15.0-1040 linux-azure-headers-4.15.0-1041
  linux-azure-headers-4.15.0-1045 linux-azure-headers-4.15.0-1046
  linux-azure-headers-4.15.0-1047 linux-azure-headers-4.15.0-1049
  linux-azure-headers-4.15.0-1050 linux-azure-headers-4.15.0-1051
  linux-azure-headers-4.15.0-1052 linux-azure-headers-4.15.0-1055
  linux-azure-headers-4.15.0-1056 linux-azure-headers-4.15.0-1057
  linux-azure-headers-4.15.0-1059 linux-azure-headers-4.15.0-1060
  linux-azure-headers-4.15.0-1061 linux-azure-headers-4.15.0-1063
  linux-azure-headers-4.15.0-1064 linux-azure-headers-4.15.0-1066
  linux-azure-headers-4.15.0-1067 linux-azure-headers-4.15.0-1069
  linux-azure-headers-4.15.0-1071 linux-azure-headers-4.15.0-1075
  linux-azure-headers-4.15.0-1077 linux-azure-headers-4.15.0-1082
  linux-azure-headers-4.15.0-1083 linux-azure-headers-4.15.0-1089
  linux-azure-headers-4.15.0-1091 linux-azure-headers-4.15.0-1092
  linux-azure-headers-4.15.0-1093 linux-azure-headers-4.15.0-1095
  linux-azure-headers-4.15.0-1096 linux-azure-headers-4.15.0-1098
  linux-azure-headers-4.15.0-1100 linux-azure-headers-4.15.0-1102
  linux-azure-headers-4.15.0-1103 linux-azure-headers-4.15.0-1106
  linux-azure-headers-4.15.0-1108 linux-azure-headers-4.15.0-1109
  linux-azure-headers-4.15.0-1110 linux-azure-headers-4.15.0-1111
  linux-azure-tools-4.13.0-1011 linux-azure-tools-4.13.0-1014
  linux-azure-tools-4.13.0-1018 linux-azure-tools-4.15.0-1013
  linux-azure-tools-4.15.0-1014 linux-azure-tools-4.15.0-1018
  linux-azure-tools-4.15.0-1019 linux-azure-tools-4.15.0-1021
  linux-azure-tools-4.15.0-1022 linux-azure-tools-4.15.0-1023
  linux-azure-tools-4.15.0-1025 linux-azure-tools-4.15.0-1031
  linux-azure-tools-4.15.0-1032 linux-azure-tools-4.15.0-1035
  linux-azure-tools-4.15.0-1036 linux-azure-tools-4.15.0-1037
  linux-azure-tools-4.15.0-1039 linux-azure-tools-4.15.0-1040
  linux-azure-tools-4.15.0-1041 linux-azure-tools-4.15.0-1045
  linux-azure-tools-4.15.0-1046 linux-azure-tools-4.15.0-1047
  linux-azure-tools-4.15.0-1049 linux-azure-tools-4.15.0-1050
  linux-azure-tools-4.15.0-1051 linux-azure-tools-4.15.0-1052
  linux-azure-tools-4.15.0-1055 linux-azure-tools-4.15.0-1056
  linux-azure-tools-4.15.0-1057 linux-azure-tools-4.15.0-1059
  linux-azure-tools-4.15.0-1060 linux-azure-tools-4.15.0-1061
  linux-azure-tools-4.15.0-1063 linux-azure-tools-4.15.0-1064
  linux-azure-tools-4.15.0-1066 linux-azure-tools-4.15.0-1067
  linux-azure-tools-4.15.0-1069 linux-azure-tools-4.15.0-1071
  linux-azure-tools-4.15.0-1075 linux-azure-tools-4.15.0-1077
  linux-azure-tools-4.15.0-1082 linux-azure-tools-4.15.0-1083
  linux-azure-tools-4.15.0-1089 linux-azure-tools-4.15.0-1091
  linux-azure-tools-4.15.0-1092 linux-azure-tools-4.15.0-1093
  linux-azure-tools-4.15.0-1095 linux-azure-tools-4.15.0-1096
  linux-azure-tools-4.15.0-1098 linux-azure-tools-4.15.0-1100
  linux-azure-tools-4.15.0-1102 linux-azure-tools-4.15.0-1103
  linux-azure-tools-4.15.0-1106 linux-azure-tools-4.15.0-1108
  linux-azure-tools-4.15.0-1109 linux-azure-tools-4.15.0-1110
  linux-azure-tools-4.15.0-1111 linux-cloud-tools-4.15.0-1037-azure
  linux-cloud-tools-4.15.0-1039-azure linux-cloud-tools-4.15.0-1040-azure
  linux-cloud-tools-4.15.0-1041-azure linux-cloud-tools-4.15.0-1045-azure
  linux-cloud-tools-4.15.0-1046-azure linux-cloud-tools-4.15.0-1047-azure
  linux-cloud-tools-4.15.0-1049-azure linux-cloud-tools-4.15.0-1050-azure
  linux-cloud-tools-4.15.0-1051-azure linux-cloud-tools-4.15.0-1052-azure
  linux-cloud-tools-4.15.0-1055-azure linux-cloud-tools-4.15.0-1056-azure
  linux-cloud-tools-4.15.0-1057-azure linux-cloud-tools-4.15.0-1059-azure
  linux-cloud-tools-4.15.0-1060-azure linux-cloud-tools-4.15.0-1061-azure
  linux-cloud-tools-4.15.0-1063-azure linux-cloud-tools-4.15.0-1064-azure
  linux-cloud-tools-4.15.0-1066-azure linux-cloud-tools-4.15.0-1067-azure
  linux-cloud-tools-4.15.0-1069-azure linux-cloud-tools-4.15.0-1071-azure
  linux-cloud-tools-4.15.0-1075-azure linux-cloud-tools-4.15.0-1077-azure
  linux-cloud-tools-4.15.0-1082-azure linux-cloud-tools-4.15.0-1083-azure
  linux-cloud-tools-4.15.0-1089-azure linux-cloud-tools-4.15.0-1091-azure
  linux-cloud-tools-4.15.0-1092-azure linux-cloud-tools-4.15.0-1093-azure
  linux-cloud-tools-4.15.0-1095-azure linux-cloud-tools-4.15.0-1096-azure
  linux-cloud-tools-4.15.0-1098-azure linux-cloud-tools-4.15.0-1100-azure
  linux-cloud-tools-4.15.0-1102-azure linux-cloud-tools-4.15.0-1103-azure
  linux-cloud-tools-4.15.0-1106-azure linux-cloud-tools-4.15.0-1108-azure
  linux-cloud-tools-4.15.0-1109-azure linux-cloud-tools-4.15.0-1110-azure
  linux-cloud-tools-4.15.0-1111-azure linux-headers-4.13.0-1011-azure
  linux-headers-4.13.0-1014-azure linux-headers-4.13.0-1018-azure
  linux-headers-4.15.0-1013-azure linux-headers-4.15.0-1014-azure
  linux-headers-4.15.0-1018-azure linux-headers-4.15.0-1019-azure
  linux-headers-4.15.0-1021-azure linux-headers-4.15.0-1022-azure
  linux-headers-4.15.0-1023-azure linux-headers-4.15.0-1025-azure
  linux-headers-4.15.0-1031-azure linux-headers-4.15.0-1032-azure
  linux-headers-4.15.0-1035-azure linux-headers-4.15.0-1036-azure
  linux-headers-4.15.0-1037-azure linux-headers-4.15.0-1039-azure
  linux-headers-4.15.0-1040-azure linux-headers-4.15.0-1041-azure
  linux-headers-4.15.0-1045-azure linux-headers-4.15.0-1046-azure
  linux-headers-4.15.0-1047-azure linux-headers-4.15.0-1049-azure
  linux-headers-4.15.0-1050-azure linux-headers-4.15.0-1051-azure
  linux-headers-4.15.0-1052-azure linux-headers-4.15.0-1055-azure
  linux-headers-4.15.0-1056-azure linux-headers-4.15.0-1057-azure
  linux-headers-4.15.0-1059-azure linux-headers-4.15.0-1060-azure
  linux-headers-4.15.0-1061-azure linux-headers-4.15.0-1063-azure
  linux-headers-4.15.0-1064-azure linux-headers-4.15.0-1066-azure
  linux-headers-4.15.0-1067-azure linux-headers-4.15.0-1069-azure
  linux-headers-4.15.0-1071-azure linux-headers-4.15.0-1075-azure
  linux-headers-4.15.0-1077-azure linux-headers-4.15.0-1082-azure
  linux-headers-4.15.0-1083-azure linux-headers-4.15.0-1089-azure
  linux-headers-4.15.0-1091-azure linux-headers-4.15.0-1092-azure
  linux-headers-4.15.0-1093-azure linux-headers-4.15.0-1095-azure
  linux-headers-4.15.0-1096-azure linux-headers-4.15.0-1098-azure
  linux-headers-4.15.0-1100-azure linux-headers-4.15.0-1102-azure
  linux-headers-4.15.0-1103-azure linux-headers-4.15.0-1106-azure
  linux-headers-4.15.0-1108-azure linux-headers-4.15.0-1109-azure
  linux-headers-4.15.0-1110-azure linux-headers-4.15.0-1111-azure
  linux-image-4.13.0-1011-azure linux-image-4.13.0-1014-azure
  linux-image-4.13.0-1018-azure linux-image-4.15.0-1013-azure
  linux-image-4.15.0-1014-azure linux-image-4.15.0-1018-azure
  linux-image-4.15.0-1019-azure linux-image-4.15.0-1021-azure
  linux-image-4.15.0-1022-azure linux-image-4.15.0-1023-azure
  linux-image-4.15.0-1025-azure linux-image-4.15.0-1031-azure
  linux-image-4.15.0-1032-azure linux-image-4.15.0-1035-azure
  linux-image-4.15.0-1036-azure linux-image-4.15.0-1037-azure
  linux-image-4.15.0-1039-azure linux-image-4.15.0-1040-azure
  linux-image-4.15.0-1041-azure linux-image-4.15.0-1045-azure
  linux-image-4.15.0-1046-azure linux-image-4.15.0-1047-azure
  linux-image-4.15.0-1049-azure linux-image-4.15.0-1050-azure
  linux-image-4.15.0-1051-azure linux-image-4.15.0-1052-azure
  linux-image-4.15.0-1055-azure linux-image-4.15.0-1056-azure
  linux-image-4.15.0-1057-azure linux-image-4.15.0-1059-azure
  linux-image-4.15.0-1060-azure linux-image-4.15.0-1061-azure
  linux-image-4.15.0-1063-azure linux-image-4.15.0-1064-azure
  linux-image-4.15.0-1066-azure linux-image-4.15.0-1067-azure
  linux-image-4.15.0-1069-azure linux-image-4.15.0-1071-azure
  linux-image-4.15.0-1075-azure linux-image-4.15.0-1077-azure
  linux-image-4.15.0-1082-azure linux-image-4.15.0-1083-azure
  linux-image-4.15.0-1089-azure linux-image-4.15.0-1091-azure
  linux-image-4.15.0-1092-azure linux-image-4.15.0-1093-azure
  linux-image-4.15.0-1095-azure linux-image-4.15.0-1096-azure
  linux-image-4.15.0-1098-azure linux-image-4.15.0-1100-azure
  linux-image-4.15.0-1102-azure linux-image-4.15.0-1103-azure
  linux-image-4.15.0-1106-azure linux-image-4.15.0-1108-azure
  linux-image-4.15.0-1109-azure linux-image-4.15.0-1110-azure
  linux-image-4.15.0-1111-azure linux-modules-4.15.0-1013-azure
  linux-modules-4.15.0-1014-azure linux-modules-4.15.0-1018-azure
  linux-modules-4.15.0-1019-azure linux-modules-4.15.0-1021-azure
  linux-modules-4.15.0-1022-azure linux-modules-4.15.0-1023-azure
  linux-modules-4.15.0-1025-azure linux-modules-4.15.0-1031-azure
  linux-modules-4.15.0-1032-azure linux-modules-4.15.0-1035-azure
  linux-modules-4.15.0-1036-azure linux-modules-4.15.0-1037-azure
  linux-modules-4.15.0-1039-azure linux-modules-4.15.0-1040-azure
  linux-modules-4.15.0-1041-azure linux-modules-4.15.0-1045-azure
  linux-modules-4.15.0-1046-azure linux-modules-4.15.0-1047-azure
  linux-modules-4.15.0-1049-azure linux-modules-4.15.0-1050-azure
  linux-modules-4.15.0-1051-azure linux-modules-4.15.0-1052-azure
  linux-modules-4.15.0-1055-azure linux-modules-4.15.0-1056-azure
  linux-modules-4.15.0-1057-azure linux-modules-4.15.0-1059-azure
  linux-modules-4.15.0-1060-azure linux-modules-4.15.0-1061-azure
  linux-modules-4.15.0-1063-azure linux-modules-4.15.0-1064-azure
  linux-modules-4.15.0-1066-azure linux-modules-4.15.0-1067-azure
  linux-modules-4.15.0-1069-azure linux-modules-4.15.0-1071-azure
  linux-modules-4.15.0-1075-azure linux-modules-4.15.0-1077-azure
  linux-modules-4.15.0-1082-azure linux-modules-4.15.0-1083-azure
  linux-modules-4.15.0-1089-azure linux-modules-4.15.0-1091-azure
  linux-modules-4.15.0-1092-azure linux-modules-4.15.0-1093-azure
  linux-modules-4.15.0-1095-azure linux-modules-4.15.0-1096-azure
  linux-modules-4.15.0-1098-azure linux-modules-4.15.0-1100-azure
  linux-modules-4.15.0-1102-azure linux-modules-4.15.0-1103-azure
  linux-modules-4.15.0-1106-azure linux-modules-4.15.0-1108-azure
  linux-modules-4.15.0-1109-azure linux-modules-4.15.0-1110-azure
  linux-modules-4.15.0-1111-azure linux-tools-4.13.0-1011-azure
  linux-tools-4.13.0-1014-azure linux-tools-4.13.0-1018-azure
  linux-tools-4.15.0-1013-azure linux-tools-4.15.0-1014-azure
  linux-tools-4.15.0-1018-azure linux-tools-4.15.0-1019-azure
  linux-tools-4.15.0-1021-azure linux-tools-4.15.0-1022-azure
  linux-tools-4.15.0-1023-azure linux-tools-4.15.0-1025-azure
  linux-tools-4.15.0-1031-azure linux-tools-4.15.0-1032-azure
  linux-tools-4.15.0-1035-azure linux-tools-4.15.0-1036-azure
  linux-tools-4.15.0-1037-azure linux-tools-4.15.0-1039-azure
  linux-tools-4.15.0-1040-azure linux-tools-4.15.0-1041-azure
  linux-tools-4.15.0-1045-azure linux-tools-4.15.0-1046-azure
  linux-tools-4.15.0-1047-azure linux-tools-4.15.0-1049-azure
  linux-tools-4.15.0-1050-azure linux-tools-4.15.0-1051-azure
  linux-tools-4.15.0-1052-azure linux-tools-4.15.0-1055-azure
  linux-tools-4.15.0-1056-azure linux-tools-4.15.0-1057-azure
  linux-tools-4.15.0-1059-azure linux-tools-4.15.0-1060-azure
  linux-tools-4.15.0-1061-azure linux-tools-4.15.0-1063-azure
  linux-tools-4.15.0-1064-azure linux-tools-4.15.0-1066-azure
  linux-tools-4.15.0-1067-azure linux-tools-4.15.0-1069-azure
  linux-tools-4.15.0-1071-azure linux-tools-4.15.0-1075-azure
  linux-tools-4.15.0-1077-azure linux-tools-4.15.0-1082-azure
  linux-tools-4.15.0-1083-azure linux-tools-4.15.0-1089-azure
  linux-tools-4.15.0-1091-azure linux-tools-4.15.0-1092-azure
  linux-tools-4.15.0-1093-azure linux-tools-4.15.0-1095-azure
  linux-tools-4.15.0-1096-azure linux-tools-4.15.0-1098-azure
  linux-tools-4.15.0-1100-azure linux-tools-4.15.0-1102-azure
  linux-tools-4.15.0-1103-azure linux-tools-4.15.0-1106-azure
  linux-tools-4.15.0-1108-azure linux-tools-4.15.0-1109-azure
  linux-tools-4.15.0-1110-azure linux-tools-4.15.0-1111-azure
  python-backports.ssl-match-hostname python-cached-property
  python-cffi-backend python-chardet python-cryptography python-docker
  python-dockerpty python-docopt python-enum34 python-funcsigs
  python-functools32 python-idna python-ipaddress python-jsonschema
  python-mock python-ndg-httpsclient python-openssl python-pbr
  python-pkg-resources python-pyasn1 python-requests python-six
  python-texttable python-urllib3 python-websocket python-yaml
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python3-acme python3-certbot python3-requests-toolbelt
Suggested packages:
  python3-certbot-apache python-certbot-doc python-acme-doc
The following NEW packages will be installed:
  python3-requests-toolbelt
The following packages will be upgraded:
  certbot python3-acme python3-certbot
3 upgraded, 1 newly installed, 0 to remove and 128 not upgraded.
Need to get 310 kB of archives.
After this operation, 339 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://ppa.launchpad.net/certbot/certbot/ubuntu xenial/main amd64 python3-requests-toolbelt all 0.8.0-1+ubuntu16.04.1+certbot+1 [38.3 kB]
Get:2 http://ppa.launchpad.net/certbot/certbot/ubuntu xenial/main amd64 python3-acme all 0.31.0-2+ubuntu16.04.6+certbot+2 [50.6 kB]
Get:3 http://ppa.launchpad.net/certbot/certbot/ubuntu xenial/main amd64 certbot all 0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3 [11.2 kB]
Get:4 http://ppa.launchpad.net/certbot/certbot/ubuntu xenial/main amd64 python3-certbot all 0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3 [209 kB]
Fetched 310 kB in 1s (250 kB/s)      
Selecting previously unselected package python3-requests-toolbelt.
(Reading database ... 1557293 files and directories currently installed.)
Preparing to unpack .../python3-requests-toolbelt_0.8.0-1+ubuntu16.04.1+certbot+1_all.deb ...
Unpacking python3-requests-toolbelt (0.8.0-1+ubuntu16.04.1+certbot+1) ...
Preparing to unpack .../python3-acme_0.31.0-2+ubuntu16.04.6+certbot+2_all.deb ...
Unpacking python3-acme (0.31.0-2+ubuntu16.04.6+certbot+2) over (0.22.2-1+ubuntu16.04.1+certbot+1) ...
Preparing to unpack .../certbot_0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3_all.deb ...
Unpacking certbot (0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3) over (0.22.2-1+ubuntu16.04.1+certbot+1) ...
Preparing to unpack .../python3-certbot_0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3_all.deb ...
Unpacking python3-certbot (0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3) over (0.22.2-1+ubuntu16.04.1+certbot+1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up python3-requests-toolbelt (0.8.0-1+ubuntu16.04.1+certbot+1) ...
Setting up python3-acme (0.31.0-2+ubuntu16.04.6+certbot+2) ...
Setting up python3-certbot (0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3) ...
Setting up certbot (0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3) ...
Installing new version of config file /etc/cron.d/certbot ...
certbot.service is a disabled or a static unit, not starting it.
root@scslin:/home/scslin# sudo certbot update_account
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Enter email address (used for urgent renewal and security notices) (Enter 'c' to
cancel): nydalal@gmail.com
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Would you be willing to share your email address with the Electronic Frontier
Foundation, a founding partner of the Let's Encrypt project and the non-profit
organization that develops Certbot? We'd like to send you email about our work
encrypting the web, EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: N

IMPORTANT NOTES:
 - Your e-mail address was updated to nydalal@gmail.com.
root@scslin:/home/scslin# sudo systemctl restart nginx^C
root@scslin:/home/scslin# exit
exit
scslin@scslin:~$ sudo certbot renew
Saving debug log to /var/log/letsencrypt/letsencrypt.log

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Processing /etc/letsencrypt/renewal/scsapi.shreemaycommunity.org.conf
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Cert is due for renewal, auto-renewing...
Plugins selected: Authenticator nginx, Installer nginx
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org
Renewing an existing certificate
Performing the following challenges:
http-01 challenge for scsapi.shreemaycommunity.org
Waiting for verification...
Cleaning up challenges

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
new certificate deployed with reload of nginx server; fullchain is
/etc/letsencrypt/live/scsapi.shreemaycommunity.org/fullchain.pem
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Processing /etc/letsencrypt/renewal/shreemaycommunity.org.conf
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Cert is due for renewal, auto-renewing...
Plugins selected: Authenticator nginx, Installer nginx
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org
Renewing an existing certificate
Performing the following challenges:
http-01 challenge for shreemaycommunity.org
Waiting for verification...
Cleaning up challenges

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
new certificate deployed with reload of nginx server; fullchain is
/etc/letsencrypt/live/shreemaycommunity.org/fullchain.pem
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Processing /etc/letsencrypt/renewal/zoom.shreemaycommunity.org.conf
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Cert is due for renewal, auto-renewing...
Plugins selected: Authenticator nginx, Installer nginx
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org
Renewing an existing certificate
Performing the following challenges:
http-01 challenge for zoom.shreemaycommunity.org
Waiting for verification...
Cleaning up challenges

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
new certificate deployed with reload of nginx server; fullchain is
/etc/letsencrypt/live/zoom.shreemaycommunity.org/fullchain.pem
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

Congratulations, all renewals succeeded. The following certs have been renewed:
  /etc/letsencrypt/live/scsapi.shreemaycommunity.org/fullchain.pem (success)
  /etc/letsencrypt/live/shreemaycommunity.org/fullchain.pem (success)
  /etc/letsencrypt/live/zoom.shreemaycommunity.org/fullchain.pem (success)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
scslin@scslin:~$ 


