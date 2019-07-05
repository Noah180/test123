# 如何在vps上搭建ss

## 前期准备：

在搬瓦工或者是vultr上租一个服务器，具体配置根据自己的需求来.

买完之后服务商会给你提供IP地址和端口号，用户名和密码, 此时你可以用远程连接工具去

connect，我自己用puutty.

## 配置ss

新建一个配置文件，比如名叫ss-configure.json.
vim ss-configure.json
在里面填上
```
{
  "server": "0.0.0.0",
  
  "port_password":
    {
      "port_1": "password_1", 
      "port_2": "password_2", 
      "port_3": "password_3", 
      "port_4": "password_4", 
      "port_5": "password_5", 
      ...
    },
    
    "local_address": "127.0.0.1",
    
    "local_port": 1080,
    
    "method": "ase-256-cfb"
}
```
## 填写完之后保存推出,然后启动.
```

ssserver -c location of this json file -d start.
```

结束进程

```
ssserver -c /etc/shadowsocks.json -d stop
```

## 客户端在github上有仓库：

https://github.com/shadowsocks/shadowsocks

根据自己的系统的去下载.

苹果手机可以下载wingy.

win7 SP1如果想使用4.0以上的版本需要升级.NET。

win8 和 win10 使用4.0以及以上版本无障碍.

win7 SP1以下的版本用不了4.0以及以上的版本，因为不支持升级.NET

此外为了更快，可以使用bbr，这个配置网上很多.

记住科学上网，尽管服务器在国外，但是出去的流量都会经过1080端口，所以想定位，和容易
