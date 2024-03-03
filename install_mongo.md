# Cerberus

[назад к описанию](readme.md)

###  Установка и настройка mongoDB on debian 11

Установка mongoDB
```
apt update
apt install gnupg curl
wget -qO -  https://pgp.mongodb.com/server-7.0.asc  | apt-key add -
echo "deb http://repo.mongodb.org/apt/debian bullseye/mongodb-org/7.0 main" | tee /etc/apt/sources.list.d/mongodb-org.list
apt update
apt install mongodb-org
systemctl enable --now mongod
```

Установить пароль администратора БД
```
mongosh
use admin
db.createUser({user: "root", pwd: "my_password",roles: [ { role: "root", db: "admin" } ]})
```

Отредактировать конфиг-файл  mongoDB */etc/mongod.conf*

Установить порт и IP для БД
```
net:
  port: 27017
  bindIp: 127.0.0.1, 192.168.0.1
```
Включить авторизацию по паролю
```
security:
  authorization: enabled
```

Перезапустить сервис mongoDB
```
systemctl restart mongod
```

Добавить базу данных для Cerberus
```
mongosh -u root -p 
use cerberus 
db.createUser({user: "admin", pwd: "my_password",roles: [ { role: "readWrite", db: "cerberus" } ]})
```

[назад к описанию](readme.md)