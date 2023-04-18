# django-mysql-quickstart

The quickstart provides a comprehensive guide for creating and launching a containerized Django application and MySQL database.

## 1. Create your project
```
docker-compose run web django-admin.py startproject <your-project-name> .
```

## 2. Add two lines in manage.py
```
import pymysql
pymysql.install_as_MySQLdb()
```

## 3. Configure your database
docker-compose.yaml
```
MYSQL_ROOT_PASSWORD:  root
      MYSQL_DATABASE: <your-db-name>
      MYSQL_USER:     <username>
      MYSQL_PASSWORD: <password>
 ```
settings.py
```
DATABASES = {
    'default': {
        'ENGINE':   'django.db.backends.mysql',
        'NAME':     '<your-db-name>',
        'USER':     '<username>',
        'PASSWORD': '<password>',
        'HOST':     'localhost',
        'PORT':     '3306'
    }
}
```


## 4. Create and start containers
```
docker-compose up -d
```


## 5. Create your application
```
docker exec -it web /bin/bash
```

```
python manage.py startapp <your-app-name>
```

## 6. Migrate your database to MySQL database

```
python manage.py makemigrations <your-app-name>
```

```
python manage.py migrate
```

## 7. Check if MySQL database is configured 
```
docker exec -it db /bin/bash
```
```
mysql -u root -proot
```
```
show databases;
```
```
use <your-db-name>;
```
```
show tables;
```

## 8. Have fun developing!
