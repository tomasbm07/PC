# Ficha 2 PC - NAT

## 1

/24 -> 255.255.255.0
X = 22

### Router

Nat inside IP 192.168.X.0/24 
e0/0 -> 192.168.X.254

Nat outside -> 10.254.0.0/24;
f0/0 -> 10.254.0.N

#### Computer

ip -> 192.168.X.100

### Commands

access-list 25 permit 192.168.X.100 0.0.0.255
ip nat inside source list 25 interface Ethernet0 overload
interface FastEthernet0
ip address 192.168.100.1 255.255.255.0
ip nat inside
exit
interface Ethernet0
ip address 172.16.1.1 255.255.255.0
ip nat outside
end


