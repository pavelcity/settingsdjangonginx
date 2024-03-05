# Настройка Django / Nginx
## Создание конфигурационного файла для вашего Django-проекта:



## Создайте новый конфигурационный файл для вашего Django-проекта в директории

#### - Вы можете назвать файл по имени вашего проекта или как вам угодно
```
/etc/nginx/sites-available/
```

#### - Например
```
mvpcode_django.conf
```

```
sudo nano /etc/nginx/sites-available/mvpcode_django.conf
```


## Символическая ссылка в sites-enabled:
### Теперь создайте символическую ссылку на ваш файл конфигурации в директории sites-enabled:
```
sudo ln -s /etc/nginx/sites-available/mvpcode_django.conf /etc/nginx/sites-enabled/
```


### Полезные команды
``` 
sudo apt update
```

``` 
sudo apt install python3 python3-pip
```

``` 
pip3 --version
```

``` 
pip install gunicorn
```

``` 
pip install pipenv
```

``` 
pip cache purge
```

* `Подкоманда pip cache purge полностью очищает весь кэш, удаляя все загруженные пакеты. Это может быть полезно, если нужно освободить место на диске или обновить пакеты до последних версий`



#### Nginx

``` py linenums="1"
server {
    
    server_name 00.000.000.000;
    
    location /static/ {
        root '/var/www/mvpcode_django/';
    }
    
    location /media/ {
        root '/var/www/mvpcode_django/';
    }
    
    location / {
        include proxy_params;
        proxy_pass http://unix:/run/gunicorn.sock;
    }
}
```






