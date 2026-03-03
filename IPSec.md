**IPSec** 



![](/home/knight/snap/marktext/9/.config/marktext/images/2025-12-23-07-18-03-image.png)



```site1
site1#sh run
site1#sh running-config 
Building configuration...

Current configuration : 1503 bytes
!
version 12.4
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname site1
!
boot-start-marker
boot-end-marker
!
!
no aaa new-model
memory-size iomem 5
ip cef
!
!
!
!
no ip domain lookup
!
multilink bundle-name authenticated
!
!
!
!
archive
 log config
  hidekeys
! 
!
crypto isakmp policy 10
 encr aes
 hash md5
 authentication pre-share
 lifetime 1000
crypto isakmp key cisco address 102.1.1.1
!
!
crypto ipsec transform-set PM esp-3des esp-md5-hmac 
 mode transport
!
crypto ipsec profile PM
 set transform-set PM 
!
!
!
!
!
!
!         
!
interface Tunnel10
 ip address 192.168.10.1 255.255.255.0
 tunnel source FastEthernet0/1
 tunnel destination 102.1.1.1
 tunnel protection ipsec profile PM
!
interface FastEthernet0/0
 ip address 10.1.1.1 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet0/1
 ip address 101.1.1.1 255.255.255.252
 duplex auto
 speed auto
!
interface FastEthernet1/0
 no ip address
 shutdown
 duplex auto
 speed auto
!         
interface FastEthernet2/0
 no ip address
 shutdown
 duplex auto
 speed auto
!
router ospf 1
 log-adjacency-changes
 passive-interface FastEthernet0/0
 network 10.1.1.0 0.0.0.255 area 0
 network 192.168.10.0 0.0.0.255 area 0
!
ip forward-protocol nd
ip route 0.0.0.0 0.0.0.0 FastEthernet0/1 101.1.1.2
!
!
ip http server
no ip http secure-server
!
!
!
!
!         
!
!
control-plane
!
!
!
!
!
!
!
!
!
!
line con 0
 logging synchronous
line aux 0
line vty 0 4
!
!
end

site1# 
site1#
site1#
```

```isp
isp>
isp>en
isp#
isp#sh runn
isp#sh running-config 
Building configuration...

Current configuration : 953 bytes
!
version 12.4
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname isp
!
boot-start-marker
boot-end-marker
!
!
no aaa new-model
memory-size iomem 5
ip cef
!
!
!
!
no ip domain lookup
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
archive
 log config
  hidekeys
! 
!
!
!
!
!
!
!
interface Loopback0
 ip address 8.8.8.8 255.255.255.255
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex auto
 speed auto
!
interface FastEthernet0/1
 ip address 101.1.1.2 255.255.255.252
 duplex auto
 speed auto
!         
interface FastEthernet1/0
 no ip address
 shutdown
 duplex auto
 speed auto
!
interface FastEthernet2/0
 ip address 102.1.1.2 255.255.255.252
 duplex auto
 speed auto
!
ip forward-protocol nd
!
!
ip http server
no ip http secure-server
!
!
!
!
!
!
!         
control-plane
!
!
!
!
!
!
!
!
!
!
line con 0
 logging synchronous
line aux 0
line vty 0 4
!
!
end

isp# 
isp#
isp#
```

```site2
site2#
site2#
site2#sh runn
site2#sh running-config  
Building configuration...

Current configuration : 1502 bytes
!
version 12.4
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname site2
!
boot-start-marker
boot-end-marker
!
!
no aaa new-model
memory-size iomem 5
ip cef
!
!
!
!
no ip domain lookup
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
archive
 log config
  hidekeys
! 
!
crypto isakmp policy 1
 encr aes
 hash md5
 authentication pre-share
 lifetime 1000
crypto isakmp key cisco address 101.1.1.1
!
!
crypto ipsec transform-set PM esp-3des esp-md5-hmac 
 mode transport
!
crypto ipsec profile PM
 set transform-set PM 
!
!
!
!
!
!
!         
!
interface Tunnel10
 ip address 192.168.10.2 255.255.255.0
 tunnel source FastEthernet2/0
 tunnel destination 101.1.1.1
 tunnel protection ipsec profile PM
!
interface FastEthernet0/0
 ip address 20.1.1.1 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet0/1
 no ip address
 shutdown
 duplex auto
 speed auto
!
interface FastEthernet1/0
 no ip address
 shutdown
 duplex auto
 speed auto
!
interface FastEthernet2/0
 ip address 102.1.1.1 255.255.255.252
 duplex auto
 speed auto
!
router ospf 1
 log-adjacency-changes
 passive-interface FastEthernet0/0
 network 20.1.1.0 0.0.0.255 area 0
 network 192.168.10.0 0.0.0.255 area 0
!
ip forward-protocol nd
ip route 0.0.0.0 0.0.0.0 FastEthernet2/0 102.1.1.2
!
!
ip http server
no ip http secure-server
!
!
!
!
!         
!
!
control-plane
!
!
!
!
!
!
!
!
!
!
line con 0
 logging synchronous
line aux 0
line vty 0 4
!
!
end

site2# 
site2#
site2#
```


