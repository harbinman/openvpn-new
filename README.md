# openvpn-new

一个内网vpn项目，此种方式可以在无法进行port forward的情况下，实现异地通过openvpn登录局域网。


openvpn access server  docker部署

docker run -d \
  --name=openvpn-as --cap-add=NET_ADMIN \
  -p 943:943 -p 443:443 -p 1194:1194/udp \
  -v /usr/openvpn:/openvpn \
  openvpn/openvpn-as

frps github 下载地址  https://github.com/fatedier/frp/releases

内网穿透frp具体实现方式

./frps -c frps.ini

./frpc -c frpc.ini

--frps.ini
[common]
bind_port = 7000 

--frpc.ini

  [common]
server_addr = 114.116.222.211   # 为 FRP 服务端的公网 IP
server_port = 7000              # 为 FRP 服务端监听端口 上面配置端口对应

[vpn_test_tcp]
type = tcp
#local_ip = 127.0.0.1
local_port = 1194
remote_port = 21194

[vpn_test_udp]
type = udp
#local_ip = 127.0.0.1
local_port = 1194
remote_port = 21194
