# OculusGoEthernet

#### for oculus go rooted firmware

##### 1、connect the usb ethernet adapter

##### 2、check eth0 by :

``
ifconfig -a
``

##### 3、use these commands to enable ethernet

``
ifconfig eth0 10.0.40.164 netmask 255.255.254.0 up

ip addr add 10.0.40.0/23 dev eth0

ip link set dev eth0 up

ip route add default via 10.0.40.1 dev eth0

``
