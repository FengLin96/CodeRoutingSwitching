**Preparing for basic switch management**

op afstand een switch beheren moet volgende punten ingesteld zijn:

* een ip adres
* een subnetmasker
* een default gateway als op een remote netwerk wil beheren

Configure management interface

```
Configure terminal

interface vlan 99
ip address 172.17.99.11 255.255.255.0
no shutdown

end

copy run startup    // opslaan
```

Configure Switch Default Gateway

```
configure terminal

ip default-gateway 172.17.99.1
end
copy run startup
```

**Configure Duplex and Speed**

```
Configure terminal

interface FastEthernet 0/1
duplex full
speed 100
end

copy running-config startup-config
```

**Configure auto-MDIX **

When using auto-MDIX on an interface, the interface speed and duplex must be set to auto so that the feature operates correctly.

```
conf term

interface fastethernet 0/1

duplex auto
speed auto
mdix auto
end

copy run startup
```

examine the auto-MDIX setting for a specific interface

```
S1# show controllers ethernet-controller fa 0/1 phy | include Auto-MDIX
```

**Configuration SSH**

```
configure terminal

ip domain-name cisco.com

crypto key generate rsa
user name admin secret ccna
line vty 0 15
transport input ssh
login local 
exit
ip ssh version 2 //SSH 第 1 版存在已知安全缺陷。 要配置 SSH 第 2 版
exit
```

verwijder de RSA

```
cypto key zerosize rsa
```

Disable CDP

```
conf term

no cdp run
```

M**ake configuration changes to multiple ports on a switch**

```
conf term

interface range module/first-number - last-number
```

**DHCP Snooping**

```
ip dhcp snooping

ip dhcp snooping vlan 10,20

interface fastethernet 0/1
ip dhcp snooping trust

interface range fa0/2
ip dhcp snpping limit rate 54
```

**Sticky secure MAC adres**

```
switchport portsecurity mac-address sticky // dynamisch

switchport portsecurity mac-address sticky ...(mac-adres) //statis mac adres toevoegen
```

```
To change the violation mode on a switch port, use the switchport port-security violation {protect | restrict | shutdown} interface configuration mode command
```

Change the violation mode on a switch port

```
switchport port-security violation {protect | restrict | shutdown}
```

**Port Security:  Verifying**

Verify Port Security Settings

```
show port-security interface fastethernet 0/18
```

Verigying Port Security Sticky - Running Config

```
show run | begin FastEthernet 0/19
```

![](/assets/VerifyPortSecuritySticky.png)

Verify Secure MAC Addresses

```
show port-security address

show port-security address fa0/18 // of a speciaal interface
```

**Comfiguring NTP**

```
conf t

ntp master 1 // If the NTP master cannot reach any clock with a lower stratum number, the system will claim to be synchronized at the configured stratum number, and other systems will be willing to synchronize to it using NTP.


ntp server 10.1.1.1

---------------------------------EXEC mode
show ntp associations //This command will indicate the IP address of any peer devices that are synchronized to this peer, statically configured peers, and stratum number.


show ntp status
```



