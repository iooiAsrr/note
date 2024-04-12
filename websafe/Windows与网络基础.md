# 目录

[TOC]

# 虚拟机基本操作









# Windows基本命令

#### 目录和文件操作

coding /?

1. cd 切换目录

2. dir 显示目录和文件列表

3. md (mkdir)创建目录文件夹

4. rd (removedir)删除文件夹

   - /s 删除目录和文件

   - /q 静默删除

5. del 删除文件

6. move 移动文件/改名

   - /y  /-y 是否提示

7. copy 复制问卷

   - 复制多个用+号

8. xcopy 文件目录树复制



#### 文本处理

1. `>` 文字重定向
2. type 显示文本内容
3. 管道符`|` 
   - 前面执行结果作为后面命令操作对象
4. findstr 查找文件内容
   - findstr 11 c:\1.txt

#### 网络相关

1. 配置TCP/IP参数

   - IP地址 标识主机
   - 子网掩码 标识IP所处网络范围,子网掩码越大,网络范围越小
   - 默认网关 标识与主机的直连路由器的IP地址
   - DNS服务器 域名解析

   ```powershell
   #TCP/IP参数
   netsh interface ipv4 set address "netname" static(静态) ip 	子网掩码 网关
   #DHCP
   netsh interface ipv4 set address "netname" dhcp
   #DNS
   netsh interface ip set dnsserver "netname" static dns
   netsh interface ip add dnsserver "netname" dns index=2(索	引,备用DNS服务器)
   net interface ip add dnsserver "netname" dhcp
   ```

   

2. 查看TCP/IP配置,用ipconfig

   ```powershell
   #查看所有网卡TCP/IP参数(IP地址,子网掩码,默认网关)
   ipconfig
   #查看所有网卡参数(IP地址,子网掩码,默认网关,MAC地址,DHCP地址,DNS	地址,主机名)
   ipconfig /all
   #释放TCP/IP参数
   ipconfig /release
   #重新获取TCP/IP参数
   ipconfig /renew
   #刷新DNS缓存
   ipconfig /flushdns
   ```

   

3. ping

   ```powershell
   #默认发送32字节4报文
   #-n 发送10个报文 -l 单个报文1000字节 -a 返回主机名 -t 一直ping
   ping -n 10 -l 1000  -a IP
   ```

4. tracert

   ```powershell
   #路由跟踪
   tracert IP
   ```

5. route

   ```powershell
   #操作路由表
   #0.0.0.0代表的任意网络
   
   #打印路由表
   route -4 -print
   
   #添加路由条目
   #(1.1.1.1目标地址或网络 /32代表子网掩码或者1.1.1.0目标网络,/24代表子网掩码,2.2.2.2网关地址)
   route add 1.1.1.1/32 2.2.2.2
   
   #删除路由条目
   route delete 1.1.1.1(目标)
   ```

6. netstat

   ```powershell
   #查看所有TCP链接,包括进程,以数字形式显示
   netstat -anop tcp
   #查看路由表
   netstat -r 等同于 route print
   ```

   

# Windows用户/组管理

#### Windows用户管理

1. 什么是用户

   - 不同的用户身份有不同的权限

   - 每个用户包含了一个名称和密码

   - 每个用户具有唯一安全标识符(SID)

   - 查看系统用户

     ```powershell
     net user
     ```

     - 注册表查看

       ```powershell
       regedit
       #路径
       Prodilelist
       ```

     - 管理员SID是500,普通用户SID是从1000开始

2. 进行用户管理

   - 用户名,全名,密码

   - 账户已锁定:若开启了账户锁定阈值,输错密码多次讲=将锁定

     ```powershell
     #创建用户不指定密码
     net user user1 /add
     #创建用户指定密码
     net user user1 123123 /add
     #创建用户手动输入密码
     net user user1 /add *
     #删除用户
     net user user1 /del
     ```

     ```powershell
     #修改用户密码
     net user user1 123123
     net user user1 *
     ```

3. 管理用户

4. 设置密码

5. 隐藏用户

   - 在用户后面加上了$符号,用net user命令无法查看

#### Windows的内置用户账户

1. 与使用者关联的
   - 管理员:使用者最高权限administrator
   - 普通用户:具有一般的读取权限
   - 来宾用户:一般提供访客使用,权限最低,默认禁用
