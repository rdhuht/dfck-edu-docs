# 东方创科 2.0 教育开发板文档

基于 ESP32-S3-WROOM-1 的教育开发板 MicroPython SDK 文档。

## 硬件平台

| 平台 | 模块名 | 导入方式 |
|------|--------|----------|
| 2.0 主板 | `dfck_block` | `from dfck_block import *` |
| E1 拓展板 | `tqpy` | `from tqpy import *`<br>`set_extend_board("E1")` |
| E2 拓展板 | `tqpy` | `from tqpy import *`<br>`set_extend_board("E2")` |
| E3 拓展板 | `tqpy` | `from tqpy import *`<br>`set_extend_board("E3")` |
| AI 模块 | `tqpy` | `from tqpy import *`<br>`set_extend_board("E2")` |

## 特性

- ESP32-S3
- MicroPython
- WiFi
- RGB LED
- 屏幕显示
- IMU 姿态传感器
- 麦克风与语音识别
- UDP 网络通信
- 板载音频
- 丰富的外设接口

!!! info "AI 模块连接说明"
    AI 模块使用 I2C 接口，可连接 E1 / E2 / E3 任一拓展板的 I2C 接口，无需选择 port 端口。

## 快速开始

1. 刷入 MicroPython 固件
2. 使用 Thonny 连接开发板
3. 上传对应的 Python 模块
4. 运行示例程序

## 文档结构

- [快速开始](getting-started/index.md) - 环境搭建与固件刷写
- [2.0 主板 API](api/mainboard.md) - dfck_block 模块 API
- [E1 拓展板 API](api/e1-extension.md) - tqpy 模块 E1 接口
- [E2 拓展板 API](api/e2-extension.md) - tqpy 模块 E2 接口
- [E3 拓展板 API](api/e3-extension.md) - tqpy 模块 E3 接口（含编码电机）
- [AI 模块 API](api/ai-module.md) - 摄像头与视觉识别
- [示例代码](examples/index.md) - 常用示例

## 示例

```python
# 2.0 主板
from dfck_block import *

print("Hello DFCK")
dfck.screen_clear()
dfck.draw_text("Hello", 10, 20, [255, 255, 255])
dfck.screen_flush()
```

```python
# E1 拓展板
from tqpy import *

set_extend_board("E1")
rgb.set_color("P0", [0, 255, 0], 50)
```
