## A Security Protocol for Information-CentricNetworking in Smart Grids ##

**作者：** Bárbara Vieira，Erik Poll

**单位：** Radboud University Nijmegen, The Netherlands

**出处：** SEGS'13：关于智能能源安全的首届ACM研讨会论文集.2013年11月.第1-10页

**原文链接：** <https://dl.acm.org/doi/pdf/10.1145/2516930.2516932>

**笔记作者：** pluto


### 主要内容 ###
早期，欧盟FP7项目C-DAX(Cyber-secure Data and Control Cloud)研究了一种基于infor-map-centric networking (ICN)解决方案(IP覆盖)的智能电网监控信息共享解决方案。C-DAX方案它没有应用以主机为中心的点对点通信，而是支持以数据为中心的组通信，这种方法可以避免通信双方知晓双方IP地址，在一定程度上降低了网络传播攻击的风险。但这种方案的实现使得像**TLS/SSL或IPSec等传统的安全解决方案不能保证整个通信消息的机密性、完整性和真实性。**

因此，针对上述问题，作者提出了一种**基于内容的签密方案(CBS)**，用于以信息为中心的通信加密模型。CBS方案由四种算法组成：第一个算法在系统设置程序中执行（由PKG执行），并推导系统参数（公共和私有参数）； 第二种算法用于派生每个主题组的秘密密钥，每次将新主题添加到系统时执行。 第三和第四算法分别用于发布和订阅主题数据。在将这种算法应用于C-DAX方案后，会由一个安全云服务器统一创建并发布一个主题密钥，每个发布者再自行创建签名并加密相应内容进行发布。云服务器会对出版用户身份进行验证，验证成功即可将信息内容发送至订阅者。应用CBS模式的C-DAX结构使得发布与订阅的密钥相分离，**达到了对消息通信过程中机密性、完整性的保护。**

### 创新点 ###

- 密钥安全性更高。它可以通过专用的私有密钥生成器(即C-DAX安全云服务器)向本地客户端发出密钥，从而在不同的智能电网域中实施端到端安全性。

- 它在发布/订阅级别提供了细粒度的访问控制:每个主题的公钥都关联了两个秘钥，一个用于发布，另一个用于订阅。

- 提议的方案是可公开验证的。云服务器可以对所有的主题进行身份验证，像客户端发布的数据。在验证过程中不需要知道密钥，也不需要发布者创建的任何其他身份验证令牌。


### 缺点 ###
- 基于CBS模式的C-DAX方案对向外部方公开发布密钥的弹性较弱。例如，如果某个发布者受到攻击，任何人都可以伪装成某个特定主题组的合法发布者。

- 因为在整个方案中，所有的主题密钥都来自相同的主密钥。所以该方案对于当客户端加入或离开某个主题时的情况时，具有较差的键控能力。

- 该方案下基本是PKG控制整个系统，因此可能存在单点故障的风险。

### 缺点解决方案 ###
- 针对于公开发布密钥的弹性较弱这一缺点，解决该问题的一种方案是利用一种基于身份的加密(HIBE)的方法，向主题组中的每个发布者提供不同的发布密钥(来自单个发布主密钥)。例如，发布密钥可以派生自主发布密钥和每个发布服务器的唯一标识符。

- 针对于主题密钥来源单一的缺点，该问题的解决方案是为每个主题生成主密钥，以避免在客户端加入或离开特定主题时替换所有的主题密钥。

- 针对于可能存在单点故障的缺点，可以应用底层无证书签密的方法，删除密钥托管功能，以此来降低这种故障发生的风险。

### 替代方法 ###
- 经查阅相关文献后，为解决C-DAX方案中消息机密性问题，可以采用一种结合PKI和IBE的协议。其中PKI用于保证不同域的公共参数的真实性，发布者发送用其私钥签名的公共参数，订阅者可以使用相应的公钥证书验证其真实性。而IBE和IBS主要用于端到端安全性。

- 此外还可以通过建立一种基于自认证名称的模型的方法来替代本文作者提出的方法。该模型将内容的安全性与主机的信任联系在一起。发布者选择一个用户友好的名称，并通过数字签名将其与内容联系起来。

