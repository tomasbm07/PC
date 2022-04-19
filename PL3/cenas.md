# Lab 3

## Exercise 1
X = 23

Network 1 -> 192.168.24.0/24
Host A - 192.168.24.1
R1 (int. 1) - 192.168.24.254 (last of network)

Network 2 -> 192.168.25.0/24
R1 (int. 2) - 192.168.25.1
R2 (int. 1) - 192.168.25.2

Network 3 -> 192.168.26.0/24
R2 (int. 2) - 192.168.26.1
R3 (int. 1) - 192.168.26.2 

Network 4 -> 192.168.27.0/24
Host B - 192.168.27.1
R3 (int. 2) - 192.168.27.254



## Exercise 2

R1
(Com HOST A)
ip address 192.168.24.254 255.255.255.0
no shutdown
(Com R2)
ip address 192.168.25.1 255.255.255.0
no shutdown

HOST A
ip 192.168.(X + 1).1/24 192.168.24.254

R2
(Com R1)
ip address 192.168.25.2 255.255.255.0
no shutdown
(Com R3)
ip address 192.168.26.1 255.255.255.0
no shutdown

R3
(Com R2)
ip address 192.168.26.2 255.255.255.0
no shutdown
(Com PC2)
ip address 192.168.27.254 255.255.255.0
no shutdown

HOST B
ip 192.168.27.1/24 192.168.27.254



## Exercise 3
R1#config t
R1(config)#ip route 192.168.26.0 255.255.255.0 192.168.25.2
R1(config)#ip route 192.168.27.0 255.255.255.0 192.168.25.2

R2#config t
R2(config)#ip route 192.168.24.0 255.255.255.0 192.168.25.1
R2(config)#ip route 192.168.27.0 255.255.255.0 192.168.26.2

R3#config t
R3(config)#ip route 192.168.24.0 255.255.255.0 192.168.26.1
R3(config)#ip route 192.168.25.0 255.255.255.0 192.168.26.1

## Exercise 4
R1
R1(config)#no ip route 192.168.26.0 255.255.255.0 
R1(config)#no ip route 192.168.27.0 255.255.255.0 
ip route 0.0.0.0 0.0.0.0 192.168.25.2

R3
R3(config)#no ip route 192.168.24.0 255.255.255.0
R3(config)#no ip route 192.168.25.0 255.255.255.0
ip route 0.0.0.0 0.0.0.0 192.168.26.1

## Exercise 5
R1
    router rip
    version 2
    net(tab) 192.168.24.0
    net(tab) 192.168.25.0
    pass(tab) e0/0 # interface interior

R2
    router rip
    version 2
    net(tab) 192.168.25.0
    net(tab) 192.168.26.0

R3 
    router rip
    version 2
    net\t 192.168.26.0
    net(tab) 192.168.27.0
    pass(tab) e0/0 # interface interior
