# Shparhalka
## MySQL

Created dump:
```sh
mysqldump -u[USER_NAME] -p [DB_NAME] > dumpDB.sql
```
Restore dump:
```sh
mysql -u[USER_NAME] -p [DB_NAME] < dumpDB.sql
```
Created dump *.gz:
```sh
mysqldump -u[USER_NAME] -p [DB_NAME] | gzip -c9 > dumpDB.sql.gz
```
Restore dump *.gz:
```sh
zcat dumpDB.sql.gz | mysql -u[USER_NAME] -p [DB_NAME]
```
Created user and DB:
```sh
CREATE USER '[USER_NAME]'@'localhost' IDENTIFIED BY '[USER_PASS]';
CREATE DATABASE [DB_NAME];
GRANT ALL PRIVILEGES ON [DB_NAME].* TO '[USER_NAME]'@'localhost';
FLUSH PRIVILEGES;
```
DB list:
```sh
SHOW DATABASES;
```
User list:
```sh
SELECT User, Host FROM mysql.user;
```
User privilegas:
```sh
SHOW GRANTS FOR '[USER_NAME]'@'localhost';
```
Drop DB:
```sh
DROP DATABASE [DB_NAME];
```
Drop user:
```sh
DROP USER '[USER_NAME]'@'localhost';
```
List mysql user with bed privileges:
```sh
USE information_schema;
SELECT * FROM schema_privileges LEFT JOIN schemata ON (catalog_name=table_catalog and schema_name=TABLE_SCHEMA) WHERE schema_name IS NULL;
```
All DB size:
```sh
SELECT table_schema "database_name", sum( data_length + index_length )/1024/1024 "database size in MB" FROM information_schema.TABLES GROUP BY table_schema
```
