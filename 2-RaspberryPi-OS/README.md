# 树莓派操作系统


## 介绍

Raspberry Pi OS 是一款基于 Debian 的免费操作系统，针对 Raspberry Pi 硬件进行了优化。 Raspberry Pi OS 支持超过 35,000 个 Debian 软件包。对于大多数 Raspberry Pi 使用案例，我们建议使用 Raspberry Pi OS。

由于 Raspberry Pi 操作系统源自 Debian，因此它遵循 Debian 的交错版本 Debian 发布周期。大约每两年发布一次。
最新版本的Raspberry Pi OS基于 Debian 书虫。之前的版本是基于 Debian 靶心.


## 更新软件

始终保持 Raspberry Pi 上运行的软件更新到最新版本。这可以确保您的设备免受来自 漏洞 并确保您获得最新的错误修复。

### 使用 APT 管理软件包

高级打包工具 (APT) 是在 Raspberry Pi OS 中安装、更新和删除软件的推荐方法。您可以通过以下方式访问 APT apt 命令行界面。

#### 安装更新

apt 将软件源列表存储在位于以下位置的文件中 `/etc/apt/sources.list`。

在安装软件之前，运行以下命令 更新 您本地的软件包列表使用`/etc/apt/sources.list`:

```bash
sudo apt update
```

运行以下命令 升级 将所有已安装的软件包更新为最新版本：

```bash
sudo apt full-upgrade
```

> 提示： 与 Debian 不同，Raspberry Pi 操作系统正在持续开发中。因此，包依赖关系有时会发生变化，因此您应该始终使用full-upgrade而不是标准upgrade.

定期运行这些命令以使您的软件保持最新。使用 apt 使 Raspberry Pi 操作系统保持最新还可以使您的 Linux 内核和固件保持最新，因为 Raspberry Pi 将它们作为 Debian 软件包进行分发。

当 Raspberry Pi 发布新的 Raspberry Pi OS 主要版本时，上述命令不会将您的操作系统升级到该新的主要版本。要升级到新的主要版本，请按照我们的操作系统升级说明.

### 搜索软件

要在档案中搜索包，请将搜索关键字传递给apt-cache search:

```bash
apt-cache search <keyword>
```

例如，考虑以下对关键字“raspi”的搜索：

```bash
apt-cache search raspi
raspi3-firmware - Raspberry Pi 2 and 3 GPU firmware and bootloaders
libcamera-apps - libcamera-apps
libcamera-apps-lite - libcamera-apps-lite
python-picamera - Pure Python interface to the Raspberry Pi's camera module.
python-picamera-docs - Documentation for the Python interface to the RPi's camera module.
python3-picamera - Pure Python interface to the Raspberry Pi's camera module.
raspi-config - Raspberry Pi configuration tool
raspi-gpio - Dump the state of the BCM270x GPIOs
raspi-gpio-dbgsym - debug symbols for raspi-gpio
raspinfo - Dump information about the Pi
rc-gui - raspi-config GUI
raspi-copies-and-fills - ARM-accelerated versions of selected functions from string.h
raspi-copies-and-fills-dbgsym - debug symbols for raspi-copies-and-fills
```

搜索返回多个名称或描述包含关键字的包。

使用以下命令查看软件包的详细信息：

```bash
apt-cache show <package-name>
```
例如，考虑以下针对“raspi-config”包的查询：

```bash
apt-cache show raspi-config
Package: raspi-config
Version: 20210212
Architecture: all
Maintainer: Serge Schneider <serge@raspberrypi.org>
Installed-Size: 121
Depends: whiptail, parted, lua5.1, alsa-utils, psmisc, initramfs-tools
Recommends: triggerhappy, iw
Priority: optional
Section: utils
Filename: pool/main/r/raspi-config/raspi-config_20210212_all.deb
Size: 27976
SHA256: 772d4fd3c6d8c9da47ac56012b74e7828b53c8521ff1c47266bb38ec71750c10
SHA1: 08254c976a8260bde914c2df72f92ffb9317fef6
MD5sum: 80aaac13be6a9b455c822edb91cf8ea2
Description: Raspberry Pi configuration tool
 A simple configuration tool for common Raspberry Pi administrative tasks
Description-md5: 19630c04463bfe7193152448b53d85a0
```

使用此命令验证维护者、版本和大小是否符合您对包的期望。


