# 远程访问

## 远程访问简介

有时您需要访问 Raspberry Pi，而不将其连接到显示器、键盘和鼠标。也许 Raspberry Pi 嵌入在机器人中或安装在不方便的位置。或者您可能没有备用显示器。

### 通过本地网络远程控制

要从本地网络上的另一台设备远程控制 Raspberry Pi，请使用以下服务之一：

- SSH
- VNC 虚拟网络控制器
- Raspberry Pi Connect 树莓派连接

SSH（Secure SHell）提供对 Raspberry Pi 上终端会话的安全访问。 VNC（虚拟网络计算）提供对 Raspberry Pi 上桌面屏幕共享的安全访问。您所需要的只是另一台计算机、本地网络和 Raspberry Pi 的本地 IP 地址。 Raspberry Pi Connect 安全地共享您的 Raspberry Pi 屏幕，无需确定您的本地 IP 地址。

### 通过本地网络在设备之间共享文件

NFS（网络文件系统）、SCP（安全复制协议）、Samba 和 rsync 等服务使您能够在本地网络上的设备之间共享文件，而无需直接控制远程设备。当您需要从一台设备访问存储在另一台设备上的数据时，这些服务会很有用。

### 通过互联网远程控制


要从任何连接到互联网的设备远程控制您的 Raspberry Pi，您可以：

- 通过开放互联网、VPN 或使用 RealVNC 的云 VNC 查看器等外部服务在 Raspberry Pi 上公开 SSH 或 VNC。

- 使用 Raspberry Pi Connect，这是 Raspberry Pi 提供的免费屏幕共享服务。

## 查找 Raspberry Pi 的IP 地址

从另一台计算机连接到 Raspberry Pi 的大多数方法都要求您知道 Raspberry Pi 的本地 IP 地址。

连接到局域网的任何设备都会分配一个 IP 地址。为了使用 SSH 或 VNC 从另一台计算机连接到 Raspberry Pi，您需要知道 Raspberry Pi 的 IP 地址。如果您连接了显示器，这很容易，并且有多种方法可以从网络上的另一台计算机远程查找它。

要查找 Raspberry Pi 的本地 IP 地址，请使用以下方法之一。


### 桌面

将鼠标悬停在系统托盘中的网络图标上，将会出现一个工具提示。此工具提示显示您当前连接的网络的名称以及您的 IP 地址。

### 命令行

运行以下命令将本地 IP 地址输出到命令行：

```sh
hostname -I
```

### 启动输出

如果您的 Raspberry Pi 使用显示器，并且启动到命令行而不是桌面，则启动顺序将包括您的 IP 地址，作为登录提示之前的最后几条输出消息之一。



### 网络管理器


您可以使用内置网络管理器 CLI (nmcli) 来访问有关网络的详细信息。运行以下命令：

```sh
nmcli device show
```

您应该看到类似于以下内容的输出：

```sh
GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.HWADDR:                         D0:3B:FF:41:AB:8A
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     exampleNetworkName
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
IP4.ADDRESS[1]:                         192.168.1.42/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[2]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 600
IP4.DNS[1]:                             192.168.1.3
IP6.ADDRESS[1]:                         ab80::11ab:b1fc:bb7e:a8a5/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ab80::/64, nh = ::, mt = 1024

GENERAL.DEVICE:                         lo
GENERAL.TYPE:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATE:                          100 (connected (externally))
GENERAL.CONNECTION:                     lo
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            --
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:                            --

GENERAL.DEVICE:                         p2p-dev-wlan0
GENERAL.TYPE:                           wifi-p2p
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         D0:3B:FF:41:AB:89
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               off
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
```

此命令输出有关 Raspberry Pi 上可访问的各种网络接口的信息。检查 GENERAL.TYPE 行以查看每个块描述的网络接口类型。例如，“以太网”是设备上的以太网端口，“wifi”是指某些设备内置的 Wi-Fi 芯片。您将根据设备访问互联网的方式查看不同的输出块来查找您的 IP 地址：

- 如果您的设备使用 Wi-Fi 连接到互联网，请选中“wifi”块

- 如果您的设备使用以太网端口连接到互联网，请选中“以太网”块

确定正确的网络接口块后，查找名为 IP4.ADDRESS[1]（对于 IPv4 地址）或 IP6.ADDRESS[1]（对于 IPv6 地址）的字段。您可以忽略这些字段中的尾部斜杠和数字（例如 /24）。

在上面的示例中，Raspberry Pi 使用 Wi-Fi 访问互联网。检查 GENERAL.TYPE 字段读取“wifi”的块以查找 IP 地址。在这种情况下，您可以使用 IP4.ADDRESS[1] 字段中的 IPv4 地址访问此设备：192.168.1.42。

### 使用 mDNS 解析 raspberrypi.local

Raspberry Pi OS 支持多播 DNS 作为 Avahi 服务的一部分。

如果您的设备支持 mDNS，您可以使用主机名和 .local 后缀访问 Raspberry Pi。新安装的 Raspberry Pi 操作系统上的默认主机名是 raspberrypi，因此默认情况下，任何运行 Raspberry Pi 操作系统的 Raspberry Pi 都会响应：

```sh
ping raspberrypi.local
```
如果 Raspberry Pi 可以访问，则 ping 将显示其 IP 地址：

```sh
PING raspberrypi.local (192.168.1.131): 56 data bytes
64 bytes from 192.168.1.131: icmp_seq=0 ttl=255 time=2.618 ms
```

> TIP 
> 如果您使用 Raspberry Pi 配置、raspi-config 或 /etc/hostname 更改 Raspberry Pi 的系统主机名，Avahi 会更新 .local mDNS 地址。如果您不记得 Raspberry Pi 的主机名，可以在另一台设备上安装 Avahi，然后使用 avahi-browse 浏览本地网络上的所有主机和服务。



### 检查路由器的设备列表

在网络浏览器中，导航到路由器的 IP 地址。然后，使用您的凭据登录。

> TIP
> 您的路由器的 IP 地址通常是 http://192.168.1.1，但并非总是如此。您也许可以找到印在路由器标签上的路由器地址和凭据。

这将带您进入控制面板。浏览到已连接设备或类似设备的列表（所有路由器都不同），您应该会看到一些您识别的设备。有些设备被检测为 PC、平板电脑、手机、打印机等。因此您应该识别一些设备并排除它们，以确定哪个是您的 Raspberry Pi。

> TIP
> 如果您使用电线将 Raspberry Pi 连接到网络，请尝试在列表中过滤有线设备。可供选择的设备应该更少。



### 使用 nmap 查找设备 


网络映射器命令 (nmap) 是一个用于网络发现的免费开源工具。它适用于 Linux、macOS 和 Windows。

要在 Linux 上安装，请安装 nmap 软件包，例如易于安装 nmap。

要在 macOS 或 Windows 上安装，请参阅 nmap.org 下载页面。

要使用 nmap 扫描网络上的设备，您需要知道您连接到的子网。首先，找到您正在使用的计算机的本地 IP 地址：

- 在 Linux 上，在终端窗口中输入主机名 -I
- 在 macOS 上，转到“系统设置”>“网络”，选择您的活动网络连接，然后单击“详细信息...”按钮
- 在 Windows 上，转到控制面板，然后在网络和共享中心下，单击查看网络连接，选择活动网络连接，然后单击查看此连接的状态

接下来，扫描整个子网中的其他设备。大多数本地网络使用 IPv4，每个 IP 地址使用四个值在 1 到 255 之间的数字。您子网上的设备都使用相同的前三个数字。例如，如果您的 IP 地址是 192.168.1.5，其他设备将使用 192.168.1.2、192.168.1.6 和 192.168.1.200 等地址。要使用 nmap 扫描此子网，请传递字符串 192.168.1.0/24，该字符串涵盖子网范围 192.168.1.0 到 192.168.1.255。使用 -sn 标志在整个子网范围上运行 ping 扫描：

```sh
sudo nmap -sn 192.168.1.0/24
```

> TIP
> 这可能最多需要一分钟，具体取决于您的本地网络速度。

ping 扫描会查询范围内的所有 IP 地址以获取响应。对于响应 ping 的每个设备，输出显示主机名和 IP 地址，如下所示：

```sh
Starting Nmap 6.40 ( http://nmap.org ) at 2014-03-10 12:46 GMT
Nmap scan report for hpprinter (192.168.1.2)
Host is up (0.00044s latency).
Nmap scan report for Gordons-MBP (192.168.1.4)
Host is up (0.0010s latency).
Nmap scan report for ubuntu (192.168.1.5)
Host is up (0.0010s latency).
Nmap scan report for raspberrypi (192.168.1.8)
Host is up (0.0030s latency).
Nmap done: 256 IP addresses (4 hosts up) scanned in 2.41 seconds
```

上面的输出显示主机名为 raspberrypi 的设备的 IP 地址为 192.168.1.8。


### 使用智能手机应用程序查找设备

Fing 应用程序是一款适用于智能手机的免费网络扫描仪。它适用于 Android 和 iOS。

将您的手机连接到与 Raspberry Pi 相同的网络。

打开 Fing 应用程序时，触摸屏幕右上角的刷新按钮。

