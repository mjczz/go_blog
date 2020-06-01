# 安装mysql-shell

- Enable the MySQL Tools Preview subrepository. You can do that by editing manually the `/etc/yum.repos.d/mysql-community.repo` file. This is an example of the subrepository's default entry in the file (the `baseurl` entry in your file might look different, depending on your Linux distribution):

```
[mysql-tools-preview]
name=MySQL Tools Preview
baseurl=http://repo.mysql.com/yum/mysql-tools-preview/el/6/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```

Change the entry `enabled=0` to `enabled=1` to enable the subrepository.

- Install MySQL Shell with this command:

```shell
sudo yum install mysql-shell
```

For dnf-enabled systems, do this instead:

```bash
sudo dnf install mysql-shell
```



## Access MySQL from Host

This one is a little bit tricky because you have to install mysql-shell in your host then you can access it from host terminal. 

After installation, try to access mysql container from host with following command.

```bash
$ mysql -h localhost -P 3306 --protocol=tcp -u root -p
```

