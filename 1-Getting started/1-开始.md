## 入门

### 开始使用你的树莓派

要开始使用 Raspberry Pi，您需要以下各项：

- 一个电源
- 启动介质（例如具有充足存储空间和速度的 microSD 卡）

您可以将 Raspberry Pi 设置为带有桌面的交互式计算机，或者设置为只能通过网络访问的无头计算机。要将 Raspberry Pi 设置为无头，您不需要任何额外的外围设备：您可以在安装操作系统时预先配置主机名、用户帐户、网络连接和 SSH。如果您想直接使用 Raspberry Pi，则需要以下附加配件：

- 一个显示器
- 用于将 Raspberry Pi 连接到显示器的电缆
- 一个键盘
- 一个鼠标

## 电源

下表显示了为各种 Raspberry Pi 型号供电所需的 USB-PD 电源模式。您可以使用任何提供正确电源模式的高质量电源。

|型号 |推荐电源(电压/电流)	| 电源 | 
|:-- |:-- |:-- |
|树莓派5           | 5V/5A、5V/3A 将外设电流限制为 600mA| 27W USB-C 电源 |
|树莓派 4 B 型     | 5V/3A  | 15W USB-C 电源 |
|树莓派 3（所有型号）| 5V/2.5A | 12.5W Micro USB 电源 |
|树莓派 2（所有型号）| 5V/2.5A | 12.5W Micro USB 电源 |
|树莓派 1（所有型号）| 5V/2.5A | 12.5W Micro USB 电源 |
|树莓派 0（所有型号）| 5V/2.5A | 12.5W Micro USB 电源 |


将电源插入标有“POWER IN”、“PWR IN”或“PWR”的端口。某些 Raspberry Pi 型号（例如 Zero 系列）具有与电源端口形状相同的 USB 输出端口。请确保在 Raspberry Pi 上使用正确的端口！

### 启动媒体

Raspberry Pi 型号缺乏板载存储，因此您必须提供它。您可以从安装在任何支持的介质上的操作系统映像启动 Raspberry Pi：通常使用 microSD 卡，但也可以使用 USB 存储、网络存储和通过 PCIe HAT 连接的存储。但是，只有最新的 Raspberry Pi 型号支持所有这些媒体类型。


自 Raspberry Pi 1 Model A+ 以来的所有 Raspberry Pi 消费型号均配有 microSD 插槽。当 microSD 插槽包含卡时，您的 Raspberry Pi 会自动从该插槽启动。

#### 推荐的 SD 卡

我们建议使用至少具有 32GB 存储空间的 SD 卡来安装 Raspberry Pi 操作系统。
对于 Raspberry Pi OS Lite，我们建议至少 16GB。
您可以使用任何容量小于 2TB 的 SD 卡。由于 MBR 的限制，目前不支持 2TB 以上的容量。
与任何其他启动介质一样，您将看到 SD 卡的性能得到改善，读写速度更快。

由于硬件限制，以下设备只能从 256GB 或更少的启动分区启动：

- Raspberry Pi Zero - 树莓派0
- Raspberry Pi 1 - 树莓派1
- early Raspberry Pi 2 models with the BCM2836 SoC - 具有 BCM2836 SoC 的早期 Raspberry Pi 2 型号

其他操作系统有不同的要求。检查操作系统的文档以了解容量要求。


## 键盘

您可以使用 Raspberry Pi 上的任何 USB 端口连接有线键盘或 USB 蓝牙接收器。

## 鼠标

您可以使用 Raspberry Pi 上的任何 USB 端口连接有线鼠标或 USB 蓝牙接收器。

## 显示器

Raspberry Pi 型号具有以下显示连接：

|型号 | 显示输出 |
|:--|:--|
|树莓派5 |2个 micro HDMI |
|树莓派 4（所有型号） | 2个 micro HDMI、音频和复合输出（通过 3.5 毫米 TRRS 插孔）|
|树莓派 3（所有型号） | HDMI、音频和复合输出通过 3.5mm TRRS 插孔 |
|树莓派 2（所有型号） | HDMI、音频和复合输出通过 3.5mm TRRS 插孔 |
|树莓派 1 型号 B+    | HDMI、音频和复合输出通过 3.5mm TRRS 插孔 |
|树莓派 1 型号 A+   |  HDMI、音频和复合输出通过 3.5mm TRRS 插孔 |
|Raspberry Pi 0（所有型号） | mini HDMI |