#### 安装一个包

要在 Raspberry Pi 上安装软件包，请将软件包的名称传递给以下命令：


```bash
sudo apt install <package-name>
```

apt将显示包将消耗的磁盘空间量。进入 是 并按 进入 确认软件包的安装。您可以通过添加以下内容来跳过此确认步骤 -y 标记上面的命令。



#### 卸载一个包
要从 Raspberry Pi 卸载软件包，请将软件包的名称传递给以下命令：


```bash
sudo apt remove <package-name>
```

> 提示： 要完全删除包的所有痕迹，包括配置文件，请使用 purge 代替 remove.

apt 将显示删除软件包将释放的磁盘空间量。 Enter 是 并按 进入 确认软件包的安装。您可以通过添加以下内容来跳过此确认步骤 -y 标记上面的命令。


#### 管理 apt 磁盘使用情况

跑步前， sudo apt full-upgrade 显示完成升级所需下载并存储在磁盘上的数据量。要检查是否有足够的可用磁盘空间，请运行以下命令：

```bash
df -h 
```

apt存储下载的包（.deb）文件在 `/var/cache/apt/archives`。在安装过程中， apt 下载这些包，然后将文件从包复制到正确的安装位置。根据您安装的软件，包文件可能会占用大量空间。要删除任何延迟的包文件，请运行以下命令：

```bash
sudo apt clean
```

### 将你的操作系统升级到新的主要版本

> 警告：在尝试主要版本升级之前，请进行备份。

要将 Raspberry Pi 上的操作系统更新到新的主要版本，请使用新版本镜像第二张 SD 卡。使用 USB SD 读卡器或网络存储将文件和配置从当前安装复制到新的 SD 卡。然后，将新的 SD 卡插入 Raspberry Pi 上的插槽，然后启动。

### 升级你的固件

> 警告：在尝试主要版本升级之前，请进行备份。

> 警告：不保证软件的预发布版本能够正常工作。不使用 rpi-update 在任何系统上，除非 Raspberry Pi 工程师建议这样做。它可能会使您的系统不可靠或损坏。不使用 rpi-update 作为任何常规更新过程的一部分。

要将 Raspberry Pi 上的固件更新到最新版本，请使用 rpi-update.

rpi-update 下载最新预发布版本的 Linux 内核、其匹配模块、设备树文件以及最新版本的 VideoCore 固件。然后，它将这些文件安装到现有的 Raspberry Pi 操作系统安装中。
使用的所有源数据 rpi-update 来自 rpi-firmware 存储库。该存储库包含来自 官方固件存储库.

跑步 rpi-update 以 root 身份启动更新。更新完成后，重新启动 Raspberry Pi 以使这些更改生效：

```bash
sudo rpi-update
sudo reboot
```

### 将固件降级到最新稳定版本

如果您将固件更新到最新版本并遇到问题，请使用以下命令返回到最新的稳定固件版本：

```bash
sudo apt-get update
sudo apt install --reinstall raspi-firmware
```

> 笔记：
> 如果您仍然运行 Raspberry Pi OS Bullseye，则必须重新安装 raspberrypi-kernel 使用以下命令：

```bash
sudo apt install --reinstall libraspberrypi0 libraspberrypi-{bin,dev,doc} raspberrypi-{kernel,bootloader}
```

> 重新启动你的树莓派 sudo reboot 使这些变化生效。


## 播放音频和视频

Raspberry Pi 操作系统附带 VLC媒体播放器 预安装。您可以使用 VLC 播放视频和音频文件。 VLC在Raspberry Pi操作系统中使用硬件加速，并支持许多流行的音频和视频文件格式。


### VLC媒体播放器

#### VLC图形用户界面

要从 Raspberry Pi Desktop 播放音频或视频文件，请双击文件管理器中的文件。这会自动启动 VLC 来播放该文件。或者，从 声音和视频 菜单，启动 VLC 媒体播放器。然后，从 媒体 菜单，选择 打开文件...​ 并导航到您要播放的文件。

默认情况下，Raspberry Pi 操作系统通过 HDMI 将音频发送到您的显示器。要将音频输出到不同的接口，例如耳机插孔或 USB 扬声器，请右键单击系统托盘中的扬声器图标，然后选择一个选项。


#### vlc命令行界面
您还可以从命令行启动 VLC。在下面的示例中，我们使用了 Big Buck Bunny 的一个短片。要从 Raspberry Pi 下载此剪辑，请运行以下命令：