几秒钟后，您应该会看到一个列表，其中包含连接到网络的所有设备。

向下滚动到制造商“Raspberry Pi”的条目。 IP 地址显示在条目的左下角，MAC 地址显示在条目的右下角。

## 使用 SSH 访问远程终端

您可以使用 Secure SHell (SSH) 协议从同一网络上的另一台计算机远程访问 Raspberry Pi 的终端。

### 启用 SSH 服务器


默认情况下，Raspberry Pi 操作系统禁用 SSH 服务器。通过以下方式之一启用 SSH：

#### 在桌面上

- 从首选项菜单中，启动 Raspberry Pi 配置。
- 导航至“Interfaces”选项卡。
- 选择 SSH 旁边的启用。
- 单击“确定”。


#### 刷新的操作系统映像时

要在全新安装的 Raspberry Pi OS 上配置 SSH：

1. 请按照使用 Imager 安装指南中的说明进行操作。

2. 在操作系统自定义步骤中，导航到“服务”选项卡。

3. 勾选复选框以启用 SSH。

4. 选择密码身份验证，使用与实际使用 Raspberry Pi 时使用的用户名和密码相同的用户名和密码登录。选择仅允许公钥身份验证以配置 SSH 密钥以进行无密码登录。

#### terminal 操作

1. 在终端窗口中输入 sudo raspi-config。

2. 选择【接口】选项。

3. 导航到 SSH 并选择它。

4. 选择是。

5. 选择确定。

6. 选择完成。

#### 手动操作

1. 在启动分区中创建一个名为 ssh 的空文件：

```sh
sudo touch /boot/firmware/ssh
```

2. 重新启动机器：

```sh
sudo reboot
```

### 连接到 SSH 服务器

在计算机上打开终端窗口并输入以下命令，将 <ip 地址> 占位符替换为您尝试连接的 Raspberry Pi 的 IP 地址，将 <用户名> 替换为您的用户名：

```sh
ssh <username>@<ip address>
```

连接正常后，您将看到安全警告。输入 yes 继续。您仅在第一次连接时才会看到此警告。

出现提示时输入您的帐户密码。

您现在应该看到 Raspberry Pi 命令提示符.

您现在已远程连接到 Raspberry Pi，并且可以执行命令。

> Note:
> 如果您收到连接超时错误，则您可能输入了错误的 Raspberry Pi IP 地址。检查树莓派的IP地址。

#### 通过 SSH 转发 X11

> Note:
> 在 Raspberry Pi 4 和 5 上，Raspberry Pi OS Bookworm 默认使用 Wayland 窗口服务器。如果您使用 X 窗口服务器，则只能转发 X11。要通过 X11 启用窗口转发，请在 Raspberry Pi 配置中将桌面切换到 X 窗口服务器。

> Note:
> 许多桌面环境中不再默认安装 X11。安装第三方X服务器（例如XQuartz）以使用X11转发。


X11 支持通过 SSH 进行图形应用程序。传递 -Y 标志以通过 SSH 转发 X 会话：

```sh
ssh -Y <username>@<ip address>
```

经过身份验证后，您将像往常一样看到命令行。但是，您也可以打开 X 服务器可以为您呈现的图形窗口。例如，键入以下命令来启动 Geany 窗口：

```sh
geany &
```

### 配置 SSH 无密码

要远程访问 Raspberry Pi，而无需在每次连接时提供密码，请使用 SSH 密钥对。

#### 使用 Raspberry Pi Imager 预配置操作系统映像

使用 Raspberry Pi Imager 配置启动映像时，您可以预先配置 SSH 密钥。您可以生成新的 SSH 密钥对或现有的 SSH 密钥。

1. 按照使用 Imager 安装指南来配置启动映像。

2. 在操作系统自定义步骤中，导航至“服务”选项卡并勾选“启用 SSH”复选框。

3. 选择仅允许公钥身份验证单选按钮。如果您已在 `~/.ssh/id_rsa.pub` 中存储了 SSH 公钥，Imager 会自动使用该公钥来预填充文本框。如果 Imager 没有找到 SSH 公钥，您可以单击 【RUN SSH-KEYGEN】 按钮来生成新的密钥对。

#### 手动配置 SSH 密钥

如果您已经安装了 Raspberry Pi OS，则可以更新现有配置以使用 SSH 密钥身份验证。

#### 检查现有的 SSH 公钥

要检查用于远程连接到 Raspberry Pi 的计算机上现有的 SSH 公钥，请运行以下命令：

```sh
如果您看到名为 `id_ed25519.pub`、`id_rsa.pub` 或 `id_dsa.pub` 的文件，则您已经拥有 SSH 密钥。跳过 SSH 密钥对生成并继续将 SSH 密钥添加到您的 SSH 身份列表中。
```
#### 生成新的 SSH 密钥对

> TIP
> 本指南提供了生成新 RSA 密钥的说明。为了提高安全性，您可以生成 Ed25519 密钥。当引用您的公钥和私钥文件名以使用 Ed25519 密钥时，将 `-t ed25519` 传递给 `ssh-keygen` 并将 rsa 替换为 ed25519。

要生成新的 SSH 密钥对，请输入以下命令：

```sh
ssh-keygen
```

当询问在哪里保存密钥时，按 Enter 键使用默认位置 ~/.ssh/id_rsa。

当询问可选的关键短语时，按 Enter 键不使用关键短语。

执行以下命令查看.ssh目录下的内容：

```sh
ls ~/.ssh
```
您应该看到文件 id_rsa 和 id_rsa.pub：

```sh
authorized_keys  id_rsa  id_rsa.pub  known_hosts
```
id_rsa 文件包含您的私钥。将其安全地保存在用于远程连接到 Raspberry Pi 的计算机上。

id_rsa.pub 文件包含您的公钥。您将与您的 Raspberry Pi 共享此密钥。当您远程连接 Raspberry Pi 时，它将使用此密钥来验证您的身份。

#### 将 SSH 密钥添加到您的 SSH 身份列表

启动 SSH 代理：

```sh
eval "$(ssh-agent -s)"
```

接下来，使用以下命令将您的密钥身份添加到 ssh-agent：

```sh
ssh-add ~/.ssh/id_rsa
```

#### 将公钥复制到您的 Raspberry Pi

在用于远程连接到 Raspberry Pi 的计算机上，使用以下命令将公钥安全地复制到 Raspberry Pi：

```sh
ssh-copy-id <username>@<ip address>
```

出现提示时，输入 Raspberry Pi 上用户帐户的密码。您现在无需输入密码即可连接到 Raspberry Pi。

#### 手动将公钥复制到您的 Raspberry Pi

如果您的操作系统不支持 ssh-copy-id，您可以使用 scp 复制公钥。

首先，在 Raspberry Pi 上创建 Linux 期望找到密钥的目录：

```sh
mkdir .ssh
```
然后，为 .ssh 目录配置适当的权限：

```sh
chmod 700 .ssh
```
在您常用的计算机上，使用 scp 将公钥复制到 Raspberry Pi 上名为 .ssh/authorized_keys 的文件中：

```sh
scp .ssh/id_rsa.pub <username>@<ip address>:.ssh/authorized_keys
```

> TIP
> 上面的命令假设您之前从未授权过任何密钥来访问您的 Raspberry Pi。如果您之前至少添加了一个密钥，则应将包含公钥的新行添加到authorized_keys 文件的末尾，以保留现有密钥。

出现提示时，输入 Raspberry Pi 上用户帐户的密码。


然后，在您的 Raspberry Pi 上，配置authorized_keys 文件的权限：

```sh
chmod 644 .ssh/authorized_keys
```

您现在无需输入密码即可连接到 Raspberry Pi。


## 使用 VNC 共享屏幕


有时使用设备进行物理工作并不方便。虚拟网络计算 (VNC) 允许您从一台设备控制另一台设备的桌面。

VNC 依赖于客户端和服务器。客户端在您可以物理交互的设备上运行，例如个人笔记本电脑、台式机、平板电脑或手机。服务器在您的 Raspberry Pi 上运行。使用 VNC 时，客户端将键盘和鼠标事件传输到服务器。服务器在 Raspberry Pi 上执行这些事件，并将屏幕更新返回给客户端。

VNC 客户端在窗口中显示 Raspberry Pi 的桌面。您可以与桌面交互，就像在 Raspberry Pi 本身上工作一样。

Raspberry Pi 操作系统包含 wayvnc。这提供了一个 VNC 服务器，您可以在设备首选项中启用该服务器。

在 Raspberry Pi 上使用 VNC 之前，必须启用 VNC 服务器。

### 启用 VNC 服务器

Raspberry Pi OS 支持以图形方式和命令行启用 VNC 服务器。

> TIP:
> 启用后，您可以在 `/etc/wayvnc/` 访问 `WayVNC` 配置。

#### 以图形方式启用 VNC 服务器

1. 启动至 Raspberry Pi 上的图形桌面。

2. 单击桌面系统托盘中的 Raspberry Pi 图标。

3. 从菜单中选择首选项 > Raspberry Pi 配置。

4. 导航至“接口”选项卡。

5. 单击 VNC 旁边的单选按钮进入活动位置。