> Note: 没有 Raspberry Pi 型号支持 USB-C 视频（DisplayPort alt 模式）。

如果您的 Raspberry Pi 有多个 HDMI 端口，请将主显示器插入标记为 HDMI0 的端口。

大多数显示器没有微型或迷你 HDMI 端口。但是，您可以使用微型 HDMI 到 HDMI 电缆或微型 HDMI 到 HDMI 电缆将 Raspberry Pi 上的这些端口连接到任何 HDMI 显示器。
对于不支持 HDMI 的显示器，请考虑使用适配器将显示输出从 HDMI 转换到显示器支持的端口。

## 声音

所有配备 HDMI、micro HDMI 或 mini HDMI 的 Raspberry Pi 型号都支持通过 HDMI 进行音频输出。所有 Raspberry Pi 型号均支持 USB 音频。所有配备蓝牙的 Raspberry Pi 型号都支持蓝牙音频。 Raspberry Pi 1、2、3 和 4 的所有变体均包含 3.5 毫米辅助 TRRS 插孔，可能需要放大以获得足够的输出音量。

## 网络

以下 Raspberry Pi 型号配备 Wi-Fi 和蓝牙连接：

- Raspberry Pi 5
- Raspberry Pi 4
- Raspberry Pi 3B+
- Raspberry Pi 3
- Raspberry Pi Zero W
- Rsapberry Pi Zero 2 W

“型号B”后缀表示带有以太网端口的型号； 
“型号A”表示没有以太网端口。

如果您的 Raspberry Pi 没有以太网端口，您仍然可以使用 USB 转以太网适配器连接到有线互联网连接。

## 安装操作系统

要使用 Raspberry Pi，您需要一个操作系统。默认情况下，Raspberry Pi 检查插入 SD 卡插槽的任何 SD 卡上的操作系统。


根据您的 Raspberry Pi 型号，您还可以从其他存储设备启动操作系统，包括 USB 驱动器、通过 HAT 连接的存储和网络存储。

要在 Raspberry Pi 的存储设备上安装操作系统，您需要：

- 可用于将存储设备映像到启动设备的计算机
- 将存储设备插入该计算机的方法

大多数 Raspberry Pi 用户选择 microSD 卡作为启动设备。

我们建议使用 Raspberry Pi Imager 安装操作系统。

Raspberry Pi Imager 是一款可帮助您在 macOS、Windows 和 Linux 上下载和写入映像的工具。 Imager 包含许多适用于 Raspberry Pi 的流行操作系统映像。 Imager还支持加载直接从Raspberry Pi或第三方供应商（例如Ubuntu）下载的图像。您可以使用 Imager 为 Raspberry Pi 预配置凭据和远程访问设置。

Imager 支持以 .img 格式打包的图像以及 .zip 等容器格式。

如果您没有其他计算机可以将映像写入启动设备，您可以直接从互联网在 Raspberry Pi 上安装操作系统。

## 使用 Imager 安装

您可以通过以下方式安装Imager：

- 从 raspberrypi.com/software 下载最新版本并运行安装程序。
- 使用包管理器从终端安装它，例如sudo apt install rpi-imager。

安装 Imager 后，通过单击 Raspberry Pi Imager 图标或运行 rpi-imager 来启动应用程序。

