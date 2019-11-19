title: LKB-Core使用说明
category: 蓝牙键盘
time: 1574162588286
---
## 简介

LKB-Core是一块用于DIY的蓝牙键盘主控板。它提供了26个IO接口，任意一个IO接口都可以用来连接LED或者是按键阵列。如果你会编程的话，还可以实现更多需要的功能。

## 测试

LKB-Core发货前就已经刷好了测试固件，收到后，使用USB Type-C线将其连接到电脑。使用手机搜索蓝牙设备，如果出现了名为`LKB-Core`的设备的话，即说明蓝牙部分工作正常。

使用镊子短接 { 9, 8, 7, 6, 5, 4 } 和 { 3, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 30, 29, 28, 25, 24 } 中的两个（即左边一个，右边一个，比如3和4，或者9和12，等等），观察是否有按键输出，如有输出则说明按键正常。

## 硬件设计使用说明

1. USB接口部分可以用剪刀剪下来，飞线到你需要的地方；
2. 短接两个ISP接口，再插入USB，可以进入USB下载模式（ISP模式）；
3. 默认的Bootloader下，将P10接口短接到地，然后接通电源（插入USB或接上电池），就可以强制进入DFU模式
4. BAT+、BAT-分别是电池接口。此模块不接电池也能正常工作；
5. DIO和DCLK是SWD接口，方便集成到板子上后还能正常下载固件。
6. USB通讯用的接口：UART_RXD：27、UART_TXD：26

## IO接口图

![IO接口](/raw/lkb-core/silk.png)

## 机械外形图

![机械外形](/raw/lkb-core/mach.png)

## 固件编译和移植指南

见[固件编译移植教程](/page/bluetooth/build-guide/)

## 固件更新

参见[通用固件更新教程](/page/bluetooth/upgrade/)

## 测试固件的配置

- P22：NumLock LED 上拉驱动
- P23：CapsLock LED 上拉驱动
- 按键阵列如下，Fn+Tab切换设备，Fn+CapsLock睡眠，二极管从列到行方向。

|      | P3       | P11  | P12  | P13   | P14   | P15   | P16   | P17   | P18   | P19  | P20  | P30   | P29   | P28       | P25        | P24      |
| ---- | -------- | ---- | ---- | ----- | ----- | ----- | ----- | ----- | ----- | ---- | ---- | ----- | ----- | --------- | ---------- | -------- |
| P9   | ESC      | F1   | F2   | F3    | F4    | F5    | F6    | F7    | F8    | F9   | F10  | F11   | F12   | PtrSc     | ScrollLock | Pause    |
| P8   | `        | 1    | 2    | 3     | 4     | 5     | 6     | 7     | 8     | 9    | 0    | -     | =     | BackSpace | Insert     | Home     |
| P7   | Tab      | Q    | W    | E     | R     | T     | Y     | U     | I     | O    | P    | [     | ]     | \         | Del        | PageUP   |
| P6   | CapsLock | A    | S    | D     | F     | G     | H     | J     | K     | L    | ;    | '     | Enter | KC_NO     | End        | PageDown |
| P5   | Lshift   | Z    | X    | C     | V     | B     | N     | M     | ,     | .    | /    | KC_NO | -     | KC_NO     | Up         | KC_NO    |
| P4   | LCtrl    | LGUI | Lalt | KC_NO | KC_NO | Space | KC_NO | KC_NO | KC_NO | Fn0  | Lalt | Menu  | LCtrl | Left      | Down       | Right    |

测试固件睡眠后按任意键自动唤醒，仅供测试。

## 其他资源

- Kicad的[封装](/raw/lkb-core/LKB_Core.kicad_mod)
