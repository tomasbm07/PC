# Lab 3

## Exercise 1
X = 1

Network 1 -> 192.168.(X + 1).0/24
Host A - 192.168.(X + 1).1
R1 (int. 1) - 192.168.(X + 1).254 (last of network)

Network 2 -> 192.168.(X + 2).0/24
R1 (int. 2) - 192.168.(X + 2).1
R2 (int. 1) - 192.168.(X + 2).2

Network 3 -> 192.168.(X + 3).0/24
R2 (int. 2) - 192.168.(X + 3).1
R3 (int. 1) - 192.168.(X + 3).2 

Network 4 -> 192.168.(X + 4).0/24
Host B - 192.168.(X + 4).1
R3 (int. 2) - 192.168.(X + 4).254

## Exercise 2


## Exercise 3
R1#config t
R1(config)#ip route 192.168.(X+3).0 255.255.255.0 192.168.(X+2).1
R1(config)#ip route 192.168.(X+4).0 255.255.255.0 192.168.(X+3).2

R2#config t
R2(config)#ip route 192.168.(X+3).0 255.255.255.0 < R2_if1_IP_addr>
R2(config)#ip route 192.168.(X+4).0 255.255.255.0 < R2_if1_IP_addr>

R3#config t
R3(config)#ip route 192.168.(X+3).0 255.255.255.0 < R2_if1_IP_addr>
R3(config)#ip route 192.168.(X+4).0 255.255.255.0 < R2_if1_IP_addr>

## Exercise 4
Usar comando `no ip route [ip_adress]` para apagar as rotas estáticas em R1 e R3