6. 单击“确定”按钮保存您的配置更改。


#### 在命令行上启用VNC服务器

使用 raspi-config 在命令行上启用 VNC 服务器。

1. 使用以下行打开 raspi-config：

```sh
sudo raspi-config
```
2. 导航至界面选项。按 Enter 键进行选择。

3. 选择VNC。按 Enter 键进行选择。

4. 在您想要启用 VNC 服务器吗？下，突出显示 <是> 并按 Enter。

5. 按 Enter 返回菜单。按 Esc 退出 raspi-config。

### 连接到 VNC 服务器

要连接到 Raspberry Pi，您需要以下内容：

- 您的 Raspberry Pi 和运行 VNC 客户端的设备连接到同一网络（例如家庭无线网络或 VPN）
- Raspberry Pi 的主机名或 IP 地址
- Raspberry Pi 上帐户的有效用户名和密码组合

如果您不知道设备的 IP 地址，请参阅我们有关查找 IP 地址的说明。

1. 下载 TigerVNC。您可以从 GitHub 存储库的“发布”页面安装最新版本。单击最新版本中的链接，找到适合您平台的二进制文件。 Windows 用户应下载 exe； macOS 用户应下载 dmg； Linux 用户应该安装该 jar。

2. 在您的客户端设备上，启动 TigerVNC。在 macOS 和 Windows 上，您可以双击二进制文件。在 Linux 上，使用 sudo apt install default-jre 安装 java，然后运行 ​​java -jar VncViewer-<version>.jar，将 <version> 占位符替换为您下载的版本。

3. 在“VNC 服务器”字段中，输入 Raspberry Pi 的 IP 地址。

