### TCP/IP特征
  + 逻辑编址
    > Internet为接入的计算机分配一个逻辑地址：包含**网络ID号**，**子网络ID号**，**主机ID号**
  + 路由选择
    > TCP/TP中包含了定义路由器如何选择网络路径的协议
  + 域名解析
    > 将域名映射为IP地址的操作称为域名解析
  + 错误检测
    > 检测数据信息的传输错误、确认已传递的数据信息已被成功接收
  + 流量控制
    > 监控网络系统中的信息流量，防止出现网络拥塞
 
### TCP/IP分层模型
  + 模型图示<br>
  ![10-2](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E5%8D%81%E7%AB%A0-%E7%BD%91%E7%BB%9C%E4%B8%8E%E4%BF%A1%E6%81%AF%E5%AE%89%E5%85%A8/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/10-2.png)
  + 协议关系图示<br>
  ![10-3](https://github.com/flysafely/Software-Design-Engineer-Note/blob/master/%E7%AC%AC%E5%8D%81%E7%AB%A0-%E7%BD%91%E7%BB%9C%E4%B8%8E%E4%BF%A1%E6%81%AF%E5%AE%89%E5%85%A8/%E6%9C%AC%E7%AB%A0%E5%9B%BE%E7%A4%BA/10-3.png)
  + 应用层
  
  |协议名|端口号|基于协议|功能|
  |:--:|:--:|:--:|:--:|
  |POP3|110|TCP|邮件收取|
  |SMTP|25|TCP|邮件发送|
  |FTP|20数据端口/21控制端口|TCP|文件传输|
  |HTTP|80|TCP|超文本传输协议|
  |HTTPS|443|TCP|加密超文本传输协议|
  |Telnet|23|TCP|远程登录服务协议|
  |DHCP|67|UDP|IP地址自动分配|
  |TFTP|69|UDP|简单文件传输协议|
  |SNMP|161|UDP|简单网络管理协议|
  |DNS|53|UDP|域名解析服务|
  + 传输层
  
  |协议|协议名|
  |:--:|:--:|
  |TCP|控制传输协议(可靠)|
  |UDP|用户数据报协议(不可靠)|
  + 网际层
  
  |协议|协议名|
  |:--:|:--:|
  |IP|IP协议|
  |ICMP|因特网控制协议|
  |IGMP|组播协议|
  |ARP|地址解析协议|
  |RARP|反向地址解析协议|
  + 网络接口层(硬件层)
