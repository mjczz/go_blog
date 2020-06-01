# php容器中安装源码包中的扩展

### 查看运行的php容器

```bash
[root@localhost ~]# docker ps
CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS                    NAMES
cbf0cca7bcb5        php:7.4-fpm           "docker-php-entrypoi…"   3 days ago          Up 20 seconds       0.0.0.0:9074->9000/tcp   php7.4

```


### 进入容器

```bash
[root@localhost ~]# docker exec -it php7.4 /bin/bash
```

### 查看docker提供的辅助脚本

```bash
#按tab键可自动提示
root@cbf0cca7bcb5:/var/www/html# docker-php-
docker-php-entrypoint     docker-php-ext-configure  docker-php-ext-enable     docker-php-ext-install    docker-php-source
```



### 查询docker-php-source用法

```bash
root@cbf0cca7bcb5:/var/www/html# docker-php-source
usage: /usr/local/bin/docker-php-source COMMAND

Manage php source tarball lifecycle.

Commands:
   将php源tarball解压到目录中
   extract  extract php source tarball into directory /usr/src/php if not already done.

    删除已解压的php源
   delete  delete extracted php source located into /usr/src/php if not already done.
```



### 将php源tarball解压到目录/usr/src/php

```bash
root@cbf0cca7bcb5:/var/www/html# docker-php-source extract
root@cbf0cca7bcb5:/var/www/html# cd /usr/src/php/ext
```

### 查看php源码包中的扩展

```bash
root@cbf0cca7bcb5:/usr/src/php/ext# ls
bcmath      ctype  dom           ffi       gd       iconv  ldap      mysqlnd  openssl      pdo           pdo_oci     pgsql   readline    simplexml  sockets  standard          sysvsem    xml        xsl
bz2         curl   enchant       fileinfo  gettext  imap   libxml    oci8     package.xml  pdo_dblib     pdo_odbc    phar    reflection  skeleton   sodium   swoole-4.5.0      sysvshm    xmlreader  zend_test
calendar    date   exif          filter    gmp      intl   mbstring  odbc     pcntl        pdo_firebird  pdo_pgsql   posix   session     snmp       spl      swoole-4.5.0.tgz  tidy       xmlrpc     zip
com_dotnet  dba    ext_skel.php  ftp       hash     json   mysqli    opcache  pcre         pdo_mysql     pdo_sqlite  pspell  shmop       soap       sqlite3  sysvmsg           tokenizer  xmlwriter  zlib
```

### 使用docker提供的辅助脚本安装存在于 /usr/src/php/ext 中的扩展

```bash
root@cbf0cca7bcb5:/usr/src/php/ext# docker-php-ext-install pdo
```

docker-php-ext-install 辅助脚本帮我执行了源码安装php扩展的一系列命令

