# PL4 - OSPF

## Exercise 1

R0 - R1:
172.16.(X + 1).0/24

R0 - R2:
172.16.(X + 2).0/24

R1:
192.168.(X + 1).0/24

R2:
192.168.(X + 2).0/24

*R0 router:*

```bash
router ospf 100
network 172.16.(X + 1).0 255.255.255.0 area 0
network 172.16.(X + 2).0 255.255.255.0 area 0
```

*R1 router:*

```bash
router ospf 100
network 172.16.(X + 1).0 255.255.255.0 area 0
network 192.168.(X + 1).0 255.255.255.0 area 1
```

*R2 router:*

```bash
router ospf 100
network 172.16.(X + 2).0 255.255.255.0 area 0
network 192.168.(X + 2).0 255.255.255.0 area 2
```

- Get routing table with `show ip route` in all routers
- Get list of neighbour routers `show ip ospf neighbor` in all routers
- Check connectivity with `ping`

## Exercice 2

- Set up the scenario

*R1 router:*
__not sure__
router ospf 100
network 172.16.(X + 1).0 255.255.255.0 area 0
network 192.168.51.0 255.255.255.0 area 1
area 1 nssa

- Get the routing tables of the R0 router, of the ABR router in the NSSA area, of the RIP router in the NSSA area, and of the ABR router in the standard area, using the `show ip route` command in each of these router
- Check that the routes injected by RIP show up in the routing tables
- Check the connectivity between the various sub-networks, using the `ping` command. In particular, check the connectivity with the RIP networks.
- Analyse and interpret the obtained results.

## Exercise 3

```bash
router ospf 100
network 172.30.10.0 0.0.0.255 area 0
network 10.11.1.0 0.0.0.255 area 1
! area 1 route summarisation command
area 1 range 10.11.0.0 255.255.0.0
```

- Get the routing tables of all routers, using the ‘show ip route’
- Compare these routing tables with the ones obtained in Exercise 2. Which routes have been summarised?
- Analyse and interpret the obtained results.
