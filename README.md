# django-mysql-quickstart

The quickstart demonstrates how to create and start django application and mysql which are containerized.
## 1. Create your project
```
❯ docker-compose run web django-admin.py startproject <your-project-name> .
```

## 2. Add two lines below in manage.py
```
import pymysql
pymysql.install_as_MySQLdb()
```

## 3. Set up database config in docker-compose.yaml and settings.py
```
environment:
    MYSQL_ROOT_PASSWORD: root
    MYSQL_DATABASE: <your-db-name>
 ```

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '<your-db-name>',
        'USER': 'root',
        'PASSWORD': 'root',
        'HOST': 'localhost',
        'PORT': '3306'
    }
}
```


## 4. Create and start containers
```
docker-compose up -d
```
