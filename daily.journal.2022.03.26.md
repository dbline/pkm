---
id: cg4swj89a2t401qjfb6co8d
title: '2022-03-26'
desc: ''
updated: 1648322806679
created: 1648302729737
traitIds:
  - journalNote
---
# Saturday.

## Need todo:

- [ ] Do Smithworks import.
- [ ] create import_big.sh file to run it every day
- [ ] modify Edge importer class to look in the Raw


![[daily journal.journal.2022.02.28#personal-stuff,1:#jewelers-mutual-page-updates-with-language-support]]


Old cisco router configs:

dbl switch - in the office
homeswitch - in the laundry room


dbl:
User Access Verification

Username: cisco
Password:
dbl-switch>en
Password:
dbl-switch#sh
dbl-switch#show run
dbl-switch#show running-config
Building configuration...

Current configuration : 7209 bytes
!
! Last configuration change at 19:43:31 CDT Sat May 3 2003
!
version 15.2
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
service password-encryption
service compress-config
service sequence-numbers
!
hostname dbl-switch
!
boot-start-marker
boot system flash bootflash:cat4500e-entservicesk9-mz.152-4.E5.bin
boot-end-marker
!
!
vrf definition mgmtVrf
 !
 address-family ipv4
 exit-address-family
 !
 address-family ipv6
 exit-address-family
!
enable secret 5 $1$ORVg$uOWzp5q8H85EfJAvMnl0l1
enable password 7 06160E325F59060B01
!
username cisco password 7 030752180500
no aaa new-model
clock timezone CST -6 0
clock summer-time CDT recurring
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
ip name-server 8.8.8.8
ip name-server 8.8.4.4
!
!
!
!
crypto pki trustpoint TP-self-signed-161349
 enrollment selfsigned
 subject-name cn=IOS-Self-Signed-Certificate-161349
 revocation-check none
 rsakeypair TP-self-signed-161349
!
!
crypto pki certificate chain TP-self-signed-161349
 certificate self-signed 01
  30820223 3082018C A0030201 02020101 300D0609 2A864886 F70D0101 05050030
  2D312B30 29060355 04031322 494F532D 53656C66 2D536967 6E65642D 43657274
  69666963 6174652D 31363133 3439301E 170D3030 30323230 30373334 33395A17
  0D323030 31303130 30303030 305A302D 312B3029 06035504 03132249 4F532D53
  656C662D 5369676E 65642D43 65727469 66696361 74652D31 36313334 3930819F
  300D0609 2A864886 F70D0101 01050003 818D0030 81890281 8100C960 FBD96BDA
  5D8E1D59 443DB998 C1A40DCD 37E0518B DEC98D92 B3E06198 99764F63 49C796D2
  049ACAA3 F44673A6 7C1F67DA FA51ACF5 2CD01E00 D92268F9 33F9670C B248AC42
  64D4A4BD 776294F0 51BC4FD3 4DAED38C 1BA020D7 106F4393 41B7B503 2F4B7590
  CEB13598 52D84345 377AF470 9DC85240 F2F8D4A1 F83EBF12 12C50203 010001A3
  53305130 0F060355 1D130101 FF040530 030101FF 301F0603 551D2304 18301680
  14A1C89F F114A24A 00A79F3D 5F7A60B6 E43DEDCE 1F301D06 03551D0E 04160414
  A1C89FF1 14A24A00 A79F3D5F 7A60B6E4 3DEDCE1F 300D0609 2A864886 F70D0101
  05050003 81810030 C54E3481 DED5AE18 F5AB939E 6D4A79A7 9423C1F9 A94A8F6C
  91D1D18D B7CD9EEE CDA92632 4A7C8934 B9701E6F D535CF89 577D4966 F05D5E5E
  659CE129 5DF1AB67 98C04958 5D3C7A50 7D018BCF F87AC020 1CDC9A2D 02AE730A
  8F652468 11FA89C2 5D117AC3 6C1F0D4A 271FEC2F 61693C3D A610D38A F6B17F8F
  07E5887B 749F38
        quit
errdisable recovery cause psecure-violation
power redundancy-mode redundant
!
spanning-tree mode rapid-pvst
spanning-tree extend system-id
!
vlan internal allocation policy ascending
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
!
!
!
!
!
interface FastEthernet1
 vrf forwarding mgmtVrf
 no ip address
 speed auto
 duplex auto
!
interface GigabitEthernet1/1
 description ZyXel USG-50 LAN 1
 ip arp inspection trust
 spanning-tree bpduguard disable
 ip verify source vlan dhcp-snooping port-security
 ip dhcp snooping trust
!
interface GigabitEthernet1/2
!
interface GigabitEthernet1/3
!
interface GigabitEthernet1/4
!
interface GigabitEthernet1/5
!
interface GigabitEthernet1/6
!
interface GigabitEthernet1/7
!
interface GigabitEthernet1/8
!
interface GigabitEthernet1/9
!
interface GigabitEthernet1/10
!
interface GigabitEthernet1/11
!
interface GigabitEthernet1/12
!
interface GigabitEthernet1/13
 description ZyXel USG50 LAN 6
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/14
 switchport access vlan 6
!
interface GigabitEthernet1/15
 switchport access vlan 6
!
interface GigabitEthernet1/16
 switchport access vlan 6
!
interface GigabitEthernet1/17
 switchport access vlan 6
!
interface GigabitEthernet1/18
 switchport access vlan 6
!
interface GigabitEthernet1/19
 switchport access vlan 6
!
interface GigabitEthernet1/20
 switchport access vlan 6
!
interface GigabitEthernet1/21
 switchport access vlan 6
!
interface GigabitEthernet1/22
 switchport access vlan 6
!
interface GigabitEthernet1/23
 switchport access vlan 6
!
interface GigabitEthernet1/24
 switchport access vlan 6
!
interface GigabitEthernet1/25
 description USG WAN
!
interface GigabitEthernet1/26
!
interface GigabitEthernet1/27
!
interface GigabitEthernet1/28
!
interface GigabitEthernet1/29
!
interface GigabitEthernet1/30
!
interface GigabitEthernet1/31
!
interface GigabitEthernet1/32
!
interface GigabitEthernet1/33
!
interface GigabitEthernet1/34
!
interface GigabitEthernet1/35
!
interface GigabitEthernet1/36
 description USG Gateway
 switchport mode access
!
interface GigabitEthernet1/37
!
interface GigabitEthernet1/38
!
interface GigabitEthernet1/39
!
interface GigabitEthernet1/40
!
interface GigabitEthernet1/41
!
interface GigabitEthernet1/42
!
interface GigabitEthernet1/43
 description Globe Surfer 3G
 switchport access vlan 20
 switchport mode access
 ip verify source vlan dhcp-snooping port-security
!
interface GigabitEthernet1/44
 description ZyXel USG-50
 switchport access vlan 20
 switchport mode access
 ip verify source vlan dhcp-snooping
!
interface GigabitEthernet1/45
 description Polycom IP Phone
 switchport access vlan 20
 switchport mode access
 switchport voice vlan 20
 switchport port-security maximum 2
 switchport port-security violation restrict
 switchport port-security aging time 2
 switchport port-security aging type inactivity
 switchport port-security
!
interface GigabitEthernet1/46
!
interface GigabitEthernet1/47
 description ZyXel USG-50 DMZ
 switchport access vlan 30
 switchport trunk allowed vlan 30
 switchport mode access
!
interface GigabitEthernet1/48
!
interface TenGigabitEthernet1/49
 description Garage Dsktp 10Gb
 switchport access vlan 30
 switchport trunk allowed vlan 30
 switchport mode access
!
interface TenGigabitEthernet1/50
 description Trunk DBL-HOME
 switchport trunk pruning vlan none
 switchport mode trunk
 speed nonegotiate
!
interface TenGigabitEthernet1/51
 description ESXi-IP100
 switchport access vlan 30
 switchport mode access
!
interface TenGigabitEthernet1/52
 description ESXi-IP200
 switchport access vlan 30
 switchport mode access
!
interface Vlan1
 ip address 192.168.1.253 255.255.255.0
!
ip default-gateway 192.168.1.1
ip http server
ip http secure-server
ip forward-protocol nd
!
ip route 0.0.0.0 0.0.0.0 192.168.1.1
!
!
ip source binding FCF5.286B.580A vlan 30 10.10.10.1 interface Gi1/47
ip source binding 0004.F239.BD05 vlan 20 192.168.2.200 interface Gi1/45
ip source binding FCF5.286B.5806 vlan 20 192.168.2.11 interface Gi1/44
ip source binding 000C.E373.5B0A vlan 20 192.168.2.1 interface Gi1/43
ip source binding FCF5.286B.5809 vlan 6 192.168.6.1 interface Gi1/13
ip source binding FCF5.286B.5807 vlan 1 192.168.1.1 interface Gi1/1
!
!
snmp-server host 1.1.1.1 cms
!
vstack
!
line con 0
 password 7 030752180500
 logging synchronous
 login local
 length 0
 stopbits 1
line vty 0 4
 password 7 030752180500
 logging synchronous
 login local
line vty 5 15
 password 7 030752180500
 logging synchronous
 login local
!
ntp authentication-key 1 md5 0870 7
ntp authenticate
ntp trusted-key 1
ntp server 206.55.191.142 key 1 prefer
ntp server 0.pool.ntp.org
mac address-table static fcf5.286b.5807 vlan 1 interface GigabitEthernet1/1
mac address-table static fcf5.286b.5809 vlan 6 interface GigabitEthernet1/13
mac address-table static fcf5.286b.580a vlan 30 interface GigabitEthernet1/47
!
end

dbl-switch#

User Access Verification

Username: cisco
Password:
dbl-switch>en
Password:
dbl-switch#sh
dbl-switch#show run
dbl-switch#show running-config
Building configuration...

Current configuration : 7209 bytes
!
! Last configuration change at 19:43:31 CDT Sat May 3 2003
!
version 15.2
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
service password-encryption
service compress-config
service sequence-numbers
!
hostname dbl-switch
!
boot-start-marker
boot system flash bootflash:cat4500e-entservicesk9-mz.152-4.E5.bin
boot-end-marker
!
!
vrf definition mgmtVrf
 !
 address-family ipv4
 exit-address-family
 !
 address-family ipv6
 exit-address-family
!
enable secret 5 $1$ORVg$uOWzp5q8H85EfJAvMnl0l1
enable password 7 06160E325F59060B01
!
username cisco password 7 030752180500
no aaa new-model
clock timezone CST -6 0
clock summer-time CDT recurring
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
ip name-server 8.8.8.8
ip name-server 8.8.4.4
!
!
!
!
crypto pki trustpoint TP-self-signed-161349
 enrollment selfsigned
 subject-name cn=IOS-Self-Signed-Certificate-161349
 revocation-check none
 rsakeypair TP-self-signed-161349
!
!
crypto pki certificate chain TP-self-signed-161349
 certificate self-signed 01
  30820223 3082018C A0030201 02020101 300D0609 2A864886 F70D0101 05050030
  2D312B30 29060355 04031322 494F532D 53656C66 2D536967 6E65642D 43657274
  69666963 6174652D 31363133 3439301E 170D3030 30323230 30373334 33395A17
  0D323030 31303130 30303030 305A302D 312B3029 06035504 03132249 4F532D53
  656C662D 5369676E 65642D43 65727469 66696361 74652D31 36313334 3930819F
  300D0609 2A864886 F70D0101 01050003 818D0030 81890281 8100C960 FBD96BDA
  5D8E1D59 443DB998 C1A40DCD 37E0518B DEC98D92 B3E06198 99764F63 49C796D2
  049ACAA3 F44673A6 7C1F67DA FA51ACF5 2CD01E00 D92268F9 33F9670C B248AC42
  64D4A4BD 776294F0 51BC4FD3 4DAED38C 1BA020D7 106F4393 41B7B503 2F4B7590
  CEB13598 52D84345 377AF470 9DC85240 F2F8D4A1 F83EBF12 12C50203 010001A3
  53305130 0F060355 1D130101 FF040530 030101FF 301F0603 551D2304 18301680
  14A1C89F F114A24A 00A79F3D 5F7A60B6 E43DEDCE 1F301D06 03551D0E 04160414
  A1C89FF1 14A24A00 A79F3D5F 7A60B6E4 3DEDCE1F 300D0609 2A864886 F70D0101
  05050003 81810030 C54E3481 DED5AE18 F5AB939E 6D4A79A7 9423C1F9 A94A8F6C
  91D1D18D B7CD9EEE CDA92632 4A7C8934 B9701E6F D535CF89 577D4966 F05D5E5E
  659CE129 5DF1AB67 98C04958 5D3C7A50 7D018BCF F87AC020 1CDC9A2D 02AE730A
  8F652468 11FA89C2 5D117AC3 6C1F0D4A 271FEC2F 61693C3D A610D38A F6B17F8F
  07E5887B 749F38
        quit
errdisable recovery cause psecure-violation
power redundancy-mode redundant
!
spanning-tree mode rapid-pvst
spanning-tree extend system-id
!
vlan internal allocation policy ascending
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
!
!
!
!
!
interface FastEthernet1
 vrf forwarding mgmtVrf
 no ip address
 speed auto
 duplex auto
!
interface GigabitEthernet1/1
 description ZyXel USG-50 LAN 1
 ip arp inspection trust
 spanning-tree bpduguard disable
 ip verify source vlan dhcp-snooping port-security
 ip dhcp snooping trust
!
interface GigabitEthernet1/2
!
interface GigabitEthernet1/3
!
interface GigabitEthernet1/4
!
interface GigabitEthernet1/5
!
interface GigabitEthernet1/6
!
interface GigabitEthernet1/7
!
interface GigabitEthernet1/8
!
interface GigabitEthernet1/9
!
interface GigabitEthernet1/10
!
interface GigabitEthernet1/11
!
interface GigabitEthernet1/12
!
interface GigabitEthernet1/13
 description ZyXel USG50 LAN 6
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/14
 switchport access vlan 6
!
interface GigabitEthernet1/15
 switchport access vlan 6
!
interface GigabitEthernet1/16
 switchport access vlan 6
!
interface GigabitEthernet1/17
 switchport access vlan 6
!
interface GigabitEthernet1/18
 switchport access vlan 6
!
interface GigabitEthernet1/19
 switchport access vlan 6
!
interface GigabitEthernet1/20
 switchport access vlan 6
!
interface GigabitEthernet1/21
 switchport access vlan 6
!
interface GigabitEthernet1/22
 switchport access vlan 6
!
interface GigabitEthernet1/23
 switchport access vlan 6
!
interface GigabitEthernet1/24
 switchport access vlan 6
!
interface GigabitEthernet1/25
 description USG WAN
!
interface GigabitEthernet1/26
!
interface GigabitEthernet1/27
!
interface GigabitEthernet1/28
!
interface GigabitEthernet1/29
!
interface GigabitEthernet1/30
!
interface GigabitEthernet1/31
!
interface GigabitEthernet1/32
!
interface GigabitEthernet1/33
!
interface GigabitEthernet1/34
!
interface GigabitEthernet1/35
!
interface GigabitEthernet1/36
 description USG Gateway
 switchport mode access
!
interface GigabitEthernet1/37
!
interface GigabitEthernet1/38
!
interface GigabitEthernet1/39
!
interface GigabitEthernet1/40
!
interface GigabitEthernet1/41
!
interface GigabitEthernet1/42
!
interface GigabitEthernet1/43
 description Globe Surfer 3G
 switchport access vlan 20
 switchport mode access
 ip verify source vlan dhcp-snooping port-security
!
interface GigabitEthernet1/44
 description ZyXel USG-50
 switchport access vlan 20
 switchport mode access
 ip verify source vlan dhcp-snooping
!
interface GigabitEthernet1/45
 description Polycom IP Phone
 switchport access vlan 20
 switchport mode access
 switchport voice vlan 20
 switchport port-security maximum 2
 switchport port-security violation restrict
 switchport port-security aging time 2
 switchport port-security aging type inactivity
 switchport port-security
!
interface GigabitEthernet1/46
!
interface GigabitEthernet1/47
 description ZyXel USG-50 DMZ
 switchport access vlan 30
 switchport trunk allowed vlan 30
 switchport mode access
!
interface GigabitEthernet1/48
!
interface TenGigabitEthernet1/49
 description Garage Dsktp 10Gb
 switchport access vlan 30
 switchport trunk allowed vlan 30
 switchport mode access
!
interface TenGigabitEthernet1/50
 description Trunk DBL-HOME
 switchport trunk pruning vlan none
 switchport mode trunk
 speed nonegotiate
!
interface TenGigabitEthernet1/51
 description ESXi-IP100
 switchport access vlan 30
 switchport mode access
!
interface TenGigabitEthernet1/52
 description ESXi-IP200
 switchport access vlan 30
 switchport mode access
!
interface Vlan1
 ip address 192.168.1.253 255.255.255.0
!
ip default-gateway 192.168.1.1
ip http server
ip http secure-server
ip forward-protocol nd
!
ip route 0.0.0.0 0.0.0.0 192.168.1.1
!
!
ip source binding FCF5.286B.580A vlan 30 10.10.10.1 interface Gi1/47
ip source binding 0004.F239.BD05 vlan 20 192.168.2.200 interface Gi1/45
ip source binding FCF5.286B.5806 vlan 20 192.168.2.11 interface Gi1/44
ip source binding 000C.E373.5B0A vlan 20 192.168.2.1 interface Gi1/43
ip source binding FCF5.286B.5809 vlan 6 192.168.6.1 interface Gi1/13
ip source binding FCF5.286B.5807 vlan 1 192.168.1.1 interface Gi1/1
!
!
snmp-server host 1.1.1.1 cms
!
vstack
!
line con 0
 password 7 030752180500
 logging synchronous
 login local
 length 0
 stopbits 1
line vty 0 4
 password 7 030752180500
 logging synchronous
 login local
line vty 5 15
 password 7 030752180500
 logging synchronous
 login local
!
ntp authentication-key 1 md5 0870 7
ntp authenticate
ntp trusted-key 1
ntp server 206.55.191.142 key 1 prefer
ntp server 0.pool.ntp.org
mac address-table static fcf5.286b.5807 vlan 1 interface GigabitEthernet1/1
mac address-table static fcf5.286b.5809 vlan 6 interface GigabitEthernet1/13
mac address-table static fcf5.286b.580a vlan 30 interface GigabitEthernet1/47
!
end

dbl-switch#


homeswitch config:

User Access Verification

Password:
homeswitch>en
Password:
homeswitch#sh
homeswitch#sh
homeswitch#show run
homeswitch#show running-config
Building configuration...

Current configuration : 5054 bytes
!
! Last configuration change at 08:08:20 CST Fri Jan 21 2022
!
version 15.2
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
service sequence-numbers
!
hostname homeswitch
!
boot-start-marker
boot-end-marker
!
!
vrf definition mgmtVrf
 !
 address-family ipv4
 exit-address-family
 !
 address-family ipv6
 exit-address-family
!
enable password cisco
!
no aaa new-model
clock timezone CST -6 0
clock summer-time CDT recurring
!
!
!
!
!
!
no ip domain-lookup
ip domain-name dbline.co
!
!
!
!
!
errdisable recovery cause psecure-violation
power redundancy-mode redundant
spanning-tree mode pvst
spanning-tree extend system-id
!
vlan internal allocation policy ascending
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
!
!
!
!
interface FastEthernet1
 vrf forwarding mgmtVrf
 no ip address
 speed auto
 duplex auto
!
interface GigabitEthernet1/1
!
interface GigabitEthernet1/2
 switchport mode access
 history BPS all
!
interface GigabitEthernet1/3
 switchport mode access
!
interface GigabitEthernet1/4
 switchport mode access
!
interface GigabitEthernet1/5
 switchport mode access
!
interface GigabitEthernet1/6
 switchport mode access
!
interface GigabitEthernet1/7
 switchport mode access
!
interface GigabitEthernet1/8
 switchport mode access
!
interface GigabitEthernet1/9
 switchport mode access
!
interface GigabitEthernet1/10
 switchport mode access
!
interface GigabitEthernet1/11
 switchport mode access
 speed 1000
!
interface GigabitEthernet1/12
 switchport trunk allowed vlan 1,6,20,30
 switchport mode trunk
 spanning-tree bpduguard disable
!
interface GigabitEthernet1/13
!
interface GigabitEthernet1/14
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/15
 switchport access vlan 6
!
interface GigabitEthernet1/16
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/17
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/18
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/19
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/20
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/21
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/22
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/23
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/24
 switchport access vlan 6
 switchport mode access
!
interface GigabitEthernet1/25
 shutdown
!
interface GigabitEthernet1/26
 shutdown
!
interface GigabitEthernet1/27
 shutdown
!
interface GigabitEthernet1/28
 shutdown
!
interface GigabitEthernet1/29
 shutdown
!
interface GigabitEthernet1/30
 shutdown
!
interface GigabitEthernet1/31
 shutdown
!
interface GigabitEthernet1/32
 shutdown
!
interface GigabitEthernet1/33
 shutdown
!
interface GigabitEthernet1/34
 shutdown
!
interface GigabitEthernet1/35
 shutdown
!
interface GigabitEthernet1/36
 shutdown
!
interface GigabitEthernet1/37
 switchport trunk allowed vlan 1,6,20,30
 switchport mode trunk
 spanning-tree bpduguard disable
!
interface GigabitEthernet1/38
!
interface GigabitEthernet1/39
!
interface GigabitEthernet1/40
!
interface GigabitEthernet1/41
!
interface GigabitEthernet1/42
!
interface GigabitEthernet1/43
 switchport access vlan 20
 switchport mode access
!
interface GigabitEthernet1/44
 switchport access vlan 20
 switchport mode access
!
interface GigabitEthernet1/45
!
interface GigabitEthernet1/46
!
interface GigabitEthernet1/47
 switchport access vlan 30
 switchport trunk native vlan 30
 switchport mode trunk
 switchport nonegotiate
 spanning-tree bpduguard disable
!
interface GigabitEthernet1/48
!
interface TenGigabitEthernet1/49
 switchport access vlan 30
 switchport mode access
 shutdown
!
interface TenGigabitEthernet1/50
 description Trunk Route
 switchport mode trunk
!
interface TenGigabitEthernet1/51
 switchport access vlan 30
 switchport mode access
 shutdown
!
interface TenGigabitEthernet1/52
 switchport access vlan 30
 switchport mode access
 shutdown
!
interface Vlan1
 ip address 192.168.1.254 255.255.255.0
 no ip proxy-arp
!
interface Vlan6
 ip address 192.168.6.254 255.255.255.0
 no ip proxy-arp
!
interface Vlan10
 ip address 10.0.10.254 255.255.255.0
 shutdown
!
interface Vlan30
 ip address 10.10.10.254 255.255.255.0
!
!
router eigrp 100
 network 192.168.1.0
 network 192.168.6.0
 eigrp stub connected summary
!
ip default-gateway 192.168.1.1
ip http server
no ip http secure-server
ip forward-protocol nd
ip route 0.0.0.0 0.0.0.0 192.168.1.1
!
!
!
!
!
line con 0
 length 0
 stopbits 1
line vty 0 4
 password cisco
 login
 length 0
line vty 5 15
 password cisco
 login
 length 0
!
!
monitor session 1 source interface Gi1/12 , Gi1/37
monitor session 1 destination interface Gi1/48 encapsulation dot1q
monitor session 1 filter packet-type good rx
ntp authentication-key 1 md5 0657 7
ntp authenticate
ntp trusted-key 1
ntp server 206.55.191.142 key 1 prefer
!
end

homeswitch#

