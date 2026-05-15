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

### 3. 上传 Python 模块

根据使用的硬件平台上对应的模块文件：

| 硬件平台 | 模块文件 | 上传路径 |
|----------|----------|----------|
| 2.0 主板 | `dfck_block.py` | `/lib/dfck_block.py` |
| E1 拓展板 | `tqpy.py` | `/lib/tqpy.py` |

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

!!! warning "端口输入格式"
    E1 拓展板端口输入时需要完整输入，例如 `D0`、`P0`、`S0`
