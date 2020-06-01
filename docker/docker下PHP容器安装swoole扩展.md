# docker下PHP容器安装swoole扩展

使用docker提供的命令工具


首先进入php容器里，在这里我执行过

```bash
docker-php-ext-install swoole
pecl install https://pecl.php.net/get/swoole-4.4.1.tgz
pecl install swoole-2.1.2
```

都以失败告终，由于第一条安装命令报：/usr/src/php/ext/swoole does not exist
swoole文件夹不存在的错误，心生一计，手动将官网swoole扩展下载下来, https://pecl.php.net/package/swoole 下载对应的版本后本地解压后，将文件夹copy到php容器里：

```bash	
docker cp f:/docker/copy/swoole 7c6b282a6a9c:/usr/src/php/ext
```

此时再进入php容器里执行：

```bash
docker-php-ext-install swoole
```

回车后发现不报错了，并且在编译安装中，完成后查看swoole版本：

```bash
php --ri swoole
```

到此为止PHP的swoole扩展就安装成功了~
测试运行swoole，需要用php CLI模式（php命令行模式运行： php -f 运行文件名.php）
