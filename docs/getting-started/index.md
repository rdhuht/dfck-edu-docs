# 快速开始

## 安装依赖

### 1. 安装 Thonny

下载并安装 [Thonny IDE](https://thonny.org/)

### 2. 刷入 MicroPython 固件

1. 下载 ESP32-S3 MicroPython 固件
2. 使用 Thonny 或 esptool 刷入

```bash
esptool.py --chip esp32s3 --port COMX erase_flash
esptool.py --chip esp32s3 --port COMX write_flash 0x0 firmware.bin
```

!!! tip "MicroPython 官方文档"
    了解更多 MicroPython 语法和标准库，请参阅 [MicroPython 官方文档](https://docs.micropython.org/)。

### 3. 上传 Python 模块

根据使用的硬件平台上对应的模块文件：

| 硬件平台 | 模块文件 | 上传路径 |
|----------|----------|----------|
| 2.0 主板 | `dfck_block.py` | `/lib/dfck_block.py` |
| E1 拓展板 | `tqpy.py` | `/lib/tqpy.py` |
| E2 拓展板 | `tqpy.py` | `/lib/tqpy.py` |
| E3 拓展板 | `tqpy.py` | `/lib/tqpy.py` |
| AI 模块 | `tqpy.py` | `/lib/tqpy.py` |

!!! note "tqpy 模块共用"
    E1 / E2 / E3 拓展板与 AI 模块共用同一个 `tqpy.py` 模块，通过 `set_extend_board(...)` 切换不同的硬件平台。

### 4. 连接开发板

1. 打开 Thonny
2. 选择 MicroPython (ESP32) 解释器
3. 连接开发板

## 硬件端口说明

### 2.0 主板 (dfck_block)

| 端口 | 说明 |
|------|------|
| P1, P2 | 扩展端口 |
| A, B, C, D | 板载按键 |

### E1 拓展板 (tqpy)

| 类型 | 端口 | 说明 |
|------|------|------|
| 数字类 | P0-P5 | 数字输入输出 |
| 模拟类 | P0-P5 | 模拟输入 |
| IIC | P6-P8 | I2C 通信（不用写 Pin 口）|

### E2 拓展板 (tqpy)

| 类型 | 端口 | 说明 |
|------|------|------|
| 数字类 | D0-D7 | 数字输入输出 |
| 舵机 | S0-S7 | 舵机驱动 |
| 模拟类 | P0-P3 | 模拟输入 |
| IIC | P4-P7 | I2C 通信（不用写 Pin 口）|
| 电机 | M0-M7 | 直流电机 |

### E3 拓展板 (tqpy)

| 类型 | 端口 | 说明 |
|------|------|------|
| 编码电机 | EM0、EM1 | 编码电机 |
| 舵机 | S0-S3 | 舵机驱动 |
| 模拟类 | P0-P3 | 模拟输入 |
| IIC | — | I2C 通信（不用写 Pin 口）|

!!! warning "端口输入格式"
    E1 / E2 / E3 拓展板端口输入时需要完整输入，例如 `D0`、`P0`、`S0`、`EM0`
