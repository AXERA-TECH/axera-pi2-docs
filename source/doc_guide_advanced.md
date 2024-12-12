# 固件升级指导

由于 **爱芯派2** 作为社区开发板，其功能正处于逐渐完善中。因此建议新购买的开发者参考本章节将固件升级到最新版本，提高评估效率。 

## 基本说明

### AXP文件

AXP文件即后缀名为 `*.axp` 是由 AX620E SDK 编译生成的固件文件。爱芯派2提供了一种不同型号的Sensor模组板（OS04A10），因此对应了两个不同的 `*.axp` 固件文件。开发者升级固件之前请务必确认。 

### AXDL工具

AXDL 是用于烧写 `.axp` 固件的PC软件，目前支持在 Windows10、Windows11 操作系统上运行。
- 运行前请安装网盘中对应的驱动程序；
- 详细使用说明请参考《AXDL 工具使用指南》；
- AXDL 支持多种通信接口烧写，爱芯派Zero使用USB下载口进行固件烧写(升级)。

## 详细指导

### **烧录准备**

**供电**

爱芯派2（AXera—Pi 2）通过载板上的电源接口供电，**官方板载**（此处需要补链接）通过DC接口供电，推荐使用认证配件清单中推荐的**12V/2A**适配器。

> [!WARNING]
>
> 请不要使用电脑USB接口为开发板供电，否则会因供电不足造成开发板**异常断电、反复重启**等异常情况。
>
> 更多问题的处理，可以查阅 [常见问题](https://developer.d-robotics.cc/rdk_doc/FAQ/hardware_and_system) 章节。

**存储**

爱芯派2（AXera—Pi 2）采用Micro SD存储卡作为系统启动介质，推荐至少8GB容量的存储卡，以便满足Ubuntu系统、应用功能软件对存储空间的需求。

**显示**

爱芯派2（AXera—Pi 2）支持HDMI显示接口，通过HDMI线缆连接开发板和显示器，支持图形化桌面显示。

**网络连接**

爱芯派2（AXera—Pi 2）支持以太网、Wi-Fi两种网络接口，用户可通过任意接口实现网络连接功能

**系统烧录**

爱芯派2（AXera—Pi 2）目前提供Ubuntu 22.04系统镜像，可支持Desktop桌面图形化交互。

> [!CAUTION]
>
> 爱芯派2（AXera—Pi 2）出厂已经烧写测试版本系统镜像，为确保使用最新版本的系统，建议参考本文档完成最新版本系统镜像的烧写。

**镜像下载**

镜像文件下载，需通过爱芯派2（AXera—Pi 2）官方渠道提供；

下载完成后，解压出系统烧录的axp文件，如![图片描述](media\board\axp.png)

下载完成后，SD卡烧写文件，如![图片描述](media\board\烧写4.png)

**系统烧录流程**

爱芯派2（AXera—Pi 2）支持从有线 USB Type C 和SD卡烧录两种方式；

**有线烧录方式**

爱芯派2（AXera—Pi 2）有线（USB Type C）烧录方式需要使用AXDL工具进行烧录；

AXDL是运行在windows 10（32/64）操作系统上的应用程序，用于FLASH分区，镜像下载和读取等功能，支持USB或UART一托多下载；

> [!WARNING]
>
> USB下载时若PC未安装USB驱动，请首先安装USB驱动
>
> USB驱动仅支持window 10 32/64操作系统

**驱动安装**

步骤1：移除PC连接USB线

步骤2：使用管理员权限，双击DriversForWin10\DriverSetup.exe按照提示进行安装

步骤3：连接USB线，Windows会自动安装USB驱动

连接位置如图所示：

![图片描述](media\board\Type-C版刷机.png)

安装完成之后，Windows设备管理器显示如下：

![图片描述](media\board\usb驱动.png)

**烧写步骤**

为简化用户操作，.axp文件已经包含了所需的下载镜像文件和参数配置（.xml），用户在下载时只需要加载这个.axp文件即可；

axp包支持对镜像文件计算MD5或者CRC，并在工具加载zxp包时进行校验，确保镜像文件完整性；

步骤1：双击AXDL.exe运行工具，界面显示如图所示：

![图片描述](media\board\axdl1.png)

步骤2：工具栏单击axp加载按钮![图片描述](media\board\axdl2.png)，选择.axp镜像包文件![图片描述](media\board\axdl3.png)

axp加载中![图片描述](media\board\axdl4.png)

步骤3：工具栏单击“设置”![图片描述](media\board\axdl5.png)按键，在“Setting”页面AXDL将axp镜像包镜像文件释放到本地Temp目录并自动进行配置，加载完成后用户可以鼠标双击或者**右键单击**镜像文件，激活文件选择框重新选择下载镜像文件![图片描述](media\board\axdl6.png)

步骤4：爱芯派2（AXera—Pi 2）目前仅支持USB下载，切换到“Option”页面，配置如图所示：

![图片描述](media\board\axdl7.png)

> [!WARNING]
>
> Repartition默认勾选，推荐用户勾选
>
> 爱芯派2（AXera—Pi 2）目前仅支持USB下载，不要勾选“Uart Download”和"Upgrade Frequency"

步骤5：单击“OK”确认设置，在工具栏单击“开始”![图片描述](media\board\axdl8.png)按钮启动下载，此时给开发板上电，下载工具将自动与开发板握手交互，开始下载。

具体连接如图所示：

![图片描述](media\board\Type-C版刷机.png)

然后同时按住下载（DOWNLOAD）和复位（RESET），随后松开复位（RESET），等几秒后，再松开下载（DOWNLOAD），之后请等待30秒左右工具上面会出行进度条，如下图所示：

![图片描述](media\board\Type-C版下载按键.png)

![图片描述](media\board\烧写2.png)

步骤6：等待几分钟后，下载完成结果如下图所示：

![图片描述](media\board\烧写3.png)

**SD卡烧录方式**

> [!WARNING]
>
> 通过SD卡烧录系统镜像前，需要做如下准备：
>
> - 准备至少8GB容量的Mico SD卡
> - SD读卡器
> - 下载镜像烧录工具balenaEtcher（[可点击此处下载](https://etcher.balena.io/)）

balenaEtcher是一款支持Windows/Mac/Linux等多平台的PC端启动盘制作工具，制作SD启动卡流程如下：

1，打开balenaEtcher工具，点击`从文件烧录`按钮，选择解压出来的`ax_pi2.img.zip`文件作为烧录镜像

![图片描述](media\board\SD卡烧录.png)

2，点击`选择目标磁盘`按钮，选择对应的Micro SD存储卡作为目标存储设备

![图片描述](media\board\SD卡烧录1.png)

![图片描述](media\board\SD卡烧录2.png)

3，点击`现在烧录！`按钮开始烧录，待工具提示`烧录完成！`时，表示镜像烧录完成，可以关闭balenaEtcher并取出存储卡

![图片描述](media\board\SD卡烧录3.png)

![图片描述](media\board\SD卡烧录4.png)

![图片描述](media\board\SD卡烧录5.png)

> [!WARNING]
>
> 在验证过程后，会出现上述提示，此时点击“Cancle”即可

4，SD卡插入爱芯派2（AXera—Pi 2），板卡上电，即自动进入SD卡烧录过程

5，此时可通过串口，查看烧录状态，烧录完成如下图所示：

![图片描述](media\board\SD卡烧录8.png)

6，如果没有进入SD卡烧录过程，请使用如下方法重置SD卡烧录

> [!NOTE]
>
> - 通过串口，输入fw_printenv命令，可查看SD卡烧写状态，如下图所示
> - 如果sdupdate=finish，可输入fw_sdupdate，重置SD烧写，如下图所示,fdtcontroladdr=bbdc75a0，表示可重新进行SD卡烧写，此时重新板卡上电即可

![图片描述](media\board\SD卡烧录6.png)

![图片描述](media\board\SD卡烧录7.png)

> [!WARNING]
>
> 如烧录过程中发生中断，请按照上述步骤重新进行

**启动系统**

爱芯派2（AXera—Pi 2）支持从eMMC和SD卡两种模式启动系统

- 当板卡的eMMC没有烧录过系统镜像的情况下，插入制作好系统的SD卡到载板即可通过从SD卡启动系统
- 如果模组上的eMMC已经烧录过系统镜像，则直接从eMMC启动系统

最后，首先保持板卡断电，然后通过HDMI线缆连接板卡与显示器，最后给开发板上电

Ubuntu Desktop版本系统启动完成后，会通过HDMI接口在显示器上输出系统桌面，如下图所示：

![图片描述](media\board\系统.jpg)

**常见问题**

首次使用开发板时的常见问题如下：

- **上电不开机** ：请确保使用[供电](https://developer.d-robotics.cc/rdk_doc/Quick_start/install_os/rdk_x3#供电)中推荐的适配器供电；请确保板卡的Micro SD卡或eMMC已经烧录过Ubuntu系统镜像
- **USB Host接口无反应** ：请确保板卡Micro USB接口有接入数据线
- **使用中热插拔存储卡** ：开发板不支持热插拔Micro SD存储卡，如发生误操作请重启开发板

**注意事项**

- 禁止带电时拔插除USB、HDMI、网线之外的任何设备
- 爱芯派2（AXera—Pi 2）的Type C USB接口不能用作供电
- 选用符合供电规格的电源适配器，否则会出现供电异常，导致系统异常断电的问题

### 远程登录

本章节旨在向需要通过个人电脑(PC)远程访问爱芯派2（AXera—Pi 2）的用户介绍如何通过串口方式进行远程登录

在使用串口登录前，需要确认开发板串口线跟电脑正确连接，连接方式如下图所示：

![图片描述](media\board\type-C版本debug图片.jpg)

串口登录需要借助PC终端工具，目前常用的工具有`Putty`、`MobaXterm`等，用户可根据自身使用习惯来选择；

不同工具的端口配置流程基本类似，下面以`MobaXterm`为例，介绍新建串口连接过程：

- 当串口USB转接板首次插入电脑时，需要安装串口驱动；驱动安装完成后，设备管理器可正常识别串口端口，如下图所示：

  ![图片描述](E:/AX630C/git/axera-pi2-docs/source/media/board/远程登录串口.png)

- 打开`MobaXterm`工具，点击`Session`，然后选择`Serial`

- 配置端口号，例如`COM4`，实际使用的串口号以PC识别到的串口号为准。如下图所示：

  ![图片描述](media\board\远程登录串口设置.png)

- 设置串口配置参数，如下：

  |        配置项        | 参数值 |
  | :------------------: | :----: |
  | 波特率（Baud rate）  | 115200 |
  | 数据位（Data bits）  |   8    |
  |  奇偶校验（Parity）  |  None  |
  | 停止位（Stop bits）  |   1    |
  | 流控（Flow Control） |   无   |

  

- 点击如`OK`，登录设备

### 文件说明

