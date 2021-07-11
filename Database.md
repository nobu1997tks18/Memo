# DataBase

## 接続

|title|content|
|:--|:--|
|MAMPのMysql接続|/Applications/MAMP/Library/bin/mysql -u root -p|
|MAMPのmysqlソケット|/Applications/MAMP/tmp/mysql/mysql.sock|

## コマンド

|||
|:--|:--|
|mysql.server start|サーバ始動|
|mysql.server stop|サーバ止める|
|mysql -u|ユーザー名 -p : ログイン|
|select Host, user, password from mysql.user|ユーザー一覧の取得|
|create user user_name@localhost IDENTIFIED BY 'password'|ユーザ作成|
|drop user username@localhost|ユーザ削除|
|show grants for 'user_name'@'host'|ユーザ権限の確認|
|grant all on *.* to 'username'@'localhost' IDENTIFIED BY 'password';|ユーザーに権限をすべて与える|
|show databases|データベース一覧表示|
|use [database] |データベース使用|
|create database [database]|データベース作成|
|drop [database] |データベース削除|
|show tables [database] |テーブル一覧表示|
|show fields from [tables] |フィールド構成の確認|
|show full columns from [tables] |データベースのカラム表示|
|alter table department rename to departments; |テーブル名変更|
|ALTER TABLE [table_name] change [old_column] [new_column] [data_type];|カラム名変更|
|ALTER TABLE code_master auto_increment = 1;|Auto_incrementリセット|
|alter table [table_name] drop index [Column_name];|Unique外す|
|ALTER TABLE incomes MODIFY walfare_cost int NOT NULL|Not nullを外す方法|
|foreign key(user_id) references users(id) on delete cascade|外部キーの設定|
|alter table users drop foreign key users_ibfk_1;;| 外部キー制約を外す |
