# 1-command-install  
install php+composer in docker ubuntu container, and auto setup environment for laravel  

7.2
```
apt update && apt install php ca-certificates git zip unzip php-zip curl php-curl php-xml wget -y && cd /tmp && wget https://getcomposer.org/installer -O composer-setup.php --no-check-certificate && wget https://composer.github.io/installer.sig --no-check-certificate && HASH=`cat installer.sig` && php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

7.4
```
apt update && apt -y install software-properties-common && add-apt-repository -y ppa:ondrej/php && apt update && apt -y install php7.4 && apt -y install curl unzip && apt install -y php7.4-{bcmath,bz2,intl,gd,mbstring,mysql,zip,common,curl} && curl -sS https://getcomposer.org/installer -o composer-setup.php && php composer-setup.php --install-dir=/usr/local/bin --filename=composer && composer self-update && apt -y install php7.4-mbstring  php7.4-xml php7.4-sqlite3 && php -v && composer -V
```
