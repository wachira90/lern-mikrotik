# vvrp

## vrrp config 

````
#R1 configuration:
/ip address add address=192.168.1.1/24 interface=ether1
/interface vrrp add interface=ether1 vrid=49 priority=254
/ip address add address=192.168.1.200/32 interface=vrrp1


#R2 configuration:
/ip address add address=192.168.1.2/24 interface=ether1
/interface vrrp add interface=ether1 vrid=49
/ip address add address=192.168.1.200/32 interface=vrrp1
````
