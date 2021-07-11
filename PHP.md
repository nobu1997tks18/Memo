# PHP

## MAMPでサーバー切り忘れた時
1. lsof -i:80でhttodをすべて切る
2. sudo apachectl stop
3. MAMPで再起動


## Cake
### プロジェクト作成
|||
|:--|:--|
|php -r "readfile('https://getcomposer.org/installer'); \| php|composer.pharの生成	|
|php composer.phar create-project --prefer-dist cakephp/app:4.* my_app_name |プロジェクト作成|
|php -r　"readfile('https://getcomposer.org/installer');" \| php|プロジェクトが作れない|

### MVC作成
|||
|:--|:--|
|bin/cake bake controller Users|コントローラー作成	
|bin/cake bake model Users|モデル作成コマンド	

### マイグレーションコマンド
|||
|:--|:--|
|bin/cake bake migration_snapshot |テーブル名 マイグレーションファイル作成	
|bin/cake migrations migrate| マイグレーション実行（1個ずつ）	
|bin/cake migrations mark_migrated |マイグレーション実行（全て）	
|bin/cake migrations rollback| ロールバック（1個）	
|bin/cake migrations rollback -t ID| ロールバック（指定したところまで）	
|bin/cake migrations status| マイグレーションのステータス確認	
|bin/cake migrations seed |seedファイル読み込み	

MAMPのMySqlに接続したい
mysqlの指定（app_local.phpに追加以下を追記）	'unix_socket' => '/Applications/MAMP/tmp/mysql/mysql.sock'
エラーログ・ファイル書き込み　
error_log(print_r($array,true),"3","C:/xampp/log/debug.log");
1. errer_log関数の第1引数に出力したい変数/文字列を入れる。
2. print_rの第2引数のtrueを渡してあげると配列が展開されてログに出力される。
3. error_log関数の第2引数に設定している”3”は任意のファイルに出力ということ
4. error_log関数の第3引数に設定しているパスは出力したい任意のファイルパスを入れること


### 開発メモ
#### 2021/05/23　フォームでパスワードがinvalidになる
* User.phpのaccesibleでpasswordをtrueにする
* そもそもentrance_dateでもエラー起きてた
* dumpで確認するとわかりやすくなる

#### 2021/05/23　マイグレーションファイルが外部キーのせいでロールバックできない
* changeメソッドがあるとupとdownメソッド適用されない
* 外部キーの制約をdownメソッドで解除しないといけない

## Laravel
### Laravelコマンド
|||
|:--|:--|
|composer create-project "laravel/laravel=5.8.*" project_name |プロジェクト作成 : 
|php artisan -v |バージョン確認 : 
|php artisan serve |サーバー立ち上げ : 
|php artisan make:controller Admin/NewsController |コントローラー作成 : 
|php artisan config:cache |envの設定反映コマンド : 
|php artisan make:auth ,php artisan migrate |authの設定コマンド : 
|php artisan make:migration create_news_table |migrationファイルの作成 : 
|php artisan migrate |migration実行 :
|php artisan migrate:rollback |migrationロールバック : 
|php artisan make:model News |Modelの作成コマンド : 

### SQLのバージョンが5.7以下だとLaravelのmigrationがうまく行かない
* バージョン確認 :mysql --v 
* 5.7系のインストール : brew install mysql@5.7
* 5.7系のパスを通す : echo 'export　PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc, source ~/.zshrc  
* 5.7の起動 : brew services start mysql@5.7 
* 5.7再起動 :brew services restart mysql@5.7
* バージョン再確認 : mysql --v 
* デフォルトのSQLの確認 :which mysql
* MySQLのリスト確認 :brew services list
* 必要ないものを止める : brew services stop mysql@5.6