2. 与Windows组件关联
   - system 本地系统 拥有最高权限
   - local service 本地服务 权限相对于普通用户低
   - network service 网络服务 权限和普通用户一样

#### Windows组的管理

1. 用户组

   - 概念：一组用户的集合，组内成员具有所组权限

   - 管理组

     ```powershell
     #创建
     net localgroup group_name /add
     #删除组
     net localgroup group_name /del
     #把用户添加/删除到组里面
     net localgroup group_name user1 /add|del
     ```

     

2. 内置组账户

   - 需要人为添加的
     - administrators:管理员组
     - guests:来宾用户组
     - power users:向下兼容的组,现在一般没有使用
     - users:标准用户组,创建用户后默认处于此组中
   - 动态包含的成员组
     - interactive:动态包含在本地登录的用户
     - authenticated users:动态包含通过验证的用户
     - everyone:所有人,包含了来宾用户

# NTFS

#### NTFS权限

- 文件系统

  - 早期Windows,使用fat16,fat32
  - 目前Windows使用ntfs文件系统
    - ACL(访问控制列表,设置权限)
    - EFS(加密文件系统,私用bitlocker进行磁盘加密)
    - 压缩和磁盘配额
  - ReFS文件系统

- Linux

  - swap:交换文件系统,将磁盘部分空间划分给内存使用
  - ext4: 

- 早期FAT文件系统不支持单个大文件(超过4GB)

- 文件系统转换

  ```powershell
  #h:盘符
  convert h:/fs ntfs
  ```

#### 文件权限

- 设置文件权限
  - 读取数据
  - 写入数据
  - 附加数据
  - 删除
  - 执行文件

#### 文件夹权限

- 设置文件夹权限
  - 列出文件夹
  - 创建文件夹
  - 创建文件
  - 删除
  - 删除文件夹及子文件

#### 权限分类

- 完全控制

- 修改

  ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012039984.png)

- 读取和执行

  ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012039890.png)

- 读取

  ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040309.png)

- 写入 

  ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040411.png)

- 特殊权限 

  ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040562.png)

#### NTFS权限规则

1. 权限规则
   - 权限累加
     - 用户分配所有权限累加
   - 拒绝权限
     - 拒绝权限大于一切(优先级最高)
   - 继承权限
     - 子文件/文件夹的访问控制列表默认情况下会继承上级文件夹的权限
   - 特殊权限
     - 读取权限(和读取文件或文件夹的内容没有任何关系)
       - 读取文件或文件夹的访问控制列表
       - 读取文件内容必须勾选此权限
     - 更改权限(和修改文件或文件夹内容没有任何关系)
       - 相当于完全控制,一般不赋予[前提是必须能查看/读取(特殊)]
       - 自己给自己赋权
     - 取得所有权(对比更改权限更鸡肋)
       - 能够修改文件或文件夹所有者
       - 前提是必须得读取和修改

# 本地安全策略

#### 本地安全策略基本内容

1. 概念

   - 主要是对登录到计算机的账户进行一些安全设置
   - 主要影响是本地计算机安全设置

2. 打开方式

   - 开始菜单->管理工具->本地安全策略

   - 命令

     ```powershell
     secpol.msc
     ```

   - 从本地组策略进去

     ```powershell
     gpedit.msc
     ```

#### 账户策略

1. 密码策略

   - ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040864.png)

2. 账户锁定策略

   - 管理员不受限制(Windows管理员爆破)/隐藏管理员

   - 计数器<=账户锁定时间

   - ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040212.png)

#### 本地策略

1. 审核策略
   - ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040170.png)
2. 用户权限分配
3. 安全选项
4. 远程桌面登陆

# Windows共享

#### 共享要求

1. 一般是同处于同一局域网
   - 同意公司网络
   - 同一家庭网络
   - 同一热点
2. 逻辑上处于同一局域网
   - 直接可以ping通对方主机

#### 共享权限

1. 共享权限

   - 一般为everyone完全控制

2. NTFS权限

   - 前面已经设置完成

3. 用户从网络访问server的最终权限

   - 由共享权限和NTFS权限的交际部分
     - 例:user1共享权限是读取,NTFS权限是读取和写入,user1的网络共享最终权限是读取
   - 经常设置办法
     - 共享权限设置最大,NTFS进行精细化设置

4. 访问共享

   - ```powershell
     \\IP 	#IP访问
     \\hostname	#主机名访问
     ```

# 组策略应用

