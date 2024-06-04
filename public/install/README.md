## 部署过程
1. 拉取代码
2. 并在站点根目录创建public目录，将本源码的public目录下的的所有文件上传到创建的public目录里
```shell
sudo chmod -R 775 public/
chown -R www-data:www-data public/
```
3. nginx配置为此目录
`root /var/www/public/public;`
4. 打开浏览器，访问 http://<绑定网站的域名名称>/dl.php，按照指示安装升级即可




## 删除流量限制
流量限制是discuz包内置功能，即使不配置，也会有缺省的保护机制。所以，如果要去掉流量设置，必须通过增加withfrequency，同时把限流参数设置成非常大，来“去除”某个接口的限制。 所有加大了调用批次的设置都在routes/apiv3.php中。

具体改动在：public/install/apiv3.php和public/install/CreateThreadController.php

需要部署完成后将文件内容替换到对应路径中：
```text
public/routes/apiv3.php
public/app/Api/Controller/Threads/CreateThreadController.php
```

## 用户名15位的限制
改动的文件：public/install/User.php和public/install/UserValidator.php

需要部署完成后将文件内容替换到对应路径中：
```text
app/Models/User.php
app/Validators/UserValidator.php
```
