#### Configure the Switch Management Interface

Vlan instellen

## ![](/assets/Schermafbeelding 2017-05-20 om 02.55.43.png)

#### Configure Basic Router Settings

* Name van router instellen
* password van router instellen
* password console line instellen
* password vty line instellen
* wachtwoorden encrypteren
* banner motd instellen
* configuraties bewaren
  ![](/assets/Schermafbeelding 2017-05-20 om 03.31.54.png)
  ![](/assets/Schermafbeelding 2017-05-20 om 03.37.41.png)

---

#### Configure an IPv4 Router interface

![](/assets/Schermafbeelding 2017-05-20 om 16.24.39.png)

In the lab environment, the serial interface connecting to the serial cable end labeled DCE must be configured with the clock rate command.

## ![](/assets/Schermafbeelding 2017-05-20 om 16.24.45.png)

---

#### Configure the Loopback9 interface

## ![](/assets/Schermafbeelding 2017-05-20 om 17.50.24.png)

---

#### Verify the gigabitethernet 0/0 interface setting

```cisco
enable
- 
show interface gigabitethernet 0/0
```

---

**Default static route \( beetje als default gateway op host\)**

```
ip route 0.0.0.0 0.0.0.0 Serial0/0/0 
```

the configuration of two static routes from R2 to reach the two LANs on R1.

![](/assets/Schermafbeelding 2017-06-05 om 01.42.32.png)

```
conf t

ip route 192.168.10.0 255.255.255.0 s0/0/0

ip route 192.168.11.0 255.255.255.0 209.165.200.225 // gaat ook met ip adres

exit
```



