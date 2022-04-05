# Static IPv6 Routing


## Configuration Router1

````
[admin@R1] /ipv6 address> print 
Flags: X - disabled, I - invalid, D - dynamic, G - global, L - link-local 
 #    ADDRESS                                     FROM-POOL INTERFACE     ADVERTISE
 0 DL fe80::219:d1ff:fe00:3511/64                           ether1        no 
 1 DL fe80::219:d1ff:fe00:3512/64                           ether2        no 
 1 DL fe80::219:d1ff:fe00:3513/64                           ether3        no 

````

## Configuration Router2
````
[admin@R2] /ipv6 address> print 
Flags: X - disabled, I - invalid, D - dynamic, G - global, L - link-local 
 #    ADDRESS                                     FROM-POOL INTERFACE     ADVERTISE
 0 DL fe80::219:d1ff:fe39:3535/64                           ether1        no 
 1 DL fe80::219:d1ff:fe39:3536/64                           ether2        no 


````

## Router1
````
/ipv6 address 
add address=2001:db8:0:1::1/64 interface=ether3 advertise=yes

/ipv6 route 
add gateway=fe80::1:1%ether1
add dst-address=2001:db8:0:2::/64 gateway=fe80::219:d1ff:fe39:3535%ether2

````

## Router2
````
/ipv6 address 
add address=2001:db8:0:2::1/64 interface=ether2 advertise=yes

/ipv6 route 
add gateway=fe80::219:d1ff:fe00:3512%ether1

````
