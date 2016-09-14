
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

    