VPN技术(IPsec/L2TP/SSLVPN/PPTP)学习笔记
http://www.safebase.cn/article-259910-1.html



# VPN 虚拟专用网
目前 VPN 产品中主要分 IPSec VPN 和 SSL VPN 两大类， IPSec VPN 是指采用 IPSec 安全技术标准的 VPN 设备，而 SSL VPN 指采用 SSL 协议来加密 IP 数据链路实现 远程接入 的一种新型 VPN 技术。
SSL VPN （浏览器协议）与IPSec VPN 相比， SSL VPN 具有部署简单，无客户端，维护成本低，网络适应强。


# 工作过程
VPN的基本处理过程如下：
①要保护主机发送明文信息到其他VPN设备。 
②VPN设备根据网络管理员设置的规则，确定是对数据进行加密还是直接传输。 
③对需要加密的数据，VPN设备将其整个数据包（包括要传输的数据、源IP地址和目的lP地址）进行加密并附上数据签名，加上新的数据报头（包括目的地VPN设备需要的安全信息和一些初始化参数）重新封装。 
④将封装后的数据包通过隧道在公共网络上传输。 
⑤数据包到达目的VPN设备后，将其解封，核对数字签名无误后，对数据包解密。 



# 分类标准
根据不同的划分标准，VPN可以按几个标准进行分类划分： 

## 按VPN的协议分类
VPN的隧道协议主要有三种，PPTP、L2TP和IPSec，其中PPTP和L2TP协议工作在OSI模型的第二层，又称为二层隧道协议；IPSec是第三层隧道协议。 
OSI（Open System Interconnect），即开放式系统互连。OSI定义了网络互连的七层框架（物理层、数据链路层、网络层、传输层、会话层、表示层、应用层）
TCP/IP五层模型（物理层、数据链路层、网络层、传输层、应用层（会话层、表示层、应用层））
![OSI与TCP](1.png)
![OSI与TCP/IP对应](2.png)
![各层设备](3.png)
![各层协议](4.png)

## 按VPN的应用分类
（1）Access VPN（远程接入VPN）：客户端到网关，使用公网作为骨干网在设备之间传输VPN数据流量； 
（2）Intranet VPN（内联网VPN）：网关到网关，通过公司的网络架构连接来自同公司的资源； 
（3）Extranet VPN（外联网VPN）：与合作伙伴企业网构成Extranet，将一个公司与另一个公司的资源进行连接。 

## 按所用的设备类型进行分类
网络设备提供商针对不同客户的需求，开发出不同的VPN网络设备，主要为交换机、路由器和防火墙： 
（1）路由器式VPN：路由器式VPN部署较容易，只要在路由器上添加VPN服务即可； 
（2）交换机式VPN：主要应用于连接用户较少的VPN网络； 

## 按照实现原理划分
（1）重叠VPN：此VPN需要用户自己建立端节点之间的VPN链路，主要包括：GRE、L2TP、IPSec等众多技术。 
（2）对等VPN：由网络运营商在主干网上完成VPN通道的建立，主要包括MPLS、VPN技术。 


# 实现方式
VPN的实现有很多种方法，常用的有以下四种： 
1．VPN服务器：在大型局域网中，可以通过在网络中心搭建VPN服务器的方法实现VPN。 
2．软件VPN：可以通过专用的软件实现VPN。 
3．硬件VPN：可以通过专用的硬件实现VPN。 
4．集成VPN：某些硬件设备，如路由器、防火墙等，都含有VPN功能，但是一般拥有VPN功能的硬件设备通常都比没有这一功能的要贵。 




# SSL VPN 与 IPSec VPN对比

SSL VPN，指的是使用者利用浏览器内建的Secure Socket Layer封包处理功能，用浏览器连回公司内部SSL VPN服务器，然后透过网络封包转向的方式，让使用者可以在远程计算机执行应用程序，读取公司内部服务器数据。它采用标准的安全套接层（SSL）对传输中的数据包进行加密，从而在应用层保护了数据的安全性。
由于 SSL 协议广泛内置于 IE 等各种浏览器中，具体来讲， SSL VPN 与 IPSec VPN 相比有如下 4 大明显的技术优势：
(1) SSL VPN 比 IPSec VPN 部署和管理成本更低： IPSec VPN 最大的难点在于客户端需要安装复杂的软件，而且当用户的 VPN 策略稍微有所改变时， VPN 的管理难度将呈几何级数增长。 SSL VPN 则正好相反，客户端不需要安装任何软件或硬件，使用标准的浏览器，就可通过简单的 SSL 安全加密协议，安全地访问网络中的信息。