#### 组策略基本概念

//计算机策略>用户策略

1. 概念:一组策略的集合

2. 打开方式

   ```powershell
   gpedit.msc
   ```

3. 刷新策略

   ```powershell
   gpupdate /force
   ```

4. 模块

   1. 计算机配置
      - 针对于计算机生效
   2. 用户配置
      - 针对用户生效

#### 案例

1. 隐藏桌面的系统图标(针对用户配置)

   - 用户配置->管理模版

2. 保护"任务栏"和开始菜单

   - 用户配置->开始菜单和任务栏

3. 保护个人文档隐私

   - 用户配置->开始菜单和任务栏->不保留最近的历史和退出时清理

4. 禁用浏览器在新窗口打开(弹跳转广告)

5. 禁用控制面板

   - ```powershell
     control.exe	#控制面板
     ```

6. 关闭自动播放

7. 配置Windows更新 

8. 从网络组中找3个组策略应用

# 注册表

#### 注册表基础

1. 概述

   - 册表是Windows操作系统、硬件设备以及客户应用程序得以正常运行和保存设置的核心数据库”，也可以说是一个非常巨大的树状分层结构的数据库系统
   - 册表记录了用户安装在计算机上的软件和每个程序的相互关联信息，它包括了计算机的硬件配置，包括自动配置的即插即用的设备和已有的各种设备说明、状态属性以及各种状态信息和数据。利用一个功能强大的注册表数据库来统一集中地管理系统硬件设施、软件配置等信息，从而方便了管理，增强了系统的稳定性

2. 早期注册表

   - 以ini为扩感名的文本文件的配置文件

3. Windows95后注册表

   - Windows95操作系统开始，注册表真正成为Windows用户经常接触的内容，并在其后的操作系统中继续沿用。注册表数据库由多个文件组成oWindows提供了注册表编辑器

   - ```powershell
     regedit #打开注册表编辑器
     ```

4. 注册表结构

   - 树（实际只有两棵子树，为了方便操作，分成了5棵子树）
     - KEY_LOCAL_MACHINE：记录关于本地计算机系统的信息，包括硬件和操作系统数据
     - EY_USERS：记录关于动态加载的用户配置文件和默认配置文件的信息
     - EY_CURRENT_USER：HKEY_USERS子树，它指向"HKEY_USERS\当前用户的安全ID"包含当前以交互方式登录的用户的用户配置文件
     - EY_CURRENT_CONFIG:HKEY_LOCAL_MACHINE子树，指向HKEY_LOCAL_MACHINEISYSTEM\CurrentControlSet\HardwareProfiles\Current包含在启动时由本地计算机系统使用的硬件配置文件的相关信息加载的设备驱动程序、显示时要使用的分辨率
     - EY_CLASSES_ROOT：HKEY_CURRENT_USER子树包含用于各种OLE技术和文件类关联数据的信息
   - 项
     - 可以简单的理解文件夹，项中可以包含项和值
   - 值
     - 个注册表项或子项都可以包含称为值的数据
     - 分值应用于某个用户的信息
     - 分值应用于计算机所有用户的信息
     - 由三部分组成（值的名称、值类型、值的数据）

   ![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040092.png)

#### 注册表基本操作

1. 创建项
2. 创建值(六种)
   - 符串值（REG_SZ）：固定长度的文本字符串
   - 进制值（REG_BINARY）：原始二进制数据。多数硬件组件信息都以二进制数据存储
   - WORD值（REG_DWORD）：数据由4字节长的数表示。设备驱动程序和服务的很多参数都是这种类型
   - WORD值（REG_QWORD）：数据由8字节长的数表示
   - 字符串值（REG_MULTI_SZ）：多重字符串。包含列表或多值的值通常为该类型
   - 扩充字符串值（REGrEXPAND_SZ）：长度可变的数据串。该数据类型包含在程序或服务使用该数据时解析的变量

#### 注册表应用

1. 案例
   - 禁用任务管理
     - 打开注册表编辑器，锁定HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\PoliciesISystem下新建DWORD值DisableTaskMgr，设置值为1
   - 用控制面板
     - 开注册表编辑器，锁定"HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer下新建DWORD值NoControlPanel，设置值为1
   - 除快捷方式左下角小箭头
     - 开注册表编辑器，锁定“HKEY_CLASSES_ROOTInkfile”找到项下的IsShortcut值，直接删除
