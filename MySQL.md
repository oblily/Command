
# mysql -V

バージョン確認

# mysql -u [ユーザー名] -p

u / p ログイン \
mysql -h localhost -P 3306 -u example_user -p example_db

# exit

\q; \
quit \
ログアウト

## mysql -uroot -p -e "select * from users" test_db > /tmp/mysql.txt

SQL実行結果をファイルに出力

# User関連

## SELECT Host, User FROM mysql.user

ユーザー情報取得

## create user `testuser`@`localhost` IDENTIFIED BY 'password'

ユーザーの追加

## grant all privileges on test_db.* to testuser@localhost IDENTIFIED BY 'password'

ユーザーにDB操作権限を付与

## set password = password('hogehoge123')

ログイン中のユーザーのパスワードを設定する

set password for 'testuser'@'localhost' = password('hogehoge123');

特定のユーザーのパスワードを設定する場合

# DB関連

## show databases

データベース一覧の表示

## create database test_db

データベースの追加(test_dbを追加する場合)

## use test_db

データベースの選択(test_dbを選択する場合)

# Table関連

## show tables

テーブル一覧の表示

status ステータスまで表示する

## CREATE TABLE

テーブル作成

CREATE TABLE [テーブル名] (
  [フィールド名] [データ型] [オプション]
) ENGINE=[InnoDB/MyISAM] DEFAULT CHARSET=[文字コード];

例：
mysql > CREATE TABLE `m_users` ( \
&nbsp;&nbsp;&nbsp;&nbsp;`id` int NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT "ID", \
&nbsp;&nbsp;&nbsp;&nbsp;`user_name` VARCHAR(100) NOT NULL COMMENT "ユーザー名", \
 &nbsp;&nbsp;&nbsp;&nbsp;`mail_address` VARCHAR(200) NOT NULL COMMENT "メールアドレス", \
&nbsp;&nbsp;&nbsp;&nbsp;`password` VARCHAR(100) NOT NULL COMMENT "パスワード", \
&nbsp;&nbsp;&nbsp;&nbsp;`created` datetime DEFAULT NULL COMMENT "登録日", \
&nbsp;&nbsp;&nbsp;&nbsp;`modified` datetime DEFAULT NULL COMMENT "更新日" \
&nbsp;&nbsp;) ENGINE=InnoDB DEFAULT CHARSET=utf8;

## DROP TABLE [テーブル名]

テーブルの削除

## desc [テーブル名]

テーブル定義

SHOW FULL COLUMNS FROM [テーブル名];　詳細情報表示

# Record関連

## INSERT INTO [テーブル名] [フィールド名] VALUES [値]

追加行

例：
INSERT INTO m_users (user_name, mail_address, password, created, modified) \
&nbsp;&nbsp;&nbsp;&nbsp;VALUES ("Qii Taro", "qiitaro@hoge.com", "123123", now(), now())

## UPDATE [テーブル名] SET [フィールド名]=[値] [条件式]

更新行

例：UPDATE m_users SET user_name="Qii Takao", mail_address="qiitakao@hoge.com" WHERE id = 5;

## DELETE FROM [テーブル名] (WHERE [条件式])

レコード削除

## Alter table [テーブル名] add [フィールド名]=[値] [条件式]

テーブルの構造を変更する \
例： \
列追加：alter table test add col1 varchar(255) ; \
属性変更：
alter table test change col1 varchar(100); \
外部参照追加： \
ALTER TABLE XXA ADD FOREIGN KEY (col_id) REFERENCES XXB (id) ON UPDATE RESTRICT ON DELETE RESTRICT; \
カラム名の変更方法 \
ALTER TABLE tbl_name CHANGE [COLUMN] old_col_name column_definition; \
外部キーを削除する \
alter table article drop foreign key article_ibfk_1; \
外部キーを付ける \
alter table article add constraint article_ibfk_1 foreign key (user_id) references user(id) on delete cascade on update cascade; \
-- alter table article add foreign key (user_id) references user(id) on delete cascade on update cascade;

# DB DUMP関連

## mysqldump -u [ユーザー名] -p -x --all-databases > [出力ファイル名]

全データベースを対象とするのダンプをとる

## mysqldump -u [ユーザー名] -p -x test_db > [出力ファイル名]

test_dbデータベースを対象とするのダンプをとる

## mysqldump -u [ユーザー名] -p -x test_db users > [出力ファイル名]

test_dbデータベースのusersテーブルを対象とする

## mysqldump -u [ユーザー名] -p -x test_db users --where="id < 5" > [出力ファイル名]

test_dbデータベースのusersテーブルのデータ内でidが５未満を対象とする

# DB Retore関連

## mysql -u[ユーザー名] -p new_db < [ダンプファイル名]

リストア(定義ファイルからDDL作成)