(2) SSL VPN 比 IPSec VPN 更安全 : SSL VPN 只需要开放 443 端口，而 IP Sec VPN 需要根据不同的应用开放不同的端口，而且是等于直接物理访问内部网络，会因为外部接入点的不安全而影响到内网的安全。

(3) SSL VPN 比 IPSec VPN 有更好可扩展性 : IPSec VPN 在部署时一般放置在网络网关处， SSL VPN 一般部署在内网中任一节点处， IPSec VPN 的可扩展性比较差。

(4) SSL VPN 在访问控制方面比 IPSec VPN 有更细粒度 : IPSec VPN 部署在网络层，可以访问整个内部网；而 SSL VPN 则在应用层，可以控制用户访问不同的应用系统和不同的数据，具有更细的控制度。 OA 、 CRM 、 ERP 、 SCM。

一般而言， SSL VPN 必须满足最基本的两个要求：
(1) 必须使用 SSL 协议进行认证和加密；没有采用 SSL 协议的 VPN 产品自然不能称为 SSL VPN 。而且必须采用 128 位或以上密钥长度加密，否则会由于加密强度不够而形同虚设；
(2) 一般来讲，访问 SSL VPN 直接使用浏览器就能登录到内部网管理系统，无需安装独立的客户端。如果采用专用 VPN 客户端软件，则一定要确保使用了 https 方式实现 VPN 访问。


# SSL VPN 应用考虑
1、应用需求
    选择 VPN 是为了支持远程访问内部网络的应用，因此这一点也是最先需要考虑的一点，目前，大多数 SSL VPN 支持我们日常经常会用到的邮件系统、 OA 系统、 CRM/ERP 等等，但并不是所有的应用 SSL VPN 都能够提供支持。因此，在决定使用一款 SSL VPN 前一定要先确定是否能支持你的应用。
2、安全需求
    秘钥长度保证传输安全，双因素身份认证，防火墙、防病毒软件结合，清除缓存数据，日志审计追踪
    要构建一个安全的 VPN 系统，不仅仅需要传输过程安全，还要提高系统安全性，以下几个方面是缺一不可的：
    (1) 传输过程安全
    传输的过程加密强度是确保内部数据不在传输过程中被黑客盗取的关键因素。传输过程加密强度越高，传输安全性就越有保障。如上所述， 40 位和 56 位加密已经不安全，必须选择支持 128 位加密的 SSL VPN 产品，选择时需要特别注意此点。

    (2) 用户身份验证
    用户名加密码的验证方式已经非常不安全了，除了用户名和密码外，能提供其他的双因素验证方式的产品更加具有优势，如：客户端证书认证或 OTP 动态密码认证等。

    (3) 客户端电脑的安全性：
    客户端电脑是否安装了防火墙、防病毒软件等。如果客户端电脑不够安全，比如有木马程序，那么系统依然存在安全隐患。目前部分 SSL VPN 能够提供客户端环境检测，比如检测客户端是否安装了防火墙和防病毒软件。当客户端不符合某个条件时，系统将禁止用户登陆。

    (4) 完成访问后，客户端需要清除客户端电脑的缓存
    在移动用户完成远程访问后，系统应该提醒用户清除客户端电脑中的各种缓存，否则，如果是共用电脑的话，不法分子可以通过拷贝、复制驻留在客户端电脑中的缓冲区内数据盗取企业机密信息。当然，如果系统支持用户离线后可自动清除用户缓冲区的内容就更好了。
    (5) 服务端管理和日志跟踪
    SSL VPN 服务器应该提供访问统计和跟踪功能，这样管理员能够根据日志随时掌握系统访问情况。并且能有实时监控功能，对于发现不安全连接应该有能断开其连接的功能。

3、管理需求 
    SSL VPN 的突出优势之一就在于移动性强、易用性强。但这些特性往往会增加管理难度。因此用户在选购 SSL VPN 时要重点考虑产品的管理性能。产品要做到界面简单，使用方便，灵活、细致地设置访问权限 , 采用基于用户 / 组 / 角色的认证机制，每个文件、网址或应用都可进行单独设置，使访问控制更易于管理。

