mysql在linux上出现Access denied for user 'root'@'localhost' (using password: NO)解决方案

或者忘记root的密码，通过重设root的密码就行，执行下面的四条密码命令就行，如下
先关闭msyql，如下
service mysqld stop
然后设置mysql为无密码状态就可以登录的状态，先进入到mysql命令所在的目录，然后执行下面的命令
mysqld_safe --skip-grant-tables
然后新开一个cmd，为什么要新开会话？因为你执行上面的命令后你怎么也退不出了，也执行不了代码了，卡在了那里，它没有在后台运行，所以如果是linux就新建一个会话，即用putty再来登录linux，再来执行操作，然后进入到mysql数据库，即
Use mysql
然后执行下面的代码，更新我们的root的密码，如下
UPDATE user SET Password=PASSWORD('新密码') where USER='root';
//然后刷新
flush privileges;
//最后重新启动我们的mysql
service mysqld restart 

然后再来登录我们的root看看是否可用登录了