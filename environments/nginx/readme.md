# 使用Nginx进行域名转发

## 安装
1. 安装aginx程序

``` bash
# 切换至root用户
sudo su root
sudo apt-get install nginx

# 查看nginx是否安装成功
nginx -v

# 启动nginx
service nginx start
```
启动后，在网页重输入ip地址，即可看到nginx的欢迎页面，至此nginx安装成功。nginx文件安装完成之后的文件位置：
/usr/sbin/nginx：主程序
/etc/nginx：存放配置文件
/usr/share/nginx：存放静态文件
/var/log/nginx：存放日志

2. 使用docker安装nginx
``` bash
mkdir ~/nginx-conf
docker run -d --name nginx-test -p 80:80 -d -v ~/nginx-conf:/etc/nginx/conf.d nginx
```
目前这种形式只支持http的请求，因为容器内是这样的


## 反向代理配置
1. 域名指向端口
conf 文件示例
``` conf
server {
    listen 80;
    autoindex on;
    server_name dev-client.boat-house.cn;
    index index.html index.htm index.jsp index.php;
    if ( $query_string ~* ".*[\;'\<\>].*" ){
        return 404;
    }
    location / {
        proxy_pass http://40.73.38.39:5000;
        add_header Access-Control-Allow-Origin *;
    }
}
```

2. SSH
``` conf
# nginx version > 1.9
stream {
    server {
        listen           nginx-server:2222;
        proxy_pass my-ssh-server:22;
    }
}
```

## 特殊配置
jenkins、nexus

[boat-house.tools.conf](boat-house.tools.conf)

## 流水线配置 TODO
