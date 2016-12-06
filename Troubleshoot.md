# Troubleshoot mysql root permissions

In case the role failed in some step setting permissions, you can use these steps to recover root: 

1. Create reset file:  
 
  `echo "grant all privileges on *.* to root@localhost with GRANT OPTION;" > /tmp/reset.sql`
  `chown mysql /tmp/reset.sql`

You can also use `GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'somepassword' WITH GRANT OPTION;`

2. Stop mysql  

  `service mysql stop`

3. Start mysql with reset file:

  `mysqld --user=mysql --init-file=/tmp/reset.sql`
  
4. Stop mysql

  `ps -aux | grep mysql`  
  `kill NNNN`  
  
(use PID number)

5. Start mysql service

  `service mysql start`
