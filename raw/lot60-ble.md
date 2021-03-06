title: Lot60-BLE 键盘使用说明
category: 蓝牙键盘
time: 1567123076035
---
# 概述

Lot60-BLE 是一款低功耗蓝牙双模键盘。其固件底层使用了TMK作为键盘功能核心，几乎完全实现了TMK功能[^1]。其采用了与GH60完全一致的按键阵列，使其配列文件与GH60几乎完全兼容[^3]。

## LED 一览
Lot60-BLE 包含了1个CapsLock LED，和一个RGB LED 状态指示灯（或3个单色LED状态指示灯）。

RGB 状态指示灯位于Esc按键处，使用贴片的LED灯，故需要使用RGB轴。

如果不想使用RGB轴，可以放弃这个LED灯，转而使用位于按键1, 2, 3处的LED指示灯（参见：[如何改为3LED指示灯](#如何改为3_LED指示灯)）。

# 使用手册

## 快速入门
1. （如果购买的是散件）按照线路板上的标识，将两个芯片焊接到线路板上，并焊接USB口。
2. 将电池插入电池插口。注意电池的线序，红色线对应“+”标记，黑色线对应“-”标记。
3. 使用USB线连接到你的电脑。如果电脑能够成功的识别到名字类似“Lot60.X”的设备，并且LED等亮起，说明USB芯片和蓝牙芯片工作正常。这时用镊子尝试短路任意一个按键，观察是否有按键输入。若有按键输入，则说明整块键盘工作正常。
4. 如果你想使用3个状态指示灯而不是一个RGB状态指示灯，那么请参考：[如何改为3LED指示灯](#如何改为3_LED指示灯)。
5. 组装你的键盘。注意要先装定位板，再装轴哦~
6. 好了，你的Lot60-BLE键盘已经组装完成了。插上USB尝试一下吧！

## 默认配列

![默认配列图](/raw/lot60-ble/keymap.png)

图中Fn1是休眠，Fn2是切换设备。按住Fn0键会临时启用第2层，即`Fn0+Tab`切换USB和蓝牙设备，`Fn0+CapsLock`休眠键盘。

## 操作说明

### 开机

同时按下`Space(空格)+U`，直到LED指示灯亮起即可开机。

插入USB的同时键盘会自动开机。

### 蓝牙连接设备

在键盘开机的状态下，使用你要连接设备的蓝牙搜索功能搜索蓝牙设备。你会见到一个叫做`Lot60.X_XXXXXX`的设备，使用你的主机设备连接此蓝牙设备，若提示输入配对码，请在键盘上输入配对码即可。

### USB 连接设备

直接将USB线缆插入到键盘的USB接口，键盘即自动切换至USB模式。这时候就可以使用USB模式输入了。

### USB/蓝牙状态切换

在默认配列下，按下`Fn0+Tab`，即可在USB和蓝牙两种模式下切换。

### 省电模式

在没有接入USB电源的情况下，键盘处于省电模式。

在省电模式下，所有的指示灯仅在变化后亮起5秒，然后熄灭。键盘在无操作15秒后转入慢速扫描模式，无操作600秒后自动睡眠。

慢速扫描模式下，按键检测将可能略有延迟。在慢速扫描模式下按任意按键即可恢复到快速扫描模式。

自动睡眠后，按下键盘的任意按键即可再次唤醒。

### 电量显示

在新版本的iOS、安卓和Windows上，应该能够正确的显示蓝牙设备的电量百分比。

由于测量方式可能有误差，电量百分比可能无法达到100%或者低至0%，这是正常现象。电量百分比仅供参考。

对于安卓手机，如果没有正确的显示电量，可以尝试下载BatON软件来获取蓝牙设备电量。

### RGB 颜色说明

注意显示的颜色可能和实际颜色有略微色差

- <span style="color: #FFFFFF">■</span>白色：无连接
- <span style="color: #99FFFF">■</span>青色：蓝牙已连接
- <span style="color: #0099FF">■</span>天蓝色：USB已连接
- <span style="color: #FF8000">■</span>橙色：充电中
- <span style="color: #00FF00">■</span>绿色：充电完毕
- <span style="color: #FFFF00">■</span>黄色：输入配对密码
- <span style="color: #FF0080">■</span>紫红色：配对密码输入完毕
- <span style="color: #FF00FF">■</span>紫色：休眠

### 休眠键盘

在默认配列下，按下`Fn0+CapsLock`，即可让键盘进入休眠状态。

如果键盘按键错乱导致无法休眠，请尝试[强制休眠键盘](#如何强制休眠键盘)。

手动休眠后，需要手工按下`Space+U`才能再次唤醒。

### 删除绑定

若想要连接到其他的蓝牙设备，或蓝牙连接不正常，则可尝试以下删除所有绑定。

1. 手动[休眠键盘](#休眠键盘)
2. 在开机时按下`Space+E`即可删除绑定。（即在休眠后，按下Space+U+E开机）

### 全键无冲（NKRO）

此键盘支持NKRO（全键无冲）模式，但默认不启用全键无冲。全键无冲仅在USB模式下才可使用。

在键盘开机时按下`Space+N`（即在休眠后，按下Space+U+N开机），即可切换全键无冲的状态。

### 其他功能键（BootMagic）

以下是所有的开机时功能键的列表，你可以在开机时同时按下Space+下面的键来实现对应的功能。(即，在休眠后同时按下Space+U+下面的键开机，或按住Space+下面的键再插入USB开机。)

需要注意的是，下面的按键全部都指的是当前配列的第0层按键。如果你更改了配列，那么这些按键的位置可能会发生变化。

- E: 擦除蓝牙绑定
- Esc：跳过Bootmagic
- Backspace：重置eeconfig
- B: 进入Bootloader
- D：切换Debug模式
  - X：切换阵列Debug模式
  - K：切换键盘Debug模式
  - M：切换鼠标Debug模式
- LCtrl：交换capslock和左ctrl
- CapsLock: 将capslock用作ctrl
- LAlt：交换LAlt和LGUI
- RAlt: 交换RAlt和RGUI
- LGUI：禁用GUI按钮
- `(1左边那个, Grave): 交换Esc和Grave
- \\: 交换\和Backspace
- N：切换NKRO状态
- 0~7：设置默认层为对应数字的层

### 更改配列

#### 方法A：配置网站配置法

访问 [Lotlab 键盘配置工具](https://keyboard.lotlab.org) ，配置你的配列即可。

注意在线更新、宏、鼠标键等功能暂时不支持，暂时只能使用“下载EEP”功能将EEP文件下载并保存，并使用配列更新工具更新配列。

将键盘使用USB连接到电脑。打开 [配列下载工具(KeymapDownloader.exe)](https://github.com/Lotlab/nrf52-keyboard/releases) ，选择你的键盘和配列，点击下载，即可将新的配列下载到键盘中。

#### 方法B：传统的 TKG 配置方法

我们可以使用 GH60 中最常用的配置方法进行配置。

在这里，我假设你已经熟悉如何使用 [Keyboard layout editor(KLE)](https://www.keyboard-layout-editor.com/) 和 [TMK Keymap Generator(TKG)](https://tools.lotlab.org/tkg/) 来创建适用于键盘的配列了。如果你从未使用过这两者，建议参考百度上面的GH60配列的相关教程作为参考。

因这个键盘含有额外的两项功能键（即切换设备和睡眠），故通常的TKG无法满足要求。请使用上面给出的链接中的TKG，里面包含了这块自定义键盘的额外两颗功能按键。

在TKG中配置好配列并点击下载配列，将配列的eep文件下载后，将键盘使用USB连接到电脑。打开 [配列下载工具(KeymapDownloader.exe)](https://github.com/Lotlab/nrf52-keyboard/releases) ，选择你的键盘和配列，点击下载，即可将新的配列下载到键盘中。

### 固件更新

参见[通用固件更新教程](/page/bluetooth/upgrade/)

# 常见问题

## Q&A

### 键盘的功耗与电池容量的选择

此键盘的典型工作功耗为0.4ma[^4]，电池容量与使用时长的关系可以按照以下算法来估计：

> t(天) = C(容量, mah) * 2 / n (每日使用时长,h)
>
> 例如，使用500mah的电池，每日使用10小时的话，键盘约能使用100天。

### 信号改善的方法

蓝牙的信号可能受到多方面因素的影响。你可以尝试以下方法来改善蓝牙信号：

- 使用非金属外壳、非金属定位板与非金属桌面
- 将键盘和主机尽可能的靠近
- 适当降低2.4GHZ的WiFi的发射功率
- 减少空间内其他WiFi和蓝牙设备的存在
- 不要触摸蓝牙模块的天线位置

### 是否支持多媒体键

支持。

系统键（关机、休眠、重启）因使用较少未能测试，若无法使用请联系我。

### 如何判断我的设备是否支持蓝牙4.0

若您在使用手机。如果您的手机使用的是Android5.0及以上系统，或 iOS 7 及以上系统，或 Windows Mobile 10系统，则应当支持蓝牙4.0。

若您在您的计算机上使用Windows。请查看您的设备管理器，寻找“蓝牙 LE”相关字样的设备。建议使用最新版Windows以增加蓝牙使用体验。

MacOS应该支持，但没有实体设备测试。有报告称MacOS蓝牙电量无法正常显示。

### 如何强制休眠键盘

如果休眠按键不起作用了，那么你可能会需要知道如何强制休眠键盘。

- 方法1：将键盘放置15分钟，其会自动转入休眠状态。
- 方法2：按下键盘背面的RESET按钮，键盘即进入休眠状态。
- 方法3：拔下键盘的USB线和电池，再重新插上。

### 如何查看键盘的硬件版本

- 方法1：查看设备名称，名称为Lot60.X，X即为你的硬件版本。
- 方法2：键盘PCB背面空格下方，写着“Lot60-BLE REV.X”，X即为你的硬件版本。

### 如何进入DFU模式

- 方法1：
  1. 将[键盘休眠](#休眠键盘)；
  2. 在唤醒的同时按下`Space+B`；
  3. 蓝牙会搜索到一个名为`DFUTarg`的设备，表明已经进入DFU模式了。
- 方法2：
  1. 将键盘翻到背面，找到GPIO0接口。
  2. 使用镊子将GPIO0接口与GND接口连接。
  3. 将键盘的电池断开并重新连接，或按下RESET按钮使键盘强制重启。
  4. 蓝牙会搜索到一个名为`DFUTarg`的设备，表明已经进入DFU模式了。进入DFU模式后即可断开GPIO0和GND的连接。

### 如何退出DFU模式

在DFU模式下无操作1分半钟后即可自动退出DFU模式。

### 如何进入USB ISP模式

1. 将键盘与电脑连接的USB线断开。
2. 按住键盘背面的K1按钮[^7]，再使用USB线连上电脑。
3. 听到发现新设备的声音后，即可松开按钮。

### 如何改为3 LED指示灯

将Esc位置的RGB灯焊下，然后在1-3按键位置上焊上轴灯。接着刷新底部提供的3LED灯版本的蓝牙升级包，即可将键盘的指示灯改为3LED指示灯。

在此模式下，灯光说明如下：
- 1号位置：蓝牙指示灯，当蓝牙成功连接后亮起。
- 2号位置：充电指示灯，当前在充电中亮起，充满后熄灭。
- 3号位置：USB指示灯，当前处于USB模式则亮起

## 故障排除

### 通用故障排除指南

如果你的键盘遇到了无法正常工作的问题，请按下列步骤进行：

1. 将键盘关机并重新开机。如果遇到了蓝牙方面的问题，可以尝试[清空键盘绑定信息](#删除绑定)
2. 将键盘使用USB连接到电脑，观察电脑的新增硬件状态和键盘的工作状态指示灯。若电脑提示发现新硬件，并且指示灯提示工作于USB状态的话，则说明主控硬件没有出现问题。
3. 如果遇到了按键不正常的情况，请将键盘关机。重新开机时，按下`Space+BackSpace`重置EEPROM的设定。

### 我的键盘无法开机了

1. 首先将键盘使用USB连接到电脑。如果LED灯亮起，则可能是电池没电了，或者是开机相关的两个按键出现了问题；
2. 尝试按下键盘背面的RESET按钮，然后重复上面的步骤；
3. 尝试断开USB和电池的连接，然后重新插入电池和USB；
4. 尝试强制进入[DFU模式](#如何进入DFU模式)，刷新最新的固件；

### 按键部分（全部）混乱了

可能是你选择了不正确的默认层。可以尝试以下步骤恢复默认层的设置：

1. 先[休眠键盘](#休眠键盘)
2. 在开机时按 `Space+BackSpace` 重置默认层的设定。

### 更新配列后无法正常保存配列

重启键盘后再次更新即可。

### 更新配列后所有按键失效

使用配列下载工具将自定义配列清空，使用内置的配列试试。

### Windows 下出现“驱动程序错误”

1. 在Windows的设备管理器中删除这个设备，或取消这个设备的绑定
2. 重启你的电脑
3. [清空键盘绑定信息](#删除绑定)
4. 在电脑上尝试重新连接

### 有时候出现卡键的问题

这是蓝牙信号不好的原因。请查看上面的蓝牙信号的改善方法来改善蓝牙信号。

# 固件发布

请参考[通用固件更新教程](/page/bluetooth/upgrade/)更新你的键盘固件。

### 1.0.3.1

此版本更新于2019年12月2日，是 Rev.F 出厂版本的固件。

此版本改善了误触按键导致键盘开机的问题。

请对应硬件版本更新软件。可以参考 [如何查看键盘的硬件版本](#如何查看键盘的硬件版本) 部分来确定此键盘的硬件版本。

- [Rev.E 蓝牙升级包](https://tools.lotlab.org/dl/rev_e-nrf52-2019_12_02-db6e8ae.zip)
- [Rev.F 蓝牙升级包](https://tools.lotlab.org/dl/rev_f-nrf52-2019_12_02-db6e8ae.zip)
- [Rev.F 出厂USB固件](https://tools.lotlab.org/dl/rev_f-ch554-2019_12_02-db6e8ae.hex)
- [Rev.E 3LED灯版本蓝牙升级包](https://tools.lotlab.org/dl/rev_e_3led-nrf52-2019_12_02-db6e8ae.zip)
- [Rev.F 3LED灯版本蓝牙升级包](https://tools.lotlab.org/dl/rev_f_3led-nrf52-2019_12_02-db6e8ae.zip)

### 1.0.3

此版本是 Rev.E 出厂版本的固件。

- [Rev.E 蓝牙升级包](https://tools.lotlab.org/dl/rev_e-nrf52-2019_09_30-68552e4.zip)
- [Rev.E 出厂USB固件](https://tools.lotlab.org/dl/rev_e-ch554-2019_09_30-68552e4.hex)
- [Rev.E 3LED灯版本蓝牙升级包](https://tools.lotlab.org/dl/rev_e_3led-nrf52-2019_09_30-68552e4.zip)


[^1]: 没用实现的TMK功能包括：Command Key(固件空间不够), 鼠标键(EndPoint不够)，以及LED灯效(这个键盘没灯)
[^3]: 几乎完全兼容：两者格式是一致的，但存在部分Fn功能的差异。若直接使用tmk的eep文件，则会造成休眠和设备切换两颗功能键不可用。
[^4]: 典型功耗为0.4ma: 使用万用表，在蓝牙连接且无任何灯光的情况下测得。蓝牙搜索和灯光的启用会增加额外的耗电量，不同的无线环境下也有可能造成功耗的增加。此功耗不代表所有工况下的工作电流，仅供参考。
[^7]: K1按钮位于键盘背面的下方偏右位置，即在下方左ALT键的背面附近。若没有焊接此按钮，也可以使用镊子或其他导电的东西短接K1的上下两个脚，用来模拟按钮按下。