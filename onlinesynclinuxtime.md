# 1、编辑时间配置文件
~~~
vi /etc/sysconfig/clock 
ZONE="Asia/Shanghai"
UTC=false #设置为false，硬件时钟不于utc时间一致
ARC=false
~~~
# 2、linux的时区设置为上海时区
~~~
ln -sf /usr/share/zoneinfo/Asia/Shanghai  /etc/localtime 
~~~

# 3、对准时间
~~~
ntpdate 192.43.244.18 
如果没有安装ntp服务器，刚需要先执行以下命令：

yum install ntp #安装ntp服务器
~~~
# 4、设置硬件时间和系统时间一致并校准
~~~
/sbin/hwclock --systohc 
~~~
