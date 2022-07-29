# 1-command-install  
php+composer in docker ubuntu container, and auto setup environment for laravel  

```
apt update && apt install php ca-certificates git zip unzip php-zip curl php-curl php-xml -y && cd /tmp && wget https://getcomposer.org/installer -O composer-setup.php --no-check-certificate && wget https://composer.github.io/installer.sig --no-check-certificate && HASH=`cat installer.sig` && php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
