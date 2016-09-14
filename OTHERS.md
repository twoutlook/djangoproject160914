


Need to allow 8000 for testing 
    demo@chttl-8acc489f1587c5dc:~$ sudo ufw status
    [sudo] password for demo:
    Status: active
    
    To                         Action      From
    --                         ------      ----
    22                         ALLOW       Anywhere
    80                         ALLOW       Anywhere
    21/tcp                     ALLOW       Anywhere
    10000/tcp                  ALLOW       Anywhere
    22 (v6)                    ALLOW       Anywhere (v6)
    80 (v6)                    ALLOW       Anywhere (v6)
    21/tcp (v6)                ALLOW       Anywhere (v6)
    10000/tcp (v6)             ALLOW       Anywhere (v6)
    
    demo@chttl-8acc489f1587c5dc:~$


For this case, ufw is better than editing iptables

    demo@chttl-8acc489f1587c5dc:~$ sudo ufw allow 8000
    Rule added
    Rule added (v6)
    demo@chttl-8acc489f1587c5dc:~$ sudo ufw status
    Status: active
    
    To                         Action      From
    --                         ------      ----
    22                         ALLOW       Anywhere
    80                         ALLOW       Anywhere
    21/tcp                     ALLOW       Anywhere
    10000/tcp                  ALLOW       Anywhere
    8000                       ALLOW       Anywhere
    22 (v6)                    ALLOW       Anywhere (v6)
    80 (v6)                    ALLOW       Anywhere (v6)
    21/tcp (v6)                ALLOW       Anywhere (v6)
    10000/tcp (v6)             ALLOW       Anywhere (v6)
    8000 (v6)                  ALLOW       Anywhere (v6)



# Use ufw --help, to check commands

    (myvenv) demo@chttl-8acc489f1587c5dc:~/webapp$ sudo ufw status
    Status: active
    
    To                         Action      From
    --                         ------      ----
    22                         ALLOW       Anywhere
    80                         ALLOW       Anywhere
    21/tcp                     ALLOW       Anywhere
    10000/tcp                  ALLOW       Anywhere
    8000                       DENY        Anywhere
    8080                       ALLOW       Anywhere
    22 (v6)                    ALLOW       Anywhere (v6)
    80 (v6)                    ALLOW       Anywhere (v6)
    21/tcp (v6)                ALLOW       Anywhere (v6)
    10000/tcp (v6)             ALLOW       Anywhere (v6)
    8000 (v6)                  DENY        Anywhere (v6)
    8080 (v6)                  ALLOW       Anywhere (v6)
    
    (myvenv) demo@chttl-8acc489f1587c5dc:~/webapp$ sudo ufw delete 8000
    ERROR: Could not find rule '8000'
    (myvenv) demo@chttl-8acc489f1587c5dc:~/webapp$ sudo ufw delete 5
    Deleting:
     deny 8000
    Proceed with operation (y|n)? y


## wsgi is ready? NOT REALLY

    demo@chttl-8acc489f1587c5dc:~$ apt list | grep libapache2-mod-wsgi-py3
    
    WARNING: apt does not have a stable CLI interface yet. Use with caution in scripts.
    
    libapache2-mod-wsgi-py3/trusty-updates,trusty-security 3.4-4ubuntu2.1.14.04.2 amd64
    demo@chttl-8acc489f1587c5dc:~$

## Need to install libapache2-mod-wsgi-py3

    (myvenv) demo@chttl-8acc489f1587c5dc:~/webapp$ sudo apt-get install libapache2-mod-wsgi-py3
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
      linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
      linux-headers-3.13.0-35 linux-headers-3.13.0-35-generic
      linux-image-3.13.0-32-generic linux-image-3.13.0-35-generic
      linux-image-extra-3.13.0-32-generic linux-image-extra-3.13.0-35-generic
    Use 'apt-get autoremove' to remove them.
    The following extra packages will be installed:
      libpython3.4
    The following NEW packages will be installed:
      libapache2-mod-wsgi-py3 libpython3.4
    0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
    Need to get 1,376 kB of archives.
    After this operation, 4,644 kB of additional disk space will be used.
    Do you want to continue? [Y/n] Y




## manage.py --help to see commands
./manage.py collectstatic



## My first work wsgi was usig [Digitalocean's article](https://www.digitalocean.com/community/tutorials/how-to-serve-django-applications-with-apache-and-mod_wsgi-on-ubuntu-14-04)


    <VirtualHost *:80>
    Alias /static /home/demo/djangogirls/djangogirls004/static
    <Directory /home/demo/djangogirls/djangogirls004/static>
    Require all granted
    </Directory>
    
    <Directory /home/demo/djangogirls/djangogirls004/mysite>
    <Files wsgi.py>
    Require all granted
    </Files>
    </Directory>
    
    WSGIDaemonProcess myproject python-path=/home/demo/djangogirls/djangogirls004:/home/demo/djangogirls/myvenv/lib/python3.5/site-packages
    WSGIProcessGroup myproject
    WSGIScriptAlias / /home/demo/djangogirls/djangogirls004/mysite/wsgi.py
    </VirtualHost>

