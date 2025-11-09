# ベースイメージをphp-fpm 8.3とする
FROM php:8.3-fpm

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    && docker-php-ext-install pdo pdo_mysql

# Composerのインストール バージョンは2.8.2とする
RUN php -r "copy('https://getcomposer.org/installer', '/tmp/composer-setup.php');" \
    && php /tmp/composer-setup.php --install-dir=/bin --filename=composer --version=2.8.2

# 作業ディレクトリを指定
WORKDIR /var/www/html

# ソースコードを作業ディレクトリにコピー
COPY ./laravel-api-template /var/www/html

# ポートを公開
EXPOSE 8000

CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]
