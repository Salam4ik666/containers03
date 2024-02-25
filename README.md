# IWNO3: Использование контейнеров как среды выполнения

- [IWNO3: Использование контейнеров как среды выполнения](#iwno3-использование-контейнеров-как-среды-выполнения)
  - [Цель работы](#цель-работы)
  - [Задание](#задание)
  - [Описание выполнения работы](#описание-выполнения-работы)
  - [Выводы](#выводы)

## Цель работы
Данная лабораторная работа призвана напомнить основные команды ОС Debian/Ubuntu. Также она позволит познакомиться с Docker и его основными командами.
## Задание
Запустить контейнер Ubuntu, установить Web-сервер Apache и вывести в браузере страницу с текстом "Hello, World!".
## Описание выполнения работы

Откройте терминал в папке containers03 и выполните команду:
```
docker run -ti -p 8000:80 --name containers03 ubuntu bash
```

В открывшемся окне выполните следующие команды и объясните их назначение:

```
apt update
apt install apache2 -y
service apache2 start
```

`apt update`: Эта команда используется для обновления списка доступных пакетов с удаленных репозиториев. 

`apt install apache2 -y`: Эта команда используется для установки пакета Apache HTTP Server с помощью менеджера пакетов APT. Флаг -y указывает, что ответ на все вопросы о подтверждении установки должен быть автоматически "да".

`service apache2 start`: После установки Apache необходимо запустить его службу, чтобы веб-сервер начал прослушивать запросы и обслуживать их. Эта команда запускает службу Apache.

Откройте браузер и введите в адресной строке http://localhost:8000. Что вы видите?

![скрин1](https://github.com/Salam4ik666/containers03/assets/159524637/7713efed-29d9-4488-b85a-f13010bbe1e4)



Выполните следующие команды:
```
ls -l /var/www/html/
echo "<h1>Hello, World</h1>" > /var/www/html/index.html
```
![скрин2](https://github.com/Salam4ik666/containers03/assets/159524637/28710720-8206-400d-aa6a-7fc8cfccf590)



Обновите страницу в браузере. Что вы видите?



Выполните следующие команды:
```
cd /etc/apache2/sites-enabled/
cat 000-default.conf
```
Что вы видите на экране?

```
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

Закройте окно терминала командой exit.

Просмотрите список контейнеров:
```
docker ps -a
```
![crhby3](https://github.com/Salam4ik666/containers03/assets/159524637/d02e72bb-3120-4572-8370-00a1124d1808)



Удалите контейнер:
```

Данная работа представляет собой лабораторную работу, целью которой является знакомство с основными командами операционной системы Debian/Ubuntu и Docker, а также выполнение задачи по развертыванию веб-сервера Apache в контейнере Docker.

В процессе выполнения работы были выполнены следующие шаги:

Запуск контейнера Ubuntu с использованием Docker.
Установка веб-сервера Apache внутри контейнера.
Просмотр страницы "Hello, World!" в веб-браузере.
Создание файла index.html с текстом "Hello, World!" в директории веб-сервера.
Просмотр конфигурационного файла Apache.
Каждый шаг сопровождался выполнением соответствующих команд и их объяснением. Работа также включает скриншоты результатов выполнения команд.

В ходе выполнения работы были продемонстрированы навыки работы с Docker, установка и настройка веб-сервера Apache в контейнере, а также основные команды операционной системы.

В целом, выполнение работы прошло успешно, и были достигнуты поставленные цели.
docker rm containers03
```

![image](https://github.com/S1ngle777/containers03/assets/128795707/fcbf971c-34a9-41f7-84d7-15976c1d9dc9)