```bash
wget --trust-server-names http://rptl.io/big-buck-bunny
```

要从命令行在 VLC 中播放剪辑，请运行以下命令：

```bash
vlc big-buck-bunny-1080p.mp4
```

为了防止 VLC GUI 在文件播放完毕后保持打开状态，请添加 --play-and-exit 旗帜：

```bash
vlc --play-and-exit big-buck-bunny-1080p.mp4
```

要以全屏模式播放视频（在某些情况下可以使播放更流畅），请添加 --fullscreen 旗帜：

```bash
vlc --play-and-exit --fullscreen big-buck-bunny-1080p.mp4
```

#### 使用 cvlc 无需 GUI 即可播放媒体

如果你使用 cvlc 代替 vlc 使用以下任何命令，都不会显示 VLC GUI：

```bash
cvlc --play-and-exit big-buck-bunny-1080p.mp4
```

### 在 Raspberry Pi OS Lite 上播放音频和视频

与完整版 Raspberry Pi OS 不同，VLC 并未预装在 Raspberry Pi OS Lite 上。要使用 VLC 在 Raspberry Pi OS Lite 上播放视频和音频，请安装无需桌面即可播放所需的软件包：

```bash
sudo apt install --no-install-recommends vlc-bin vlc-plugin-base
```

对于下面的示例，我们使用了一个简短的音频剪辑。要从 Raspberry Pi 下载此剪辑，请运行以下命令：

```bash
wget --trust-server-names http://rptl.io/startup-music
```

要从命令行在 VLC 中播放剪辑，请运行以下命令：

```bash
cvlc --play-and-exit computer-startup-music.mp3
```

### 指定音频输出设备

要强制音频输出到特定设备，请传递 alsa 的价值 -A 使用选项阿尔萨斯 音频输出，以及 --alsa-audio-device 指定音频输出设备的选项：

```bash
cvlc --play-and-exit -A alsa --alsa-audio-device <alsa-device> computer-startup-music.mp3
```

更换 <alsa-device> 具有以下选项之一的占位符：

|ALSA设备| 描述|
|:--|:--|
|sysdefault:CARD=Headphones |耳机插孔 |
|sysdefault:CARD=vc4hdmi |Raspberry Pi Zero 或 Raspberry Pi Model 1、2 或 3 上的 HDMI 输出 |
|sysdefault:CARD=vc4hdmi0 |Raspberry Pi 4、5、400 或计算模块 4 上的 HDMI0 输出 |
|sysdefault:CARD=vc4hdmi1 |	
Raspberry Pi 4、5、400 或计算模块 4 上的 HDMI1 输出|

> 提示：使用以下命令获取 Raspberry Pi 上所有 ALSA 设备的列表：

```bash
aplay -L | grep sysdefault
```

### 指定视频输出设备

要强制视频输出到特定设备，请使用 --drm-vout-display 指定视频输出设备的选项：

```bash
cvlc --play-and-exit --drm-vout-display <drm-device> big-buck-bunny-1080p.mp4
```

更换 `<drm-device>` 具有以下选项之一的占位符：

|数字版权管理设备 |	描述|
|:--|:--|
|HDMI-A-1| Raspberry Pi Zero 或 Raspberry Pi Model 1、2 或 3 上的 HDMI 输出； 或者 Raspberry Pi 4、5 或 400 上的 HDMI0 输出 |
|HDMI-A-2 | Raspberry Pi 4、5 或 400 上的 HDMI1 输出 |
|DSI-1 | Raspberry Pi 触摸显示屏 |

> 提示：使用以下命令获取 Raspberry Pi 上所有 DRM 设备的列表：
> `kmsprint | grep Connector`


### 指定音频和视频输出设备

您可以组合音频和视频输出选项。例如，要将视频输出定向到触摸屏，并将音频输出定向到耳机插孔，请使用上述命令的以下组合：

```bash
cvlc --play-and-exit --fullscreen --drm-vout-display DSI-1 -A alsa --alsa-audio-device sysdefault:CARD=Headphones your_video.mp4
```

### 提高流媒体播放性能

如果您有原始 H.264 流（例如从 Raspberry Pi 相机模块捕获的流），则可以通过将流包装在 MP4 等容器格式中来提高 VLC 中的播放性能。您可以使用 ffmpeg 将流内容转换为容器文件。例如，以下命令转换名为的流 video.h264 到名为的 MP4 容器 video.mp4 每秒 30 帧：

