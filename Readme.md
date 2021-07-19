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
cancel): 
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


