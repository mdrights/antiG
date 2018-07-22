---
layout: post
date: 2018-07-22
---

## antiG 用户手册   

**系统帐号/密码：user/freedom123**  
**root帐号密码：toor**     


### antiG 能防御什么 & 不能防御什么

**请一定阅读这一部分**   

- 能防御什么  
> 从邮件附件、外界进入的文档/图片中的恶意程序，网页下载下来的木马，如果无法阻挡，那就防止它们**长期**驻留在系统对用户进行监视并回传用户数据，并保持一个干净的操作系统；   
> 不会对本地（原来）的系统和磁盘内容有任何影响，可以当作一个隔离的环境（如不联网的话）；
> 另一方面，也可以作为一个安全的查看不安全的、不信任的文件/程序的平台。

- 不能防御什么   
> 1. 阻止木马等恶意程序下载到当前环境； 
2. 如果当前环境有木马下载下来，并且当前环境中有敏感文件，并不能防止木马读取这些文件（除非使用一些隔离技术如沙盒（firejail））；   

## 启动方法  

1. 放在虚拟机 （如 Virtualbox）里使用（须先安装 [Virtualbox虚拟机软件](https://www.virtualbox.org/wiki/Downloads)；或   
2. 刻录到 USB盤上，插入任何一台电脑启动；（记得开机时进入BIOS设置为USB优先启动；刻录方法见[这里](https://rufus.akeo.ie/?locale=zh_CN)，或[这里](https://program-think.blogspot.com/2013/12/create-bootable-usb-stick-from-iso.html)。   
- 这两种方法都不会访问和修改本来的系统和文件（除非你主动挂载）
- 在开机画面可以选择不同的语言（目前有英语、简体中文、台湾正体、香港繁体、藏文、维吾尔文和日文；注：软件的中文化程度取决于各个软件项目作者和志愿者的努力，会有翻译不完整或错误的地方，本项目并不对此负责。）

## 软件使用方法

### 基本需求
- fcitx 輸入法     
	（按 `Ctrl + 空格` 激活；目前有簡體和繁體等）
- Wicd
	网络连接工具，如果你是用 USB盤啓動本系統的 XFCE版，請点击右上角图标连接WiFi（如果点出的菜单没有见到热点，很可能是本系统没有该机器无线网卡的驱动）；用虛擬機方式或其他版本則不必特意设置。    
- Libreoffice 
	（文檔編輯套件；已加入中文包，即界面是中文的了）
- 挂载本地硬盘或外置存储（如U盘/移动硬盘等）    
	（一般情况下直接在文件管理器左侧就能看到你机器本地的磁盘（分区）了；直接插入U盘一般都能识别。如有弹出提示要求密码的话，请输入 root（超级管理员）的密码：toor）    

### 穿牆
- Shadowsocks-libev 
	（执行：`ss-local -c <你的ss配置文件>`）
- Shadowsocks
	(执行：`sslocal -c <你的ss配置文件>`)


### 隱匿/隱身
- Tor Browser 洋葱浏览器 ( & Tor 命令行版 )    
	（記得啓動時，第一個問題選否（我們不用網橋），第二個選是（我們走本地代理），在Socks5處選擇 127.0.0.1 端口 1080 ）
	（或者，使用网桥；目前（2017.11）推荐选 meek-amazon，或 meek-azure。）    

 
### 安全地聯繫 (部分软件只在cinnamon版才有)  
- Telegram 
	(記得可在設置裏設置 socks（1080）代理（翻牆），或 Tor（9050））
- Hexchat    
	( IRC 客戶端，無需註冊帳戶；記得本軟件最好要 **走代理（包括翻牆或Tor）再用** ！！！否則會直接暴露你所用的 IP 地址，別說我沒提醒你蛤~）
- Signal-Desktop 桌面版
	（加密通讯软件；须先在移动设备安装Signal客户端，并有帐号）
- Riot-web   
	（新型“邦联化”聊天/协作工具，可以完美桥接 IRC，slack 等平台）   
- uTox   
	（p2p架构的（去中心化）通讯工具）   

### 加密大法   
- VeraCrypt     
	（加密工具；）
- keepassx    
	（密码管理器）
- GnuPG     
	(当然啦，GPG 是每款 GNU/Linux 都自带哒）
- gpa   
	(PGP密钥管理器)

### 毀屍滅跡 vs 反毀屍滅跡   
- wipe, secure-delete     
	（磁盘擦除工具 -注：一般仅对 **传统磁盘** 有效）   
	（在終端，`wipe` 接你要刪除的文件/目錄 即可；   
	secure-delete 則包括：    
	`srm`: 反覆擦除文件/目錄    
	`sfill`: 填充磁盤或某個目錄的可用空間（一般耗時很長.avi）   
	`smem`: 擦除內存中的數據（不知要等到什麼時候.jpg）
- testdisk    
	（数据恢复工具，在終端裏輸入 `testdisk` 即可按提示操作）

### 一些高級用法
- 防火牆 iptables    
	（在桌面菜单「网络」里，會要求輸入用戶密碼 `live`；配有一些簡單的規則）
- firejail    
	（沙盒，用于隔离应用软件，執行 `firejail` 後接你想要運行的程序即可）
- macchiato    
	（MAC地址随机化工具; 進入 `/opt/macchiato/`，執行 `macchiato` 看看）
- proxychains    
	（网络代理工具；用於在終端中讓程序走代理，第一次使用前請在配置文件 `/etc/proxychains.conf` 設置你自己的代理服務器地址/端口如：`socks5 127.0.0.1 1080`）
- privoxy    
	（网络代理工具, http 代理服務器；用於讓本地和同網的其他機器的流量走代理（像全局一樣））
	（第一次使用前請在 `/etc/privoxy/config` 設置你自己的代理服務器地址：`forward-sock5 / 127.0.0.1:1080`）


（還會陸續添加喔，如你有好點子，歡迎告訴我~）


### 【最后再强调一次：应对策略】    

1. 当前系统不要保留重要敏感文件（反正也不會保存），文件需要保存的话请转存到其他盘上；
2. 每次开机只做**一件事**，比如不是同一封邮件的附件就不要在同一次开机（环境）中打开；
3. 严格区分/定义每次使用的目的/性质：**是当作一个隔离的环境（如看一份重要的文件）呢，还是当作一个对不信任的文件/程序的载体**。 也就是说，如果你这次开机选择的是后者，就请尽量不要把放了重要文件的 U 盤挂载到当前环境，如果你这次环境选择的是前者，那不联网是最好的；
4. 下载下来的文件就不要再在宿主环境里打开了（就是安装了 Virtualbox的那个系统））


更新日期：2018.07.22