![vnc-tigervnc-enter-ip](https://www.raspberrypi.com/documentation/computers/images/vnc-tigervnc-enter-ip.png)

4. 单击“选项”按钮。导航到“输入”选项卡。选中“没有光标时显示点”旁边的框，以确保您始终可以在 TigerVNC 中看到光标。

![vnc-tigervnc-show-dot](https://www.raspberrypi.com/documentation/computers/images/vnc-tigervnc-show-dot.png)

5. 单击“连接”按钮启动与服务器的连接。

- 如果 TigerVNC 警告您“主机名与服务器证书不匹配”，请单击“是”按钮继续。

- 如果 TigerVNC 警告您“证书已由未知机构签署”，请单击“是”按钮为您的 Raspberry Pi 授予例外。

6. 当提示输入用户名和密码时，输入您的凭据。

7. 单击“确定”按钮以通过 VNC 服务器进行身份验证。如果您的凭据正确，TigerVNC 应打开一个窗口，其中包含与您在 Raspberry Pi 上的帐户相对应的桌面。您应该能够移动鼠标和键盘来输入文本并与桌面交互。



## 使用 Raspberry Pi Connect 共享屏幕

您可以使用 Raspberry Pi Connect 从另一台设备上的浏览器远程访问 Raspberry Pi 的桌面。 Raspberry Pi Connect 自动处理配置，因此您无需查找 Raspberry Pi 的本地 IP 地址或修改本地网络。

有关更多信息，请参阅连接文档。


## 与 SCP 共享文件

安全复制协议 (scp) 通过 SSH 发送文件。您可以使用 scp 在 Raspberry Pi 和另一台计算机之间复制文件。

要使用 scp，请找到 Raspberry Pi 的 IP 地址。

### 将文件复制到你的 Raspberry Pi

要将名为 myfile.txt 的文件从您的个人计算机复制到 Raspberry Pi 上的用户主文件夹，请从包含 myfile.txt 的目录运行以下命令，将 `<username>` 占位符替换为您用于登录 Raspberry Pi 的用户名Raspberry Pi 和带有 Raspberry Pi IP 地址的 `<pi_ip_address>` 占位符：

```sh
scp myfile.txt <username>@<pi_ip_address>:
```

要将文件复制到特定目录，请在 scp 命令中的 : 后面附加目录路径。在运行 scp 之前创建文件夹，因为 scp 不会自动创建文件夹。例如，以下命令将名为 myfile.txt 的文件复制到用户主文件夹中的 project/ 目录中：

```sh
scp myfile.txt <username>@<pi_ip_address>:project/
```

### 从 Raspberry Pi 复制文件

要将名为 myfile.txt 的文件从 Raspberry Pi 上的用户主目录复制到另一台计算机上的当前目录，请运行以下命令：

```sh
scp <username>@<pi_ip_address>:myfile.txt .
```

### 用一个命令复制多个文件

要复制多个文件，请在单个命令中列出文件名，并用空格分隔：
```sh
scp myfile.txt myfile2.txt <username>@<pi_ip_address>:
```
或者，使用通配符复制与特定过滤器匹配的所有文件。以下命令复制所有以 .txt 结尾的文件：
```sh
scp *.txt <username>@<pi_ip_address>:
```
以下命令复制所有以 m 开头的文件：
```sh
scp m* <username>@<pi_ip_address>:
```
以下命令复制所有以 m 开头并以 .txt 结尾的文件：
```sh
scp m*.txt <username>@<pi_ip_address>:
```

> NOTE
> 要复制名称包含空格的文件，请将文件名用引号引起来：

```sh
scp "my file.txt" <username>@<pi_ip_address>:
```

### 复制文件夹

要复制文件夹及其所有内容，请使用 -r（递归）标志传递文件夹名称：
```sh
scp -r project/ <username>@<pi_ip_address>:
```

## 使用 raync 在计算机之间同步文件夹

您可以使用 rsync 在计算机之间同步文件夹。例如，您可以使用 rsync 将 Raspberry Pi 拍摄的新照片自动传输到您的个人计算机。

在配置 rsync 之前，请确定以下各项的值：

- `<pi_ip_address>`：您的 Raspberry Pi 的本地 IP 地址：请参阅查找您的 Raspberry Pi 的 IP 地址以获取更多信息

- `<pi_username>`：用于登录 Raspberry Pi 的用户名

- `<pi_folder_name>`：您要从 Raspberry Pi 上复制文件的文件夹的名称

- `<pc_folder_name>`：您要在个人计算机上同步的文件夹的名称

要配置 rsync 来同步文件，请在个人计算机上完成以下步骤，并将命令中的占位符替换为您在上面确定的值：

1. 创建您想要同步的文件夹：

```sh
mkdir <pc_folder_name>
```

2. 使用rsync将文件同步到文件夹：

```sh
rsync -avz -e ssh <pi_username>@<pi_ip_address>:<pi_folder_name>/ <pc_folder_name>/
```

此命令将 Raspberry Pi 上选定文件夹中的所有文件复制到个人计算机上选定文件夹。如果您多次运行该命令，rsync 会跟踪您已下载的文件并跳过它们。如果您删除或修改 Raspberry Pi 上已同步的文件，rsync 会相应更新您个人计算机上的文件。

## 网络文件系统（NFS）

网络文件系统 (NFS) 允许您与同一网络上的其他计算机或设备共享位于一台联网计算机上的目录。目录所在的计算机称为服务器，连接到该服务器的计算机或设备称为客户端。客户端通常会挂载共享目录，使其成为自己的目录结构的一部分。共享目录是共享资源或网络共享的示例。

NFS 是在 Linux/Unix 环境中创建简单 NAS（网络附加存储）的流行方法。

NFS 也许最适合更永久的网络安装目录，例如 /home 目录或定期访问的共享资源。如果您想要来宾用户可以轻松连接到的网络共享，Samba 更适合该任务。跨操作系统更容易使用临时安装和分离 Samba 共享的工具。

在部署 NFS 之前，您应该熟悉：

- Linux 文件和目录权限
- 挂载和卸载文件系统



### 设置基本 NFS 服务器

使用以下命令安装所需的软件包：

```sh
sudo apt install nfs-kernel-server
```

为了更方便维护，我们将所有 NFS 导出隔离在单个目录中，真实目录将使用 --bind 选项挂载到该目录中。

假设我们要导出用户的主目录，位于 /home/users 中。首先我们创建导出文件系统：

> TIP
> 如果您计划配置 LDAP/NIS 身份验证，请跳过下面的 chmod 步骤。

授予 /export 和 /export/users 读取、写入和执行权限 (777)，以便您无需 LDAP/NIS 身份验证即可从客户端访问 NFS 共享：
```sh
chmod -R 777 777 /export
```
接下来，使用以下命令挂载真实用户目录：
```sh
sudo mount --bind /home/users /export/users
```
为了避免每次重新启动后重新输入此内容，我们将以下行添加到 `/etc/fstab` 中：
```sh
/home/users    /export/users   none    bind  0  0
```
与 NFS 服务器相关的三个配置文件：

1. `/etc/default/nfs-kernel-server`
2. `/etc/default/nfs-common`
3. `/etc/exports`

目前 `/etc/default/nfs-kernel-server` 中唯一重要的选项是 `NEED_SVCGSSD`。默认情况下它设置为“no”，这很好，因为我们这次没有激活 NFSv4 安全性。

为了自动映射 ID 名称，客户端和服务器上必须存在文件 `/etc/idmapd.conf`，且文件内容相同且域名正确。此外，该文件的映射部分应包含以下行：
```sh
[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
```

但请注意，客户端可能对无人用户和无人组有不同的要求。例如，在 RedHat 变体上，两者都是 nfsnobody。如果您不确定，请通过以下命令检查是否有任何人和没有组：
```sh
cat /etc/passwd
cat /etc/group
```
这样，服务器和客户端不需要用户共享相同的 UID/GUID。对于使用基于 LDAP 的身份验证的用户，请将以下行添加到客户端的 idmapd.conf 中：
```sh
[Translation]

Method = nsswitch
```
这将使 idmapd 知道查看 nsswitch.conf 以确定应在何处查找凭据信息。如果您的 LDAP 身份验证已经正常工作，则 nsswitch 不需要进一步解释。

要将我们的目录导出到本地网络 192.168.1.0/24，请将以下两行添加到 /etc/exports：
```sh
/export       192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/users 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
```

#### 端口映射锁定（可选）

NFS 上的文件对网络上的任何人开放。作为一项安全措施，您可以限制对指定客户端的访问。

将以下行添加到 `/etc/hosts.deny`：
```sh
rpcbind mountd nfsd statd lockd rquotad : ALL
```
通过首先阻止所有客户端，只有 `/etc/hosts.allow`（在下面添加）中的客户端将被允许访问服务器。

现在将以下行添加到 `/etc/hosts.allow` 中：
```sh
rpcbind mountd nfsd statd lockd rquotad : <list of IPv4s>
```

其中 `<IPv4 列表>` 是服务器和所有客户端的 IP 地址列表。 （这些必须是 IP 地址，因为 rpcbind 的限制，它不喜欢主机名。）请注意，如果您设置了 NIS，则只需将它们添加到同一行即可。

请确保授权 IP 地址列表包含 localhost 地址 (127.0.0.1)，因为最新版本的 Ubuntu 中的启动脚本使用 rpcinfo 命令来发现 NFSv3 支持，如果 localhost 无法连接，该功能将被禁用。

最后，为了使更改生效，请重新启动服务：
```sh
sudo systemctl restart nfs-kernel-server
```

### 配置 NFS 客户端

现在您的服务器正在运行，您需要设置任何客户端才能访问它。首先，安装所需的软件包：
```sh
sudo apt install nfs-common
```
在客户端，我们可以使用一个命令挂载完整的导出树：
```sh
mount -t nfs -o proto=tcp,port=2049 <nfs-server-IP>:/ /mnt
```
您还可以指定 NFS 服务器主机名而不是其 IP 地址，但在这种情况下，您需要确保主机名可以在客户端解析为 IP。确保始终解决此问题的一个可靠方法是使用 `/etc/hosts` 文件。

请注意，与 NFSv3 中不同，`<nfs-server-IP>:/export` 在 NFSv4 中不是必需的。根导出：/默认以fsid=0导出。

我们还可以使用以下命令挂载导出的子树：
```sh
mount -t nfs -o proto=tcp,port=2049 <nfs-server-IP>:/users /home/users
```

为了确保每次重新启动时都会安装此文件，请将以下行添加到 `/etc/fstab` 中：

```sh
<nfs-server-IP>:/   /mnt   nfs    auto  0  0
```
如果挂载后， `/proc/mounts` 中的条目显示为 `<nfs-server-IP>://` （带有两个斜杠），那么您可能需要在 `/etc/fstab` 中指定两个斜杠，否则 umount 可能会抱怨它找不到安装座。

#### 端口映射锁定（可选）

将以下行添加到 `/etc/hosts.deny`：
```sh
rpcbind : ALL
```
通过首先阻止所有客户端，只有 `/etc/hosts.allow`（在下面添加）中的客户端将被允许访问服务器。

现在将以下行添加到 `/etc/hosts.allow` 中：

```sh
rpcbind : <NFS server IP address>
```
其中 `<NFS 服务器 IP 地址>` 是服务器的 IP 地址。

### 配置复杂的 NFS 服务器

NFS 用户权限基于用户 ID (UID)。客户端上任何用户的 UID 都必须与服务器上的 UID 相匹配，以便用户能够访问。执行此操作的典型方法是：

- 手动密码文件同步
- LDAP 的使用
- DNS的使用
- 使用NIS

请注意，在主用户具有 root 访问权限的系统上必须小心：该用户可以更改系统上的 UID 以允许自己访问任何人的文件。此页面假定管理团队是唯一具有 root 访问权限的组，并且他们都是受信任的。其他的都代表更高级的配置，这里不再赘述。

#### 组权限
用户的文件访问权限由其客户端组的成员身份决定，而不是服务器上的组成员身份。但是，有一个重要的限制：从客户端传递到服务器的最大组数为 16 个，如果用户是客户端上超过 16 个组的成员，则某些文件或目录可能会意外无法访问。

#### DNS（可选，仅当使用 DNS 时）
将任何客户端名称和 IP 地址添加到 `/etc/hosts`。 （服务器的 IP 地址应该已经存在。）这可以确保即使 DNS 出现故障，NFS 仍然可以工作。或者，如果您愿意，您也可以依赖 DNS - 这取决于您。

#### NIS（可选，仅当使用 NIS 时）
这适用于使用 NIS 的客户端。否则，您无法使用网络组，并且应在 `/etc/exports` 中指定单独的 IP 或主机名。阅读 man netgroup 中的 BUGS 部分以获取更多信息。

首先，编辑 `/etc/netgroup` 并添加一行对您的客户端进行分类（此步骤不是必需的，但为了方便起见）：
```sh
myclients (client1,,) (client2,,) ...
```
其中 myclients 是网络组名称。

接下来运行以下命令来重建 NIS 数据库：
```sh
sudo make -C /var/yp
```
文件名 yp 指的是黄页，即 NIS 的前身名称。

#### 端口映射锁定（可选）
将以下行添加到 `/etc/hosts.deny`：
```sh
rpcbind mountd nfsd statd lockd rquotad : ALL
```
通过首先阻止所有客户端，只有 `/etc/hosts.allow`（在下面添加）中的客户端将被允许访问服务器。

考虑将以下行添加到 `/etc/hosts.allow` 中：
```sh
rpcbind mountd nfsd statd lockd rquotad : <list of IPs>
```
其中 `<IP 列表>` 是服务器和所有客户端的 IP 地址列表。由于 rpcbind 的限制，这些必须是 IP 地址。请注意，如果您设置了 NIS，则只需将它们添加到同一行即可。

#### 包安装和配置

安装必要的软件包：
```sh
sudo apt install rpcbind nfs-kernel-server
```
编辑 `/etc/exports` 并添加共享：
```sh
/home @myclients(rw,sync,no_subtree_check)
/usr/local @myclients(rw,sync,no_subtree_check)
```
上面的示例将 `/home` 和 `/usr/local` 共享给 myclients 网络组中的所有客户端。

```sh
/home 192.168.0.10(rw,sync,no_subtree_check) 192.168.0.11(rw,sync,no_subtree_check)
/usr/local 192.168.0.10(rw,sync,no_subtree_check) 192.168.0.11(rw,sync,no_subtree_check)
```
上面的示例将 `/home` 和 `/usr/local` 共享给两个具有静态 IP 地址的客户端。如果您希望允许访问专用网络中指定 IP 地址范围内的所有客户端，请考虑以下事项：
```sh
/home 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
/usr/local 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
```
在这里，rw 使共享读/写，而sync 要求服务器仅在任何更改刷新到磁盘后才回复请求。这是最安全的选择；异步速度更快，但很危险。如果您正在考虑其他选择，强烈建议您阅读 man Exports。

设置 `/etc/exports` 后，导出共享：
```sh
sudo exportfs -ra
```
每当修改 `/etc/exports` 时，您都需要运行此命令。

#### 重启服务
重新启动 rpcbind 和 NFS 以使更改生效：
```sh
sudo systemctl restart rpcbind
sudo systemctl restart nfs-kernel-server
```
#### 需要考虑的安全事项
除了上面讨论的 UID 问题之外，还应该注意的是，攻击者可能会伪装成允许映射共享的计算机，从而允许他们创建任意 UID 来访问您的文件。一种可能的解决方案是 IPSec。您可以将所有域成员设置为仅通过 IPSec 相互通信，这将有效地验证您的客户端的真实身份。

IPSec 的工作原理是使用服务器的公钥对发送到服务器的流量进行加密，然后服务器发回使用客户端的公钥加密的所有回复。使用各自的私钥对流量进行解密。如果客户端没有应有的密钥，则无法发送或接收数据。

IPSec 的替代方案是物理上独立的网络。这需要单独的网络交换机和单独的以太网卡，以及该网络的物理安全性。



### 故障排除

只有在您成功登录并且您的主目录被解密后，才能在加密的主目录中挂载 NFS 共享。这意味着在启动时使用 /etc/fstab 挂载 NFS 共享将不起作用，因为挂载时您的 home 尚未解密。有一个简单的方法可以使用符号链接来解决这个问题：

1.创建一个替代目录来挂载 NFS 共享：
```sh
sudo mkdir /nfs
sudo mkdir /nfs/music
```
2.编辑 /etc/fstab 以将 NFS 共享挂载到该目录中：
```sh
nfsServer:music    /nfs/music    nfs    auto    0 0
```

3.在您的家中创建一个符号链接，指向实际的安装位置。例如，在这种情况下，首先删除已经存在的 Music 目录：
```sh
rmdir /home/user/Music
ln -s /nfs/music/ /home/user/Music
```

## Samba (SMB/CIFS)

Samba 是服务器消息块 (SMB) 网络协议的免费软件重新实现。使用 Samba，您可以在 Windows、macOS 和 Linux 计算机之间共享文件夹。



### 在您的 Raspberry Pi 上安装 Samba

默认情况下，Raspberry Pi 操作系统不包含 Samba。要在 Raspberry Pi 上安装 Samba，请运行以下命令，该命令会安装运行 Samba 服务器或客户端所需的所有依赖项：
```sh
sudo apt update
sudo apt install samba samba-common-bin smbclient cifs-utils
```

### 挂载从 Windows 共享的文件夹

首先，您需要在 Windows 设备上共享一个文件夹。

#### 开启共享

1. 右键单击系统托盘并从菜单中选择网络和共享中心。
2. 选择更改高级共享设置。
3. 选择打开网络发现。
4. 选择打开文件和打印机共享。
5. 单击“保存”按钮保存您的更改。



### 从 Rasyberry Pi 共享文件夹

首先，创建一个共享文件夹。此示例在当前用户的主文件夹中创建一个名为共享的文件夹：

```sh
cd ~
mkdir shared
chmod 0740 shared
```

现在我们需要告诉 Samba 您访问该文件夹时的默认用户帐户。出现提示时，输入您的密码，并将 <username> 占位符替换为您的主用户帐户的用户名：
```sh
sudo smbpasswd -a <username>
```

现在我们需要使用 Samba 配置文件告诉 Samba 共享该文件夹。
```sh
sudo nano /etc/samba/smb.conf
```

在文件末尾添加以下内容以共享文件夹，并授予远程用户读/写权限。将 <username> 占位符替换为 Raspberry Pi 上主用户帐户的用户名：

```sh
[share]
    path = /home/<username>/shared
    read only = no
    public = yes
    writable = yes
```

在同一文件中，找到工作组行，如有必要，将其更改为本地 Windows 网络的工作组的名称。

```sh
workgroup = <your workgroup name here>
```
共享文件夹现在应该显示在网络上的 Windows 或 macOS 设备上。输入您的 Raspberry Pi 用户名和密码以挂载该文件夹。

## 设置 Apache Web 服务器
Apache 是一种流行的 Web 服务器应用程序，您可以将其安装在 Raspberry Pi 上以允许其提供网页服务。

Apache 本身可以通过 HTTP 提供 HTML 文件，并且通过附加模块可以使用 PHP 等脚本语言提供动态网页。




### 安装 Apache 

首先，通过在终端中键入以下命令来更新可用的软件包：
```sh
sudo apt update
```

然后，使用以下命令安装 apache2 软件包：
```sh
sudo apt install apache2 -y
```


### 测试网络服务器

默认情况下，Apache 将测试 HTML 文件放在 web 文件夹中。当您在 Raspberry Pi 本身上浏览 http://localhost/ 或从网络上的另一台计算机浏览 http://192.168.1.10（无论 Raspberry Pi 的 IP 地址是什么）时，就会提供此默认网页。要查找 Raspberry Pi 的 IP 地址，请在命令行中键入主机名 -I（或阅读有关查找 IP 地址的更多信息）。

在 Raspberry Pi 上或从网络上的另一台计算机浏览到默认网页，您应该看到以下内容：

![apache-it-works](https://www.raspberrypi.com/documentation/computers/images/apache-it-works.png)

This means you have Apache working!

#### 更改默认网页
这个默认网页只是文件系统上的一个 HTML 文件。它位于`/var/www/html/index.html`。

在终端窗口中导航到该目录并查看其中的内容：

```sh
cd /var/www/html
ls -al
```
这将向您展示：
```sh
total 12
drwxr-xr-x  2 root root 4096 Jan  8 01:29 .
drwxr-xr-x 12 root root 4096 Jan  8 01:28 ..
-rw-r--r--  1 root root  177 Jan  8 01:29 index.html
```
这表明默认情况下 `/var/www/html/` 中有一个名为 index.html 的文件，并且该文件由 root 用户拥有（与包含的文件夹一样）。为了编辑该文件，您需要将其所有权更改为您自己的用户名。使用以下命令更改文件的所有者，并将 `<username>` 占位符替换为您的主用户帐户的用户名：
```sh
sudo chown <username>: index.html
```
您现在可以尝试编辑此文件，然后刷新浏览器以查看网页更改。如果您了解 HTML，您可以将自己的 HTML 文件和其他资源放入此目录中，并将它们作为本地网络上的网站提供服务。



### 为 Apache 安装 PHP

要允许您的 Apache 服务器处理 PHP 文件，您需要安装最新版本的 PHP 和 Apache 的 PHP 模块。键入以下命令来安装它们：
```sh
sudo apt install php libapache2-mod-php -y
```
现在删除index.html文件：
```sh
sudo rm index.html
```
并创建文件index.php：
```sh
sudo nano index.php
```
将一些PHP内容放入其中：
```php
<?php echo "hello world"; ?>
```

现在保存并刷新您的浏览器。你应该看到“你好世界”。这不是动态的，但仍然由 PHP 提供服务。尝试一些动态的东西：
```php
<?php echo date('Y-m-d H:i:s'); ?>
```
或显示您的 PHP 信息：
```php
<?php phpinfo(); ?>
```

## 网络启动你的 Raspberry Pi
您可以设置 DHCP/TFTP 服务器，该服务器允许您从网络启动 Raspberry Pi 3 或 4。

这些说明假设您有一个现有的家庭网络，并且您想要使用 Raspberry Pi 作为服务器。您还需要额外的 Raspberry Pi 3 或 4 作为要启动的客户端。仅需要一张 SD 卡，因为在初始客户端配置后客户端将从服务器启动。

> NOTE
> 由于可用的网络设备和路由器种类繁多，我们无法保证网络启动适用于任何设备。我们收到报告称，如果您无法启动网络，禁用网络上的 STP 帧可能会有所帮助。



### 配置网络启动客户端

#### 树莓派 3B 型

> NOTE
> 本部分仅适用于 Raspberry Pi 3 Model B，因为 Raspberry Pi 3 Model B+ 出厂时已启用网络启动。

在 Raspberry Pi 3 Model B 进行网络启动之前，需要从 SD 卡启动，并使用配置选项启用 USB 启动模式。这将在 Raspberry Pi SoC 的 OTP（一次性可编程）内存中设置一位，以启用网络启动。完成此操作后，Raspberry Pi 3B 将尝试从 USB 启动，如果无法从 SD 卡启动，则从网络启动。

以通常的方式在 SD 卡上安装 Raspberry Pi OS Lite 或带桌面的 Raspberry Pi OS。接下来，使用以下命令启用 USB 引导模式：
```sh
echo program_usb_boot_mode=1 | sudo tee -a /boot/firmware/config.txt
```

这会将`program_usb_boot_mode=1` 添加到`/boot/firmware/config.txt` 的末尾。使用 `sudo restart` 重新启动 Raspberry Pi。客户端 Raspberry Pi 重新启动后，检查 OTP 是否已编程：
```sh
vcgencmd otp_dump | grep 17:
17:3020000a
```
确保输出 0x3020000a 正确。

客户端配置差不多完成了。最后一步，禁用 USB 启动。运行以下命令：
```sh
sudo nano /boot/firmware/config.txt
```
删除包含文本`program_usb_boot_mode=1` 的行。最后，使用 `sudo poweroff` 关闭客户端 Raspberry Pi。

#### 树莓派 4 B 型


可以使用 `raspi-config` 工具在 Raspberry Pi 4 上启用网络启动。首先，运行 `raspi-config`，如下所示：
```sh
sudo raspi-config
```
在 raspi-config 中，选择“高级选项”，然后选择“启动顺序”，然后选择“网络启动”。然后，您必须重新启动设备，才能将引导顺序的更改编程到引导加载程序 EEPROM 中。 Raspberry Pi 重新启动后，检查启动顺序现在是否为 0xf21：

```sh
vcgencmd bootloader_config
```
有关配置 Raspberry Pi 4 引导加载程序的更多详细信息，请参阅Raspberry Pi 引导加载程序配置。



### 以太网 MAC 地址

在配置网络启动之前，请记下序列号和 MAC 地址，以便 TFTP/DHCP 服务器可以识别该板。

在 Raspberry Pi 4 上，MAC 地址在制造时已编程，MAC 地址和序列号之间没有联系。 MAC 地址和序列号均显示在引导加载程序 HDMI 诊断屏幕上。

要查找以太网 MAC 地址：
```sh
ethtool -P eth0
```
要查找序列号：
```sh
grep Serial /proc/cpuinfo | cut -d ' ' -f 2 | cut -c 9-16
```

### 配置网络启动服务器

将SD卡插入服务器Raspberry Pi，然后启动服务器。客户端 Raspberry Pi 需要一个根文件系统来启动：我们将使用服务器根文件系统的副本并将其放置在 /nfs/client1 中：
```sh
sudo mkdir -p /nfs/client1
sudo apt install rsync
sudo rsync -xa --progress --exclude /nfs / /nfs/client1
```
通过 chroot 到客户端文件系统上重新生成 SSH 主机密钥：
```sh
cd /nfs/client1
sudo mount --bind /dev dev
sudo mount --bind /sys sys
sudo mount --bind /proc proc
sudo chroot .
rm /etc/ssh/ssh_host_*
dpkg-reconfigure openssh-server
exit
sudo umount dev sys proc
```
找到本地网络的设置。您需要找到路由器（或网关）的地址，可以通过以下方式完成：

```sh
ip route | awk '/default/ {print $3}'
```
然后运行：
```sh
ip -4 addr show dev eth0 | grep inet
```
您应该看到类似于以下内容的输出：
```sh
inet 10.42.0.211/24 brd 10.42.0.255 scope global eth0
```
第一个地址是你的服务器Raspberry Pi在网络上的IP地址，斜杠后面的部分是网络大小。您的很可能是 /24。另请注意网络的 brd（广播）地址。记下上一个命令的输出，其中包含 Raspberry Pi 的 IP 地址和网络的广播地址。

最后，记下您的 DNS 服务器的地址，该地址与您的网关地址相同。您可以通过以下方式找到它：
```sh
cat /etc/resolv.conf
```
通过 systemd 网络在服务器 Raspberry Pi 上配置静态网络地址，该网络充当网络处理程序和 DHCP 服务器。

为此，您需要创建一个 10-eth0.netdev 和一个 11-eth0.network，如下所示：
```sh
sudo nano /etc/systemd/network/10-eth0.netdev
```
添加以下行：
```sh
[Match]
Name=eth0

[Network]
DHCP=no
```
然后创建一个网络文件：
```sh
sudo nano /etc/systemd/network/11-eth0.network
```
添加以下内容：
```
[Match]
Name=eth0

[Network]
Address=10.42.0.211/24
DNS=10.42.0.1

[Route]
Gateway=10.42.0.1
```
此时，您将没有可用的 DNS，因此您需要将之前记下的服务器添加到 `systemd/resolved.conf` 中。在此示例中，网关地址为 10.42.0.1。

```sh
sudo nano /etc/systemd/resolved.conf
```
取消注释 DNS 行并在其中添加 DNS IP 地址。此外，如果您有后备 DNS 服务器，也请将其添加到此处。
```
[Resolve]
DNS=10.42.0.1
#FallbackDNS=
```
启用 systemd-networkd，然后重新启动以使更改生效：
```sh
sudo systemctl enable systemd-networkd
sudo reboot
```
现在启动 tcpdump，以便您可以从客户端 Raspberry Pi 搜索 DHCP 数据包：
```sh
sudo apt install tcpdump dnsmasq
sudo systemctl enable dnsmasq
sudo tcpdump -i eth0 port bootpc
```
将客户端 Raspberry Pi 连接到您的网络并打开电源。大约 10 秒后检查客户端上的 LED 是否亮起，然后您应该从客户端收到一个数据包“DHCP/BOOTP，来自……的请求”
```sh
IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from b8:27:eb...
```
现在您需要修改 dnsmasq 配置以使 DHCP 能够回复设备。按 CTRL + C 退出 tcpdump 程序，然后键入以下内容：
```sh
echo | sudo tee /etc/dnsmasq.conf
sudo nano /etc/dnsmasq.conf
```
然后将 dnsmasq.conf 的内容替换为：

```sh
# Note: comment out port if you want DNS services for systems on the network.
port=0
dhcp-range=10.42.0.255,proxy
log-dhcp
enable-tftp
tftp-root=/tftpboot
pxe-service=0,"Raspberry Pi Boot"
```
在 dhcp-range 行的第一个地址所在的位置，使用您之前记下的广播地址。

现在创建一个 `/tftpboot` 目录：
```sh
sudo mkdir /tftpboot
sudo chmod 777 /tftpboot
sudo systemctl enable dnsmasq.service
sudo systemctl restart dnsmasq.service
```
现在监控 dnsmasq 日志：
```sh
journalctl -f
```
你应该看到这样的东西：
```sh
raspberrypi dnsmasq-tftp[1903]: file /tftpboot/bootcode.bin not found
```
接下来，您需要将 boot 文件夹的内容复制到 `/tftpboot` 目录中。

首先按CTRL+C退出监控状态。然后输入以下内容：
```sh
cp -r /boot/firmware/* /tftpboot
```
由于 tftp 位置已更改，因此重新启动 dnsmasq：
```sh
sudo systemctl restart dnsmasq
```
#### 设置 NFS root

现在，这应该允许您的 Raspberry Pi 客户端尝试引导，直到它尝试加载根文件系统（它没有）。

此时，导出之前创建的 `/nfs/client1` 文件系统以及 TFTP 启动文件夹。
```sh
sudo apt install nfs-kernel-server
echo "/nfs/client1 *(rw,sync,no_subtree_check,no_root_squash)" | sudo tee -a /etc/exports
echo "/tftpboot *(rw,sync,no_subtree_check,no_root_squash)" | sudo tee -a /etc/exports
```
重新启动 RPC-Bind 和 NFS 服务器，以便它们检测新文件。
```sh
sudo systemctl enable rpcbind
sudo systemctl restart rpcbind
sudo systemctl enable nfs-kernel-server
sudo systemctl restart nfs-kernel-server
```

编辑 `/tftpboot/cmdline.txt` 并从 `root=` 开始，并将其替换为：
```sh
root=/dev/nfs nfsroot=10.42.0.211:/nfs/client1,vers=3 rw ip=dhcp rootwait
```
您应该用您记下的 IP 地址替换此处的 IP 地址。同时删除命令行中以 init= 开头的任何部分。

最后，编辑 `/nfs/client1/etc/fstab` 并删除 `/dev/mmcblk0p1` 和 p2 行（仅保留 proc）。然后，将启动分区添加回：
```sh
echo "10.42.0.211:/tftpboot /boot/firmware/ nfs defaults,vers=3 0 0" | sudo tee -a /nfs/client1/etc/fstab
```

如果第一次尝试无法启动，请继续尝试。 Raspberry Pi 启动可能需要一分钟左右的时间，因此请耐心等待。

## 使用 IPv6 进行网络启动

通过网络启动 Raspberry Pi 计算机分为 4 个阶段：

1. 引导加载程序使用 DHCP 协商获取 IP 地址和 TFTP 服务器的详细信息。

2. 引导加载程序通过 TFTP 加载固件，并将引导过程移交给固件，并向其传递网络详细信息。

3. 固件通过 TFTP 加载内核和命令行。

4. 内核引导系统的其余部分，通过 NFS 或其他机制加载根文件系统 (rootfs)。

引导加载程序和固件（第 1 至 3 阶段）已得到增强，可支持通过 IPv6 引导。

> IMPORTANT
> IPv6 网络引导是一项实验性 alpha 功能，根据反馈，我们将来可能需要更改其工作方式。这仅适用于 Raspberry Pi 4 和计算模块 4。

### 它是如何工作的

要通过 IPv6 启动，您需要更新版本的固件（例如 start4.elf）和引导加载程序。使用最新版本的 Raspberry Pi OS 和最新的稳定引导加载程序应该足够了。

> NOTE
> 常用的 dnsmasq DHCP 服务器目前不支持 IPv6 网络启动所需的网络启动参数，因此暂时您必须使用其他 DHCP 服务器，例如 ISC DHCP。

要通过网络挂载 rootfs，IPv4 网络引导教程建议使用 nfsroot。它不支持 IPv6，因此需要另一种方法通过网络挂载 rootfs。

如果您的 ISP 和路由器不支持 IPv6，您的操作将会受到限制。

#### 网络地址
引导加载程序所做的第一件事是发送路由器请求以获取网络的详细信息。路由器以标识其以太网地址的通告数据包进行响应，如果 TFTP 服务器位于不同的网络上，引导加载程序可能需要该数据包。

路由器通告包含一个标志，告诉它是否对其 IP 地址使用有状态（托管）或无状态（非托管）配置。无状态配置意味着设备配置自己的IP地址。目前，引导加载程序生成一个从其以太网 MAC 地址和路由器提供的网络前缀派生的地址。

如果路由器指示启用了状态配置，则使用 DHCP 来获取设备的 IP 地址。这涉及设备向 DHCP 服务器发送请求请求，该服务器以广告进行响应。然后，客户端在从服务器获得回复确认之前请求该地址。

DHCP 服务器和客户端使用可变长度的 DUID（设备唯一 ID）来标识自己。在 Raspberry Pi 上，该值源自 MAC 地址 (DUID_LL)。

#### TFTP地址
无论使用无状态配置还是有状态配置，都会使用 DHCP 服务器来获取 TFTP 服务器地址。这是在 BOOTFILE-URL 参数中编码的。我们发送客户端架构类型值 0x29 来标识设备。

请参阅 RFC 5970 和 IANA 动态主机配置协议 IPv6 文档。

#### 开机流程
设备现在应该有 IP 地址和 TFTP 详细信息。它从 TFTP 服务器下载固件二进制文件 start4.elf 并继续运行。固件会传递 IP 地址和 TFTP 服务器详细信息，以便它可以下载内核并启动系统的其余部分。

#### 内核启动
对于 IPv4 netboot，nfsroot 用于通过网络挂载 rootfs。这不支持 IPv6，因此需要另一个解决方案。它可能涉及一个小型 RAM 文件系统，可以在切换到正确的 rootfs 内容之前挂载适当的网络位置。

> NOTE
> 通过 IPv6 使用 NFS 启动 Linux 内核的机制仍有待论证。

### 测试设备 

如果您想尝试一下，您将需要另一个 Raspberry Pi 来充当 TFTP 和 DHCP 服务器。

理论上，TFTP 服务器可以位于任何可路由的网络上，但 DHCP 服务器必须与其服务的设备位于同一网络上。

#### TFTP服务器
如果您有有效的 IPv4 网络启动设置，您可以在 dnsmasq 中重用 TFTP 服务器来提供文件（它可以与 IPv4 和 IPv6 通信）。

或者，您可以使用独立的 TFTP 服务器，例如 tftpd-hpa。
```sh
$ sudo apt-get install tftpd-hpa
$ sudo systemctl start tftpd-hpa
```

#### DHCP服务器
IPv6 中的 DHCP 发生了很大变化。我们需要 DHCP 至少告诉我们 TFTP 服务器的地址，在本例中是同一台机器。
```sh
$ sudo apt-get install isc-dhcp-server
```
修改 `/etc/default/isc-dhcp-server`中的配置
```sh
DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf
INTERFACESv6="eth0"
```

在 `/etc/dhcp/dhcpd6.conf` 中，您需要指定 TFTP 服务器地址并设置子网。这里，DHCP 服务器配置为提供一些组成的唯一本地地址 (ULA)。主机 test-rpi4 行告诉 DHCP 为测试设备提供固定地址。

```sh
not authoritative;

# Check if the client looks like a Raspberry Pi
if option dhcp6.client-arch-type = 00:29 {
        option dhcp6.bootfile-url "tftp://[fd49:869:6f93::1]/";
}

subnet6 fd49:869:6f93::/64 {
        host test-rpi4 {
                host-identifier option dhcp6.client-id 00:03:00:01:e4:5f:01:20:24:0b;
                fixed-address6 fd49:869:6f93::1000;
        }
}
```
必须在 `/etc/dhcpcd.conf` 中为您的服务器分配 IPv6 地址
```sh
interface eth0
static ip6_address=fd49:869:6f93::1/64
```
现在启动 DHCP 服务器。
```sh
$ sudo systemctl restart isc-dhcp-server.service
```
#### 引导装载程序

修改配置以告诉它尝试通过 IPv6 而不是 IPv4 进行网络引导。
```sh
BOOT_ORDER=0xf21 # 2=Network boot
USE_IPV6=1 # Enable IPv6 network boot
BOOT_UART=1 # Debug
```

要恢复到 IPv4 网络启动，只需从 boot.conf 中删除 USE_IPV6 行。

#### 路由器
要使用 IPv6，您确实需要支持 IPv6 的路由器和 ISP。互联网上的一些站点可以为您检查这一点，或者运行以下命令。
```sh
sudo apt-get install ndisc6
rdisc6 -1 eth0
```

这会向您的路由器发送路由器请求，询问您的网络详细信息，例如网络前缀、路由器以太网地址以及是否使用 DHCP 进行寻址。如果此命令没有响应，则可能是您的网络和 ISP 仅支持 IPv4。如果支持 IPv6，则很可能将其配置为使用无状态配置，其中客户端生成自己的地址。
```sh
Soliciting ff02::2 (ff02::2) on eth0...
Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :          Yes
Mobile home agent         :           No
Router preference         :       medium
Neighbor discovery proxy  :           No
Router lifetime           :          180 (0x000000b4) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
```


您可以将路由器配置为有状态配置，这意味着它将使用 DHCP 来获取 IP 地址。
```sh
Hop limit                 :           64 (      0x40)
Stateful address conf.    :          Yes
Stateful other conf.      :          Yes
Mobile home agent         :           No
Router preference         :       medium
Neighbor discovery proxy  :           No
Router lifetime           :          180 (0x000000b4) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
```

### 调试


#### 日志和痕迹
如果启动 UART 已启用，您应该从串行端口看到类似这样的内容。以 RX6 开头的行表示 IPv6 正在使用中。

这里 dc:a6:32:6f:73:f4 是 TFTP 服务器的 MAC 地址，它的 IPv6 地址为 fd49:869:6f93::1。设备本身具有 MAC 地址 e4:5f:01:20:24:0b 和 IPv6 地址 fd49:869:6f93::1000


```sh
Boot mode: NETWORK (02) order f
GENET: RESET_PHY
PHY ID 600d 84a2
NET_BOOT: e4:5f:01:20:24:0b wait for link TFTP6: (null)
LINK STATUS: speed: 100 full duplex
Link ready
GENET START: 64 16 32
GENET: UMAC_START 0xe45f0120 0x240b0000
RX6: 12 IP: 1 MAC: 1 ICMP: 1/1 UDP: 0/0 ICMP_CSUM_ERR: 0 UDP_CSUM_ERR: 0
NET fd49:869:6f93::1000 tftp fd49:869:6f93::1
RX6: 17 IP: 4 MAC: 4 ICMP: 2/2 UDP: 2/2 ICMP_CSUM_ERR: 0 UDP_CSUM_ERR: 0
TFTP_GET: dc:a6:32:6f:73:f4 fd49:869:6f93::1 ab5a4158/start4.elf

RX6: 17 IP: 4 MAC: 4 ICMP: 2/2 UDP: 2/2 ICMP_CSUM_ERR: 0 UDP_CSUM_ERR: 0
RX6: 18 IP: 5 MAC: 5 ICMP: 2/2 UDP: 3/3 ICMP_CSUM_ERR: 0 UDP_CSUM_ERR: 0
TFTP_GET: dc:a6:32:6f:73:f4 fd49:869:6f93::1 ab5a4158/config.txt
```

最后引导加载程序将其交给应该加载内核的固件。

#### 有状态配置
您可以使用 tcpdump 检查网络活动。

```sh
sudo tcpdump -i eth0 -e ip6 -XX -l -v -vv
```
下面是 TCP 转储的摘录，其中路由器配置为使用有状态 (DHCP) 网络配置。

设备发送路由器请求。

```sh
12:23:35.387046 e4:5f:01:20:24:0b (oui Unknown) > 33:33:00:00:00:02 (oui Unknown), ethertype IPv6 (0x86dd), length 70: (hlim 255, next-header ICMPv6 (58) payload length: 16) fe80::e65f:1ff:fe20:240b > ip6-allrouters: [icmp6 sum ok] ICMP6, router solicitation, length 16
          source link-address option (1), length 8 (1): e4:5f:01:20:24:0b
            0x0000:  e45f 0120 240b
```
路由器发送响应告诉设备使用状态配置。

```sh
12:23:35.498902 60:8d:26:a7:c1:88 (oui Unknown) > 33:33:00:00:00:01 (oui Unknown), ethertype IPv6 (0x86dd), length 110: (hlim 255, next-header ICMPv6 (58) payload length: 56) bthub.home > ip6-allnodes: [icmp6 sum ok] ICMP6, router advertisement, length 56
        hop limit 64, Flags [managed, other stateful], pref medium, router lifetime 180s, reachable time 0ms, retrans timer 0ms
          rdnss option (25), length 24 (3):  lifetime 60s, addr: bthub.home
            0x0000:  0000 0000 003c fe80 0000 0000 0000 628d
            0x0010:  26ff fea7 c188
          mtu option (5), length 8 (1):  1492
            0x0000:  0000 0000 05d4
          source link-address option (1), length 8 (1): 60:8d:26:a7:c1:88
            0x0000:  608d 26a7 c188
```

设备发送 DHCP 请求。

```sh
12:23:35.502517 e4:5f:01:20:24:0b (oui Unknown) > 33:33:00:01:00:02 (oui Unknown), ethertype IPv6 (0x86dd), length 114: (hlim 255, next-header UDP (17) payload length: 60) fe80::e65f:1ff:fe20:240b.dhcpv6-client > ff02::1:2.dhcpv6-server: [udp sum ok] dhcp6 solicit (xid=8cdd56 (client-ID hwaddr type 1 e45f0120240b) (IA_NA IAID:0 T1:0 T2:0) (option-request opt_59) (opt_61) (elapsed-time 0))
```
DHCP 服务器回复一条通告。

```sh
12:23:35.510478 dc:a6:32:6f:73:f4 (oui Unknown) > e4:5f:01:20:24:0b (oui Unknown), ethertype IPv6 (0x86dd), length 172: (flowlabel 0xad54d, hlim 64, next-header UDP (17) payload length: 118) fe80::537a:52c:c647:b184.dhcpv6-server > fe80::e65f:1ff:fe20:240b.dhcpv6-client: [bad udp cksum 0xd886 -> 0x6d26!] dhcp6 advertise (xid=8cdd56 (IA_NA IAID:0 T1:3600 T2:7200 (IA_ADDR fd49:869:6f93::1000 pltime:604800 vltime:2592000)) (client-ID hwaddr type 1 e45f0120240b) (server-ID hwaddr/time type 1 time 671211709 dca6326f73f4) (opt_59))
```
设备向 DHCP 服务器发送地址和 TFTP 详细信息的请求。

```sh
12:23:35.510763 e4:5f:01:20:24:0b (oui Unknown) > 33:33:00:01:00:02 (oui Unknown), ethertype IPv6 (0x86dd), length 132: (hlim 255, next-header UDP (17) payload length: 78) fe80::e65f:1ff:fe20:240b.dhcpv6-client > ff02::1:2.dhcpv6-server: [udp sum ok] dhcp6 request (xid=8cdd56 (client-ID hwaddr type 1 e45f0120240b) (server-ID hwaddr/time type 1 time 671211709 dca6326f73f4) (IA_NA IAID:0 T1:0 T2:0) (option-request opt_59) (opt_61) (elapsed-time 1))
```

DHCP服务器回复，opt_59用于传递TFTP服务器的地址。

```sh
12:23:35.512122 dc:a6:32:6f:73:f4 (oui Unknown) > e4:5f:01:20:24:0b (oui Unknown), ethertype IPv6 (0x86dd), length 172: (flowlabel 0xad54d, hlim 64, next-header UDP (17) payload length: 118) fe80::537a:52c:c647:b184.dhcpv6-server > fe80::e65f:1ff:fe20:240b.dhcpv6-client: [bad udp cksum 0xd886 -> 0x6826!] dhcp6 reply (xid=8cdd56 (IA_NA IAID:0 T1:3600 T2:7200 (IA_ADDR fd49:869:6f93::1000 pltime:604800 vltime:2592000)) (client-ID hwaddr type 1 e45f0120240b) (server-ID hwaddr/time type 1 time 671211709 dca6326f73f4) (opt_59))
```
设备向 FTP 服务器发送邻居请求，因为它需要其 MAC 地址。

```sh
12:23:36.510768 e4:5f:01:20:24:0b (oui Unknown) > 33:33:ff:00:00:01 (oui Unknown), ethertype IPv6 (0x86dd), length 86: (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::e65f:1ff:fe20:240b > ff02::1:ff00:1: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has fd49:869:6f93::1
          source link-address option (1), length 8 (1): e4:5f:01:20:24:0b
            0x0000:  e45f 0120 240b
```

FTP 服务器回复其 MAC 地址。

```sh
12:23:36.510854 dc:a6:32:6f:73:f4 (oui Unknown) > e4:5f:01:20:24:0b (oui Unknown), ethertype IPv6 (0x86dd), length 86: (hlim 255, next-header ICMPv6 (58) payload length: 32) fd49:869:6f93::1 > fe80::e65f:1ff:fe20:240b: [icmp6 sum ok] ICMP6, neighbor advertisement, length 32, tgt is fd49:869:6f93::1, Flags [solicited, override]
          destination link-address option (2), length 8 (1): dc:a6:32:6f:73:f4
            0x0000:  dca6 326f 73f4
```

TFTP 请求由现在应通过网络启动的设备发出。

```sh
12:23:36.530820 e4:5f:01:20:24:0b (oui Unknown) > dc:a6:32:6f:73:f4 (oui Unknown), ethertype IPv6 (0x86dd), length 111: (hlim 255, next-header UDP (17) payload length: 57) fd49:869:6f93::1000.61785 > fd49:869:6f93::1.tftp: [udp sum ok]  49 RRQ "ab5a4158/start4.elf" octet tsize 0 blksize 1024
```
#### 无状态配置

下面是无状态（非 DHCP）网络配置的 tcp 转储的摘录。

设备发送路由器请求。

```sh
12:55:27.541909 e4:5f:01:20:24:0b (oui Unknown) > 33:33:00:00:00:02 (oui Unknown), ethertype IPv6 (0x86dd), length 70: (hlim 255, next-header ICMPv6 (58) payload length: 16) fe80::e65f:1ff:fe20:240b > ip6-allrouters: [icmp6 sum ok] ICMP6, router solicitation, length 16
          source link-address option (1), length 8 (1): e4:5f:01:20:24:0b
            0x0000:  e45f 0120 240b
```

路由器回复网络详细信息。

```sh
12:55:27.834684 60:8d:26:a7:c1:88 (oui Unknown) > 33:33:00:00:00:01 (oui Unknown), ethertype IPv6 (0x86dd), length 174: (hlim 255, next-header ICMPv6 (58) payload length: 120) bthub.home > ip6-allnodes: [icmp6 sum ok] ICMP6, router advertisement, length 120
        hop limit 64, Flags [other stateful], pref medium, router lifetime 180s, reachable time 0ms, retrans timer 0ms
          prefix info option (3), length 32 (4): 2a00:23c5:ee00:5001::/64, Flags [onlink, auto, router], valid time 300s, pref. time 120s
            0x0000:  40e0 0000 012c 0000 0078 0000 0000 2a00
            0x0010:  23c5 ee00 5001 0000 0000 0000 0000
          prefix info option (3), length 32 (4): fd4d:869:6f93::/64, Flags [onlink, auto, router], valid time 10080s, pref. time 2880s
            0x0000:  40e0 0000 2760 0000 0b40 0000 0000 fd4d
            0x0010:  0869 6f93 0000 0000 0000 0000 0000
          rdnss option (25), length 24 (3):  lifetime 60s, addr: bthub.home
            0x0000:  0000 0000 003c fe80 0000 0000 0000 628d
            0x0010:  26ff fea7 c188
          mtu option (5), length 8 (1):  1492
            0x0000:  0000 0000 05d4
          source link-address option (1), length 8 (1): 60:8d:26:a7:c1:88
            0x0000:  608d 26a7 c188
```

设备向 DHCP 多播地址发送信息请求，询问 TFTP 详细信息。

```sh
12:55:27.838300 e4:5f:01:20:24:0b (oui Unknown) > 33:33:00:01:00:02 (oui Unknown), ethertype IPv6 (0x86dd), length 98: (hlim 255, next-header UDP (17) payload length: 44) fe80::e65f:1ff:fe20:240b.dhcpv6-client > ff02::1:2.dhcpv6-server: [udp sum ok] dhcp6 inf-req (xid=e5e0a4 (client-ID hwaddr type 1 e45f0120240b) (option-request opt_59) (opt_61) (elapsed-time 0))
```

DHCP 服务器回复 TFTP 服务器详细信息 (opt_59)。

```sh
12:55:27.838898 dc:a6:32:6f:73:f4 (oui Unknown) > e4:5f:01:20:24:0b (oui Unknown), ethertype IPv6 (0x86dd), length 150: (flowlabel 0xd1248, hlim 64, next-header UDP (17) payload length: 96) fe80::537a:52c:c647:b184.dhcpv6-server > fe80::e65f:1ff:fe20:240b.dhcpv6-client: [bad udp cksum 0xd870 -> 0x78bb!] dhcp6 reply (xid=e5e0a4 (client-ID hwaddr type 1 e45f0120240b) (server-ID hwaddr/time type 1 time 671211709 dca6326f73f4) (opt_59))
```

设备会询问 TFTP 服务器 MAC 地址，因为它可以知道它位于同一网络上。

```sh
12:55:28.834796 e4:5f:01:20:24:0b (oui Unknown) > 33:33:ff:1d:fe:2a (oui Unknown), ethertype IPv6 (0x86dd), length 86: (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::e65f:1ff:fe20:240b > ff02::1:ff1d:fe2a: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2a00:23c5:ee00:5001:57f1:7523:2f1d:fe2a
          source link-address option (1), length 8 (1): e4:5f:01:20:24:0b
            0x0000:  e45f 0120 240b
```
FTP 服务器回复其 MAC 地址。

```sh
12:55:28.834875 dc:a6:32:6f:73:f4 (oui Unknown) > e4:5f:01:20:24:0b (oui Unknown), ethertype IPv6 (0x86dd), length 86: (hlim 255, next-header ICMPv6 (58) payload length: 32) 2a00:23c5:ee00:5001:57f1:7523:2f1d:fe2a > fe80::e65f:1ff:fe20:240b: [icmp6 sum ok] ICMP6, neighbor advertisement, length 32, tgt is 2a00:23c5:ee00:5001:57f1:7523:2f1d:fe2a, Flags [solicited, override]
          destination link-address option (2), length 8 (1): dc:a6:32:6f:73:f4
            0x0000:  dca6 326f 73f4
```

设备开始发出 TFTP 请求。

```sh
12:55:28.861097 e4:5f:01:20:24:0b (oui Unknown) > dc:a6:32:6f:73:f4 (oui Unknown), ethertype IPv6 (0x86dd), length 111: (hlim 255, next-header UDP (17) payload length: 57) 2a00:23c5:ee00:5001:e65f:1ff:fe20:240b.46930 > 2a00:23c5:ee00:5001:57f1:7523:2f1d:fe2a.tftp: [udp sum ok]  49 RRQ "ab5a4158/start4.elf" octet tsize 0 blksize 1024
```
