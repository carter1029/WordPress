###  一键安装LNMP环境的WordPress脚本


---
#### 一键脚本 ：

```
wget -N --no-check-certificate https://github.com/taotao1058/WordPress/raw/main/WordPress && bash WordPress
```


---

安装完成后，找到```/etc/nginx/sites-available/wordpress```文件

将第二行修改为```server_name 你的域名;```

然后执行```sudo systemctl reload nginx```重新加载nginx


---

####  申请证书使用acme脚本，nginx配置文件模板如下
```
server {
    listen 80;
    server_name 你的域名;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name 你的域名;

    ssl_certificate 证书路径;
    ssl_certificate_key 密钥路径;

    root /var/www/html;
    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ /index.php?$args;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
}
```
