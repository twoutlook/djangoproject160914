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
    
    
## hicloud, install Python 3.5 on Ubuntu 14.04     
Got instruction from [askubuntu](http://askubuntu.com/questions/682869/how-do-i-install-newer-python-versions-using-apt-get)
    
    sudo add-apt-repository ppa:fkrull/deadsnakes
    sudo apt-get update
    sudo apt-get install python3.5
    
# c9.io



# hicloud LAMP(Apache2.4+MySQL5.5+PHP5.5) with Webmin

## Putty

## Webmin


## FileZilla 