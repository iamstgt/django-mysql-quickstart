# django-mysql-quickstart

The quickstart demonstrates how to create and start django application and mysql which are containerized.
## 1. Create your project
```docker-compose run web django-admin.py startproject <your-project-name> .```

## 2. Add two lines below in manage.py
```
import pymysql
pymysql.install_as_MySQLdb()
```

## 3. Set up database config in docker-compose.yaml and settings.py
docker-compose.yaml
```
MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: <your-db-name>
      MYSQL_USER: <username>
      MYSQL_PASSWORD: <password>
 ```
settings.py
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '<your-db-name>',
        'USER': '<username>',
        'PASSWORD': '<password>',
        'HOST': 'localhost',
        'PORT': '3306'
    }
}
```


## 4. Create and start containers
```docker-compose up -d```


## 5. SSH into the web container, create your app and migrate database to MySQL
```docker exec -it web /bin/bash```

```python manage.py startapp <your-app-name>```

```python manage.py makemigrations <your-app-name>```

```python manage.py migrate```


## 6. SSH into the db container and check if database is configured 
```docker exec -it db /bin/bash```

```mysql -u root -proot```

```show databases;```

```use <your-db-name>;```

```show tables;```


## 7. Have fun developing!
