

![image](https://user-images.githubusercontent.com/39460149/185774481-c4a08bbc-b26e-45f2-ade4-8994dec76756.png)




不同内网的设备搭建远程桌面  
利用服务端，客户端和客户端建立服务，流量不经过服务端  
frps服务端公网ip 100.100.100.100  
frpc客户端所在服务器的账户 root/pwd  



frps.ini
```
[common]
## frps服务绑定的ip和端口
#bind_addr = 0.0.0.0
bind_port = 7000

#如果是xtcp服务则需要开启udp
bind_udp_port = 7001
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

被访问的设备A
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

[p2p_rdp_1]
type = stcp
sk = stcp_secret_key
local_ip = 127.0.0.1
local_port = 3389

#[p2p_rdp_2]
#type = xtcp
#sk = xtcp_secret_key
#local_ip = 127.0.0.1
#local_port = 3389

```


发起远程桌面的设备B
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

[p2p_rdp_1_visitor]
type = stcp
role = visitor
server_name = p2p_rdp_1
sk = stcp_secret_key
bind_addr = 127.0.0.1
bind_port = 6001


#[p2p_rdp_2_visitor]
#type = xtcp
#role = visitor
#server_name = p2p_rdp_2
#sk = xtcp_secret_key
#bind_addr = 127.0.0.1
#bind_port = 6002

```

使用：
在设备B上使用远程桌面 使用地址127.0.0.1:6001 即可登录到设备A
