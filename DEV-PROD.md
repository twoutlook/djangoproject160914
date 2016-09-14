# Development and Product environment

1. Python 3.5
2. Django 1.10
3. in virtual environment

# Plan ahead


1. Don't put myvenv to github
2. Follow [Djangogirls' advice] (http://tutorial.djangogirls.org/en/deploy/)

create .gitignore with content:
    
    *.pyc
    __pycache__
    myvenv
    db.sqlite3
    /static
    .DS_Store


## c9.io, Python 3.5  
http://tutorial.djangogirls.org/en/python_installation/
  
    twoutlook:~/workspace (master) $ python --version
    Python 2.7.6
    twoutlook:~/workspace (master) $ python3 --version
    Python 3.4.3
    twoutlook:~/workspace (master) $ 
    sudo apt-get install python3.5
    twoutlook:~/workspace (master) $ python3.5 --version
    Python 3.5.2
    
## c9.io, Python 3.5 virtual environment    
Inspired by [djangogirls' django_installation ](http://tutorial.djangogirls.org/en/django_installation/  )
  


    sudo apt-get install python3.5-venv
    python3.5 -m venv myvenv
    source myvenv/bin/activate
    pip install django 

Current (2016-09-14) latest Django version is 1.10.1
    
## hicloud, install Python 3.5 on Ubuntu 14.04     
Got instruction from [askubuntu](http://askubuntu.com/questions/682869/how-do-i-install-newer-python-versions-using-apt-get)
    
    sudo add-apt-repository ppa:fkrull/deadsnakes
    sudo apt-get update
    sudo apt-get install python3.5

## hicloud, Setup virtual envrionment just same as c9.io

    sudo apt-get install python3.5-venv
    python3.5 -m venv myvenv
    source myvenv/bin/activate
    pip install django 


## hicloud, 
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

## wsgi is ready

    demo@chttl-8acc489f1587c5dc:~$ apt list | grep libapache2-mod-wsgi-py3
    
    WARNING: apt does not have a stable CLI interface yet. Use with caution in scripts.
    
    libapache2-mod-wsgi-py3/trusty-updates,trusty-security 3.4-4ubuntu2.1.14.04.2 amd64
    demo@chttl-8acc489f1587c5dc:~$

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

For webapp case, to modifiy

    <VirtualHost *:8080>
    Alias /static /home/demo/webapp/djangoproject160914/static
    <Directory /home/demo/webapp/djangoproject160914/static>
    Require all granted
    </Directory>
    
    <Directory /home/demo/webapp/djangoproject160914/mysite>
    <Files wsgi.py>
    Require all granted
    </Files>
    </Directory>
    
    WSGIDaemonProcess myproject python-path=/home/demo/webapp/djangoproject160914:/home/demo/webapp/myvenv/lib/python3.5/site-packages
    WSGIProcessGroup myproject
    WSGIScriptAlias / /home/demo/webapp/djangoproject160914/mysite/wsgi.py
    </VirtualHost>


# According to [Apache 2.4 doc] (http://httpd.apache.org/docs/2.4/vhosts/examples.html)
It can work for multiple ports.
We will keep 80 as traditional web and 8080 for Python-Django

# restart apache server



# c9.io



# hicloud LAMP(Apache2.4+MySQL5.5+PHP5.5) with Webmin

## Putty

## Webmin


## FileZilla 