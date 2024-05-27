## 配置

### raspi 配置

> 提示： Raspberry Pi 桌面用户可以访问此应用程序的图形版本： 优先 > 树莓派配置。但是，某些高级配置仅在 raspi-config.

raspi-config 帮助您配置 Raspberry Pi。 Raspberry Pi 型号之间的可用选项可能有所不同。要打开配置工具，请运行以下命令：

```bash
sudo raspi-config
```

您应该会看到一个蓝屏，其中的选项位于灰色框中：

![raspi-config](https://www.raspberrypi.com/documentation/computers/images/raspi-config.png)

使用 【向上】 和 【向下】 箭头键可在可用选项之间移动突出显示的选择。
按 【正确的】 箭头键或按 【标签】 访问 `<Select>` 和 `<Finish>` 纽扣。按 【左边】 或按 【标签】 返回选项。

raspi-config 自动编辑 `/boot/firmware/config.txt` 以及各种Linux配置文件。
某些选项需要重新启动才能生效。如果您更改了其中任何一个，`raspi-config` 退出时要求您重新启动。

> 提示：在选项值的长列表（例如时区城市列表）中，键入一个字母以跳到列表的该部分。例如，输入L跳至里斯本。



#### 系统选项

系统选项子菜单允许您对启动、登录和网络过程的各个部分进行配置更改，以及一些其他系统级别的更改。

![raspi-system](https://www.raspberrypi.com/documentation/computers/images/raspi-system.png)

|配置项|说明
|:--|:--
|无线网络 |配置 Wi-Fi SSID 和密码。
|声音的 |指定音频输出目的地。
|密码 |更改您的密码。有关更多信息，请参阅 更改用户密码.
|主机名 | 设置可见 组播DNS 此 Raspberry Pi 在网络上的名称。
|开机/自动登录 |选择是否启动到控制台或桌面，以及您的 Raspberry Pi 在开机时是否自动登录到您当前的用户帐户。
|启动时网络 | 在继续启动之前等待网络连接。
|启动画面 | 启用或禁用启动时显示的启动屏幕。
|电源指示灯 | 如果您的 Raspberry Pi 型号允许，请更改电源 LED 的行为。
|浏览器 | 更改默认网络浏览器。


#### 显示选项

![raspi-display](https://www.raspberrypi.com/documentation/computers/images/raspi-display.png)


##### 欠扫描

> 笔记: 运行 Wayland 时不可用。

如果屏幕上显示的初始文本从边缘消失，请启用过扫描来调整边框。在某些显示器上，尤其是显示器上，禁用过扫描将使图片填满整个屏幕并消除黑色边框。

##### 屏幕消隐
启用或禁用屏幕消隐。

##### VNC分辨率
定义要使用的视频分辨率 无头的 设置。

##### 合成的
启用或禁用复合视频。

##### 4Kp60 HDMI
启用或禁用 HDMI 输出的 4Kp60 分辨率。

#### 接口选项

启用和禁用各种物理和虚拟接口。

![raspi-interface](https://www.raspberrypi.com/documentation/computers/images/raspi-interface.png)

##### SSH
使用 SSH 启用或禁用对 Raspberry Pi 的远程终端访问。

SSH 允许您从另一台计算机远程访问 Raspberry Pi 的命令行。默认情况下禁用 SSH。阅读有关使用 SSH 的更多信息SSH 文档页面。如果将 Raspberry Pi 直接连接到公共网络，则不应启用 SSH，除非您已为所有用户设置安全密码。

##### 虚拟网络控制器
启用或禁用 WayVNC 或 RealVNC 虚拟网络计算服务器。

##### SPI
启用或禁用 SPI 接口以及自动加载 SPI 内核模块。

##### I2C
启用或禁用 I2C 接口以及 I2C 内核模块的自动加载。

##### 串行端口
启用或禁用串行连接上的 shell 和内核消息。

##### 1线
启用或禁用 Dallas 1-wire 接口，通常用于 DS18B20 温度传感器。

##### 远程GPIO
启用或禁用对 GPIO 引脚的远程访问。

#### 性能选项

![raspi-perf](https://www.raspberrypi.com/documentation/computers/images/raspi-perf.png)

##### 超频
如果您的 Raspberry Pi 型号允许，请对 CPU 进行超频。即使在同一型号中，各个 Raspberry Pi 设备的超频潜力也有所不同。超频过高可能会导致不稳定。

> 警告
> 超频可能会缩短 Raspberry Pi 的使用寿命。 如果超频达到一定程度会导致系统不稳定，请尝试更适度的超频。按住转移 启动时按 键可暂时禁用超频。

##### GPU显存
更改 GPU 可用的内存量。

##### 覆盖文件系统
启用或禁用只读文件系统。

##### 风扇
自定义 GPIO 连接的行为 Raspberry Pi 4 机箱风扇。不影响粉丝Raspberry Pi 5 保护壳 适用于 Raspberry Pi 5 或者 Raspberry Pi 5 主动冷却器，使用特殊的四针风扇接头连接器进行连接。

#### 本地化选项

配置位置和国家/地区相关选项。

![raspi-l18n](https://www.raspberrypi.com/documentation/computers/images/raspi-l18n.png)

##### 语言环境
选择一个区域设置，例如en_GB.UTF-8 UTF-8.

##### 时区
设置您当地的时区，从区域开始，然后选择城市，例如“欧洲/伦敦”。输入一个字母即可跳转到列表中的该字母。

##### 键盘
打开一个菜单，您可以在其中选择键盘布局。更改通常会立即生效，但可能需要重新启动。输入一个字母即可跳转到列表中的该字母。

##### 无线局域网国家
设置无线网络的国家/地区代码。


#### 高级选项

![raspi-adv](https://www.raspberrypi.com/documentation/computers/images/raspi-adv.png)

##### 扩展文件系统
扩展您的操作系统分区以填充整个存储设备，为您提供更多空间用于文件。重新启动您的 Raspberry Pi 以完成此操作。通常，Raspberry Pi 操作系统在首次启动时运行此操作。如果您将操作系统克隆到比原始容量更大的单独存储设备，则此选项会很有用。

> 警告
> 没有确认步骤。选择该选项立即开始分区扩展。

##### 网络接口名称
启用或禁用可预测的网络接口名称。

##### 网络代理设置
配置网络的代理设置。

##### 引导顺序
在 Raspberry Pi 4 及更高版本上，指定在未插入 SD 卡时是从 USB 还是从网络启动。有关更多信息，请参阅引导加载程序配置.

##### 引导加载程序版本
在 Raspberry Pi 4 及更高版本上，切换到最新的启动 ROM 软件。或者，如果最新版本出现问题，您可以恢复为出厂默认设置。

##### 韦兰
在 X11 和 Wayland 后端之间切换。 Raspberry Pi 4 及更高版本默认使用 Wayland；其他型号的Raspberry Pi默认使用X11。

> 笔记
> 要在 Raspberry Pi 4 之前的 Raspberry Pi 型号上使用 Wayland，您还必须添加`wayland=on` 到 `/boot/firmware/cmdline.txt`

##### 音频配置
在 PulseAudio 和 PipeWire 音频后端之间切换。在 Raspberry Pi OS Bookworm 之前，Raspberry Pi OS 使用 PulseAudio。


#### 更新

将此工具更新到最新版本。

#### 关于 raspi 配置

显示描述 `raspi-config`.

#### 结束

退出 `raspi-config`。
如果您所做的更改需要重新启动， `raspi-config` 提示您重新启动。第一次实施更改时，最好重新启动。如果您选择调整 SD 卡大小，重新启动可能需要比平时更长的时间。

### 非交互式 raspi 配置

这 `raspi-config` 工具还支持非交互式选项和标志，可以完全在命令行上更改选项，而无需可视组件。 Raspberry Pi 型号之间的可用选项可能有所不同。

```bash
sudo raspi-config nonint <command> <arguments> [optional-argument]
```

> 笔记
> 的含义 0 和 1 选项之间有所不同。在将值传递给选项之前，请务必检查文档。


#### 系统选项

##### 无线网络
配置 Wi-Fi SSID 和密码。
```bash
sudo raspi-config nonint do_wifi_ssid_passphrase <ssid> <passphrase> [hidden] [plain]
```
如果需要，请传递无线网络名称 (SSID) 和密码。以下标志是可选的：
这 <hidden> 选项指示 SSID 的可见性。如果网络广播开放 SSID，则通过 0 或省略该选项。如果您的 SSID 被隐藏，请通过 1。默认为 0.

这 <plain> 选项指示您是否打算将密码作为明文传递。如果您的密码包含空格或特殊字符，例如!，你必须通过 0 并在密码周围使用引号。否则，你可以通过1或省略该选项。默认为 1。 要传递此选项，您必须指定一个值<hidden>.

例如，运行以下命令连接到：

非隐藏网络命名 myssid 与密码短语mypassphrase:

```bash
sudo raspi-config nonint do_wifi_ssid_passphrase myssid mypassphrase
```

隐藏网络命名 myssid 与密码短语 mypassphrase:

```bash
sudo raspi-config nonint do_wifi_ssid_passphrase myssid mypassphrase 1
```

非隐藏网络命名 myssid 与密码短语my passphrase:

```bash
sudo raspi-config nonint do_wifi_ssid_passphrase myssid "my passphrase" 0 0
```

##### 声音的
指定音频输出目的地。

```bash
sudo raspi-config nonint do_audio <N>
```
在 Raspberry Pi 4B 上，您可以使用以下选项：
- 0：bcm2835耳机插孔
- 1：vc4-hdmi-0
- 2: vc4-hdmi-1

有关可能的完整列表 <N> 值，请参阅交互中使用的数字 raspi-config 该选项的版本。

##### 密码
更改您的密码。
有关更多信息，请参阅 更改用户密码.
```bash
sudo raspi-config nonint do_change_pass
```

> 笔记
> 即使从 CLI 选项运行，该函数也使用全屏交互界面。

##### 主机名
设置可见 组播DNS 此 Raspberry Pi 在网络上的名称。
```bash
sudo raspi-config nonint do_hostname <hostname>
```

##### 开机/自动登录
选择是否启动到控制台或桌面，以及您的 Raspberry Pi 在开机时是否自动登录到您当前的用户帐户。
```bash
sudo raspi-config nonint do_boot_behaviour <B1/B2/B3/B4>
```
- B1：启动到控制台，需要登录
- B2：启动到控制台，自动登录
- B3：启动到桌面，需要登录
- B4：开机进入桌面，自动登录

##### 启动时网络
等待网络连接，然后再继续启动。

```bash
sudo raspi-config nonint do_boot_wait <0/1>
```
- 0：启动时无需等待网络连接
- 1：等待网络连接后开机

##### 启动画面
启用或禁用启动时显示的启动屏幕。
```bash
sudo raspi-config nonint do_boot_splash <0/1>
```
- 0：启用闪屏
- 1：禁用启动画面

##### 电源指示灯

如果您的 Raspberry Pi 型号允许，请更改电源 LED 的行为。

```bash
sudo raspi-config nonint do_leds <0/1>
```
- 0：用于磁盘活动的闪存
- 1：保持电源 LED 始终亮起

##### 浏览器
更改默认网络浏览器。选择当前未安装的网络浏览器将不起作用。

```bash
sudo raspi-config nonint do_browser <chromium-browser/firefox>
```

#### 显示选项

##### 欠扫描
> 笔记
> 运行 Wayland 时不可用。

如果屏幕上显示的初始文本从边缘消失，请启用过扫描来调整边框。在某些显示器上，尤其是显示器上，禁用过扫描将使图片填满整个屏幕并消除黑色边框。
```bash
sudo raspi-config nonint do_overscan_kms <device> <enabled>
```

设备：
- 1: HDMI-1
- 2: HDMI-2

已启用：
- 0：启用过扫描
- 1：禁用过扫描

##### 屏幕消隐
启用或禁用屏幕消隐。
```bash
sudo raspi-config nonint do_blanking <0/1>
```
- 0：启用屏幕消隐
- 1：禁用屏幕消隐

##### VNC分辨率
定义用于 VNC 的视频分辨率 无头的 设置。
```bash
sudo raspi-config nonint do_vnc_resolution <width>x<height>
```
##### 合成的
启用或禁用复合视频输出。
在树莓派 4 上：
```bash
sudo raspi-config nonint do_pi4video <V1/V2/V3>
```
- V1：启用4Kp60 HDMI输出
- V2：启用复合视频输出
- V3：禁用4Kp60和复合输出

在其他型号上：
```bash
sudo raspi-config nonint do_composite <0/1>
```
- 0：启用复合视频
- 1：禁用复合视频

#### 接口选项

##### SSH
使用 SSH 启用或禁用对 Raspberry Pi 的远程终端访问。
SSH 允许您从另一台计算机远程访问 Raspberry Pi 的命令行。有关 SSH 的更多信息，请参阅 SSH 文档.

```bash
sudo raspi-config nonint do_ssh <0/1>
```
- 0：启用 SSH
- 1：禁用 SSH

##### 虚拟网络控制器
启用或禁用虚拟网络计算 (VNC) 服务器。有关 VNC 的更多信息，请参阅VNC文档.
```bash
sudo raspi-config nonint do_vnc <0/1>
```
- 0：启用VNC
- 1：禁用VNC

##### SPI
启用或禁用 SPI 接口以及自动加载 SPI 内核模块。
```bash
sudo raspi-config nonint do_spi <0/1>
```
- 0：启用SPI
- 1：禁用SPI

##### I2C
启用或禁用 I2C 接口以及 I2C 内核模块的自动加载。
```bash
sudo raspi-config nonint do_i2c <0/1>
```
- 0：启用I2C
- 1：禁用 I2C

##### 串行端口
启用或禁用串行连接硬件。
```bash
sudo raspi-config nonint do_serial_hw <0/1/2>
```

- 0：启用串口
- 1：禁用串口

##### 串行控制台
启用或禁用串行连接上的 shell 和内核消息。
```bash
sudo raspi-config nonint do_serial_cons <0/1/2>
```
- 0：通过串口启用控制台
- 1：禁用串行端口控制台

##### 1线
启用或禁用 Dallas 1-wire 接口。这通常用于 DS18B20 温度传感器。
```bash
sudo raspi-config nonint do_onewire <0/1>
```
- 0：启用1线
- 1：禁用1线

##### 远程GPIO
启用或禁用对 GPIO 引脚的远程访问。
```bash
sudo raspi-config nonint do_rgpio <0/1>
```
- 0：启用远程GPIO
- 1：禁用远程GPIO

#### 性能选项

##### 超频
如果您的 Raspberry Pi 型号允许，请对 CPU 进行超频。即使在同一型号中，各个 Raspberry Pi 设备的超频潜力也有所不同。超频过高可能会导致不稳定。

> 警告
> 超频可能会缩短 Raspberry Pi 的使用寿命。 如果超频达到一定程度会导致系统不稳定，请尝试更适度的超频。按住 【转移】 启动时按 键可暂时禁用超频。

```bash
sudo raspi-config nonint do_overclock <setting>
```
该命令接受以下内容 <setting> 价值观：
- None：不超频（默认）
- Modest：超频至最大值的 50%
- Medium：超频至最大值的 75%
- High：超频至最大值的 100%
- Turbo：超频至最大值的 125%

##### GPU显存
更改 GPU 可用的内存量。
```bash
sudo raspi-config nonint do_memory_split <megabytes>
```

##### 覆盖文件系统
启用或禁用只读文件系统。
```bash
sudo raspi-config nonint do_overlayfs <0/1>
```
- 0：启用覆盖文件系统
- 1: 禁用覆盖文件系统

##### 风扇
自定义 GPIO 连接的行为 Raspberry Pi 4 机箱风扇。不影响粉丝Raspberry Pi 5 保护壳 适用于 Raspberry Pi 5 或者 Raspberry Pi 5 主动冷却器，使用特殊的四针风扇接头连接器进行连接。
```bash
sudo raspi-config nonint do_fan <0/1> [gpio] [onTemp]
```
- 0：启用风扇
- 1：禁用风扇

gpio 默认为14.
onTemp 默认为 80 摄氏度.

#### 本地化选项

##### 语言环境
选择一个区域设置，例如 en_GB.UTF-8 UTF-8.
```bash
sudo raspi-config nonint do_change_locale <locale>
```
有关可能的完整列表 `<locale>` 值，请参阅交互中使用的缩写 `raspi-config` 该选项的版本。

##### 时区
设置您当地的时区，从区域开始，然后选择城市，例如“欧洲/伦敦”。
```bash
sudo raspi-config nonint do_change_timezone <timezone>
```
有关可能的完整列表 `<timezone>` 值，请参阅交互中使用的缩写 `raspi-config` 该选项的版本。

##### 键盘
设置键盘布局。更改通常会立即生效，但可能需要重新启动。
```bash
sudo raspi-config nonint do_configure_keyboard <keymap>
```
有关可能的完整列表 `<keymap>` 值，请参阅交互中使用的缩写 `raspi-config` 该选项的版本。

##### 无线局域网国家
设置您的无线网络的国家代码。
```bash
sudo raspi-config nonint do_wifi_country <country>
```
有关可能的完整列表 `<country>` 值，请参阅交互中使用的缩写 `raspi-config` 该选项的版本。

#### 高级选项

##### 扩展文件系统
扩展操作系统分区以填充整个存储设备，为您提供更多空间用于文件。重新启动 Raspberry Pi 以完成此操作。通常，Raspberry Pi 操作系统在首次启动时运行此操作。如果您将操作系统克隆到比原始容量更大的单独存储设备，则此选项会很有用。

> 警告
> 没有确认步骤。选择该选项立即开始分区扩展。

```bash
sudo raspi-config nonint do_expand_rootfs
```

##### 网络接口名称
启用或禁用可预测的网络接口名称。
```bash
sudo raspi-config nonint do_net_names <0/1>
```
- 0：启用可预测的网络接口名称
- 1：禁用可预测的网络接口名称

##### 网络代理设置
配置网络的代理设置。
```bash
sudo raspi-config nonint do_proxy <SCHEMES> <ADDRESS>
```

##### 引导顺序
在 Raspberry Pi 4 及更高版本上，指定在未插入 SD 卡时是从 USB 还是从网络启动。请参阅 引导加载程序配置 部分了解更多信息。
```bash
sudo raspi-config nonint do_boot_order <B1/B2/B3>
```
根据您的设备，您可以从以下选项中进行选择：
- B1：SD 卡启动 - 从 SD 卡启动（如果可用），否则从 NVMe 启动，否则从 USB 启动
- B2：NVMe/USB 启动 - 从 NVMe 启动（如果可用），否则从 USB 启动（如果可用），否则从 SD 卡启动
- B3：网络启动-从SD卡启动 如果插入，否则从网络启动

##### 引导加载程序版本
在 Raspberry Pi 4 及更高版本上，切换到最新的启动 ROM 软件。或者，如果最新版本出现问题，您可以恢复为出厂默认设置。
```bash
sudo raspi-config nonint do_boot_rom <E1/E2>
```
- E1：使用最新的启动ROM
- E2：使用出厂默认值

##### 韦兰
在 X11 和 Wayland 后端之间切换。 Raspberry Pi 4 及更高版本默认使用 Wayland；其他型号的Raspberry Pi默认使用X11。
```bash
sudo raspi-config nonint do_wayland <W1/W2>
```
- W1：使用X11后端
- W2：使用 Wayland 后端

> 笔记
> 要在 Raspberry Pi 4 之前的 Raspberry Pi 型号上使用 Wayland，您还必须添加 `wayland=on` 到 `/boot/firmware/cmdline.txt`.

##### 音频配置
使用此选项可在 PulseAudio 和 PipeWire 音频后端之间切换。在 Raspberry Pi OS Bookworm 之前，Raspberry Pi OS 使用 PulseAudio。

```bash
sudo raspi-config nonint do_audioconf <1/2>
```
- 1：使用 PulseAudio 后端
- 2：使用 PipeWire 后端

#### 更新

将此工具更新到最新版本。

```bash
sudo raspi-config nonint do_update
```

### 配置网络

Raspberry Pi OS 提供了用于设置无线连接的图形用户界面 (GUI)。 Raspberry Pi OS Lite 和无头机器的用户可以通过命令行设置无线网络 nmcli.

> 笔记
> Network Manager是Raspberry Pi OS下默认的网络配置工具 书呆子 或稍后。虽然网络管理器可以使用以下方式安装在早期版本的操作系统上apt并使用配置为默认值 raspi-config，使用早期版本 dhcpd 以及默认的其他网络配置工具。

#### 使用桌面

通过菜单栏右侧的网络图标访问网络管理器。如果您使用的是具有内置无线连接功能的 Raspberry Pi，或者已插入无线适配器，请单击此图标以显示可用无线网络的列表。如果您看到消息“未找到 AP - 扫描...​”，请等待几秒钟，网络管理器应该会找到您的网络。

> 笔记
> 支持双频无线的 Raspberry Pi 设备（Raspberry Pi 3B+、Raspberry Pi 4、Compute Module 4、Raspberry Pi 400 和 Raspberry Pi 5）会自动禁用网络，直到您分配无线 LAN 国家/地区。要设置无线 LAN 国家/地区，请从“首选项”菜单中打开“Raspberry Pi 配置”应用程序，然后选择 本土化 并从菜单中选择您所在的国家/地区。


![wifi2](https://www.raspberrypi.com/documentation/computers/images/wifi2.png)

右侧的图标显示网络是否安全，并指示信号强度。单击您要连接的网络。如果网络是安全的，则会出现一个对话框提示您输入网络密钥：

![key](https://www.raspberrypi.com/documentation/computers/images/key.png)

输入密钥并单击 好的，然后等待几秒钟。网络图标将短暂闪烁，表明正在建立连接。连接后，图标将停止闪烁并显示信号强度。

##### 连接到隐藏网络

如果您想使用隐藏网络，请使用 高级选项 > 连接到隐藏的 Wi-Fi 网络 在网络菜单中：

![network-hidden](https://www.raspberrypi.com/documentation/computers/images/network-hidden.png)

然后，输入隐藏网络的 SSID。询问您的网络管理员您的网络使用哪种类型的安全性；虽然大多数家庭网络目前使用 WPA 和 WPA2 个人安全性，但公共网络有时使用 WPA 和 WPA2 企业安全性。选择您的网络的安全类型，然后输入您的凭据：

![network-hidden-authentication](https://www.raspberrypi.com/documentation/computers/images/network-hidden-authentication.png)

点击 连接 按钮启动网络连接。

#### 使用命令行

本指南将帮助您从终端配置 Raspberry Pi 上的无线连接，而无需使用图形工具。不需要额外的软件。

> 笔记
> 本指南应适用于 WEP、WPA、WPA2 或 WPA3 网络，但可能不适用于企业网络。

##### 启用无线网络
在全新安装时，您必须指定您使用设备所在的国家/地区。这允许您的设备为 5GHz 网络选择正确的频段。一旦指定了无线 LAN 国家/地区，您就可以使用 Raspberry Pi 的内置无线网络模块。

为此，请使用命令行设置您的无线 LAN 国家/地区 `raspi-config` 工具。运行以下命令：
```bash
sudo raspi-config
```

选择 【本地化选项】 使用箭头键的菜单项。选择【无线局域网国家】选项。 使用箭头键从下拉列表中选择您所在的国家/地区。按Enter选择您所在的国家/地区。

您现在应该可以访问无线网络。运行以下命令检查您的 Wi-Fi 无线电是否已启用：

```bash
nmcli radio wifi
```
如果此命令返回文本“已启用”，则您已准备好配置连接。如果此命令返回“已禁用”，请尝试使用以下命令启用 Wi-Fi：

```bash
nmcli radio wifi on
```

##### 查找网络
要扫描无线网络，请运行以下命令：

```bash
nmcli dev wifi list
```
您应该看到类似于以下内容的输出：

```bash
IN-USE  BSSID              SSID            MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
        90:72:40:1B:42:05  myNetwork       Infra  132   405 Mbit/s  89      ****  WPA2
        90:72:42:1B:78:04  myNetwork5G     Infra  11    195 Mbit/s  79      ***   WPA2
        9C:AB:F8:88:EB:0D  Pi Towers       Infra  1     260 Mbit/s  75      ***   WPA2 802.1X
        B4:2A:0E:64:BD:BE  Example         Infra  6     195 Mbit/s  37      **    WPA1 WPA2
```

在“SSID”列中查找您要连接的网络的名称。使用 SSID 和密码连接到网络。

##### 连接到网络

运行以下命令配置网络连接：
```bash
sudo nmcli --ask dev wifi connect <example_ssid>
```

别忘了更换 <example_ssid> 与您尝试配置的网络的名称。

出现提示时输入您的网络密码。

输入密码后，您的 Raspberry Pi 应该会自动连接到网络。如果您看到以下输出：

```bash
Error: Connection activation failed: Secrets were required, but not provided.
```

这意味着您输入了错误的密码。如果您看到此错误，请再次运行上述命令，并小心输入正确的密码。
要检查您是否已连接到网络，请运行以下命令：

```bash
nmcli dev wifi list
```

您应该看到类似于以下内容的输出：

```bash
IN-USE  BSSID              SSID            MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
*       90:72:40:1B:42:05  myNetwork       Infra  132   405 Mbit/s  89      ****  WPA2
        90:72:42:1B:78:04  myNetwork5G     Infra  11    195 Mbit/s  79      ***   WPA2
        9C:AB:F8:88:EB:0D  Pi Towers       Infra  1     260 Mbit/s  75      ***   WPA2 802.1X
        B4:2A:0E:64:BD:BE  Example         Infra  6     195 Mbit/s  37      **    WPA1 WPA2
```

检查是否有星号 (*) 在“使用中”栏中；它应该与您要连接的网络的 SSID 出现在同一行。

> 笔记
> 您可以在中手动编辑连接配置/etc/NetworkManager/system-connections/目录。

##### 连接到不安全的网络

如果您连接的网络不使用密码，请运行以下命令：

```bash
sudo nmcli dev wifi connect <example_ssid>
```

> 警告
> 使用不安全的无线网络时请小心。

##### 连接到隐藏网络
如果您使用隐藏网络，请在运行时将“隐藏”选项指定为“yes”nmcli:

```bash
sudo nmcli --ask dev wifi connect <example_ssid> hidden yes
```

##### 设置多个网络之间的优先级
如果您的设备同时检测到多个已知网络，它可能会连接任何检测到的已知网络。使用优先级选项强制您的 Raspberry Pi 优先选择某些网络。您的设备将连接到范围内具有最高优先级的网络。执行以下命令查看已知网络的优先级：

```bash
nmcli --fields autoconnect-priority,name connection
```

您应该看到类似于以下内容的输出：

```bash
AUTOCONNECT-PRIORITY  NAME
0                     myNetwork
0                     lo
0                     Pi Towers
0                     Example
-999                  Wired connection 1
```

使用 nmcli connection modify 用于设置网络优先级的命令。 以下示例命令将名为“Pi Towers”的网络的优先级设置为 10:

```bash
nmcli connection modify "Pi Towers" connection.autoconnect-priority 10
```

您的设备将始终尝试连接到具有最高非负优先级值的范围内网络。您还可以为网络分配负优先级；如果范围内没有其他已知网络，您的设备只会尝试连接到负优先级网络。例如，考虑三个网络：

```bash
AUTOCONNECT-PRIORITY  NAME
-1                    snake
0                     rabbit
1                     cat
1000                  dog
```

- 如果所有这些网络都在范围内，您的设备将首先尝试连接到“dog”网络。
- 如果与“dog”网络的连接失败，您的设备将尝试连接“cat”网络。
- 如果与“cat”网络的连接失败，您的设备将尝试连接“rabbit”网络。
- 如果与“兔子”网络的连接失败，并且您的设备未检测到其他已知网络，您的设备将尝试连接到“蛇”网络。


#### 配置DHCP

默认情况下，Raspberry Pi OS 尝试通过 DHCP 自动配置所有网络接口，如果 DHCP 失败，则回退到 169.254.0.0/16 范围内的自动专用地址。


#### 分配静态IP

要为 Raspberry Pi 分配静态 IP 地址，请在路由器上为其保留一个地址。您的 Raspberry Pi 将继续通过 DHCP 分配其地址，但每次都会收到相同的地址。通过将 Raspberry Pi 的 MAC 地址与 DHCP 服务器中的静态 IP 地址相关联，可以分配“固定”地址。

### 设置无头 Raspberry Pi

A 无头的 Raspberry Pi 无需显示器、键盘或鼠标即可运行。要无头运行 Raspberry Pi，您需要一种从另一台计算机访问它的方法。要远程访问 Raspberry Pi，您需要将 Raspberry Pi 连接到网络，以及通过该网络访问 Raspberry Pi 的方法。

要将 Raspberry Pi 连接到网络，您可以通过以太网将设备插入有线连接或配置无线网络。

要通过该网络访问 Raspberry Pi，请使用 SSH。通过 SSH 连接后，您可以使用 raspi-config 到 启用VNC 如果您更喜欢图形桌面环境。

如果您要从头开始设置 Raspberry Pi，请在设置过程中设置无线网络和 SSH 成像过程。如果您已经设置了 Raspberry Pi，则可以使用以下命令配置 SSHraspi-config.

> 警告
> 根据 Raspberry Pi 的型号和您使用的 SD 卡类型，您的 Raspberry Pi 首次启动时可能需要长达五分钟的时间来启动并连接到无线网络。

#### 连接到有线网络

要在首次启动时连接到有线网络，请通过以太网插入无头 Raspberry Pi，或者如果您的 Raspberry Pi 型号不包含以太网端口，则使用以太网适配器。您的 Raspberry Pi 将自动连接到网络。

#### 连接到无线网络

要在无头 Raspberry Pi 中首次启动时配置无线网络访问，请使用 Raspberry Pi Imager 中的高级设置菜单。输入您首选无线网络的 SSID 和密码。您的 Raspberry Pi 将在首次启动时使用这些凭据连接到网络。部分无线适配器和部分Raspberry Pi板不支持5GHz网络；检查无线模块的文档，以确保与您的首选网络兼容。

> 笔记
> 
> 以前版本的 Raspberry Pi OS 使用了 wpa_supplicant.conf 文件可以放置到启动文件夹中以配置无线网络设置。从 Raspberry Pi OS Bookworm 开始，此功能不可用。



#### 远程访问

如果没有键盘或显示器，您需要一种方法 远程控制 你的无头树莓派。首次启动时，唯一的选项是 SSH。要在全新安装的 Raspberry Pi OS 上启用 SSH，请选择以下方法之一：

- 在 Raspberry Pi Imager 的操作系统自定义菜单中启用 SSH，然后输入用户名和密码
- 创建一个名为 `ssh` 文件在SD卡的根目录下，然后手动配置用户 `userconf.txt` 按照下面部分中的说明进行操作

有关更多信息，请参阅 设置 SSH 服务器。通过 SSH 连接后，您可以使用 `raspi-config` 到 启用VNC 如果您更喜欢图形桌面环境。

##### 手动配置用户

在 SD 卡的根目录下，创建一个名为`userconf.txt`.

该文件应包含一行文本，其中包括 `<username>:<password>：`您想要的用户名，紧接着是冒号，紧接着是 加密的 您要使用的密码的表示形式。

> 笔记
> 
> `<username>` 只能包含小写字母、数字和连字符，并且必须以字母开头。不得超过 31 个字符。

要生成加密密码，请使用 开放式SSL 在另一台计算机上。打开终端并输入以下内容：

```bash
openssl passwd -6
```


### 在 Raspberry Pi 上托管无线网络

您的 Raspberry Pi 可以使用无线模块托管自己的无线网络。如果您通过以太网端口（或第二个无线模块）将 Raspberry Pi 连接到互联网，则连接到无线网络的其他设备可以通过您的 Raspberry Pi 访问互联网。

考虑使用以下方式的有线网络 10.x.x.x IP 块。您可以将 Raspberry Pi 连接到该网络，并在使用另一个 IP 块的单独网络上为无线客户端提供服务，例如 192.168.x.x.

在下图中，请注意笔记本电脑存在于与路由器和有线客户端分开的 IP 块中：

![host-a-network](https://www.raspberrypi.com/documentation/computers/images/host-a-network.png)

通过此网络配置，无线客户端都可以通过 Raspberry Pi 路由器相互通信。但无线网络上的客户端无法直接与树莓派以外的有线网络上的客户端交互；无线客户端存在于与服务有线客户端的网络分开的专用网络中。

> 笔记
> 
> Raspberry Pi 5、4、3 和 Raspberry Pi Zero W 可以使用内置无线模块托管无线网络。缺少内置模块的 Raspberry Pi 型号使用单独的无线适配器支持此功能。


#### 启用热点

要在命令行上创建托管无线网络，请运行以下命令，将 `<example-network-name>` 和 `<example-password>` 具有您自己的值的占位符：

```sh
sudo nmcli device wifi hotspot ssid <example-network-name> password <example-password>
```

使用另一个无线客户端（例如笔记本电脑或智能手机）连接到网络。查找 SSID 匹配的网络`<example-network-name>`。输入您的网络密码，您应该可以成功连接到网络。如果您的 Raspberry Pi 通过以太网连接或第二个无线适配器可以访问互联网，您应该能够访问互联网。

#### 禁用热点

要禁用热点网络并恢复使用 Pi 作为无线客户端，请运行以下命令：
```sh
sudo nmcli device disconnect wlan0
```

禁用网络后，运行以下命令重新连接到另一个 Wi-Fi 网络：
```sh
sudo nmcli device up wlan0
```

> 提示
> 
> 有关连接到无线网络的更多信息，请参阅 配置网络.

#### 使用 Raspberry Pi 作为网桥

默认情况下，Raspberry Pi 托管的无线网络与通过以太网连接的父网络分开存在。在这种安排中，连接到父网络的设备无法直接与连接到 Raspberry Pi 托管的无线网络的设备进行通信。如果您希望连接的无线设备能够与父网络上的设备进行通信，您可以将 Raspberry Pi 配置为网桥。网桥就位后，连接到 Pi 托管无线网络的每个设备都会在父网络中分配一个 IP 地址。

在下图中，请注意笔记本电脑与路由器和有线客户端位于同一 IP 块中：

![bridge-network](https://www.raspberrypi.com/documentation/computers/images/bridge-network.png)

以下步骤描述了如何在 Raspberry Pi 上设置网桥以实现无线客户端与父网络之间的通信。

首先创建网桥接口：

```sh
sudo nmcli connection add type bridge con-name 'Bridge' ifname bridge0
```

接下来，将设备与父网络的以太网连接添加到网桥：

```sh
sudo nmcli connection add type ethernet slave-type bridge \
    con-name 'Ethernet' ifname eth0 master bridge0
```

最后，将您的无线热点连接添加到网桥。您可以添加现有热点接口或创建新热点接口：

如果您已使用上述说明创建了无线热点连接，请使用以下命令将现有接口添加到网桥：

```sh
sudo nmcli connection modify 'Hotspot' master bridge0

```
如果您尚未创建无线热点连接，请创建一个新接口并使用单个命令将其添加到网桥，替换`<hotspot-password>`带有您选择的密码的占位符：

```sh
sudo nmcli connection add con-name 'Hotspot' \
    ifname wlan0 type wifi slave-type bridge master bridge0 \
    wifi.mode ap wifi.ssid Hotspot wifi-sec.key-mgmt wpa-psk \
    wifi-sec.proto rsn wifi-sec.pairwise ccmp \
    wifi-sec.psk <hotspot-password>
```

现在您已经配置了网桥，是时候激活它了。运行以下命令来激活网桥：
```sh
sudo nmcli connection up Bridge
```

并运行以下命令开始托管您的无线网络：
```sh
sudo nmcli connection up Hotspot
```

您可以使用 nmcli device 命令验证网桥、以太网接口和无线热点接口是否均处于活动状态。

> 提示
> 使用诸如 arp 扫描 检查连接到热点后是否可以访问父网络上的设备。


### 使用代理服务器

如果您希望 Raspberry Pi 通过代理服务器（可能来自学校或其他工作场所）访问互联网，则需要将 Raspberry Pi 配置为使用该服务器，然后才能上网。

你会需要：
- 代理服务器的 IP 地址或主机名和端口
- 您的代理的用户名和密码（如果需要）



#### 配置你的树莓派


配置你的树莓派
您需要设置三个环境变量（http_proxy, https_proxy， 和 no_proxy）这样你的 Raspberry Pi 就知道如何访问代理服务器。

打开终端窗口，然后打开文件 `/etc/environment` 使用纳米：
```sh
sudo nano /etc/environment
```
将以下内容添加到 `/etc/environment` 文件来创建 `http_proxy` 多变的：

```sh
export http_proxy="http://proxyipaddress:proxyport"
```

代替 proxyipaddress 和 proxyport 与您的代理的 IP 地址和端口。

> 笔记
> 如果您的代理需要用户名和密码，请使用以下格式添加它们：

```sh
export http_proxy="http://username:password@proxyipaddress:proxyport"
```

为环境变量输入相同的信息https_proxy:
```sh
export https_proxy="http://username:password@proxyipaddress:proxyport"
```

创建 no_proxy 环境变量，它是一个以逗号分隔的地址列表，您的 Raspberry Pi 不应使用代理：
```sh
export no_proxy="localhost, 127.0.0.1"
```

你的 /etc/environment 文件现在应该如下所示：
```sh
export http_proxy="http://username:password@proxyipaddress:proxyport"
export https_proxy="http://username:password@proxyipaddress:proxyport"
export no_proxy="localhost, 127.0.0.1"
```

![proxy-environment-variables](https://www.raspberrypi.com/documentation/computers/images/proxy-environment-variables.png)

按 Ctrl + X 保存并退出。


#### 更新 sudoers 文件

为了运行作为 sudo （例如下载和安装软件）要使用新的环境变量，您需要更新sudoers.

使用以下命令打开sudoers:

```sh
sudo visudo
```

将以下行添加到文件中，以便 sudo 将使用您刚刚创建的环境变量：

```sh
Defaults	env_keep+="http_proxy https_proxy no_proxy"
```

![proxy-edit-sudoers](https://www.raspberrypi.com/documentation/computers/images/proxy-edit-sudoers.png)

#### 重新启动你的树莓派

重新启动您的 Raspberry Pi 以使更改生效。您现在应该能够通过代理服务器访问互联网。

### HDMI配置

在绝大多数情况下，使用标准 HDMI 电缆将 Raspberry Pi 插入配备 HDMI 的显示器，即可自动使用显示器可以支持的最佳分辨率。 Raspberry Pi Zero、Zero W 和 Zero 2 W 使用迷你 HDMI 端口，因此您需要迷你 HDMI 到全尺寸 HDMI 导线或适配器。 Raspberry Pi 4、Raspberry Pi 5 和 Raspberry Pi 400 上有两个微型 HDMI 端口，因此您需要为每个要连接的显示器配备微型 HDMI 到全尺寸 HDMI 导线或适配器。在打开 Raspberry Pi 之前连接电缆。

Raspberry Pi 4 和 400 最多可驱动两个显示器，在 60Hz 刷新率下分辨率高达 1080p。在 4K 分辨率下，如果连接两个显示器，则刷新率仅限于 30Hz。您还可以以 60Hz 刷新率以 4K 驱动单个显示器：这要求将显示器连接到与 USB-C 电源输入（标记为 HDMI0）相邻的 HDMI 端口。要在 Raspberry Pi 4 和 400 上启用 4Kp60 输出，请设置 `hdmi_enable_4kp60=1` 标记在 `/boot/firmware/config.txt`.

Raspberry Pi 5 可以以 60hz 刷新率驱动最多两个 4K 分辨率的显示器，无需额外配置。
屏幕配置工具（arandr) 是一个用于选择显示模式和设置多个显示的图形工具。您可以在“桌面首选项”菜单中找到此工具。使用布局菜单选项选择屏幕、分辨率和方向。如果您使用多屏幕设置，请将显示器拖动到所需的任何位置。单击“应用”按钮应用设置。

### 设置显示器的分辨率和旋转

如果您发现 Raspberry Pi 可能无法确定最佳模式，或者您特别希望设置非默认分辨率，则可以手动设置分辨率或旋转。执行此操作的方法取决于您是引导到桌面环境还是引导到 CLI（文本控制台）。

#### 设置桌面环境分辨率和旋转

如果您使用的是 Raspberry Pi 桌面，则可以通过选择最轻松地更改分辨率或旋转 Screen Configuration 从桌面实用程序 Preferences 菜单。这将显示连接到 Raspberry Pi 的一个或多个显示器的图形表示。右键单击要修改的显示，然后选择所需的选项，然后单击Apply.

> 笔记
> 如果您使用的是 X11 后端，则需要确保关闭屏幕配置实用程序才能保存所做的更改。如果您不这样做，您所做的更改将在重新启动时被忘记。

也可以通过编辑配置文件来更改这些设置，尽管执行此操作的方法取决于您运行的是 Wayland 还是 X11 后端。打开终端窗口并输入：

```sh
ps ax | grep [w]ayfire
```

如果你看到 /usr/bin/wayfire 显示则您正在运行 Wayland；如果没有输出，则说明您正在运行 X11。

> 笔记
> 在当前版本的 Raspberry Pi OS Bookworm 中，Raspberry Pi 5、Raspberry Pi 4 和 Raspberry Pi 400 默认使用 Wayland 显示桌面环境。早期型号的 Raspberry Pi 默认使用 X11 显示桌面环境。


##### 手动设置 Wayland 的桌面环境分辨率和旋转

在 Wayland 下，您可以通过编辑来设置自定义显示分辨率 .config/wayfire.ini 文件在你的主目录中。您需要编辑现有的 `[output:<device>]` 部分，或添加新的 `[output:<device>]` 您的显示设备部分（如果不存在）。例如：

```sh
[output:HDMI-A-1]
mode = 1920x1080@60
```
这 <device> 的一部分 output: 线 （HDMI-A-1 在此显示的示例中）与显示选项匹配 为 KMS 描述.

这 mode 线是 相似的 与 KMS 使用的相同，但略有不同。咨询 Wayfire 文档 以获得更广泛的信息。

您还可以通过添加 transform 线如：

```sh
[output:HDMI-A-1]
mode = 1920x1080@60
transform = 270
```

哪里允许 transform 选项有： normal, 90, 180 和270.

如果您已将 Raspberry Pi 操作系统设置为启动到桌面，但 不是 使用自动登录，那么您还需要编辑 `/usr/share/greeter.ini`，它决定登录屏幕使用的分辨率和旋转。该文件的格式与 .`config/wayfire.ini` 前面已经描述过，所以您再次需要添加或编辑 `[output:<device>]` 部分。

#### 设置文件控制台分辨率和旋转

这是通过编辑 KMS 设置来实现的 - 请参阅 配置内核命令行 更多细节。

> 笔记
> 如果连接了多个屏幕，则必须在控制台模式下将它们全部设置为相同的旋转值，否则将不会应用旋转。

### 音频配置

Raspberry Pi 具有多达三种音频输出模式：HDMI 1 和 2，以及耳机插孔。您可以随时在这些模式之间切换。

> 笔记
> 通过 HDMI 进行音频输出将比通过耳机插孔进行音频输出提供更好的音质。

如果您的 HDMI 显示器或电视具有内置扬声器，则可以通过 HDMI 线缆播放音频，但您可以将其切换到一组耳机或插入耳机插孔的其他扬声器。如果您的显示器具有集成扬声器，则默认情况下通过 HDMI 输出音频。否则，将通过耳机插孔播放。如果这不是您想要的输出设置，或者自动检测不准确，您可以手动切换输出。

#### 更改音频输出

设置音频输出有两种方法：使用桌面音量控制，或使用 `raspi-config` 命令行工具。

##### 桌面音量控制
右键单击桌面任务栏上的音量图标会弹出音频输出选择器，允许您在内部音频输出之间进行选择。它还允许您选择任何外部音频设备，例如 USB 声卡和蓝牙音频设备。当前选定的音频输出设备上会显示一个勾号。在弹出菜单中左键单击所需的输出以更改此设置。

##### 专业音频配置文件
查看系统托盘上的音频设备时，您可能会看到名为 Pro Audio 的设备配置文件。此配置文件公开了每个音频设备的最大通道数，使您可以更好地控制信号路由。除非您对此类控制有特定的用例，否则我们建议使用不同的设备配置文件。
有关专业音频配置文件的更多信息，请访问 PipeWire 的常见问题解答.

##### 使用 raspi 配置
打开raspi 配置 通过在命令行中输入以下内容：

```sh
sudo raspi-config
```
这将打开配置屏幕：

选择 System options （当前为选项 1，但您的可能不同）并按 Enter.

现在选择 Audio 选项（当前选项 S2，但您的可能不同）并按 Enter.

选择您需要的模式，按 Enter 然后按向右箭头键退出选项列表，然后选择 Finish 退出配置工具。

### 外部存储配置

您可以将外部硬盘、SSD 或 USB 记忆棒连接到 Raspberry Pi 上的任何 USB 端口，并挂载文件系统以访问存储在其中的数据。

默认情况下，您的 Raspberry Pi 会自动挂载一些流行的文件系统，例如 FAT、NTFS 和 HFS+ `/media/pi/<HARD-DRIVE-LABEL>` 地点。

> 笔记
> Raspberry Pi OS Lite 不实现自动挂载。

要设置存储设备以使其始终安装到您选择的特定位置，您必须手动安装它。

#### 安装存储设备

您可以将存储设备安装在特定文件夹位置。按照惯例，在 /mnt 文件夹，例如 /mnt/mydisk。请注意，该文件夹必须为空。

将存储设备插入Raspberry Pi上的USB端口，然后使用以下命令列出Raspberry Pi上的所有磁盘分区：
```sh
sudo lsblk -o UUID,NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL,MODEL
```

Raspberry Pi 使用挂载点 / 和 `/boot/firmware/`。您的存储设备以及任何其他连接的存储将显示在此列表中。

使用 SIZE、LABEL 和 MODEL 列来标识指向存储设备的磁盘分区的名称。例如，sda1. FSTYPE 列包含文件系统类型。如果您的存储设备使用 exFAT 文件系统，请安装 exFAT 驱动程序：

```sh
sudo apt update
sudo apt install exfat-fuse
```

如果您的存储设备使用 NTFS 文件系统，您将对其具有只读访问权限。如果要写入设备，可以安装 ntfs-3g 驱动程序：

```sh
sudo apt update
sudo apt install ntfs-3g
```

运行以下命令获取磁盘分区的位置：

```sh
sudo blkid
```
例如，/dev/sda1.

创建目标文件夹作为存储设备的挂载点。 本例中使用的挂载点名称为 mydisk。您可以指定您选择的名称：

```sh
sudo mkdir /mnt/mydisk
```

将存储设备挂载到您创建的挂载点：

```sh
sudo mount /dev/sda1 /mnt/mydisk
```

通过列出内容来验证存储设备是否已成功安装：

```sh
ls /mnt/mydisk
```

#### 设置自动安装

您可以修改 fstab 文件来定义 Raspberry Pi 启动时自动安装存储设备的位置。在里面fstab文件中，磁盘分区由通用唯一标识符 (UUID) 标识。

获取磁盘分区的UUID：
```sh
sudo blkid
```

从列表中找到磁盘分区并记下 UUID。 （例如， 5C24-1453.) 使用命令行编辑器（例如 nano）打开 fstab 文件：

```sh
sudo nano /etc/fstab
```

在中添加以下行 fstab 文件：
```sh
UUID=5C24-1453 /mnt/mydisk fstype defaults,auto,users,rw,nofail 0 0
```
代替 fstype 与您在执行上述步骤时找到的文件系统类型，例如：ntfs.

如果文件系统类型是 FAT 或 NTFS，请添加 ,umask=000 之后立马 nofail - 这将允许所有用户对存储设备上的每个文件进行完全读/写访问。

现在您已经设置了一个条目 fstab，您可以在连接或不连接存储设备的情况下启动 Raspberry Pi。在拔下设备之前，您必须关闭 Raspberry Pi，或手动卸载它。

> 笔记
> 如果树莓派启动时没有连接存储设备，则启动时间将额外延长 90 秒。您可以通过添加来缩短此时间,x-systemd.device-timeout=30之后立马 nofail。这会将超时更改为 30 秒，这意味着系统在放弃尝试挂载磁盘之前只会等待 30 秒。

有关每个 Linux 命令的更多信息，请参阅特定的手册页，使用man命令。例如，man fstab.

#### 卸载存储设备

当 Raspberry Pi 关闭时，系统会负责卸载存储设备，以便安全地拔出它。如果您想手动卸载设备，可以使用以下命令：
```sh
sudo umount /mnt/mydisk
```
如果您收到“目标正忙”的错误，则表示存储设备未卸载。如果没有显示错误，您现在可以安全地拔掉设备。

##### 处理“目标正忙”

“目标正忙”消息意味着存储设备上有文件正在被程序使用。要关闭文件，请使用以下过程。

关闭存储设备上打开文件的所有程序。如果您打开了终端，请确保您不在存储设备安装的文件夹或其子文件夹中。

如果仍然无法卸载存储设备，您可以使用 lsof 用于检查哪个程序在设备上打开了文件的工具。您需要先安装 lsof 使用apt:

```sh
sudo apt update
sudo apt install lsof
```
要使用 lsof：
```sh
lsof /mnt/mydisk
```

### 本地化您的 Raspberry Pi

您可以设置 Raspberry Pi 以匹配您的区域设置。语言、键盘布局和时区都可以使用更改raspi-config工具。

### 更改默认引脚配置

> 笔记
> 已弃用通过用户提供的设备树 blob 进行的自定义默认引脚配置。

#### 启动序列期间的设备引脚

在启动序列期间，GPIO 引脚会执行各种操作。

- 上电 - 引脚默认为具有默认拉力的输入，这在 数据表
- 通过bootrom设置
- 设置方式bootcode.bin
- 设置方式 dt-blob.bin （这一页）
- 设置由 GPIO命令 在config.txt
- 附加固件引脚（例如 UARTS）
- 内核/设备树

在软重置时，适用相同的过程，但默认拉动除外，默认拉动仅适用于加电重置。

完成该过程可能需要几秒钟。在此期间，GPIO 引脚可能不会处于所连接的外设所期望的状态（如中所定义）dt-blob.bin或者 config.txt）。由于不同的 GPIO 引脚有不同的默认拉力，您应该这样做以下之一 对于您的外设：

- 选择一个 GPIO 引脚，该引脚在复位时默认根据外设的需要拉动
- 延迟外设的启动，直到操作完成
- 添加适当的上拉/下拉电阻

#### 提供自定义设备树 blob

为了编译设备树源（.dts）文件写入设备树 blob（.dtb）文件，设备树编译器必须通过运行来安装sudo apt install device-tree-compiler。这 dtc 然后可以按如下方式使用命令：
```sh
sudo dtc -I dts -O dtb -o /boot/firmware/dt-blob.bin dt-blob.dts
```
同样，一个 .dtb 文件可以转换回 .dts 文件（如果需要）。
```sh
dtc -I dtb -O dts -o dt-blob.dts /boot/firmware/dt-blob.bin
```

#### dt-blod 的部分

这 dt-blob.bin 用于在启动时配置二进制 blob (VideoCore)。 Linux 内核当前未使用它。 dt-blob 可以配置所有版本的 Raspberry Pi（包括计算模块）以使用替代设置。以下部分在 dt-blob 中有效：

##### videocore
此部分包含所有 VideoCore blob 信息。所有后续部分都必须包含在本部分中。


##### pin_defines
此部分用于将特定 VideoCore 功能设置到特定引脚。这使得用户能够将相机电源启用引脚移动到不同的位置，或者移动 HDMI 热插拔位置：这些是 Linux 无法控制的事情。请参阅下面的示例 DTS 文件。

#### 时钟配置

尽管很难预测结果，但可以通过此接口更改时钟的配置！时钟系统的配置非常复杂。有五个独立的 PLL，每个都有自己的固定（或可变，如果是 PLLC）VCO 频率。每个 VCO 都有多个不同的通道，可以用不同的 VCO 频率划分来设置这些通道。每个时钟目标都可以配置为来自时钟通道之一，尽管源到目标的映射受到限制，因此并非所有通道都可以路由到所有时钟目标。

以下是一些可用于更改特定时钟的示例配置。当提出时钟配置请求时，我们将添加到此资源。

```sh
clock_routing {
   vco@PLLA  {    freq = <1966080000>; };
   chan@APER {    div  = <4>; };
   clock@GPCLK0 { pll = "PLLA"; chan = "APER"; };
};

clock_setup {
   clock@PWM { freq = <2400000>; };
   clock@GPCLK0 { freq = <12288000>; };
   clock@GPCLK1 { freq = <25000000>; };
};
```

以上将 PLLA 设置为运行在 1.96608GHz 的源 VCO（该 VCO 的限制为 600MHz - 2.4GHz），将 APER 通道更改为 /4，并将 GPCLK0 配置为通过 APER 从 PLLA 获取源。这用于为音频编解码器提供产生 48000 个频率范围所需的 12288000Hz。

#### 示例设备树源文件

固件存储库包含 掌握 Raspberry Pi blob 其他的通常都是从中衍生出来的。

### 设备树、覆盖层和参数

Raspberry Pi 内核和固件使用设备树 (DT) 来描述 Raspberry Pi 上存在的硬件。这些设备树可能包括 DT 参数，这些参数提供对某些板载功能的一定程度的控制。 DT 覆盖允许描述和配置可选的外部硬件，并且它们还支持用于更多控制的参数。

固件加载器（start.elf 及其变体）负责加载 DTB（设备树 Blob - 机器可读的 DT 文件）。它根据板版本号选择加载哪一个，并进行修改以进一步定制它。这种运行时定制避免了对许多仅有微小差异的 DTB 的需要。

用户提供的参数 config.txt 连同任何叠加层及其参数一起被扫描，然后应用。加载程序检查结果以了解（例如）哪个 UART（如果有）将用于控制台。最后它启动内核，传递一个指向合并的 DTB 的指针。

#### 设备树

设备树 (DT) 是系统中硬件的描述。它应包括基本 CPU 的名称、内存配置以及任何外围设备（内部和外部）。 DT 不应该用于描述软件，尽管通过列出硬件模块，它通常会导致驱动程序模块被加载。

> 笔记
> 记住 DT 应该与操作系统无关，因此任何特定于 Linux 的东西都不应该存在。

设备树将硬件配置表示为节点层次结构。每个节点可以包含属性和子节点。属性被命名为字节数组，它可以包含字符串、数字（大端）、任意字节序列及其任意组合。与文件系统类比，节点是目录，属性是文件。树中节点和属性的位置可以使用路径来描述，并使用斜杠作为分隔符和单个斜杠（/) 来表示根。

... ...

#### 设备树覆盖

现代片上系统 (SoC) 是一种非常复杂的设备；一个完整的设备树可能有数百行长。更进一步，将 SoC 与其他组件一起放置在电路板上只会让事情变得更加复杂。为了保持其可管理性，特别是当存在共享组件的相关设备时，将公共元素放入其中是有意义的 .dtsi 文件，可能包含在多个文件中 .dts 文件。

当像 Raspberry Pi 这样的系统也支持可选的插件配件（例如 HAT）时，问题就会变得更加严重。最终，每种可能的配置都需要一个设备树来描述它，但是一旦考虑到所有不同的基本型号和大量可用配件，组合的数量就会开始迅速增加。

我们需要的是一种使用部分设备树来描述这些可选组件的方法，然后能够通过获取基本设备树并添加许多可选元素来构建完整的树。您可以这样做，这些可选元素称为“覆盖”。

除非您想学习如何为 Raspberry Pi 编写覆盖层，否则您可能更愿意跳到 第 3 部分：在 Raspberry Pi 上使用设备树.

... ...

#### 在 Raspberry Pi 上使用设备树

##### DTB、覆盖层和 config.txt

在 Raspberry Pi 上，这是加载程序的工作（加载程序之一） start.elf 图像）将覆盖层与适当的基本设备树结合起来，然后将完全解析的设备树传递给内核。基础设备树位于旁边 start.elf 在 FAT 分区中（/boot/firmware/ 来自 Linux），命名为 bcm2711-rpi-4-b.dtb, bcm2710-rpi-3-b-plus.dtb等。请注意，某些型号（3A+、A、A+）将分别使用“b”等效项（3B+、B、B+）。此选择是自动的，并且允许在各种设备中使用相同的 SD 卡映像。

> 笔记
> DT 和 ATAG 是互斥的，将 DT blob 传递给不理解它的内核将导致启动失败。固件将始终尝试加载 DT 并将其传递给内核，因为自 rpi-4.4.y 以来的所有内核在没有 DTB 的情况下都将无法运行。您可以通过添加来覆盖它device_tree=在 config.txt 中，强制使用 ATAG，这对于简单的裸机内核非常有用。

加载程序现在支持使用 bcm2835_defconfig 进行构建，它选择上游 BCM2835 支持。这个配置会导致 bcm2835-rpi-b.dtb 和 bcm2835-rpi-b-plus.dtb 待建。如果这些文件与内核一起复制，则加载程序将默认尝试加载这些 DTB 之一。

为了管理设备树和覆盖，加载程序支持许多 config.txt 指令：
```sh
dtoverlay=acme-board
dtparam=foo=bar,level=42
```

这将导致加载程序寻找 overlays/acme-board.dtbo 在 Raspberry Pi OS 挂载的固件分区中/boot/firmware/。然后它会搜索参数 foo 和 level，并将指定的值分配给它们。

加载程序还将搜索带有编程 EEPROM 的附加 HAT，并从那里加载支持覆盖 - 直接或通过“覆盖”目录中的名称加载；这无需任何用户干预即可发生。

有多种方法可以判断内核正在使用设备树：

- 启动期间的“机器型号：”内核消息具有特定于板的值，例如“Raspberry Pi 2 Model B”，而不是“BCM2709”。
- `/proc/device-tree`存在，并包含精确镜像 DT 的节点和属性的子目录和文件。

通过设备树，内核将自动搜索并加载支持指定启用设备的模块。因此，通过为设备创建适当的 DT 覆盖，您可以使设备用户免于编辑 /etc/modules;所有配置都进去 config.txt，对于 HAT，甚至该步骤也是不必要的。但请注意，分层模块，例如 i2c-dev 仍然需要显式加载。

另一方面是，由于除非 DTB 请求，否则不会创建平台设备，因此不再需要将过去由于板支持代码中定义的平台设备而加载的模块列入黑名单。事实上，当前的 Raspberry Pi 操作系统映像不附带任何黑名单文件（某些有多个驱动程序可用的 WLAN 设备除外）。

... ...

#### 固件参数

该固件使用特殊的 /选择 节点在引导加载程序和/或固件与操作系统之间传递参数。

overlay_prefix - string
这 覆盖前缀 选择的字符串config.txt.

os_prefix - string
这 操作系统前缀 选择的字符串config.txt.

rpi-boardrev-ext - 32-bit integer
扩展板修订代码来自 OTP 第 33 行.

rpi-country-code - 32-bit integer
使用的国家/地区代码 PiWiz - 仅限 Pi400。

rpi-duid - string
仅限树莓派 5。 PCB 上 QR 码的字符串表示形式。

常见引导加载程序属性 /chosen/bootloader

boot-mode - 32-bit integer
用于加载内核的引导模式。看 引导顺序.

partition - 32-bit integer
引导期间使用的分区号。如果一个 boot.img 加载 ramdisk 后，这指的是加载 ramdisk 的分区，而不是 ramdisk 内的分区号。

pm_rsts - 32-bit integer
的价值 PM_RSTS 在启动期间注册。

tryboot - 32-bit integer
设置 1 如果 tryboot 标志在启动时设置。
电源特性/chosen/power
仅限树莓派 5。

max_current - 32-bit integer
电源可以提供的最大电流（以 mA 为单位）。固件报告 USB-C、USB-PD 或 PoE 接口指示的值。
对于台式电源（例如连接到 GPIO 接头）定义 PSU_MAX_CURRENT 在引导加载程序配置中指示电源电流能力。

power_reset - 32-bit integer
仅限树莓派 5。

指示 PMIC 重置原因的位字段。

|Bit	|原因
|:-- |:--
|0      |过电压
|1	|欠电压
|2	|过温
|3	|使能信号
|4	|看门狗

rpi_power_supply - 2 个 32-bit integer
官方Raspberry Pi 27W电源的USB VID和产品VDO（如果已连接）。

usb_max_current_enable - 32-bit integer
如果启动期间 USB 端口限流器设置为低限，则为零；如果启用了上限，则为非零。 如果电源声称最大电流为 5A，则自动启用高电平或usb_max_current_enable=1被强迫进入config.txt

usb_over_current_detected- 32 位整数
如果 USB 启动期间发生 USB 过流事件，则非零。

usbpd_power_data_objects - 二进制 blob（多个 32 位整数）
引导加载程序在 USB-PD 协商期间接收到的原始二进制 USB-PD 对象（仅限固定电源）。 要捕获该对象以用于错误报告，请运行hexdump -C /proc/device-tree/chosen/power/usbpd_power_data_objects.

格式由以下定义 USB供电 规格。
BCM2711 和 BCM2712 特定引导加载程序属性/chosen/bootloader
以下属性特定于 BCM2711 和 BCM2712 SPI EEPROM 引导加载程序。

build_timestamp- 32 位整数
EEPROM 引导加载程序的 UTC 构建时间。

capabilities - 32 位整数
该位字段描述当前引导加载程序支持的功能。这可用于在引导加载程序 EEPROM 配置中启用某个功能（例如 USB 引导）之前检查该功能是否受支持。

|Bit	|特征
|:--|:--
|0	|USB启动 使用 VLI USB 主机控制器
|1	|网络启动
|2	|TRYBOOT_A_B 模式
|3	|尝试启动
|4	|USB启动 使用 BCM2711 USB 主机控制器
|5	|RAM 磁盘 - boot.img
|6	|NVMe启动
|7	|安全启动

update_timestamp - 32 位整数
设置的 UTC 更新时间戳 rpi-eeprom-update.

signed - 32 位整数
如果启用安全启动，则该位字段将不为零。各个位指示当前的安全启动配置。

|Bit	|描述
|:--|:--
|0	|SIGNED_BOOT 在 EEPROM 配置文件中定义。
|1	|预留的
|2	|ROM 开发密钥已被撤销。 看撤销_devkey.
|3	|客户公钥摘要已写入 OTP。看 程序公钥.
|4…​31	 |预留的

version - string
引导加载程序的 Git 版本字符串。

##### BCM2711 和 BCM2712 USB 启动属性/chosen/bootloader/usb

如果系统从 USB 引导，则定义以下属性。这些可用于唯一标识 USB 启动设备。
usb-version- 32 位整数
USB 主要协议​​版本（2 或 3）。

route-string- 32 位整数 USB 3.0 规范定义的设备的 USB 路由字符串标识符。

root-hub-port-number - 32 位整数
引导设备连接到的根集线器端口号 - 可能通过其他 USB 集线器连接。

lun- 32 位整数
大容量存储设备的逻辑单元号。

##### NVMEM 节点

固件通过以下方式提供引导加载程序 EEPROM 部分的只读内存副本： NVMEM子系统。

每个区域在下面显示为 NVMEM 设备 `/sys/bus/nvmem/devices/` 下有一个命名别名 `/sys/firmware/devicetree/base/aliases`.

用于读取 NVMEM 模式的示例 shell 脚本代码 rpi-eeprom-更新:

```sh
blconfig_alias="/sys/firmware/devicetree/base/aliases/blconfig"
blconfig_nvmem_path=""

if [ -f "${blconfig_alias}" ]; then
   blconfig_ofnode_path="/sys/firmware/devicetree/base"$(strings "${blconfig_alias}")""
   blconfig_ofnode_link=$(find -L /sys/bus/nvmem -samefile "${blconfig_ofnode_path}" 2>/dev/null)
   if [ -e "${blconfig_ofnode_link}" ]; then
      blconfig_nvmem_path=$(dirname "${blconfig_ofnode_link}")
      fi
   fi
fi
```

blconfig

这 blconfig 别名是指存储引导加载程序 EEPROM 配置文件副本的 NVMEM 设备。

blpubkey

这 blpubkey 别名指向 NVMEM 设备，该设备以二进制格式存储引导加载程序 EEPROM 公钥（如果已定义）的副本。 `rpi-bootloader-key-convert` 实用程序可用于将数据转换为 PEM 格式，以便与 OpenSSL 一起使用。
也可以看看： 安全启动

#### 故障排除

##### 调试

加载程序将跳过丢失的覆盖和错误的参数，但如果存在严重错误，例如基本 DTB 丢失或损坏或覆盖合并失败，则加载程序将回退到非 DT 引导。如果发生这种情况，或者您的设置不符合您的预期，则值得检查来自加载程序的警告或错误：
```sh
sudo vclog --msg
```

可以通过添加来启用额外的调试 dtdebug=1 到 config.txt.

您可以像这样创建 DT 当前状态的人类可读表示：
```sh
dtc -I fs /proc/device-tree
```
这对于查看将覆盖层合并到底层树上的效果很有用。

如果内核模块未按预期加载，请检查它们是否未列入黑名单 `/etc/modprobe.d/raspi-blacklist.conf`;使用设备树时不需要列入黑名单。如果没有显示任何异常，您还可以通过搜索来检查模块是否导出了正确的别名 `/lib/modules/<version>/modules.alias` 为了 compatible 价值。否则，您的驱动程序可能会丢失：
```sh
.of_match_table = xxx_of_match,
```

或者：
```sh
MODULE_DEVICE_TABLE(of, xxx_of_match);
```
如果失败的话， depmod 失败或更新的模块尚未安装在目标文件系统上。

### 内核命令行

Linux 内核在引导期间接受命令行参数。在 Raspberry Pi 上，此命令行定义在启动分区中的一个文件中，名为cmdline.txt。您可以使用任何文本编辑器编辑此文本文件。
```sh
sudo nano /boot/firmware/cmdline.txt
```

> 笔记
> 使用 sudo 编辑启动分区中的任何内容。将所有参数放入 cmdline.txt 在同一条线上；请勿使用回车符。

可以使用以下命令显示引导时传递给内核的命令行 `cat /proc/cmdline`。它不会与中的完全相同 cmdline.txt 因为固件可以在启动内核之前对其进行更改。

#### 命令行选项

内核命令行参数有很多，其中一些是内核本身定义的。其他的是由内核可能使用的代码定义的，例如普利茅斯闪屏系统。

### 配置 UART

Raspberry Pi 上有两种类型的 UART - PL011 和迷你UART。 PL011 是一款功能强大、广泛兼容 16550 的 UART，而迷你 UART 的功能集有所减少。

Raspberry Pi 上的所有 UART 均为 3.3V - 如果将它们连接到 5V 系统，则会发生损坏。适配器可用于连接 5V 系统。或者，可以从各个第三方获得低成本 USB 转 3.3V 串行适配器。


#### 树莓派 0、1、2、和 3

Raspberry Pi Zero、1、2 和 3 各包含两个 UART，如下所示：

|名称	|类型
|:-- |:--
|串口0	|PL011
|串口1	|迷你串口

#### 树莓派 4 和 400

Raspberry Pi 4 Model B 和 400 还有四个 PL011，默认情况下禁用：

|名称	|类型
|:-- |:--
|串口0	|PL011
|串口1	|迷你串口
|串口2	|PL011
|串口3	|PL011
|串口4	|PL011
|串口5	|PL011

#### 树莓派 5 

Raspberry Pi 5 还有四个 PL011，默认情况下禁用：

|名称	|类型
|:-- |:--
|串口0	|PL011
|串口1	|PL011
|串口2	|PL011
|串口3	|PL011
|串口4	|PL011

Raspberry Pi 5 没有迷你 UART。

#### CM1、CM3、CM3+ 和 CM4

第一代计算模块以及计算模块 3 和计算模块 3+ 具有两个 UART，而计算模块 4 具有六个 UART，如上所述。

在计算模块的所有型号上，UART 默认情况下处于禁用状态，可以使用设备树覆盖显式启用。您还可以指定要使用的 GPIO 引脚，例如：

```sh
dtoverlay=uart1,txd1_pin=32,rxd1_pin=33
```

#### 主串口

在 Raspberry Pi 上，选择一个 UART 出现在 GPIO 14（发送）和 15（接收）上 - 这是主 UART。默认情况下，这也是可能存在 Linux 控制台的 UART。请注意，GPIO 14 是 GPIO 接头上的引脚 8，而 GPIO 15 是引脚 10。

在 Raspberry Pi 5 上，主 UART 显示在调试标头上。

#### 辅助串口

辅助 UART 通常不存在于 GPIO 连接器上。默认情况下，在包含该控制器的型号上，辅助 UART 连接到组合无线 LAN/蓝牙控制器的蓝牙端。


#### 主要和次要 UART

下表总结了各种 Raspberry Pi 设备上 UART 的分配：
|模型	|主要/控制台	|辅助/蓝牙
|:--|:--|:--
|树莓派零 |串口0 |串口1
|树莓派 零 W / 树莓派 零 2 W	|串口1	|串口0
|树莓派1	|串口0	|串口1
|树莓派2	|串口0	|串口1
|树莓派3	|串口1	|串口0
|计算模块 3 和 3+ |串口0 |串口1
|树莓派4	|串口1	|串口0
|树莓派5	|串口10	|<专用UART>


Raspberry Pi 操作系统上的 Linux 设备：

|Linux设备	|描述
|:-- |:--
|/dev/ttyS0 |迷你串口
|/dev/ttyAMA0 |第一个PL011（UART0）
|/dev/serial0 |主UART
|/dev/serial1 |辅助串口
|/dev/ttyAMA10|树莓派 5 调试 UART

`/dev/serial0` 和 `/dev/serial1` 是指向任一的符号链接 `/dev/ttyS0` 或者 `/dev/ttyAMA0`.

在树莓派 5 上， `/dev/serial0` 是一个符号链接，指向 `/dev/ttyAMA10`.

由于书虫的变化， `/dev/serial1` 默认不存在。您可以重新启用 serial1 通过设置以下值config.txt:
```sh
dtparam=krnbt=off
```

> 提示
> 此选项可能不适用于将来的所有型号。仅当您的用例没有其他选择时才使用此选项。

#### Mini-UART 和 CPU 核心频率

#### 禁用 Linux 串行控制台

#### 为 Linux 启用早期控制台

尽管 Linux 内核在启动过程中相对较早地启动 UART，但在基础设施的一些关键位设置完毕之后仍然需要很长时间。如果不访问当时的内核日志消息，那么早期阶段的故障可能很难诊断。启用earlycon支持 UART 之一，添加以下选项之一 cmdline.txt，取决于哪个 UART 是主要的：

对于树莓派 5， earlycon 输出仅出现在具有以下配置的 3 针调试连接器上：
```sh
earlycon=pl011,0x107d001000,115200n8
```
对于 Raspberry Pi 4、400 和计算模块 4：
```sh
earlycon=uart8250,mmio32,0xfe215040
earlycon=pl011,mmio32,0xfe201000
```
对于 Raspberry Pi 2、Pi 3 和计算模块 3：
```sh
earlycon=uart8250,mmio32,0x3f215040
earlycon=pl011,mmio32,0x3f201000
```
对于 Raspberry Pi 1、Pi Zero 和计算模块 1：
```sh
earlycon=uart8250,mmio32,0x20215040
earlycon=pl011,mmio32,0x20201000
```

波特率默认为 115200bps。

#### UART 和设备树

各种 UART 设备树覆盖定义可以在 内核 GitHub。两个最有用的叠加层是 disable-bt 和miniuart-bt.

disable-bt禁用蓝牙设备并使第一个 PL011 (UART0) 成为主 UART。您还必须禁用初始化调制解调器的系统服务，以便它不会连接到 UART，使用sudo systemctl disable hciuart.

miniuart-bt将蓝牙功能切换为使用mini UART，并将第一个PL011（UART0）设为主UART。请注意，这可能会降低最大可用波特率（请参阅下面的微型 UART 限制）。您还必须使用以下任一方法将 VPU 核心时钟设置为固定频率 force_turbo=1 或者 core_freq=250.

叠加层 uart2, uart3, uart4， 和 uart5 用于启用 Raspberry Pi 4 上的四个附加 UART。该文件夹中还有其他特定于 UART 的覆盖层。参考/boot/firmware/overlays/README有关设备树覆盖的详细信息，或运行 dtoverlay -h overlay-name 获取描述和使用信息。
您添加一行到 config.txt 文件以应用 设备树覆盖。请注意，-overlay.dts文件名的一部分被删除。例如：

```sh
dtoverlay=disable-bt
```

#### PL011 和迷你 UART

PL011 UART 和 mini-UART 之间存在一些差异。

迷你 UART 具有较小的 FIFO。再加上缺乏流量控制，这使得在较高波特率下更容易丢失字符。它的功能通常也不如 PL011，主要是因为它的波特率与 VPU 时钟速度相关。

与 PL011 相比，迷你 UART 的具体缺陷是：
- 无断线检测
- 无帧错误检测
- 无奇偶校验位
- 无接收超时中断

PL011 的迷你 UART 和 BCM2835 实现均没有 DCD、DSR、DTR 或 RI 信号。

有关迷你 UART 的更多文档可以在 SoC外设文档.



### LED 警告闪烁代码

如果 Raspberry Pi 由于某种原因无法启动或必须关闭，在许多情况下，LED 会闪烁特定次数以指示发生了什么情况。 LED 将闪烁多次长闪烁（0 次或更多），然后产生短闪烁，以指示确切的状态。在大多数情况下，该模式会在两秒间隙后重复。

|长闪	|短闪	|地位
|:--	|:--	|:--
|0	|3	|一般无法启动
|0	|4	|未找到开始*.elf
|0	|7	|未找到内核映像
|0	|8	|SDRAM故障
|0	|9	|SDRAM 不足
|0	|10	|处于 HALT 状态
|2	|1	|分区不是 FAT
|2	|2	|无法从分区读取
|2	|3	|扩展分区不是FAT
|2	|4	|文件签名/哈希不匹配 - Pi 4 和 Pi 5
|3	|1	|SPI EEPROM 错误 - Pi 4 和 Pi 5
|3	|2	|SPI EEPROM 被写保护 - Pi 4 和 Pi 5
|3	|3	|I2C 错误 - Pi 4 和 Pi 5
|3	|4	|安全启动配置无效
|4	|3	|未找到 RP1
|4	|4	|不支持的板类型
|4	|5	|致命固件错误
|4	|6	|停电类型A
|4	|7	|停电类型B

### 保护你的 Raspberry Pi

在这里，我们介绍了一些提高 Raspberry Pi 安全性的常见方法。

#### 更改用户密码

您可以通过以下方式更改当前用户帐户的密码 raspi-config 从命令行应用程序：
```sh
sudo raspi-config
```
选择选项 2，然后按照说明更改密码。
或者，使用 passwd 应用：
```sh
passwd
```

#### 添加用户

要添加新用户，请输入以下命令，替换 <username> 带有新用户用户名的占位符：
```sh
sudo adduser <username>
```
出现提示时，输入新用户的密码。

您可以在以下位置找到新用户的主目录 `/home/<username>/`.

授予新用户必要的权限，例如 sudo，运行以下命令将用户添加到关联的用户组中，替换 <username> 带有新用户用户名的占位符：
```sh
sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,gpio,i2c,spi <username>
```

要检查权限是否已成功授予，请运行以下命令，替换 <username> 带有新用户用户名的占位符：
```sh
sudo su - <username>
```
如果上述命令运行成功，则说明该用户的权限配置成功。

#### 删除用户

要删除用户，请运行以下命令，替换 <username> 包含您要删除的用户名的占位符：
```sh
sudo deluser -remove-home <username>
```
此命令删除用户及其主目录。如果您想保留用户的主目录，请运行不带 -remove-home 选项。


### 更改默认用户

要更改启动时自动登录 Raspberry Pi 的用户，请运行以下命令：
```sh
sudo raspi-config
```
选择选项 1，S5 Boot/Auto login。然后说“是”重新启动。


#### sudo 命令需要密码

配售 sudo 在命令前面以超级用户身份运行它。默认情况下，不需要密码。但是，您可以通过要求所有命令运行的密码来使您的 Raspberry Pi 更加安全 sudo.

强迫 sudo 如果需要密码，请编辑 nopasswd sudoers 文件为您的用户帐户，替换 <username> 文件名中的占位符和您的用户名：
```sh
sudo visudo /etc/sudoers.d/010_<username>-nopasswd
```
改变 <username> 进入以下内容，替换 <username> 使用您的用户名：
```sh
ALL=(ALL) PASSWD: ALL
```
保存文件。您的新偏好应该立即生效。

#### 更新树莓派操作系统

只有最新的操作系统发行版才包含所有最新的安全修复程序。始终保留您的设备 更新 到最新版本的 Raspberry Pi 操作系统。

如果您使用 SSH 连接到 Raspberry Pi，则值得添加 cron 专门更新 SSH 服务器的作业。以下命令可能每天运行cron工作，确保您及时获得最新的 SSH 安全修复程序，独立于正常的更新过程。
```sh
apt install openssh-server
```

#### 提高 SSH 安全性

SSH 是远程访问 Raspberry Pi 的常用方法。默认情况下，使用 SSH 登录需要用户名/密码对。您可以通过基于密钥的身份验证使其更加安全。

##### 提高用户名/密码安全性

始终确保您拥有一个非常可靠的密码。你也可以 允许 或者 否定 特定用户通过改变 sshd 配置。
```sh
sudo nano /etc/ssh/sshd_config
```
在文件末尾添加、编辑或附加以下行，其中包含您希望允许登录的用户名：
```sh
AllowUsers alice bob
```
您还可以使用 DenyUsers 专门阻止某些用户名登录：
```sh
DenyUsers jane john
```
更改后需要重新启动 sshd 服务使用 sudo systemctl restart ssh 或重新启动以使更改生效。

##### 使用基于密钥的身份验证。
密钥对是两个加密安全密钥。一种是私有的，一种是公共的。它们可用于对 SSH 服务器（在本例中为 Raspberry Pi）的客户端进行身份验证。

客户端生成两个密钥，它们以加密方式相互链接。私钥永远不应该被泄露，但公钥可以自由共享。 SSH 服务器获取公钥的副本，并在请求链接时使用此密钥向客户端发送质询消息，客户端将使用私钥对该消息进行加密。如果服务器可以使用公钥将此消息解密回原始质询消息，则可以确认客户端的身份。

在 Linux 中生成密钥对是使用 ssh-keygen 命令在 客户;密钥默认存储在 .ssh 用户主目录中的文件夹。私钥将被调用id_rsa相关的公钥将被称为id_rsa.pub。密钥长度为 2048 位：破解该长度密钥的加密需要非常长的时间，因此非常安全。如果情况需要，您可以制作更长的钥匙。请注意，您应该只执行一次生成过程：如果重复，它将覆盖任何以前生成的密钥。任何依赖于这些旧密钥的内容都需要更新为新密钥。

在密钥生成过程中，系统将提示您输入密码：这提供了额外的安全级别。目前，将此项留空。
公钥现在需要是 移动到服务器上.

最后，我们需要禁用密码登录，以便所有身份验证都通过密钥对完成。
```sh
sudo nano /etc/ssh/sshd_config
```

有三行需要改成 no，如果它们还没有这样设置：

```sh
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no
```
保存文件并重新启动 ssh 系统 `sudo service ssh reload` 或重新启动。

#### 安装防火墙

有许多适用于 Linux 的防火墙解决方案。大多数使用底层 iptables项目提供数据包过滤。该项目基于 Linux 网络过滤系统。默认情况下，iptables已安装在 Raspberry Pi 操作系统上，但未设置。设置它可能是一项复杂的任务，并且一个项目提供的界面比 iptables 是 简单的防火墙 (UFW)。这是 Ubuntu 中的默认防火墙工具，可以安装在 Raspberry Pi 上：
```sh
sudo apt install ufw
```
ufw是一个相当简单的命令行工具，尽管有一些 GUI 可用。注意 ufw 需要以超级用户权限运行，因此所有命令前面都带有 sudo。也可以使用该选项 --dry-run 任何ufw命令，它指示命令的结果，但实际上没有进行任何更改。
要启用防火墙（这也将确保其在启动时启动），请使用：
```sh
sudo ufw enable
```
要禁用防火墙并禁用启动时启动，请使用：
```sh
sudo ufw disable
```
允许特定端口访问（我们在示例中使用了端口 22）：
```sh
sudo ufw allow 22
```
拒绝端口访问也非常简单（同样，我们以端口 22 为例）：
```sh
sudo ufw deny 22
```
您还可以指定在端口上允许或拒绝哪些服务。在此示例中，我们拒绝端口 22 上的 tcp：
```sh
sudo ufw deny 22/tcp
```
即使您不知道该服务使用哪个端口，您也可以指定该服务。本例允许ssh服务穿过防火墙访问：
```sh
sudo ufw allow ssh
```
status 命令列出了防火墙的所有当前设置：
```sh
sudo ufw status
```
这些规则可能非常复杂，允许阻止特定的 IP 地址、指定允许的流量方向或限制尝试连接的次数（例如帮助击败 DDoS 攻击）。您还可以指定要应用的设备规则（例如 eth0、wlan0）。请参阅 ufw 手册页（man ufw）了解以下命令之外的完整详细信息。
使用 TCP 限制 ssh 端口上的登录尝试。如果某个 IP 地址在过去 30 秒内尝试连接六次或更多次，则会拒绝连接：
```sh
sudo ufw limit ssh/tcp
```
拒绝 IP 地址 192.168.2.1 对端口 30 的访问
```sh
sudo ufw deny from 192.168.2.1 port 30
```

#### 安装 fail2ban

如果您使用 Raspberry Pi 作为某种服务器，例如 ssh 或者网络服务器，您的防火墙将故意留有“漏洞”以让服务器流量通过。在这些情况下， fail2ban 可能有用。 Fail2ban 用 Python 编写，是一个扫描器，用于检查 Raspberry Pi 生成的日志文件，并检查其中是否存在可疑活动。它可以捕获多次暴力登录尝试等情况，并可以通知任何已安装的防火墙阻止来自可疑 IP 地址的进一步登录尝试。它使您不必手动检查日志文件中是否有入侵尝试，然后更新防火墙（通过 iptables）来阻止它们。

安装 fail2ban 使用以下命令：
```sh
sudo apt install fail2ban
```
安装时，Fail2ban 会创建一个文件夹 /etc/fail2ban 其中有一个配置文件名为 jail.conf。需要将其复制到 jail.local 来启用它。该配置文件内有一组默认选项，以及用于检查特定服务是否存在异常的选项。执行以下操作来检查/更改用于的规则ssh:
```sh
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local
```
将以下部分添加到 jail.local 文件。在某些版本的fail2ban上，此部分可能已经存在，因此如果存在，请更新此预先存在的部分。
```sh
[ssh]
enabled  = true
port     = ssh
filter   = sshd
backend  = systemd
maxretry = 6
```

如您所见，此部分名为 ssh，已启用，检查 ssh 端口，使用 sshd 参数，解析系统日志中的恶意活动，并允许在达到检测阈值之前重试六次。检查默认部分，我们可以看到默认的禁止操作是：

```sh
# Default banning action (e.g. iptables, iptables-new,
# iptables-multiport, shorewall, etc) It is used to define
# action_* variables. Can be overridden globally or per
# section within jail.local file
banaction = iptables-multiport
```

iptables-multiport意味着 Fail2ban 系统将运行 `/etc/fail2ban/action.d/iptables-multiport.conf` 当达到检测阈值时文件。有许多不同的操作配置文件可以使用。多端口禁止所有端口上的所有访问。

如果您想在尝试 3 次失败后永久禁止某个 IP 地址，您可以更改 maxretry 值 [ssh] 部分，并将 bantime 设置为负数：

```sh
[ssh]
enabled  = true
port     = ssh
filter   = sshd
backend  = systemd
maxretry = 3
bantime = -1
```

### 配置屏幕消隐

#### 桌面

#### Console

这 dpms_timeout Raspberry Pi 配置使用的屏幕消隐配置仅影响桌面会话。在 控制台模式，当你的树莓派连接了显示器和键盘，只有一个终端进行输入时，使用 consoleblank 在内核命令行中设置。

##### 设置控制台模式屏幕消隐

要更改控制台模式屏幕消隐配置，请打开 /boot/firmware/cmdline.txt 以管理员身份在文本编辑器中：
```sh
sudo nano /boot/firmware/cmdline.txt
```

您可以在此处调整 Raspberry Pi OS 使控制台空白之前的秒数。例如，添加 consoleblank=600 600 秒不活动后禁用显示输出。将值设置为 0 永远不要让屏幕空白。
更改为 cmdline.txt 仅在重启后生效。使用以下命令重新启动您的 Raspberry Pi：
```sh
sudo reboot
```
##### 查看当前屏幕消隐设置
您可以使用以下命令显示当前控制台空白时间（以秒为单位）：
```sh
cat /sys/module/kernel/parameters/consoleblank
```

### 启动文件夹

Raspberry Pi OS 将启动文件存储在 SD 卡的第一个分区上，并使用 FAT 文件系统进行格式化。

启动时，每个 Raspberry Pi 都会从启动分区加载各种文件，以便在 Linux 内核启动之前启动各种处理器。

启动时，Linux 将启动分区挂载为 /boot/firmware/.

> 笔记
> 之前 书呆子, Raspberry Pi OS 将启动分区存储在 /boot/。自从 书呆子，启动分区位于 `/boot/firmware/`.

#### bootcode.bin

引导加载程序，由 SoC 在启动时加载。它执行一些非常基本的设置，然后加载其中之一start*.elf文件。
Raspberry Pi 4 和 5 不使用 bootcode.bin。它已被替换为引导代码板载EEPROM.

#### start*.elf

二进制固件 blob 加载到 SoC 中的 VideoCore GPU 上，然后接管启动过程。
- start.elf 是基本固件。
- start_x.elf 包括额外的编解码器。
- start_db.elf 可用于调试目的。
- start_cd.elf 是固件的精简版本，删除了对编解码器和 3D 等硬件模块的支持以及调试日志记录支持；它还施加了初始帧缓冲区限制。当以下情况时，会自动使用精简固件： gpu_mem=16 指定于 config.txt.

start4.elf, start4x.elf, start4db.elf 和 start4cd.elf 是特定于 Raspberry Pi 4 系列（型号 4B、Pi 400、计算模块 4 和计算模块 4S）的等效固件文件。
有关如何使用这些文件的更多信息，请参阅 config.txt 文档.

树莓派5不使用 elf 文件。固件独立于引导加载程序 EEPROM 中。

#### fixup*.dat
找到与以下匹配对的链接器文件 start*.elf 上一节中列出的文件。

#### cmdline.txt
内核 命令行 在启动时传递到内核。

#### config.txt

包含许多用于设置 Raspberry Pi 的配置参数。欲了解更多信息，请参阅 config.txt 文档.

> 笔记
> Raspberry Pi 5 需要一个非空 config.txt 启动分区中的文件。

#### issue.txt

基于文本的内务信息，包含发行版的日期和 git 提交 ID。

#### initramfs*

初始 ramdisk 的内容。这会在挂载真正的根文件系统之前将临时根文件系统加载到内存中。

> 笔记
> 自 Bookworm 以来，Raspberry Pi 操作系统包括 initramfs 默认文件。要启用初始 ramdisk，请将其配置为 config.txt 与 auto_initramfs 关键字。

#### ssh 或 ssh.txt

当此文件存在时，在启动时启用 SSH。否则默认情况下会禁用 SSH。

> 笔记
> 内容并不重要。即使是空文件也可以启用 SSH。

#### 设备树 blob 文件（*.dtb）

设备树 blob 文件包含 Raspberry Pi 各种型号的硬件定义。这些文件在启动时设置内核 基于检测到的Raspberry Pi型号.

#### 内核文件 （*.img）

各种各样的 核心 树莓派型号对应的镜像文件：

|文件名	|处理器	|树莓派型号	|备注
|:---|:---|:---|:---
|kernel.img |BCM2835	|圆周率 0、圆周率 1	 |
|kernel7.img |BCM2836、BCM2837 |Pi 零 2 W、Pi 2、Pi 3	|后来Pi 2使用了BCM2837
|kernel7l.img |BCM2711	|树莓派 4、树莓派 400、CM4、CM4S	|大型物理地址扩展 (LPAE)
|kernel8.img |BCM2837、BCM2711、BCM2712	|Pi 零 2 W、Pi 2、Pi 3、Pi 4、Pi 400、CM4、CM4S、Pi 5	|64位内核。带有 BCM2836 的 Raspberry Pi 2 不支持 64 位内核。
|kernel_2712.img |BCM2712	|圆周率5	|Pi 5 优化 64位内核.


#### overlays文件夹


包含设备树覆盖。它们用于配置各种硬件设备，例如第三方声卡。条目于 config.txt 选择这些叠加层。有关更多信息，请参阅 设备树、覆盖层和参数.
