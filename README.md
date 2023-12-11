###  一键安装LNMP环境的WordPress脚本(国际版)
#### 一键脚本：

```
wget -N --no-check-certificate https://github.com/taotao1058/WordPress/raw/main/WordPress && bash WordPress
```


---

安装完成后，找到```/etc/nginx/sites-available/wordpress```文件

将第二行修改为```server_name 你的域名;```

然后执行```sudo systemctl reload nginx```重新加载nginx


---
