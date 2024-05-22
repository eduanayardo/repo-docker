# Docker with PHP 8.2.12

This repository aims to facilitate the creation of a development environment with php 8.2.12.

## What's in the environment:

- [Php Fpm](https://php.net/)
- [Apache2](https://httpd.apache.org/)
- [MariaDB](https://mariadb.com/)
- [PhpMyAdmin](https://www.phpmyadmin.net/)

## Prerequisites:

- [Install Docker](https://docs.docker.com/install/)
- [Install Docker Compose](https://docs.docker.com/compose/install/)

## How to use:

- Clone the repository
- Enter the repository folder
- Run the `docker-compose up` command
  - if you want to run in background mode, run the command `docker-compose up -d`
- Access the address `http://localhost:8080` to access phpmyadmin
  - user access
    - user: mysql
    - password: mysql
    - host: mysql
  - root access
    - user: root
    - password: root
    - host: mysql
- Access the address `http://localhost` to access the project

## Persistent data:

- mysql data: `./docker/mysql/dbdata`

## PHP INI Config:

Local php.ini configuration is located in the `./docker/php/php.ini` file.

```ini
[PHP]
log_errors=On
xmlrpc_errors=On
html_errors=On
display_errors=On
display_startup_errors=On
report_memleaks=On
error_reporting=E_ALL
file_uploads=On
max_execution_time=120
max_input_time=120
session.gc_maxlifetime=1440
post_max_size=50M
upload_max_filesize=45M
max_file_uploads=20
variables_order="EGPCS"
max_input_vars=10000
max_input_nesting_level=64
date.timezone=UTC
memory_limit=512M
expose_php=On

[opcache]
opcache.enable=true
opcache.enable_cli=true
opcache.jit=tracing

[intl]
intl.default_locale=en_utf8

[xdebug]
xdebug.client_host=host.docker.internal
xdebug.client_port=9003
xdebug.discover_client_host=0
xdebug.start_with_request=yes
xdebug.remote_handler=dbgp
xdebug.idekey=PHPSTORM
xdebug.mode=debug,develop
xdebug.cli_color=1
```

## PHP Modules:

```
[PHP Modules]
  apcu
  bcmath
  Core
  ctype
  curl
  date
  dom
  exif
  fileinfo
  filter
  ftp
  gd
  gmp
  hash
  iconv
  imap
  intl
  json
  libxml
  mbstring
  mongodb
  mysqli
  mysqlnd
  openssl
  pcntl
  pcre
  PDO
  pdo_mysql
  pdo_pgsql
  pdo_sqlite
  pgsql
  Phar
  posix
  random
  readline
  redis
  Reflection
  session
  SimpleXML
  soap
  sockets
  sodium
  SPL
  sqlite3
  ssh2
  standard
  sysvmsg
  sysvsem
  sysvshm
  tokenizer
  xdebug
  xml
  xmlreader
  xmlwriter
  xsl
  Zend OPcache
  zip
  zlib

[Zend Modules]
  Xdebug
  Zend OPcache
```

## Comments:

The project starts the services of `apache2`, `php`, and `mariadb` by default, if you want to use `phpmyadmin` you need to comment the services
that are being used and enable the services you want to use on the `docker-compose.yml` file.

## License:

[MIT](https://opensource.org/licenses/MIT)
