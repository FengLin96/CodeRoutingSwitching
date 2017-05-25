Configure Directly connected static route

![](/assets/configureDirectlyConnectedStaticRouting.png)

```
ip route 172.168.1.0 255.255.255.0 s0/0/0 // volgende hoop
ip route 192.168.1.0 255.255.255.0 s0/0/0 
ip route 192.168.2.0 255.255.255.0 s0/0/0
```

---

Configure a Next-Hop Static Route on R1

```
ip route 192.168.1.0 255.255.255.0 172.16.2.2
ip route 192.168.2.0 255.255.255.0 172.16.2.2
```

Configure fully specified static routes on R1

```
ip route 172.16.1.0 255.255.255.0 g0/1 172.16.2.2 // the next hoop router verbind met g0/1 en met adres 172.16.2.2
ip route 192.168.1.0 255.255.255.0 g0/1 172.16.2.2
ip route 192.168.2.0 255.255.255.0 g0/1 172.16.2.2
```

Verify a Static Route

```
1.ping
2.traceroute
3.show ip route
4.show up route static
5.show ip route network
```

Configuring a Default Static Route

```
ip route 0.0.0.0 0.0.0.0 172.16.2.2
        // matches any network address
                // matches any subnet mask
                       //c{ip-address | exit-interface}
```

---

!!!必须配置 **ipv6 unicast-routing **全局配置命令，才能使路由器转发 IPv6 数据包。

```
ipv6 unicast-routing
```

Configure a fully specified static ipv6 route![](/assets/Schermafbeelding 2017-05-24 om 07.35.23.png)

