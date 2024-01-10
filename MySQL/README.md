# MySQL
***
### Расположение паролей к mysql
| Логин   | Расположение пароля              |
|---------|----------------------------------|
| bitrix0 | /bitrix/.settings.php            |
|         | /bitrix/.dbconn.php              |
|         | /bitrix/php_interface/dbconn.php |
| root    | root/.my.cnf                     |

***

### Экспорт/Импорт базы данных с индикатором прогресса

#### Для начала необходимо установить пакет pv (pipe viewer). Для CentOS:
`yum install -y pv`

#### Для Debian/Ubuntu:
`apt install -y pv`

#### Сделать дамп с отображение информации о прогрессе можно следующей командой.
`mysqldump -h <host_address> -u <user> -p<password> <db_name> | pv --size <size_db_MB> > <path_to_file>.sql`

#### Узнать размер баз данных можно выполнив следующую команду, подключившись к серверу баз данных.
`SELECT table_schema "DB Name",
    Round(Sum(data_length + index_length) / 1024 / 1024, 1) "DB Size in MB"
    FROM   information_schema.tables
    GROUP  BY table_schema;`

#### Пример использования команды.
`mysqldump -h localhost -u root -p'yZ3503E9iB4M' testbase | pv --size 1218M > testbase.sql`

#### Загрузить дамп с отображением информации о прогрессе можно следующей командой.
`pv <db_name>.sql | mysql -h<host_address> -u<user> -p<password> <db_name>`

#### Пример:
`pv testbase.sql | mysql -h localhost -u root -p'yZ3503E9iB4M' testbase`

#### При загрузке дампа указывать размер базы данных не обязательно, т.к. утилита pv уже знает размер загружаемого файла.

***

### Увеличение констант перед установкой большой базы

#### Из php консоли
`set global max_allowed_packet=1000000000;`

`set global net_buffer_length=1000000;`

***

### Команды для работы с пользователями

#### Получить пользователей
`SELECT host, user FROM mysql.user;`

#### Добавить пользователя
`create user 'bitrix0'@'localhost' identified by 'password';`
> Для внешних пользователей использовать '%' или конкретный ip вместо 'localhost'

#### Дать пользователю права на базу
`grant all on sitemanager.* to 'bitrix0'@'localhost';`