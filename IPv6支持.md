## 使用条件

连接设备的网卡上有2开头的Global类IPv6地址才能使用


## SSR(R)设置
将 `user-config.json` 中的  `"dns_ipv6"` 的 值由 `false` 改为 `true`

配置项保持默认值False时，节点不会向DNS请求IPv6结果，改完之后SSR(R)可接受IPv6连接。


另外，DNS设置成1.1.1.1那个了。
测试了下，节点到它的延迟低于1ms

```
多用户DNS：
echo -e "1.1.1.1 53
1.0.0.1 53
2606:4700:4700::1111 53
2606:4700:4700::1001 53" > /root/shadowsocksr/dns.conf

单用户DNS：
echo -e "1.1.1.1 53
1.0.0.1 53
2606:4700:4700::1111 53
2606:4700:4700::1001 53" > /root/shadowsocksr/shadowsocks/dns.conf
```


## 面板
本面板已经完全支持识别IPv6地址，据悉大量校园网和广东、福建、上海等地移动4G大量在推广IPv6。

本面板自带纯真IP库用于识别IPv4，纯真IP库的大陆区IPv4地址识别准确率高，而且带有运营商信息，但是非大陆地区识别准确率较低，故当IPv4识别为非大陆地区，则自动切使用IPIP的IPv4库查询，并以其结果作为最终结果。而一旦识别出IPv6，则去调用ip.sb的在线api接口进行识别。故当识别出IPv6地址，登录时可能较慢。

谁要是有IPv6的离线库，麻烦提供我一份。