# BigSwitch-Network-Deployment-Configuration

### v1.0 bsn-ref1

```
!
! Big Cloud Fabric 4.7.0 (bcf-4.7.0 #186)
! Current Time: 2020-04-09 23:28:58 UTC
!
version 1.0

! ntp
ntp server 0.bigswitch.pool.ntp.org
ntp server 1.bigswitch.pool.ntp.org
ntp server 2.bigswitch.pool.ntp.org
ntp server 3.bigswitch.pool.ntp.org

! aaa
aaa accounting exec default start-stop local

! local
local node
  hostname bsn-ref1
  interface management
    !
    ipv4
      ip 10.10.12.20/24 gateway 10.10.12.1
      method manual
      dns server 10.10.0.1
    !
    ipv6
      method manual

! user
user admin
  full-name 'Default admin'
  hashed-password method=PBKDF2WithHmacSHA512,salt=nfvIXJKlw5nIMBdmHh-AqA,rounds=25000,ph=true,n6aktUBO-4QCw_8oXcpeAbeqfC16DWnSy0zKCkJWIyow5akzNer3olZ0q1WawLVsZ0pHcMDa3LxWVMEAb0C1ng

! group
group admin
  associate user admin

! controller
controller
  cluster-name bigswitchlabs
  access-control
    !
    access-list api
      1 permit from ::/0
      2 permit from 0.0.0.0/0
    !
    access-list gui
      1 permit from ::/0
      2 permit from 0.0.0.0/0
    !
    access-list mininet-tun-p
      1 permit from ::/0
      2 permit from 0.0.0.0/0
    !
    access-list mininet-tun-v
      1 permit from ::/0
      2 permit from 0.0.0.0/0
    !
    access-list ns-api
      1 permit from ::/0
      2 permit from 0.0.0.0/0
    !
    access-list ssh
      1 permit from ::/0
      2 permit from 0.0.0.0/0
    !
    access-list vce-api
      1 permit from ::/0
      2 permit from 0.0.0.0/0

! switch
switch R1L1
  fabric-role leaf
  leaf-group R1
  mac 00:00:00:02:00:01

switch R1L2
  fabric-role leaf
  leaf-group R1
  mac 00:00:00:02:00:02

switch R2L1
  fabric-role leaf
  leaf-group R2
  mac 00:00:00:02:00:03

switch R2L2
  fabric-role leaf
  leaf-group R2
  mac 00:00:00:02:00:04

switch R3L1
  fabric-role leaf
  leaf-group R3
  mac 00:00:00:02:00:05

switch R3L2
  fabric-role leaf
  leaf-group R3
  mac 00:00:00:02:00:06

switch S1
  fabric-role spine
  mac 00:00:00:01:00:01

switch S2
  fabric-role spine
  mac 00:00:00:01:00:02

switch S3
  fabric-role spine
  mac 00:00:00:01:00:03

! tenant
tenant core
  logical-router
    route 0.0.0.0/0 next-hop next-hop-group firewall
    interface segment core1
      ip address 10.0.255.11/24
    !
    interface tenant system
      import-route
    !
    next-hop-group firewall
      description 'Route to firewall'
      ip 10.0.255.1
  !
  segment core1
    description VLAN=255,Network=10.0.255.0/24

tenant dmz
  !
  logical-router
    apply policy-list acl-dmz-in
    route 0.0.0.0/0 next-hop tenant system
    interface segment dmz1
      ip address 10.0.2.13/24
    !
    interface tenant system
      import-route
    !
    policy-list acl-dmz-in
      description 'Allow LB sourced connection to tenant production'
      10 permit proto icmp tenant dmz to any
      20 permit proto tcp tenant dmz to tenant production port 8080
      30 permit proto tcp tenant dmz to tenant production port 8443
      999 permit any to tenant dmz
  !
  segment dmz1
    description VLAN=2,Network=10.0.2.0/24

tenant production
  !
  logical-router
    apply policy-list acl-production-in
    route 0.0.0.0/0 next-hop tenant system
    interface segment app1
      ip address 10.0.20.1/24
    interface segment db1
      ip address 10.0.200.1/24
    !
    interface tenant system
      import-route
    policy-list acl-production-in
      10 permit proto icmp tenant dmz to tenant production
      20 permit proto icmp tenant production to any
      30 permit proto tcp tenant dmz to tenant production segment app1 port 8080
      40 permit proto tcp tenant dmz to tenant production segment app1 port 8443
      50 permit tenant production segment app1 to tenant dmz
      60 permit proto tcp tenant production segment app1 to tenant production segment db1 port 1521
      70 permit tenant production segment db1 to tenant production segment app1
  !
  segment app1
    description VLAN=20,Network=10.1.20.0/24
  !
  segment db1
    description VLAN=200,Network=10.0.200.0/24

tenant system
  logical-router
    route 0.0.0.0/0 next-hop tenant core
    !
    interface tenant core
      export-route
    !
    interface tenant dmz
      export-route
    !
    interface tenant production
      export-route
```
