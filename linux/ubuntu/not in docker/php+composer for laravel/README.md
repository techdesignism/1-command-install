# 1-command-install  
install php+composer in ubuntu (not in docker container), and auto setup environment for laravel  

```
sudo apt update && sudo apt install php ca-certificates git zip unzip php-zip curl php-curl php-xml wget -y && cd /tmp && wget https://getcomposer.org/installer -O composer-setup.php --no-check-certificate && wget https://composer.github.io/installer.sig --no-check-certificate && HASH=`cat installer.sig` && php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