```bash
ffmpeg -r 30 -i video.h264 -c:v copy video.mp4
```

## 实用程序

Raspberry Pi 操作系统中预装了几个有用的命令行实用程序。

### kmsprint

这 kmsprint 工具可用于列出连接到 Raspberry Pi 的显示器支持的显示模式。使用 kmsprint 查看连接到 Raspberry Pi 的监视器的详细信息，以及 kmsprint -m 查看每个显示器支持的所有显示模式的列表。您可以找到该项目的源代码kmsprint公用事业 在 Github 上.

### vclog 

vclog 显示来自 Arm 上运行的 Linux 的 VideoCore GPU 的日志消息。它需要以 root 身份运行。

sudo vclog --msg 打印出消息日志，同时 sudo vclog --assert 打印出断言日志。

### vcgencmd

这 vcgencmd 该工具用于从 Raspberry Pi 上的 VideoCore GPU 输出信息。您可以找到该项目的源代码 vcgencmd 公用事业 在 GitHub 上.

获取支持的所有命令的列表 vcgencmd， 使用 vcgencmd commands。下面列出了一些有用的命令及其所需的参数。

#### vcos

这 vcos 命令有两个有用的子命令：

- version 显示 VideoCore 上固件的构建日期和版本
- log status显示各个 VideoCore 固件区域的错误日志状态

#### version

显示 VideoCore 固件的构建日期和版本。

#### get_throttled

返回系统的节流状态。这是一个位模式。被设置的位表示以下含义：

|少量|十六进制值|意义
|:--|:--  |:-- 
|0	|0x1  |检测到欠压
|1	|0x2  |手臂频率上限
|2	|0x4  |目前已被限制
|3	|0x8  |软温度限制激活
|16	|0x10000|发生欠电压
|17 |0x20000|已发生臂频率上限
|18	|0x40000|发生了节流
|19	|0x80000|已发生软温度限制

#### measure_temp

返回 SoC 的温度（由其内部温度传感器测量）。 在 Raspberry Pi 4 上，measure_temp pmic返回 PMIC 的温度。

#### measure_clock [clock]

这将返回指定时钟的当前频率。接受以下时钟值：

|钟	 |描述
|:-- |:--
|arm |ARM 内核
|core |GPU核心
|h264 |H.264块
|isp  |图像传感器管线
|v3d  |3D块
|uart |串口
|pwm  |PWM模块（模拟音频输出）
|emmc |SD卡接口
|pixel|像素阀
|vec  |模拟视频编码器
|hdmi |HDMI
|dpi  |显示并行接口

例如 vcgencmd measure_clock arm

#### measure_volts [block]

显示特定模块当前使用的电压。接受以下块值：

|堵塞	|描述
|:--|:--
|core    |VC4核心电压
|sdram_c |SDRAM核心电压
|sdram_i |SDRAM I/O 电压
|sdram_p |SDRAM 物理电压

#### otp_dump

显示 SoC 内部 OTP（一次性可编程）存储器的内容。这些是 32 位值，索引从 8 到 64。请参阅 OTP 位页 更多细节。

#### get_config [configuration item|int|str]

显示指定的配置设置的值：或者，指定 int （整数）或 str （字符串）查看给定类型的所有配置项。例如，以下命令返回设备上的总内存（以兆字节为单位）：


```bash
vcgencmd get_config total_mem
```
#### get_mem type

报告 Arm 和 GPU 可寻址的内存量。要显示 Arm 可寻址内存量，请使用vcgencmd get_mem arm;要显示 GPU 可寻址内存量，请使用 vcgencmd get_mem gpu。在内存超过 1GB 的设备上， arm 参数将始终返回 1GB 减去 gpu 内存值，因为 GPU 固件仅识别前 1GB 内存。要获取设备总内存的准确报告，请参阅 total_mem 配置项和 get_config 上面的部分。


#### codec_enabled [type]

报告是否启用指定的编解码器类型。类型的可能选项包括 AGIF、FLAC、H263、H264、MJPA、MJPB、MJPG、MPG2、MPG4、MVC0、PCM、THRA、VORB、VP6、VP8、WMV9、WVC1。请注意，由于 Raspberry Pi 4 和 400 上的 H.265 硬件块不是 VideoCore GPU 的一部分，因此无法通过此命令访问其状态。

