# django-docker

## build and django startproject

```bash
$ docker-compose build
```

start django project

```
$ docker-compose run --rm app django-admin startproject config .
```

## django database setting

edit app/source/config/settings.py DATABASE

```PYTHON
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'django',
        'USER': 'root',
        'PASSWORD': '',
        'HOST': 'db',
        'PORT': 3306,
    }
}
```

必要であれば以下も

```PYTHON
LANGUAGE_CODE = 'ja'
TIME_ZONE = 'Asia/Tokyo'
```

### docker-compose up -d

```bash
$ docker-compose up -d
```

### django database migrate and create superuser

```bash
$ docker exec -it app bash
```

django database migration

```bash
$ python3 manage.py migrate
```

django create superuser

```
$ python3 manage.py createsuperuser
```

### Login

[`localhost:8000/admin`](http://localhost:8000/admin/)

### DisallowedHost at と出る場合

app/source/config/settings.py
ALLOWED_HOSTS = []
を
ALLOWED_HOSTS = ['XXX.XXX.XXX.XXX']
等に置き換える
