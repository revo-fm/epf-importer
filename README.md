Installation:

- % brew install mysql
- % brew install python
- % pip install -r requirements.txt


Database

- % mysql_secure_installation
- % brew services start mysql
- % unset TMPDIR
- % mysql_install_db --verbose --user=`whoami` \\
	--basedir="$(brew --prefix mysql)" \\
	--datadir=/usr/local/var/mysql --tmpdir=/tmp
- % mysql.server restart
- % mysql --user=root mysql -p

```
mysql> CREATE USER 'epfimporter'@'localhost' IDENTIFIED BY 'epf123';
mysql> GRANT ALL PRIVILEGES ON epf.* TO 'epfimporter'@'localhost' WITH GRANT OPTION;
mysql> CREATE USER 'epfimporter'@'%' IDENTIFIED BY 'epf123';
mysql> GRANT ALL PRIVILEGES ON epf.* TO 'epfimporter'@'%' WITH GRANT OPTION;
mysql> commit;
mysql> CREATE USER 'admin'@'localhost';
mysql> GRANT RELOAD,PROCESS ON *.* TO 'admin'@'localhost';
mysql> ALTER DATABASE DEFAULT CHARSET 'utf8';
```

Verify that the user privileges type:
- % mysql --user=epfimporter epf -p

```
mysql> show tables;
Empty set (0.00 sec)
```
