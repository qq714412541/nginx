# nginx
http://www.runoob.com/linux/nginx-install-setup.html #nginx配置
#安装起始目录在/usr/local/src

http://blog.51cto.com/akui2521/2104583 #新建主机yum

#systemctl status firewalld.service
#firewall-cmd --zone=public --add-port=80/tcp --permanent
#systemctl restart firewalld.service    #防火墙开启端口


#nginx负载均衡基本配置
worker_processes 1;

events { 
    worker_connections 1024; 
 }

http {

    include mime.types; 
    default_type application/octet-stream;
    sendfile on;
    keepalive_timeout 65;

upstream mysvr { 
    server 192.168.126.130:80;
    server 192.168.126.129:80;
}

server { 
    listen 80;
    server_name localhost;

location / { 
    proxy_pass  http://mysvr;
    root /liyaqiang;
    index index.html index.htm;
                }        
           } 
}



#nginx原始配置
#user  nobody;
worker_processes  1;
 
#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;
 
#pid        logs/nginx.pid;
 
 
events {
    worker_connections  1024;
}
 
 
http {
    include       mime.types;
    default_type  application/octet-stream;
 
    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';
 
    #access_log  logs/access.log  main;
 
    sendfile        on;
    #tcp_nopush     on;
 
    #keepalive_timeout  0;
    keepalive_timeout  65;
 
    #gzip  on;
    server {
        listen       80;
        server_name  localhost;
 
        charset utf-8;
	location / { # /表示根目录，该配置表示Nginx默认打开/www下的index.html  
	    root html;
	    index  index.html index.htm;
	}
    }
 }
