### Configuring Traditional Inter-VLAN Routing

Configure Legacy Inter-VLAN Routing: Switch Configuration

###### ![](/assets/Schermafbeelding 2017-05-23 om 21.54.52.png)

```cisco
Configure terminal
vlan 10 // create een vlan met id 10
vlan 30 // create een vlan met id 30
interface f0/11
switchport access vlan 10 // toekenen aan vlan 10

interface f0/4
switchport access vlan 10

interface f0/6
switchport access vlan 30

interface f0/5
switchport access vlan 30
end

copy running-config startup-config //opslaan -> naar restart geen verlies
```

Configure Legacy Inter-VLAN Routing: Router Interface Configuration

配置路由器以执行 VLAN 间路由

```
configure terminal
interface g0/0
ip address 172.17.10.1 255.255.255.0
no shutdown

interface g0/1
ip address 172.17.30.1 255.255.255.0
no shutdown

end

copy running-config startup-config
```

**Configure Router-on-a-Stick**: Switch Configuration

![](/assets/Schermafbeelding 2017-05-23 om 22.27.42.png)Als meerdere switches er zijn, dan moet elke connectie tussen de switch doen, zoals als volgende afbeelding.

![](/assets/Schermafbeelding 2017-05-23 om 22.32.40.png)

```
conf term
vlan 10
vlan 30

interface f 0/11
switchport access vlan 10
no shutdown

interface f 0/6
switchport access vlan 30
no shutdown

interface f0/5
switchport mode trunk
end
```

Configure Router-on-a-Stick: Router Subinterface Configuration

```
conf term
interface g0/0.10 // g0/0 is fysiek interface  .10 is subinterface_id, mag zelf kiezen, meestal is vlan id
encapsulation dot1q 10 //将 IP 地址分配给子接口之前，需要使用 encapsulation dot1q vlan_id 命令配置子接口，使之在特定 VLAN 上运行
ip address 172.17.10.1 255.255.255.0
interface g0/0.30
encapsuation dot1q 30
ip address 172.17.30.1 255.255.255.0
interface g0/0
no shutdown
```

Verifying Subinterfaces![](/assets/Schermafbeelding 2017-05-24 om 00.01.11.png)

Verify Switch Configuration![](/assets/VerifySwitchConfiguration.png)

Multilayer Switch Inter-VLAN Routing

```
ip routing 
router rip
network 10.0.0.0

interface vlan10
ip address 10.10.1.1 255.0.0.0 // te vragen
no shutdown

interface vlan 20
ip address 10.20.1.1 255.255.255.0
no shutdown
```

**Catalyst 2960 static Routing**

The sdmlanbase-routingtemplatecan be enabled to allow the switch to route between VLANsand to support static routing

```
show sdm prefer// verify which template is in use

conf t

sdm prefer ? //Change SDM template
sdm prefer lanbase routing //
```