4、性能需求
    由于是集中系统， SSL 加速决定整个网络的吞吐量。如果 SSL 加速跟不上，远程接入就会比实际的 Internet 接入带宽低很多。有的 SSL VPN 产品采用专门的 SSL 加速硬件，从而提高了 VPN 的响应速度。另外，通过数据压缩技术，还对所有的传输数据进行压缩后再进行传输，这样就提高了整个网络的运行效率和实用性。

最后需要强调是：需要单独购买支持浏览器的 SSL 证书，隐患。


# 一个理想的SSL VPN解决方案应该具备以下五大特色。
一、强有力的安全保障
SSL VPN是建立在企业移动人员和公司总部之间的一条专用通道，在这条通道中传输的数据是企业内部数据，是不公开的。因此必须要在安全的前提下进行远程连接，一是客户端接入的安全性；二是数据传输的安全性；三是内部资源访问的安全性。
二、支持全面应用的连接
随着产品研发和升级的推进，目前SSL VPN已经支持全网连接，包括基于TCP协议的B/S和C/S应用，UDP应用，如WebDav、SMB文件共享访问、标准email协议、 Lotus Note、Telnet服务、远程终端、Citrix等。
三、易于管理和维护
SSL VPN的突出优势之一就在移动性强、易用性强、界面简单、使用方便、可以灵活设置访问权限，采用基于用户/组/角色的认证机制，每个文件、网址或应用都可进行单独设置，使访问控制更易于管理。
四、不因为处理SSL降低运行效率
由于是集中系统，SSL加速决定整个网络的吞吐量。如果SSL加速跟不上，远程接入就会比实际的Internet接入带宽低很多。通过数据压缩技术对所有的传输数据进行压缩后再进行传输，这样就提高了整个网络的运行效率和实用性。
五、稳定运行
接入的稳定性是满足用户远程访问的另一关键因素，用户不可能容忍经常出现网络中断现象。


# 国产SSL VPN的关键技术  2009-07-08 15:22 何晨 边歆 网界网
SSL VPN的关键技术包括：Web代理、端口转发、应用转换、网络连接(Network Connection, NC)，目前大部分的SSL VPN产品，都是以这几项技术的一项或几项为基础研发实现的。那么，对国产SSL VPN产品而言，哪些技术尤其重要呢?

首先是Web代理技术。由于用户需要访问内网的Web应用，而且希望访问方式尽量简便，而只有具备Web代理技术，SSL VPN产品才能做到100%零客户端，才能为用户提供最简便的接入方式，因此， Web代理技术对国产SSL VPN产品而言是一项必须技术，也是SSL VPN产品是否专业的重要标准之一。

除了Web代理技术，端口转发技术的重要性也不容小觑。除了要访问除Web应用外，用户还需要经常访问组织内部的C/S架构应用，例如邮件、FTP、文件共享、数据库、ERP等，这时，SSL VPN产品采用端口转发技术实现对C/S应用的处理，是再合适不过的了。

至于应用转换技术，目前国内用户需求并不迫切。由于SSL VPN产品需要把FTP、Email，SSH等应用以Web的形式重新实现，实现起来比较复杂，还可能存在提供的功能不够完整，界面不够友好，不太符合用户的操作习惯以及控件引用是不合法等一系列问题。从另一个角度来看，用户在没有使用SSL VPN之前，都已经习惯通过相应的客户端软件对C/S应用进行访问，在使用SSL VPN后，仍然希望通过使用原来的客户端软件访问内部的各种C/S应用。由此看来，应用转换技术并不十分适应于国内的用户，也并非是国产SSL VPN产品的必须功能。

最后再看NC技术，由于NC技术可以实现SSL VPN与应用无关的特性，因此客户端通过SSL VPN访问内部整个子网的需求仍然存在。然而，在使用该功能时，需要给客户端配置虚拟IP地址，这样一来，就会遇到地址规划上的一些问题，在配置和使用上也比较复杂。目前，国内已经有SSL VPN厂商注意到这个问题，为了更好地满足用户对易用性的要求，采用了一种“网络层代理”技术，客户端通过SSL VPN产品访问内部整个子网时，不需要借助虚拟IP地址，也不需要改变内网服务器网关指向，有效地解决了NC功能配置和使用复杂的难题。但目前，“网络层代理”技术还存在一个问题，即无法处理TCP连接由内向外发起的应用，无法做到“与应用无关”。如果有SSL VPN产品能够同时具备NC和网络代理功能，将会受到更多国内用户的青睐。

