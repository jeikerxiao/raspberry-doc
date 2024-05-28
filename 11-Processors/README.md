# 处理器

## BCM2711


这是 Raspberry Pi 4 Model B、Raspberry Pi 400 和 Raspberry Pi Compute Module 4 中使用的 Broadcom 芯片。BCM2711 的架构比早期 Raspberry Pi 型号中的 SoC 使用的架构进行了相当大的升级。它延续了BCM2837的四核CPU设计，但采用了更强大的ARM A72内核。由于结合了连接 U​​SB 2 和 USB 3 端口的 PCIe 链路以及本机连接的以太网控制器，它的 GPU 功能集得到了极大改进，输入/输出速度更快。它还能够比以前使用的 SoC 寻址更多的内存。

ARM 内核的运行频率高达 1.5 GHz，使得 Raspberry Pi 4 比 Raspberry Pi 3B+ 快约 50%。新的 VideoCore VI 3D 单元现在运行频率高达 500 MHz。 ARM 内核是 64 位，而 VideoCore 是 32 位，但有一个新的内存管理单元，这意味着它可以比以前的版本访问更多的内存。

BCM2711芯片继续使用从BCM2837B0开始的散热技术，提供更好的热管理。


- 处理器：四核 Cortex-A72 (ARM v8) 64 位 SoC @ 1.5 GHz。
- 内存：可访问高达 8GB LPDDR4-2400 SDRAM（取决于型号）
- 缓存：每个核心 32kB 数据 + 48kB 指令 L1 缓存。 1MB 二级缓存。
- 多媒体：H.265（4Kp60解码）； H.264（1080p60 解码、1080p30 编码）； OpenGL ES，3.0 图形
- I/O：PCIe总线、板载以太网端口、2×DSI端口（Raspberry Pi 4B仅暴露1个）、2×CSI端口（Raspberry Pi 4B仅暴露1个）、最多6×I2C、最多6×UART （与 I2C 复用）、最多 6 个 SPI（Raspberry Pi 4B 上仅暴露了 5 个）、双 HDMI 视频输出、复合视频输出。

## BCM2712

Broadcom BCM2712 是 Raspberry Pi 5 核心的 16nm 应用处理器。它是 Raspberry Pi 4 中使用的 BCM2711 器件的后继产品，并与早期 Raspberry Pi 产品中使用的 BCM27xx 系列中的其他器件共享许多共同的架构特性。

围绕四核 Arm Cortex-A76 CPU 集群构建，主频高达 2.4GHz，每核 512KB 二级缓存和 2MB 共享三级缓存，集成改进的 12 核 VideoCore VII GPU；能够驱动双 4kp60 显示器的硬件视频缩放器和 HDMI 控制器；以及 Raspberry Pi 开发的 HEVC 解码器和图像信号处理器。 32位LPDDR4X内存接口提供高达17GB/s的内存带宽，同时x1和x4 PCI Express接口支持高带宽外围设备；在 Raspberry Pi 5 上，后者用于连接到 Raspberry Pi RP1 南桥，该南桥提供平台上的大部分面向外部的 I/O 功能。

标题特征包括：

- 四核 Arm Cortex-A76 @ 2.4GHz
    - ARMv8-A ISA
    - 64KByte I 和 D 缓存
    - 每个核心 512KB L2，2MB 共享 L3
- Raspberry Pi 开发的新 ISP
    - 1 十亿像素/秒
- 改进的 HVS 和显示管道
    - 双 4Kp60 支持
- VideoCore V3D VII
    - 速度提高约 2-2.5 倍（更多硬件，1GHz 与 Pi 4 上的 600MHz）
    - OpenGL ES 3.1、Vulkan 1.3
- 4Kp60 HEVC 硬件解码
    - 其他编解码器在软件中运行
    - H264 1080p24 解码约占 CPU 的 10–20%
    - H264 1080p60 解码 ~CPU 的 50–60%
    - H264 1080p30 编码（来自 ISP）~30–40% CPU

总的来说，对于常见的 CPU 或 I/O 密集型用例，BCM2712 中的新功能比 Raspberry Pi 4 的性能提升了 2-3 倍。