#### mem_oom

显示 VideoCore 内存空间中发生的任何 OOM（内存不足）事件的统计信息。

#### mem_reloc_stats

显示 VideoCore 上可重定位内存分配器的统计信息。

#### read_ring_osc
返回环形振荡器的当前速度、电压和温度。


## 辅助功能选项

### 视觉教具


有视觉障碍的 Raspberry Pi 操作系统用户可以在 推荐软件 菜单。
我们提供 Orca 屏幕阅读器 简化 Raspberry Pi 桌面的导航。此外，我们还提供屏幕放大器来提高 UI 和屏幕元素的可读性。

#### 屏幕阅读器

您可以从以下位置安装 Orca 屏幕阅读器 推荐软件 Raspberry Pi 主菜单部分。或者，按 控制键 + 替代 + 空间 自动安装 Orca。

安装新映像后首次启动 Raspberry Pi 操作系统时，30 秒后会自动播放语音提醒。此提醒提供有关如何安装 Orca 的说明。



### 在 Raspberry Pi 上使用 Python

Raspberry Pi 操作系统预装了 Python 3。干扰系统 Python 安装可能会导致操作系统出现问题。安装第三方 Python 库时，请始终使用正确的包管理工具。

在 Linux 上，您可以安装 python 依赖有两种方式：

- 使用 apt 安装预配置的系统包
- 使用 pip 使用 Python 的依赖管理器安装库 在虚拟环境中

> 重要信息：在 Raspberry Pi 操作系统中启动 书呆子，你只能使用 pip 安装到Python虚拟环境中（venv）。此更改是由 Python 社区而不是 Raspberry Pi 引入的：有关更多信息，请参阅 公众号 668.

#### 使用以下命令安装 Python 包 apt

通过以下方式安装的软件包 apt 专门针对 Raspberry Pi 操作系统进行打包。这些软件包通常是预先编译的，因此安装速度更快。因为 apt 管理所有包的依赖关系，使用此方法安装包括运行该包所需的所有子依赖关系。和 apt 确保卸载时不会破坏其他软件包。

例如，安装支持Raspberry Pi的Python 3库 构建帽子，运行以下命令：

```bash
sudo apt install python3-build-hat
```

查找分发的 Python 包 apt, 使用 apt search。在大多数情况下，Python 包使用前缀 python- 或者 python3-: 例如，您可以找到 numpy 名下的包裹 python3-numpy.

#### 使用以下命令安装 Python 库 pip


##### 书虫改为 pip 安装

在旧版本的 Raspberry Pi OS 中，您可以使用以下命令将库直接安装到 Python 的系统版本中 pip。自从树莓派操作系统 书呆子，用户无法将库直接安装到系统版本的Python中。

反而， 将库安装到虚拟环境中（venv)。要在系统级别为所有用户安装库， 安装它apt.

尝试在系统范围内安装 Python 包会输出类似于以下内容的错误：

```bash
pip install buildhat
error: externally-managed-environment

× This environment is externally managed
╰─> To install Python packages system-wide, try apt install
  python3-xyz, where xyz is the package you are trying to
  install.

  If you wish to install a non-Debian-packaged Python package,
  create a virtual environment using python3 -m venv path/to/venv.
  Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
  sure you have python3-full installed.

  For more information visit http://rptl.io/venv

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.
```

Python 用户长期以来一直在处理操作系统包管理器之间的冲突，例如 apt 以及 Python 特定的包管理工具，例如 pip。这些冲突包括 Python 级 API 不兼容和文件所有权冲突。

从 Raspberry Pi 操作系统启动 书呆子，通过安装的软件包 pip 必须安装到Python虚拟环境中 (venv）。虚拟环境是一个容器，您可以在其中安全地安装第三方模块，这样它们就不会干扰您的Python系统。

##### 在虚拟环境中使用 pip

要使用虚拟环境，请创建一个容器来存储环境。您可以通过多种方法来完成此操作，具体取决于您想要使用 Python 的方式。

运行以下命令创建虚拟环境配置文件夹，替换 <env-name> 带有您想要用于虚拟环境的名称（例如env):

```bash
python -m venv <env-name>
```

> 提示：通过 --system-site-packages 文件夹名称之前的标志可将系统 Python 安装中当前安装的所有包预加载到虚拟环境中。

