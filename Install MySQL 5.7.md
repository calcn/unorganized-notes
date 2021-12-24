sudo yum install wget
wget -i -c http://repo.mysql.com/mysql57-community-release-el7-10.noarch.rpm
yum -y install mysql57-community-release-el7-10.noarch.rpm
yum -y install mysql-community-server
sudo systemctl start mysqld.service
sudo systemctl status mysqld.service
sudo systemctl enable mysqld.service

grep "password" /var/log/mysqld.log # 預設密碼
sudo mysql_secure_installation # 執行 MySQL 內建的安全性設定腳本
Remove anonymous users? [Y/n]: Y
Disallow root login remotely? [Y/n]: N
Remove test database and access to it? [Y/n]: Y
Reload privilege tables now? [Y/n]: Y

mysql -u root -p
uninstall plugin validate_password; # 關閉密碼強度規則
# 允許 root 遠端存取，不建議這樣設定，正常來說應該依 Table 建立相依的帳號進行存取
# 這邊為開發用，所以就直接開 root 了
ALTER USER 'root'@'localhost' IDENTIFIED BY 'passowrd';
GRANT ALL PRIVILEGES ON *.* to root@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
FLUSH PRIVILEGES;
vi /etc/my.cnf
  bind-address = 0.0.0.0
sudo systemctl restart mysqld.service

# Firewall
firewall-cmd --permanent --add-port=3306/tcp
firewall-cmd --reload