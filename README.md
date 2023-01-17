# システム要件

## PHPバージョンと拡張
- PHP = 8.1
- BCMath PHP拡張
- Ctype PHP拡張
- cURL PHP拡張
- DOM PHP拡張
- Fileinfo PHP拡張
- JSON PHP拡張
- Mbstring PHP拡張
- OpenSSL PHP拡張
- PCRE PHP拡張
- PDO PHP拡張
- Tokenizer PHP拡張
- XML PHP拡張
- INTL PHP拡張
- Imagick PHP拡張
- Mysqlnd PHP拡張
- ZIP PHP拡張
- MCrypt PHP拡張
- GD PHP拡張

## Database情報
- MySQL 8.0.x 


# Laravelの起動手順

```
cd /var/www
sudo git clone -b main git@github.com:EXURT-Ltd/d-sr.git  d-sr
 
sudo chown -R ec2-user. d-sr

cd d-sr
find ./storage -type d -exec chmod 777 {} \;
chmod 777 bootstrap/cache/

composer install --optimize-autoloader --no-dev

cp -p .env.example .env
php artisan key:generate
```

## ENVファイルの編集

### アプリケーション状態設定

```
APP_ENV=production  # 本番環境
APP_DEBUG=false     # デバッグモードOFF
APP_URL=https://domain.com
```

### ログ設定

```
LOG_CHANNEL=daily
LOG_LEVEL=error
```

### DBサーバー設定

```
DB_CONNECTION=mysql
DB_HOST=DBサーバホスト
DB_PORT=3306
DB_DATABASE=DB名
DB_USERNAME=DBユーザー
DB_PASSWORD=パスワード
```

### メール送信サーバ設定
```
MAIL_MAILER=smtp
MAIL_HOST=ホスト名
MAIL_PORT=ポート
MAIL_USERNAME=ユーザー名
MAIL_PASSWORD=パスワード
MAIL_ENCRYPTION=暗号化プロトコル(null|tls|ssl)  # メールサーバによります。
MAIL_FROM_ADDRESS=送信元メールアドレス
MAIL_FROM_NAME=送信元名前
```

### S3設定

```
FILESYSTEM_DISK=s3
AWS_ACCESS_KEY_ID=アクセスキー
AWS_SECRET_ACCESS_KEY=シークレットキー
AWS_DEFAULT_REGION=ap-northeast-1
```

### 設定最適化

```
php artisan config:cache
php artisan route:cache
php artisan view:cache
```
### テーブル作成

```
php artisan migrate --force
```

