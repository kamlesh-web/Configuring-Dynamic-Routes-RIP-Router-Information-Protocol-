    Router>
    Router>enable
    Router#
    Router#configure terminal
    Enter configuration commands, one per line.  End with CNTL/Z.
    Router(config)#
    Router(config)#hostname Router1
    Router1(config)#
    Router1(config)#enable secret CCNA
    Router1(config)#
    Router1(config)#interface g0/0/1
    Router1(config-if)#
    Router1(config-if)#ip address 192.168.1.254 255.255.255.0
    Router1(config-if)#
    Router1(config-if)#no shutdown
    
    Router1(config-if)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/1, changed state to up
    
    Router1(config-if)#interface g0/0/0
    Router1(config-if)#
    Router1(config-if)#ip address 192.168.5.2 255.255.255.248
    Router1(config-if)#
    Router1(config-if)#no shutdown
    
    Router1(config-if)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/0, changed state to up
    
    %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0, changed state to up
    
    Router1(config-if)#exit
    Router1(config)#
    Router1(config)#router rip
    Router1(config-router)#
    Router1(config-router)#version 2
    Router1(config-router)#
    Router1(config-router)#no auto-summary
    Router1(config-router)#
    Router1(config-router)#network 192.168.5.0
    Router1(config-router)#network 192.168.1.0
    Router1(config-router)#
    Router1(config-router)#passive-interface g0/0/1
    Router1(config-router)#
    Router1(config-router)#do write
    Building configuration...
    [OK]
    Router1(config-router)#
    Router1(config-router)#do show ip protocols
    Routing Protocol is "rip"
    Sending updates every 30 seconds, next due in 23 seconds
    Invalid after 180 seconds, hold down 180, flushed after 240
    Outgoing update filter list for all interfaces is not set
    Incoming update filter list for all interfaces is not set
    Redistributing: rip
    Default version control: send version 2, receive 2
      Interface             Send  Recv  Triggered RIP  Key-chain
      GigabitEthernet0/0/0  22
    Automatic network summarization is not in effect
    Maximum path: 4
    Routing for Networks:
    	192.168.1.0
    	192.168.5.0
    Passive Interface(s):
    	GigabitEthernet0/0/1
    Routing Information Sources:
    	Gateway         Distance      Last Update
    Distance: (default is 120)
    Router1(config-router)#do show ip route
    Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
           D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
           N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
           E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
           i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
           * - candidate default, U - per-user static route, o - ODR
           P - periodic downloaded static route
    
    Gateway of last resort is 192.168.5.1 to network 0.0.0.0
    
         192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.1.0/24 is directly connected, GigabitEthernet0/0/1
    L       192.168.1.254/32 is directly connected, GigabitEthernet0/0/1
    R    192.168.2.0/24 [120/1] via 192.168.5.3, 00:00:13, GigabitEthernet0/0/0
    R    192.168.3.0/24 [120/4] via 192.168.5.1, 00:00:06, GigabitEthernet0/0/0
    R    192.168.4.0/24 [120/4] via 192.168.5.1, 00:00:06, GigabitEthernet0/0/0
         192.168.5.0/24 is variably subnetted, 5 subnets, 3 masks
    C       192.168.5.0/29 is directly connected, GigabitEthernet0/0/0
    L       192.168.5.2/32 is directly connected, GigabitEthernet0/0/0
    R       192.168.5.8/30 [120/1] via 192.168.5.1, 00:00:06, GigabitEthernet0/0/0
    R       192.168.5.12/30 [120/2] via 192.168.5.1, 00:00:06, GigabitEthernet0/0/0
    R       192.168.5.16/29 [120/3] via 192.168.5.1, 00:00:06, GigabitEthernet0/0/0
    R*   0.0.0.0/0 [120/2] via 192.168.5.1, 00:00:06, GigabitEthernet0/0/0
    
    Router1(config-router)#
