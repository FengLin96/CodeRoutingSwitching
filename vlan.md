**Creating a VLAN**

```
configure terminal

Vlan 10 // 10 = vlan id
name student // student = vlan name

end
```

A series of VLAN IDs

```
conf t

vlan 100,200,300 //onderscheiden met een comma
```

Display the contents of the vlan.dat file

```
show vlan brief
```

Assigning Ports to VLANs

```
Confi t

interface f0/18

switchport mode access // 将端口设置为接入模式
switchport access vlan 20     // 端口分配给VLAN

end
```

Remove VLAN assignment

```
conf t

no switchport access vlan //接口配置模式命令将交换机端口更改为 VLAN 1 成员的语法

end
```

```
show interfaces F0/18 switchport //verifies that the access VLAN for interface F0/18 has been reset to VLAN 1.
```

Remove VLAN

!删除 VLAN 之前，务必先将所有的成员端口重新分配给其他 VLAN。 VLAN 被删除之后，未转移到活动 VLAN 的端口都将无法与其他主机通信，直到它们分配给活动 VLAN。

```
conf t

no vlan 20

end
```

**Configuring IEEE 802.1Q Trunk Links**

![](/assets/VLANTrunk.png)

```
Configure terminal

interface f0/1

switchport mode trunk
switchport trunk native vlan 99 // to create a native vlan. The point that is really important is that a native vlan is the vlan that a switch puts all incoming frames that aren't tagged.
switchport trunk allowd vlan 10,20

end
```

Een vlan toestaan via bepaalde interface data sturen

```
conf t

interface f0/3

switchport trunk allowed vlan 10,20,99 // vlan10,20,99 kunnen nu via f0/3 data sturen
```

**Initial DTP Configuration**

Om trunking van een Switch van Cisco aan een apparaat toe te laten dat geen DTP steunt

```
1. switchport mide trunk

switchport nonegotiate
```

**PVLAN Edge**

```
interface g0/1

switchport protected

end
```



