##Repo en github del codigo helloworld en django

[Helloworld](https://github.com/django-ve/helloworld)

## Formato de Dockerfile
```Dockerfile

FROM python:3.4

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        sqlite3 git\
    && rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src/app
COPY requirements.txt ./
RUN pip install -r requirements.txt
RUN git clone https://github.com/django-ve/helloworld.git
RUN  python helloworld/manage.py migrate
EXPOSE 8000
CMD ["python", "helloworld/manage.py", "runserver", "0.0.0.0:8000"]


```
## requirements.txt
```
Django==1.9.4
```

## Docker Build
```

docker build  -t pablo1n7/django-hello . 

```

## Docker Run 
```

docker run -it -p 8000:8000 pablo1n7/django-hello

```
