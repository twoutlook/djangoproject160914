# Development and Product environment
要確定在開發和正式環境有著一樣的virtual environment:
- Python 3.5
- Django 1.10

# Source code control plan ahead


Follow [Djangogirls' advice] (http://tutorial.djangogirls.org/en/deploy/), create .gitignore with contents:
    
    *.pyc
    __pycache__
    myvenv
    db.sqlite3
    /static
    .DS_Store

其中有三樣是開發者掌控不需上傳到 Github
- myvenv 是 virtual environment 的檔案夾
- db.sqlite3 在開發測試做的不要上傳，就不會在部署時覆蓋掉正式環境的數據
- static 是透過 ./manage.py collectstatic 生成的





# 在 c9.io, 安裝 Python 3.5  
    sudo apt-get install python3.5

經過嘗試可以這麼安裝, 回頭看 [djangogirls' django_installation ](http://tutorial.djangogirls.org/en/django_installation/  )，有提到。

# 在 hicloud Ubuntu 14.04, 安裝 Python 3.5 on    
根據 [askubuntu](http://askubuntu.com/questions/682869/how-do-i-install-newer-python-versions-using-apt-get)
    
    sudo add-apt-repository ppa:fkrull/deadsnakes
    sudo apt-get update
    sudo apt-get install python3.5



## 安裝 virtual environment, 在此 c9.io 和 hicloud 已相同    

    sudo apt-get install python3.5-venv
    python3.5 -m venv myvenv
    source myvenv/bin/activate
    pip install django 

當前, 2016-09-14, Django 版本是 1.10.1
    



# hicloud 正式環境需求, 參考[其它](OTHERS.md)
- 開通 8080 端口
- 安裝 libapache2-mod-wsgi-py3

# hicloud, Apache 的設定

/etc/apache2, 增列

    Listen 8080

/etc/apache2/sites-enabled/000-default.conf, 增列

個人偏好使用 FileZilla 下載到本機應對的檔案夾裡修改再上傳

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

參考:
- [Digitalocean's article](https://www.digitalocean.com/community/tutorials/how-to-serve-django-applications-with-apache-and-mod_wsgi-on-ubuntu-14-04), 第一次正式境成功運行就是參考這則文檔。
- [Apache 2.4 doc] (http://httpd.apache.org/docs/2.4/vhosts/examples.html)
- [Djangoproject] (https://docs.djangoproject.com/en/1.10/howto/deployment/wsgi/modwsgi/)

# 更改設定必需重起 apache server
    sudo service apache2 restart
可以 PuTTY 登入後下指令，也可以在端口 10000 的 Webmin 下指令。 


# c9.io



# hicloud LAMP(Apache2.4+MySQL5.5+PHP5.5) with Webmin

## Putty

## Webmin


## FileZilla 