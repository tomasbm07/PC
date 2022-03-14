## 1

ip: 192.168.X.0/24 - /24 = 255.255.255.0

router commands:
    service dhcp
    ip dhcp pool nome_pool
    network 192.168.X.0 255.255.255.0
    default-router 192.168.X.254
    exit
    ip dhcp excluded-address 192.168.X.1 192.168.X.13
    ip dhcp excluded-address 192.168.X.224 192.168.X.254

show ip dhcp binding no terminal para ver ip atribuido



## 2

service dhcp
dns-server 192.168.X.1 10.254.0.252
domain-name net-N.dei.uc.pt

NetBIOS? - 10.1.0.253


## 3

lease 0 0 2
ipconfig /renew - para forçar novo ip do dhcp
debug ip dhcp server event e debug ip dhcp server event - analisar os resultados dos comandos
show ip dhcp server statistics - analisar resultados

## 4