2. 注册表编辑技巧
   - 查找字符串,值或项
   - 将子项添加到收藏夹
   - 打印注册表
   - 复制项名字

#### 组成表优化与维护

1. ```powershell
   注册表被破坏后的常见现象
   #无法启动系统
   #无法运行或正常运行合法的应用程序
   #找不到启动系统或运行应用程序所需的文件
   #没有访问应用程序的权限·不能正确安装或装入驱动程序
   #不能进行网络连接
   #注册表条目有错误
   ```

2. ```powershell
   册表被破坏的原因
   #用程序错误：在系统中安装过多的软件后，可能会出现彼此之间的冲突
   #动程序不兼容：安装系统时有很多驱动都是自动安装，容易产生不同硬件驱动程序不兼容情况，建议到官方网站下载对应稳定版驱动进行安装
   #件问题：主要出现在硬件质量上，比如硬盘或内存质量不过关造成读写错误、超频、CMOS、病毒等
   #操作：误操作是最常见的原因，可能会导致注册表出现错误，严重者造成系统崩溃或无法启动系统
   ```

3. 备份注册表

   - 导出
   - 导入

4. 锁定和解锁注册表

   - 开注册表编辑器，锁定到“HKEY_CURRENT_USERISOFTWARE\Microsoft\Windows\CurrentVersion\PoliciesISystem"项中新建DWORD值DisableRegistryTools，将值设置为1，表示锁定，设置为0表示解锁
   - 当注册表被锁定后，Windows自带的注册表编辑器就无法打开，需要使用外部第三方注册表编辑工具来进行打开，找到对应项，修改值为1

#### 注册表优化

1. 优化内容
   - 除多余的DLL文件
     - 打开注册表编辑器，锁定到“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SharedDLLs"项，在这个项下存放的是共享的DLL信息，注意看括号里面的数据，它表示共享文件的数目，如果为0，则可将其删除
   - 装卸载应用程序的垃圾信息
     - 打开注册表编辑器，锁定到“HKEY_CURRENT_USERISOFTWARE"项和“HKEY_LOCAL_MACHINE\SOFTWARE"项，这两个项中包含系统中的应用程序，对于已知的程序是知道的，主要是针对一些未知的程序进行删除和一些已经卸载了的残留
   - 统安装时产生的无用信息
     - 除多余时区（必要情况下只保留北京时区）
       - 定到“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\TimeZones"项
     - 除多余的语言代码（英语一0409、中文－0804)
       - 定到“HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\Locale"项
     - 除多余的键盘布局
       - 定到“HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSetIControlKeyboard Layouts"项，下面每一个子项代表一种键盘布局

# 计算机网络

#### 常见概念

1. 协议和标准
   - 协议:规则通信及实体交换信息所需要遵循的规则的集合
   - 标准:
     - ISO
     - ITU
     - IEEE
2. 网络分类
   - 广域网:WAN,万维网,外网
   - 城域网:一个城市的网络
   - 局域网:LAN,公司,家庭,内网
3.  IEEE802局域网标准(1980年2月提出)
   - 有线局域网
     - 802.3
       - 802.3u:百兆快速以太网
       - 802.3z:光钎实现千兆
       - 802.3ab:双绞线实现千兆(超五类六类)
       - 802.3ae:实现万兆
       - 802.3ba:实现十万兆
   - 无线局域网
     - 802.11
       - 802.11a:速率最高54Mbps(5G)
       - 802.11b:速率最高11Mbps(2.4G)
       - 802.11g:速率最高54Mbps(2.4G)
       - 802.11n:速率最高600Mbps(5G)
4. 主流网络厂商及设备
   - 思科
   - 华为
   - 新华三(H3C)
5.  网络拓扑
   - 星形/双星型网络拓扑![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040489.png)
     - 易实现,中心节点压力大
   - 网型拓 扑![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012040795.png)
     - 成本高可靠性高

#### 计算机网络参考模型

1. OSI七层参考模型

   ```markdown
   物理层(光纤光信号,网线电信号,无线电波):将二进制转换为光/电信号:建立,维护断开物理链接
   数据链路层(收发设备MAC地址)建立逻辑链接,进行硬件地址(MAC)寻址,差错效验
   网络层(收发设备IP)进行逻辑地址(IP)寻址,实现不同网络之间的路径选择
   传输层(协议端口号)定义传输数据的协议端口号,流控,差错效验
   会话层(程序建立回话)建立,管理,终止回话
   表示层(加密/压缩...)数据的表示加密压缩等
   应用层(文本等数据)将原始的数据转换为电脑能够识别的二进制数
   ```

   

