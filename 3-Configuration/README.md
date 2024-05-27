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

#### 启用热点

#### 禁用热点

#### 使用 Raspberry Pi 作为网桥

### 使用代理服务器

#### 配置你的树莓派

#### 更新 sudoers 文件

#### 重新启动你的树莓派

### HDMI配置

### 设置显示器的分辨率和旋转

#### 设置桌面环境分辨率和旋转

#### 设置文件控制台分辨率和旋转

### 音频配置

#### 更改音频输出

### 外部存储配置

#### 安装存储设备

#### 设置自动安装

#### 卸载存储设备

### 本地化您的 Raspberry Pi

### 更改默认引脚配置

#### 启动序列期间的设备引脚

#### 提供自定义设备树 blob

#### dt-blod 的部分

#### 时钟配置

#### 示例设备树源文件

### 设备树、覆盖层和参数

#### 设备树

#### 设备树覆盖

#### 在 Raspberry Pi 上使用设备树

#### 固件参数

#### 故障排除

### 内核命令行

#### 命令行选项

### 配置 UART

#### 树莓派 0、1、2、和 3

#### 树莓派 4 和 400

#### 树莓派 5 

#### CM1、CM3、CM3+ 和 CM4

#### 主串口

#### 辅助串口

#### 主要和次要 UART

#### Mini-UART 和 CPU 核心频率

#### 禁用 Linux 串行控制台

#### 为 Linux 启用早期控制台

#### UART 和设备树

#### PL011 和迷你 UART

### LED 警告闪烁代码

### 保护你的 Raspberry Pi

#### 更改用户密码

#### 添加用户

#### 删除用户

### 更改默认用户

#### sudo 命令需要密码

#### 更新树莓派操作系统

#### 提高 SSH 安全性

#### 安装防火墙

#### 安装 fail2ban

### 配置屏幕消隐

#### 桌面

#### 安慰

### 启动文件夹

#### 启动代码 .bin

#### 开始 *.elf

#### 修正 *.dat

#### cmdline.txt

#### 配置 .txt

#### 问题 .txt

#### 初始化内存文件系统*

#### ssh 或 ssh.txt

#### 设备树 blob 文件（*.dtb）

#### 内核文件 （*.img）

#### 覆盖文件夹


