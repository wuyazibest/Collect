![image](https://user-images.githubusercontent.com/39460149/185774441-cb834b84-b047-424f-8bb8-0f1b08e5cc18.png)


反向代理暴露内网服务器SSH服务  
frps服务端公网ip 100.100.100.100  
frpc客户端所在服务器的账户 root/pwd  
  


frps.ini
```
[common]
## frps服务绑定的ip和端口
#bind_addr = 0.0.0.0
bind_port = 7000

#bind_udp_port = 7001
#kcp_bind_port = 7000
#vhost_http_port = 80
#vhost_https_port = 443

## web管理界面的端口和账户信息
dashboard_port = 7700
dashboard_user = admin
dashboard_pwd = admin

## 日志设置
#log_file = ./frps.log
#log_level = info
log_max_days = 14


#连接服务端的秘钥
token = token 
#允许使用的端口
allow_ports = 6000-6999

```


frpc.ini
```
[common]
tls_enable = true

#连接服务端的地址和端口
server_addr = 100.100.100.100
server_port = 7000

#服务端的秘钥
token = token


## 日志设置
#log_file = ./frps.log
#log_level = info
log_max_days = 14

[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 6000

```


使用：
在任何能访问公网的设备上就能利用服务端的公网ip登录内网的客户端设备
ssh -oPort=6000 root@100.100.100.100
