##1.论文信息
* 笔记作者：不舟
* 原文作者：刘潮歌，方滨兴，刘宝旭，崔翔，刘奇旭
* 原文题目：A Hierarchical Model of Targeted Cyber Attacks Attribution 
* 原文来源：Journal of Cyber Security Vol.4 No.4 July,2019
##2.论文简要
在面对定向网络攻击所构成的威胁时，本文提出将追踪溯源作为威慑性防御手段来替代传统的以识别并阻断攻击为核心的防御体系。本文将定向网络攻击追踪溯源进行了形式化定义和分类。建立了追踪溯源纵深体系，多维度追踪溯源定向网络攻击。
##3.主要内容
定向网络攻击追踪溯源层次化模型由网络服务、主机终端、主机数据、控制信道、行为特征和数据挖掘分析六个层次组成。  
1.网络服务层次：使用主被动结合的方法，从欺骗诱捕、标记取情两个方面追踪溯源定向攻击。  
2.主机终端层次：跳板攻击主机上的追踪溯源使用通过漏洞利用、弱口令等攻击方法，在费配合情况下远程渗透跳板主机获取追踪溯源线索的技术手段和请求攻击主机的网络运营商或上级部门予以协助的协调手段。而防御者一侧的主机终端上的追踪溯源可以借鉴网络欺骗技术思路。  
3.文件数据层次：被动分析恶意样本和主动施放诱饵文档。  
4.控制信道层次：主要是从域名、服务器、网络账号等通信基础设施入手, 获取攻击者在注册、使用过程中留下的溯源线索。  
5.行为特征层次：利益相关性、TTP特征、作息规律等。  
6.数据分析层次：基于已获取的关键线索, 以威胁情报等为信息储备, 利用大数据、人工智能等技术手段, 排除干扰、关联线索, 实现溯源线索向攻击者身份的映射。
##4.模型评价
![表1 各层次与“网络入侵杀伤链”模型的关系](表1.jpg)  
![表2 各层次与追踪溯源七大线索的关系](表2.jpg)    
![表3 各层次与追踪溯源三级目标的关系](表3.jpg)  
![表4 白象APT追踪溯源证据和各追踪溯源层次的对应关系](表4.jpg) 
##5.创新点  
* 为防御定向网络攻击提出了一个新的方向
* 将定向网络攻击追踪溯源进行了形式化定义和分类
* 采用主被动相结合的方式追踪溯源定向网络攻击
* 提出了建立追踪溯源纵深体系，多维度追踪溯源定向网络攻击
##6.缺点
* 可能引发新的安全风险：将网络攻击诱骗到内网环境里面，给了攻击者一些方便，若被攻击者使用0day、社工等手段突破欺骗环境，则会带来巨大风险。