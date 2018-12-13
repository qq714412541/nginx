# nginx
http://www.runoob.com/linux/nginx-install-setup.html #nginx配置
#安装起始目录在/usr/local/src

http://blog.51cto.com/akui2521/2104583 #新建主机yum

#systemctl status firewalld.service
#firewall-cmd --zone=public --add-port=80/tcp --permanent
#systemctl restart firewalld.service    #防火墙开启端口


#killall  指令下载  yum install psmisc

#端口映射     nginx:80  <>  物理机:22222 <> 交换机:n   
#注意本地物理机提供访问需要设置防火墙允许访问22222端口