2. TCP/IP(传输控制协议/网际协议)四/五层参考模型

   - 四层
     - 网络接口层
     - 网络层
     - 传输层
     - 应用层
   - 五层
     - 物理层
     - 数据链路层
     - 网络层:IP(ARP:地址解析协议;RARP:逆地址解析;ICMP:网际控制报文协议;IGMP:网际组管理协议)
     - 传输层:TCP(传输控制协议)稳定可靠;UDP(用户数据报协议)效率高
     - 应用层:HTTP HTTPS SSH TELNET DNS POP3 IMAP TFFTP FTP NTP

# 数据封装与解封

<img src="https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012041330.png" style="zoom: 80%;" />



# 传输介质

#### 信号

1. 基本概念
   - 信息
   - 数据
   - 信号
2. 分类
   - 模拟信号(声音)
   - 数字信号(计算机大小用有限位的二进制标识)

#### 双绞线

1. 同轴电缆(有线电视)
   - 最高速率10Mbps
2. 双绞线
   - 速率高,应用广泛,技术成熟,成本低
   - 屏蔽双绞线:主要应用于电磁干扰较强的场景
   - 非屏蔽双绞线:主要应用于没有电磁干扰的场景
   - 以太网接口:RJ-45接口(水晶头)
   - <img src="https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012041314.png" style="zoom:60%;" />

#### 光纤

<img src="https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012041213.png" style="zoom:80%;" />

#### 网络接口控制器(网卡)NIC

<img src="https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012041891.png" style="zoom:80%;" />

# 二进制基础





# IP地址

#### 概念

1. IP:某一网络接口,主机唯一标识,保证主机间的正常通信
   - 一种网络编码,用来确定网络中的一个节点
   - IP地址有32为二进制组成,方便记忆,8为为一组,以逗号分隔,转换为十进制
2. IP的组成
   - 网络部分:用于标记网络的范围
   - 主机部分:用于标识网络范围中的一个节点
   - 网络部分越长,表示的网络范围越小,网络部分越短,表示的网络范围越大

#### IP地址分类

1. 公有
   - A,B,C,D,E五类
     - A类:确定前8为为网络位后面24位为主机位,并且以0开头
       - 第一个8为组范围0~127 由于"0"代表本地网络,127开头的地址一般用于回路检测,最终范围:1~126
     - B类:确定前16位为网络位,后16位为主机位,并且以10开头
       - 第一个8位组范围:128~191
     - C类:确定前24位为网络位,后8位为主机位,并且以110开头
       - 第一个8位组范围:192~223
       - 192.0.0.0~223.255.255.255
       - 网络部分范围:192.0.0.0~223.255.255
2. 私有IP地址分类
   - A:10.0.0.0~10.255.255.255
   - B:172.16.0.0~172.31.255.255
   - C:192.168.0.0~192.168.255.255
   - 私网地址本能够在公网上直接路由,需要网络地址转换将私网地址转换为公网地址后方可访问

# 子网掩码

#### 概念

1. 概念
   - 用来确定IP地址的网络部分
   - 有32位的二进制组成,对应IP的网络部分由1标识,主机部分由0表示
     - 根据子网掩码来得出网络部分和主机部分,在本网络的第一个地址就是网络地址,本网络的最后一个地址就是广播地址
     - 使用IP地址和子网掩码进行逻辑"与"得出网络地址
2. 默认子网掩码
   - A:255.0.0.0 8位
   - B:255.255.0.0 16位
   - C:255.255.255.0 24位
3. 子网掩码越长,代表网络部分越长,网络范围越小,子网掩码越短,代表网络部分越短,网络范围越大
4. 网络地址代表的是一个范围,不能够给主机使用
5. 广播地址,代表本网段的所有地址,也是不能够直接给主机使用

# 子网划分

![](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403012041553.png)

#### IP地址分类

- 如果一个IP地址采用的是默认子网掩码:有类地址
- 如果不是默认子网掩码:无类地址

#### 子网划分原理

- 子网位划分:增加网络部分(向主机位借位,借的位数称为子网位)
- 网络部分越长,网络范围越小