然后，执行 bin/activate 虚拟环境配置文件夹中的脚本进入虚拟环境：

```bash
source <env-name>/bin/activate
```

然后您应该会看到类似于以下内容的提示：

```bash
(<env-name>) $
```

这 (<env-name>) 命令提示符前缀表示当前终端会话位于名为 <env-name>.

要检查您是否处于虚拟环境中，请使用 pip list 查看已安装软件包的列表：

```bash
(<env-name>) $ pip list
Package    Version
---------- -------
pip        23.0.1
setuptools 66.1.1
```

该列表应该比系统 Python 中安装的包列表短得多。您现在可以安全地安装软件包 pip。您安装的任何软件包 pip 而在虚拟环境中则仅安装到该虚拟环境中。在虚拟环境中， python 或者 python3 命令自动使用虚拟环境的 Python 版本和已安装的软件包，而不是系统 Python。

要离开虚拟环境，请运行以下命令：

```bash
(<env-name>) $ deactivate
```

##### 为每个项目使用单独的环境

许多用户为每个 Python 项目创建单独的虚拟环境。在每个项目的根文件夹中找到虚拟环境，通常使用共享名称，例如 env。从每个项目的根文件夹运行以下命令来创建虚拟环境配置文件夹：

```bash
python -m venv env
```

在处理项目之前，请从项目的根目录运行以下命令以开始使用虚拟环境：

```bash
source env/bin/activate
```

然后您应该会看到类似于以下内容的提示：

```bash
(env) $
```

完成项目后，从任意目录运行以下命令以离开虚拟环境：

```bash
(env) $ deactivate
```

#### 为每个用户使用单独的环境

您可以为您的用户帐户创建单个虚拟环境，而不是为每个 Python 项目创建虚拟环境。 在运行任何 Python 代码之前激活该虚拟环境。 这种方法对于跨项目共享许多库的工作流程来说更加方便。

在为整个用户帐户的多个项目创建虚拟环境时，请考虑在主目录中找到虚拟环境配置文件。将您的配置存储在名称以句点开头的文件夹 默认情况下隐藏该文件夹，防止它弄乱您的主文件夹。

使用以下命令在当前用户主目录的隐藏文件夹中创建虚拟环境：

```bash
python -m venv ~/.env
```

从任意目录运行以下命令以开始使用虚拟环境：

```bash
source ~/.env/bin/activate
```
然后您应该会看到类似于以下内容的提示：

```bash
(.env) $
```

要离开虚拟环境，请从任意目录运行以下命令：

```bash
(.env) $ deactivate
```

#### 使用 Thonny 编辑器

我们推荐 桑尼 用于在 Raspberry Pi 上编辑 Python 代码。

默认情况下，Thonny 使用系统 Python。但是，您可以通过单击切换到使用 Python 虚拟环境 翻译菜单 在 Thonny 窗口的右下角。选择已配置的环境或配置新的虚拟环境Configure interpreter…​.

