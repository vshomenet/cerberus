# Cerberus

[назад к описанию](readme.md)

### Установка Cerberus
Установить nginx
```
apt update
apt install nginx
```

Добавить репозиторий
```
wget -O - https://develop.5ru.ru/repository/Other/public.gpg.key | apt-key add -
echo "deb https://develop.5ru.ru/repository/Debian/ all main" >> /etc/apt/sources.list
```

Установить Cerberus
```
apt update
apt install cerberus
```

### Настройка Cerberus
Основные настройки Cerberus хранятся в конфиг-файле */opt/cerberus/cerberus.conf*

Пример файла
```
[system]
time_get_check = 30
time_search_video = 90
enable_log = true
debug = false

[DB]
ip = 127.0.0.1
port = 27017
login = admin
password = my_password
db_name = cerberus
```
Описание параметров конфиг-файла

Блок `[system]`
* enable_log - по умолчанию true. Запись логов идет в файл. false - отключить логирование.
* debug - по умолчанию false. Необходимо для отладки приложения. Только для опытных пользователей linux.
* time_get_check - Интервал времени с какой регулярностью опрашивать касссу (в секундах)
* time_search_video - Временной диапазон поиска видео. За сколько времени до пробития чека начинать искать видео (в секундах)

Блок `[DB]`
* ip = 127.0.0.1 - IP адрес mongoDB
* port = 27017 - порт подключения к mongoDB
* login = admin - пользователь mongoDB
* password = my_password - пароль пользователя mongoDB
* db_name = cerberus - база данных с которой будет работать Cerberus

### Обновление Cerberus
```
apt update
apt install cerberus
```
[назад к описанию](readme.md)