![Imager启动图](https://www.raspberrypi.com/documentation/computers/images/imager/welcome.png)

单击选择设备并从列表中选择您的 Raspberry Pi 型号。

![选择树莓派型号](https://www.raspberrypi.com/documentation/computers/images/imager/choose-model.png)

接下来，单击“选择操作系统”并选择要安装的操作系统。 Imager 始终在列表顶部显示适合您的型号的 Raspberry Pi OS 推荐版本。

![选择要安装的操作系统](https://www.raspberrypi.com/documentation/computers/images/imager/choose-os.png)

将您首选的存储设备连接到计算机。例如，使用外部或内置 SD 读卡器插入 microSD 卡。然后，单击选择存储并选择您的存储设备。

> 警告：如果您的计算机连接了多个存储设备，请务必选择正确的设备！您通常可以通过大小来识别存储设备。如果您不确定，请断开其他设备的连接，直到确定要成像的设备为止。

![选择要安装的存储设备](https://www.raspberrypi.com/documentation/computers/images/imager/choose-storage.png)

接下来，单击“下一步”。

![选择要安装的存储设备](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-prompt.png)

在弹出窗口中，Imager 会要求您应用操作系统自定义。我们强烈建议通过操作系统自定义设置来配置您的 Raspberry Pi。单击编辑设置按钮以打开操作系统自定义。

如果您不通过操作系统自定义设置配置 Raspberry Pi，Raspberry Pi OS 将在配置向导中首次启动时要求您提供相同的信息。您可以单击“否”按钮跳过操作系统自定义。

### 操作系统定制

操作系统自定义菜单可让您在首次启动之前设置 Raspberry Pi。您可以预先配置：

- 用户名和密码
- Wi-Fi 账密
- 设备主机名
- 时区
- 键盘布局
- 远程连接

当您首次打开操作系统自定义菜单时，您可能会看到一条提示，要求您授予从主机加载 Wi-Fi 凭据的权限。如果您回答“是”，Imager 将从您当前连接的网络中预填充 Wi-Fi 凭据。如果您回答“否”，您可以手动输入 Wi-Fi 凭据。

hostname 选项定义 Raspberry Pi 使用 mDNS 广播到网络的主机名。当您将 Raspberry Pi 连接到网络时，网络上的其他设备可以使用 `<hostname>.local` 或 `<hostname>.lan` 与您的计算机进行通信。

用户名和密码选项定义 Raspberry Pi 上管理员用户帐户的用户名和密码。

无线 LAN 选项允许您输入无线网络的 SSID（名称）和密码。如果您的网络不公开广播 SSID，您应该启用“隐藏 SSID”设置。默认情况下，Imager 使用您当前所在的国家/地区作为“无线 LAN 国家/地区”。此设置控制 Raspberry Pi 使用的 Wi-Fi 广播频率。如果您计划运行无头 Raspberry Pi，请输入无线 LAN 选项的凭据。

区域设置选项允许您定义 Pi 的时区和默认键盘布局。


![操作系统配置](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-general.png)


“服务”选项卡包含可帮助您远程连接到 Raspberry Pi 的设置。

如果您计划通过网络远程使用 Raspberry Pi，请选中启用 SSH 旁边的框。如果您计划运行无头 Raspberry Pi，则应该启用此选项。

- 选择密码身份验证选项，使用您在操作系统自定义的常规选项卡中提供的用户名和密码通过网络 SSH 到您的 Raspberry Pi。
- 选择仅允许公钥身份验证以使用您当前使用的计算机中的私钥预先配置您的 Raspberry Pi，以进行无密码公钥 SSH 身份验证。如果您的 SSH 配置中已有 RSA 密钥，Imager 将使用该公钥。如果没有，您可以单击“运行 SSH-keygen”来生成公钥/私钥对。 Imager 将使用新生成的公钥。

![操作系统配置](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-services.png)


操作系统定制还包括一个选项菜单，允许您在写入期间配置成像器的行为。这些选项允许您在 Imager 完成验证图像时播放噪音、验证后自动卸载存储介质以及禁用遥测。


![操作系统配置](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-options.png)

### 写

输入完操作系统自定义设置后，单击“保存”以保存您的自定义设置。

然后，单击“是”以在将映像写入存储设备时应用操作系统自定义设置。

最后，对“您确定要继续吗？”回答“是”。弹出窗口开始将数据写入存储设备。

![操作系统配置](https://www.raspberrypi.com/documentation/computers/images/imager/are-you-sure.png)

如果您看到管理员提示，要求授予读取和写入存储介质的权限，请授予 Imager 继续操作的权限。

![写入存储](https://www.raspberrypi.com/documentation/computers/images/imager/writing.png)

> 喝杯咖啡或者去散步。这可能需要几分钟的时间。

![写入存储](https://www.raspberrypi.com/documentation/computers/images/imager/stop-ask-verify.png)

> 如果你想活得特别危险，可以点击取消验证，跳过验证过程。

当您看到“写入成功”弹出窗口时，您的映像已完全写入并验证。现在您已准备好从存储设备启动 Raspberry Pi！

![写入成功](https://www.raspberrypi.com/documentation/computers/images/imager/finished.png)

接下来，继续执行第一个启动配置说明，让 Raspberry Pi 启动并运行。

## 通过网络安装

网络安装使 Raspberry Pi 能够使用通过网络下载的 Raspberry Pi Imager 版本在存储设备上安装操作系统。通过网络安装，您可以在 Raspberry Pi 上安装操作系统，无需单独的 SD 卡读卡器，也不需要除 Raspberry Pi 之外的任何计算机。您可以在任何兼容的存储设备上运行网络安装，包括 SD 卡和 USB 存储设备。

网络安装仅在 Raspberry Pi 4、400 和 5 上运行。如果您的 Raspberry Pi 运行较旧的引导加载程序，您可能需要更新引导加载程序才能使用网络安装。

网络安装需要以下内容：

- 运行支持网络安装固件的兼容 Raspberry Pi 型号
- 显示器
- 键盘
- 有线互联网连接

要启动网络安装，请在以下配置中按住 SHIFT 键的同时打开 Raspberry Pi 电源：

- 没有可启动存储设备
- 附带键盘
- 连接的兼容存储设备，例如 SD 卡或 USB 存储设备

![网络安装](https://www.raspberrypi.com/documentation/computers/images/network-install-1.png)

如果您尚未将 Raspberry Pi 连接到互联网，请使用以太网电缆将其连接。

![网络安装](https://www.raspberrypi.com/documentation/computers/images/network-install-2.png)

连接到互联网后，您的 Raspberry Pi 将下载 Raspberry Pi 安装程序。如果下载失败，您可以重复该过程重试。

![网络安装](https://www.raspberrypi.com/documentation/computers/images/network-install-3.png)


下载完 Raspberry Pi Installer 后，您的 Raspberry Pi 将自动启动 Raspberry Pi Imager。有关运行 Raspberry Pi Imager 的更多信息，请参阅安装操作系统。

![网络安装](https://www.raspberrypi.com/documentation/computers/images/network-install-4.png)

有关网络安装配置的更多信息，请参阅 HTTP 引导。


## 设置你的树莓派

安装操作系统映像后，将存储设备连接到 Raspberry Pi。

首先，拔掉 Raspberry Pi 的电源，以确保在连接外围设备时 Raspberry Pi 处于断电状态。如果您将操作系统安装在 microSD 卡上，则现在可以将其插入 Raspberry Pi 的卡插槽。如果您在任何其他存储设备上安装了操作系统，您现在可以将其连接到 Raspberry Pi。

然后，插入任何其他外围设备，例如鼠标、键盘和显示器。

最后，将电源连接到 Raspberry Pi。当 Pi 开机时，您应该会看到状态 LED 亮起。如果您的 Pi 连接到显示器，您应该会在几分钟内看到启动屏幕。

## 首次启动时的配置

如果您使用 Imager 中的操作系统自定义来预配置您的 Raspberry Pi，那么恭喜您！您的设备已可供使用。继续执行后续步骤，了解如何充分利用 Raspberry Pi。

如果您的 Raspberry Pi 在 5 分钟内未启动，请检查状态 LED。如果闪烁，请参阅 LED 警告闪烁代码以获取更多信息。如果您的 Pi 拒绝启动，请尝试以下缓解步骤：

- 如果您使用 SD 卡以外的启动设备，请尝试从 SD 卡启动
- 重新镜像您的 SD 卡；确保在 Imager 中完成整个验证步骤
- 更新 Raspberry Pi 上的引导加载程序，然后重新映像您的 SD 卡

如果您选择跳过 Imager 中的操作系统自定义，您的 Raspberry Pi 将在首次启动时运行配置向导。您需要显示器和键盘来浏览向导；鼠标是可选的。

![首次启动](https://www.raspberrypi.com/documentation/computers/images/initial-setup/start.png)

## 蓝牙

如果您使用蓝牙键盘或鼠标，此步骤将引导您完成设备配对。您的 Raspberry Pi 将扫描可配对设备并连接到为每个项目找到的第一个设备。

此过程适用于内置或外部 USB 蓝牙适配器。如果您使用 USB 适配器，请在启动 Raspberry Pi 之前将其插入。


## 语言环境

此页面可帮助您配置您的国家/地区、语言、时区以及键盘布局。


![首次启动](https://www.raspberrypi.com/documentation/computers/images/initial-setup/locale.png)


## 用户

此页面帮助您配置默认用户帐户的用户名和密码。

默认情况下，旧版本的 Raspberry Pi OS 将用户名设置为“pi”。如果您使用用户名“pi”，请避免使用旧的默认密码“raspberry”，以确保 Raspberry Pi 的安全。

![首次启动](https://www.raspberrypi.com/documentation/computers/images/initial-setup/user.png)

## Wi-Fi


此页面可帮助您连接到 Wi-Fi 网络。从列表中选择您首选的网络。

![WiFi配置](https://www.raspberrypi.com/documentation/computers/images/initial-setup/network.png)

如果您的网络需要密码，您可以在此处输入。


![WiFi配置](https://www.raspberrypi.com/documentation/computers/images/initial-setup/network_password.png)



## 浏览器

此页面允许您选择 Firefox 或 Chromium 作为默认互联网浏览器。您可以选择卸载未设置为默认的浏览器。

![浏览器](https://www.raspberrypi.com/documentation/computers/images/initial-setup/browser.png)

## 软件更新

一旦您的 Raspberry Pi 可以访问互联网，此页面将帮助您将操作系统和软件更新到最新版本。在软件更新过程中，如果您在浏览器选择步骤中选择卸载非默认浏览器，向导将删除它。下载更新可能需要几分钟的时间。


![更新](https://www.raspberrypi.com/documentation/computers/images/initial-setup/update.png)

![更新](https://www.raspberrypi.com/documentation/computers/images/initial-setup/download.png)


当您看到弹出窗口表明您的系统是最新的时，单击“确定”继续下一步。


## 结束

在配置向导结束时，单击“重新启动”以重新启动 Raspberry Pi。您的 Raspberry Pi 将应用您的配置并启动到桌面。


![更新](https://www.raspberrypi.com/documentation/computers/images/initial-setup/restart.png)


## 下一步

现在您的 Raspberry Pi 已设置完毕并准备就绪，下一步是什么？


### 推荐软件

Raspberry Pi 操作系统预装了许多基本应用程序，因此您可以立即开始使用它们。如果您想利用我们认为有用的其他应用程序，请单击屏幕左上角的树莓派图标。从下拉菜单中选择首选项 > 推荐软件，您将找到包管理器。您可以在这里免费安装各种推荐的软件。

![更新](https://www.raspberrypi.com/documentation/computers/images/recommended-software.png)

例如，如果您计划将 Raspberry Pi 用作家用计算机，您可能会发现 LibreOffice 对于编写和编辑文档和电子表格很有用。您还可以使用屏幕放大器和 Orca 屏幕阅读器等应用程序（在通用访问下找到）让您的 Raspberry Pi 更易于访问。

### 教程

我们的教程演示了使用新计算机的各种方法。您可以按照激发您兴趣的教程来学习编码、控制外部设备以及构建令人兴奋的新项目。

### 支持

如需官方 Raspberry Pi 产品的支持，或与其他 Raspberry Pi 用户联系，请访问 Raspberry Pi 论坛。

### 进一步阅读

您可以在 Gareth Halfacree 撰写的最新版《官方 Raspberry Pi 初学者指南》中找到有关如何开始使用 Raspberry Pi 的更多信息。

了解如何：

- 设置您的 Raspberry Pi，安装其操作系统，然后开始使用这台功能齐全的计算机。
- 通过使用 Scratch 3、Python 和 MicroPython 编程语言的分步指南开始编码项目。
- 尝试连接电子元件，并享受创建令人惊叹的项目的乐趣。


第五版新增内容：

- 针对最新的 Raspberry Pi 计算机进行了更新：Raspberry Pi 5 和 Raspberry Pi Zero 2 W。
- 涵盖最新的 Raspberry Pi 操作系统。
- 包括有关 Raspberry Pi Pico 的新章节！

您可以在 Raspberry Pi Press 网站上购买这本书。