![Thonny](https://www.raspberrypi.com/documentation/computers/images/thonny-venv.png)

## GPIO 和 40 针接头


Raspberry Pi 的一个强大功能是板顶部边缘的一排 GPIO（通用输入/输出）引脚。尽管 Raspberry Pi Zero、Raspberry Pi Zero W 和 Raspberry Pi Zero 2 W 上未安装 40 针 GPIO 接头，但所有当前 Raspberry Pi 板上都有 40 针 GPIO 接头。所有板上的 GPIO 接头均具有 0.1 英寸（2.54 毫米）引脚间距。

![GPIO](https://www.raspberrypi.com/documentation/computers/images/GPIO-Pinout-Diagram-2.png)

任何 GPIO 引脚都可以在软件中指定为输入或输出引脚，并用于多种用途。


![GPIO](https://www.raspberrypi.com/documentation/computers/images/GPIO.png)

> 笔记： GPIO 引脚编号方案不按数字顺序排列。板上存在 GPIO 引脚 0 和 1（物理引脚 27 和 28），但保留供高级使用。


### 电压

板上有两个 5V 引脚和两个 3.3V 引脚，以及一些无法重新配置的接地引脚 (GND)。其余引脚都是通用 3.3V 引脚，这意味着输出设置为 3.3V，输入可耐受 3.3V。

### 输出

指定为输出引脚的 GPIO 引脚可设置为高电平 (3.3V) 或低电平 (0V)。

### 输入

指定为输入引脚的 GPIO 引脚可读取为高电平 (3.3V) 或低电平 (0V)。通过使用内部上拉或下拉电阻器可以更轻松地实现这一点。引脚 GPIO2 和 GPIO3 有固定的上拉电阻，但对于其他引脚，可以在软件中配置。

### 其他GPIO功能
除了简单的输入和输出设备之外，GPIO 引脚还可用于多种替代功能。某些功能在所有引脚上可用，其他功能在特定引脚上可用：

- PWM（脉宽调制）
    - 所有引脚均可使用软件 PWM
    - GPIO12、GPIO13、GPIO18、GPIO19 上提供硬件 PWM
- SPI
    - SPI0：MOSI（GPIO10）； MISO（GPIO9）； SCLK（GPIO11）； CE0（GPIO8）、CE1（GPIO7）
    - SPI1：MOSI（GPIO20）； MISO（GPIO19）； SCLK（GPIO21）； CE0（GPIO18）； CE1（GPIO17）； CE2（GPIO16）
- I2C
    - 数据：（GPIO2）；时钟（GPIO3）
    - EEPROM 数据：(GPIO0)； EEPROM 时钟 (GPIO1)
- 串行
    - TX（GPIO14）；接收（GPIO15）


### 查看 Raspberry Pi 的 GPIO 引脚排列

通过打开终端窗口并运行命令，可以在 Raspberry Pi 上访问 GPIO 参考 pinout。该工具由 GPIO 零 Python 库，默认安装在 Raspberry Pi 操作系统中。

> 警告
> 虽然将简单组件连接到 GPIO 引脚是安全的，但请注意接线方式。 LED 应该有电阻来限制流过它们的电流。请勿将 5V 用于 3.3V 组件。不要将电机直接连接到 GPIO 引脚，而是使用 H桥电路或电机控制器板.

### 权限

为了使用 GPIO 端口，您的用户必须是 gpio 团体。默认用户帐户默认为成员，但您必须使用以下命令手动添加其他用户：

```bash
sudo usermod -a -G gpio <username>
```

### Python 中的 GPIO

使用 GPIO 零 库使您可以轻松地使用 Python 控制 GPIO 设备。该库的详细记录位于 gpiozero.readthedocs.io.



#### LED

以下示例代码控制连接到 GPIO17 的 LED：

```python
from gpiozero import LED
from time import sleep

led = LED(17)

while True:
    led.on()
    sleep(1)
    led.off()
    sleep(1)
```

在像 Thonny 这样的 IDE 中运行它，LED 将反复闪烁。
LED 方法包括 on(), off(), toggle()， 和 blink().


#### 按钮

以下示例代码读取连接到 GPIO2 的按钮的状态：

```python
from gpiozero import Button
from time import sleep

button = Button(2)

while True:
    if button.is_pressed:
        print("Pressed")
    else:
        print("Released")
    sleep(1)
```

按钮功能包括属性 is_pressed 和 is_held;回调 when_pressed, when_released， 和 when_held;和方法 wait_for_press() 和wait_for_release.


#### 按钮和 LED

以下示例代码读取连接到 GPIO2 的按钮的状态，并在按下按钮时点亮连接到 GPIO17 的 LED：

```python
from gpiozero import LED, Button

led = LED(17)
button = Button(2)

while True:
    if button.is_pressed:
        led.on()
    else:
        led.off()
```

或者：

```python
from gpiozero import LED, Button

led = LED(17)
button = Button(2)

while True:
    button.wait_for_press()
    led.on()
    button.wait_for_release()
    led.off()
```

或者：

```python
from gpiozero import LED, Button

led = LED(17)
button = Button(2)

button.when_pressed = led.on
button.when_released = led.off
```

#### 更进一步

您可以在 Raspberry Pi Press 书中找到有关如何使用 GPIO Zero Python 库对连接到 Raspberry Pi 的电子设备进行编程的更多信息 具有 GPIO 零的简单电子设备。本书帮助您开始使用 GPIO Zero 库，并通过构建一系列项目引导您了解如何使用它。

你可以 下载这本书 作为免费的 PDF 文件，它已在 Creative Commons 下发布 归因-非商业性-ShareAlike 3.0 未移植（CC BY NC-SA）许可证。