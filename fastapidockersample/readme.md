```sh
docker-compose build
docker-compose up
```


## Migrate DB
```sh
# api モジュールの migrate_db スクリプトを実行する
$ docker-compose exec demo-app poetry run python -m api.migrate_db
$ docker-compose exec db mysql demo
mysql> SHOW TABLES;
+----------------+
| Tables_in_demo |
+----------------+
| dones          |
| tasks          |
+----------------+
2 rows in set (0.01 sec)

mysql> DESCRIBE tasks;
+-------+---------------+------+-----+---------+----------------+
| Field | Type          | Null | Key | Default | Extra          |
+-------+---------------+------+-----+---------+----------------+
| id    | int           | NO   | PRI | NULL    | auto_increment |
| title | varchar(1024) | YES  |     | NULL    |                |
+-------+---------------+------+-----+---------+----------------+
2 rows in set (0.05 sec)

mysql> DESCRIBE dones;
+-------+------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+-------+------+------+-----+---------+-------+
| id    | int  | NO   | PRI | NULL    |       |
+-------+------+------+-----+---------+-------+
1 row in set (0.00 sec)
```
