1. vi /etc/my.cnf

2. 在[mysqld]下添加skip-grant-tables，然后保存并退出

3. systemctl restart mysqld.service

4. update mysql.user set authentication_string = password('root12345') where user='root';

6. flush privileges;

7. systemctl restart mysqld.service