
# Follow [Djangogirls' tutorial](http://tutorial.djangogirls.org/en/django_start_project/)

## start project, mysite
    django-admin startproject mysite .
    
### change time zone and set static, mysite/settings.py

    TIME_ZONE = 'Asia/Taipei'

    STATIC_ROOT = os.path.join(BASE_DIR, 'static')
    
### initalize default database and create admin
    ./manage.py migrate
    ./manage.py createsuperuser
    
### on c9.io, to run server with envrionment variable $IP and $PORT
    ./manage.py runserver $IP:$PORT
    
### visit working website and login to admin
    
    https://djangoproject160914-dev2-twoutlook.c9users.io
    https://djangoproject160914-dev2-twoutlook.c9users.io/admin
    
### new terminal and activate virtual environment
    twoutlook:~/workspace (master) $ source myvenv/bin/activate
    (myvenv) twoutlook:~/workspace (master) $ 

## PuTTY hicloud
create a new Seesion, Appearance Font to 14-point
when open, copy/paste password --- I typed password before, Not necessary
top to show system info and to avoid short time disconnected
q to gain command line
  
### create non-root demo
Follow [Digitalocean's tutorial](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04)

    adduser demo
    gpasswd -a demo sudo
    su - demo
    exit
### install git beforehand
    sudo apt-get install git

### decide to use djangoproject 

    mkdir webapp
    cd webapp
    git clone https://github.com/twoutlook/djangoproject160914.git
    
### install python3.5 on Ubuntu 14.04
http://askubuntu.com/questions/682869/how-do-i-install-newer-python-versions-using-apt-get
    sudo add-apt-repository ppa:fkrull/deadsnakes
    sudo apt-get update
    sudo apt-get install python3.5