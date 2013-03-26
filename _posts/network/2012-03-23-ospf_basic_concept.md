---
layout: post
title: "ccnp_basic_concept"
description: ""
category: network
tags: [cisco, ccnp, ospf]
---
{% include JB/setup %}

* 单区域 OSPF 配置
* OSPF 基本概念

OSPF 是一个典型的基于链路状态的路由协议，它可以被高效的应用于大型的网络结构中。在这里，我会从最基本和最简单的地方起步，一步一步的来了解这个丰富多彩和功能强大的协议。

这张环境图是比较简单的，三个路由器，R1 和 R2 使用以太网链路连接，而 R2 和 R3 使用点对点的链路连接，到时我们可以看到这两种不同的链路环境会带来什么样的区别。

![单区域 OSPF](/images/network/ospf_for_one_area.png)

## 基本设置

首先，你得保证你的网络环境是通畅的，然后我们就开始设置 OSPF跌幅协议，让整个网络环境全可达。先从 R1 和 R2 开始，使用下面的命令来完成最简单的 OSPF 的设置。

    R1(config)#router ospf 1
    R1(config-router)#network 10.12.0.1 0.0.0.0 area 0

    R2(config)#router ospf 1
    R2(config-router)#network 10.12.0.2 0.0.0.0 area 0

设置完成之后，我们大概可以在 R2 路由器上看到下面的内容：

    *Mar  1 00:13:22.227: %OSPF-5-ADJCHG: Process 1, Nbr 10.12.0.1 on FastEthernet0/0 from LOADING to FULL, Loading Done

大致的意思是说什么从 LOADING 到了 FULL ，载入完成，等下我们再来解释这是什么意思。先说说上面的命令，首先：

    R1(config)#router ospf 1

这个是在路由器上启动 1 号进程来执行 OSPF，这个进程号没有什么强制性的规定，你可以使用任何一个你想用的数字，当然，不要超过 65535 就可以了。进程和你计算机上的进程是一个概念，两个不路由器进程号不一致同样也是可以连接的，就好像两台 PC 上不同进程的 QQ 一样也可以通迅一样。

    R2(config-router)#network 10.12.0.2 0.0.0.0 area 0

而这个命令是让路由器去匹配自身上的网络地址，将其加入到 OSPF 协议中，network 是命令，而 10.12.0.2 是本地的接口的 IP 地址，0.0.0.0 是反掩码，这两个加起来就是匹配 10.12.0.2 这个地址连接的网络段。而最后的 area 0 是 OSPF 里的特有的概念，区域 0 ，因为 OSPF 可以管理大型的网络，为了降低网络的复杂性和管理的便利，使用 area 区域来管理，而 0 这个是特殊的区域，称为 骨干区域，反正就是必有的一个区域，所有其它的区域必须连接到它。

<p><span class="label label-success">提示</span>
在单区域 OSPF 中，也可以不使用区域 0 ，而多区域中必须有一个区域 0。</p>



<p>概念：<span class="label label-important">进程号</span>　　<span class="label label-important">区域</span></p>

## 路由查看

现在，你可以把整个网络都剩下的部分也按同样的方法设置好：

    R2(config)#router ospf 1
    R2(config-router)#network 10.23.0.2 0.0.0.0 area 0

    R3(config)#router ospf 1
    R3(config-router)#network 10.23.0.3 0.0.0.0 area 0

设置完成后，你马上就可以得到刚才的那个 LOAD to FULL 的信息，现在整个网络就全达了，如何知道呢？可以使用命令：

    R3#show ip ro
    Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
           D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
           N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
           E1 - OSPF external type 1, E2 - OSPF external type 2
           i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
           ia - IS-IS inter area, * - candidate default, U - per-user static route
           o - ODR, P - periodic downloaded static route

    Gateway of last resort is not set

         10.0.0.0/24 is subnetted, 2 subnets
    O       10.12.0.0 [110/65] via 10.23.0.2, 00:00:20, Serial0/0
    C       10.23.0.0 is directly connected, Serial0/0

看到那个带 O 的路由项了没有：

    O       10.12.0.0 [110/65] via 10.23.0.2, 00:00:20, Serial0/0

这个就是 R3 通过 OSPF 学习到的，而且也了解到它是通过 10.23.0.2 这个接口可以到达的，现在，你可以试下使用 ping 命令，从 R3 去 ping R1 的接口地址：

    R3#ping 10.12.0.1

    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 10.12.0.1, timeout is 2 seconds:
    !!!!!

没有问题的，网络已经通过 OSPF 全部学习到了。

## OSPF 基本信息
现在开始进一步的去掌握更多的 OSPF 的特性，先使用一个简单的命令：

    R1#show ip ospf
     Routing Process "ospf 1" with ID 10.12.0.1
     Supports only single TOS(TOS0) routes
     Supports opaque LSA
     Supports Link-local Signaling (LLS)
     Initial SPF schedule delay 5000 msecs
     Minimum hold time between two consecutive SPFs 10000 msecs
     Maximum wait time between two consecutive SPFs 10000 msecs
     Minimum LSA interval 5 secs. Minimum LSA arrival 1 secs
     LSA group pacing timer 240 secs
     Interface flood pacing timer 33 msecs
     Retransmission pacing timer 66 msecs
     Number of external LSA 0. Checksum Sum 0x000000
     Number of opaque AS LSA 0. Checksum Sum 0x000000
     Number of DCbitless external and opaque AS LSA 0
     Number of DoNotAge external and opaque AS LSA 0
     Number of areas in this router is 1. 1 normal 0 stub 0 nssa
     External flood list length 0
        Area BACKBONE(0)
            Number of interfaces in this area is 1
            Area has no authentication
            SPF algorithm last executed 00:17:03.660 ago
            SPF algorithm executed 2 times
            Area ranges are
            Number of LSA 3. Checksum Sum 0x01C89B
            Number of opaque link LSA 0. Checksum Sum 0x000000
            Number of DCbitless LSA 0
            Number of indication LSA 0
            Number of DoNotAge LSA 0
            Flood list length 0

看几个 OSPF 的重要信息，第一个就是 RID，位于上面命令的第一行中：

    Routing Process "ospf 1" with ID 10.12.0.1

英文还是很好理解的，路由器进程 ospf 1 ，对吧，然 ID 10.12.0.1 就是 OSPF ID 了，它是一个不同于路由器名称的标识符，它标识的是在 OSPF 中路由器是如何标识其它路由器的，而这个 ID 的生成方式是通过本地的最大 IP 地址产生的，果然有回环地址的话，那么就是回环地址成为 OSPF ID。当然，有多个回环地址那么就是回环地址中最大的成为 OSPF ID。

下面的 Area BACKBONE(0) 显示出了这个路由器所在的区域是 backbone ，既骨干区域，也就是区域 0。下面可以看到 SPF algorithm 的一些情况，OSPF 使用该算法来生成路由表，马上会了解到成生的方法。