更贴心的功能

以上列举的只是SSL VPN产品的几项主要技术，为了更好地满足国内用户的需求，SSL VPN产品还必须在功能上进一步贴近需求，不断丰富。那么，国产SSL VPN产品在功能上应该如何“修炼内功”呢?

丰富的认证方式：国内用户类型众多，对认证方式和安全性要求也不尽相同。除了基本的本地口令外，动态口令、短信口令、口令+动态附加密、证书+USBKEY、口令+证书+USBKEY等多因素认证方式也越来越常见，成为对SSL VPN产品的基本要求。此外，随着CA体系在中国不断健全，越来越多的用户从专业的CA企业购买服务，因此国产SSL VPN产品能否很好地与标准第三方CA系统兼容，能否提供标准OSCP、CRL等证书校验接口，在一定程度上决定了该产品能否应用到用户现有环境中。

线路优化：国内用户常常向不同的ISP申请了多个公网IP提供服务。如果SSL VPN产品能够利用多个网口通过多个公网IP对外提供接入访问，并可以根据接入客户端的ISP来源选择最佳路径，那么将可以大大提高访问效率，更好地适应国内的网络环境。

单点登录：在用户的内网中，OA系统通常都带认证功能，使用者需要提交用户名及口令才可登录。加上SSL VPN后，用户就首先要登录SSL VPN，然后再次提交认证信息登录OA，导致重复认证过程。为了简化登陆程序，SSL VPN产品应该能记录用户登录SSL VPN时的认证信息，在用户访问OA时，代替用户提交认证，用户不需要再次输入用户名和口令就可打开登录成功后的页面。

端点安全：安装SSL VPN产品后，端点安全也是不得不考虑的重要方面。是否允许所有PC都接入SSL VPN，在连接SSL VPN隧道后是否允许访问互联网，在SSL VPN客户端注销后，访问痕迹是否应该清理，都是SSL VPN需要重点考虑的几个安全问题。目前，国内很多SSL VPN产品也都有应对措施。在客户端主机接入之前，先检测终端主机上是否具备管理员要求的某些特征，如操作系统版本、IE浏览器版本、是否运行了杀毒软件等等，如果不满足安全策略，则拒绝连接。在建立隧道后，SSL VPN产品还可以禁止客户端主机访问隧道以外的网络以确保隧道安全;在终端用户注销后，还会自动清除此次的访问痕迹，确保信息不被泄漏。此外，如果产品能实现帐号和客户端主机特征绑定以及防伪造功能等，将可以进一步提高客户端的端点安全性。

应用层防御：SSL VPN产品是以应用为核心的安全接入产品，因此应用层的安全防御必不可少。目前，防SQL注入，防跨站脚本和防非法URL访问等功能已经出现在一些国内品牌SSL VPN产品上。甚至有厂商还提供了基于账号的最大并发上限控制功能，有效防止了一个账号恶意产生大量连接的DoS攻击行为，有效保障了应用服务系统。

安全审计：SSL VPN产品相对传统VPN的优势之一就是审计更加详细。相比而言，SSL VPN产品更关注账号而不仅仅只是IP地址。在日志中应该可以记录哪个用户、在什么时间，在什么地理位置通过哪个ISP登录了SSL VPN，访问了什么服务，访问了哪些Web页面等等。另外，SSL VPN产品还应该提供基于各种条件(如时间范围、关键字等)的查询功能，甚至可以根据时间范围生成报表提供浏览和下载。

综合以上所有因素来看，SSL VPN产品与其说是一项技术，不如视之为服务。谁的SSL VPN产品能在上面所述各项技术和功能中做得更精细，更人性化，更贴近用户需要，谁的产品就会在激烈的市场竞争中取得胜利。

![](VPN技术(IPsec_L2TP_SSLVPN_PPTP)学习笔记-【安基网】.png)
