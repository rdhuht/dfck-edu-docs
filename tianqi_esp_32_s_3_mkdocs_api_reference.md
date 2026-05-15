# 天启 ESP32-S3 MicroPython SDK 文档

> 基于 ESP32-S3-WROOM-1 的教育开发板 MicroPython API 文档。
>
> 本文档采用 MkDocs + Material for MkDocs 风格组织，适用于：
>
> - MicroPython
> - Thonny
> - ESP32-S3
> - 教育开发板二次开发
>
> 模块名称：`dfck_block`

---

# 项目结构建议

```text
project/
├── docs/
│   ├── index.md
│   ├── getting-started/
│   ├── api/
│   └── examples/
├── examples/
├── drivers/
├── lib/
└── main.py
```

---

# 安装与导入

## 安装

将 `dfck_block.py` 上传到开发板文件系统：

```text
/lib/dfck_block.py
```

推荐使用：

- Thonny
- MicroPython
- ESP32_GENERIC_S3 固件

---

## 导入模块

```python
from dfck_block import *
```

或者：

```python
import dfck_block as dfck
```

---

# API Reference

---

# 串口输出

## print()

串口输出字符串。

### 示例

```python
print("Hello World")
```

---

# 时间 API

## dfck.get_ticks_ms()

获取主板运行时间（毫秒）。

### 返回值

| 类型 | 说明 |
|---|---|
| int | 主板运行时间（ms） |

### 示例

```python
start = dfck.get_ticks_ms()
print(start)
```

---

## dfck.get_ticks_diff(start, end)

计算两个时间戳之间的差值。

等价于：

```python
end - start
```

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| start | int | 起始时间 |
| end | int | 结束时间 |

### 返回值

| 类型 | 说明 |
|---|---|
| int | 时间差（ms） |

### 示例

```python
start = dfck.get_ticks_ms()

# some code

end = dfck.get_ticks_ms()

print(dfck.get_ticks_diff(start, end))
```

---

# 按键

## @dfck.when_button_pressed(button)

按键事件回调。

当指定按键被按下时自动执行函数。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| button | str | 按键编号：`A` `B` `C` `D` |

### 示例

```python
@dfck.when_button_pressed("A")
def on_button_a_pressed():
    print("Button A pressed")
```

---

## dfck.button_is_pressed(button)

获取按键当前状态。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| button | str | 按键编号 |

### 返回值

| 类型 | 说明 |
|---|---|
| bool | True 表示按下 |

### 示例

```python
if dfck.button_is_pressed("A"):
    print("Pressed")
```

---

# 姿态与 IMU

## dfck.get_gyro_accel_state(state)

获取主板当前姿态状态。

### 支持状态

| 状态 | 说明 |
|---|---|
| shake | 摇晃 |
| face up | 正面朝上 |
| face down | 正面朝下 |
| up | 向上 |
| down | 向下 |
| left | 左倾 |
| right | 右倾 |
| upright | 正立 |
| handstand | 倒立 |

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| state | str | 姿态名称 |

### 返回值

| 类型 | 说明 |
|---|---|
| bool | 当前是否处于指定状态 |

### 示例

```python
if dfck.get_gyro_accel_state("shake"):
    print("Device shaking")
```

---

## dfck.get_acceleration(axis)

获取加速度值。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| axis | str | `x` `y` `z` |

### 返回值

| 类型 | 说明 |
|---|---|
| float | 当前轴向加速度 |

### 示例

```python
x = dfck.get_acceleration("x")
print(x)
```

---

## dfck.get_gyroscope(axis)

获取角速度。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| axis | str | `x` `y` `z` |

### 返回值

| 类型 | 说明 |
|---|---|
| float | 当前轴向角速度 |

---

## dfck.get_pitch()

获取俯仰角。

### 返回值

| 类型 | 说明 |
|---|---|
| float | 俯仰角（弧度） |

---

## dfck.get_roll()

获取横滚角。

### 返回值

| 类型 | 说明 |
|---|---|
| float | 横滚角（弧度） |

---

# 磁敏传感器

## dfck.get_magnetic_state()

检测是否存在磁场。

### 返回值

| 类型 | 说明 |
|---|---|
| bool | 是否检测到磁铁 |

### 示例

```python
if dfck.get_magnetic_state():
    print("Magnet detected")
```

---

## @dfck.when_magnetic_detected()

磁场检测事件。

### 示例

```python
@dfck.when_magnetic_detected()
def on_magnet():
    print("Magnet detected")
```

---

# 环境传感器

## dfck.get_light_value(sensor)

获取光照值。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| sensor | str | `left` 或 `right` |

### 返回值

| 类型 | 范围 |
|---|---|
| int | 0-1023 |

---

## dfck.get_temperature_value()

获取温度值。

### 返回值

| 类型 | 范围 |
|---|---|
| float | -40℃ ~ 80℃ |

---

## dfck.get_humidity_value()

获取湿度值。

### 返回值

| 类型 | 范围 |
|---|---|
| float | 0%RH ~ 100%RH |

---

# 麦克风与语音识别

## dfck.wwe_get_command()

获取当前语音识别结果。

### 返回值

| 类型 | 说明 |
|---|---|
| str | 识别到的命令 |

---

## dfck.wwe_dete_command(command)

判断语音识别结果是否匹配。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| command | str | 待匹配命令 |

### 返回值

| 类型 | 说明 |
|---|---|
| bool | 是否匹配 |

---

## dfck.wwe_add_command(command)

新增语音命令。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| command | str | 拼音命令 |

---

## dfck.wwe_get_sound_level()

获取声音强度。

### 返回值

| 类型 | 范围 |
|---|---|
| int | 0-1023 |

---

# 喇叭与音频

## dfck.buzzer_set_note(freq, sec)

播放指定频率音调。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| freq | int | 音调频率 |
| sec | float | 节拍长度 |

### 示例

```python
dfck.buzzer_set_note(440, 0.5)
```

---

## dfck.buzzer_play_music(music, threaded)

播放内置音乐。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| music | str | 音乐名称 |
| threaded | bool | 是否后台播放 |

---

## dfck.tts_play_chinese(message)

语音合成播放。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| message | str | 拼音文本 |

---

## dfck.pb_player_start(path)

播放音频文件。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| path | str | 文件路径 |

### 示例

```python
dfck.pb_player_start("/sdcard/audio/1.mp3")
```

---

## dfck.pb_player_stop()

停止音频播放。

---

# 屏幕显示

## dfck.screen_clear()

清空屏幕缓冲区。

---

## dfck.screen_flush()

刷新显示内容。

!!! warning

    修改屏幕内容后必须调用 `screen_flush()` 才会真正显示。

---

## dfck.draw_text(text, x, y, rgb)

绘制文本。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| text | str | 显示文本 |
| x | int | X 坐标 |
| y | int | Y 坐标 |
| rgb | list | RGB 颜色 |

### 示例

```python
dfck.draw_text("Hello", 10, 20, [255, 255, 255])
dfck.screen_flush()
```

---

## dfck.draw_matrix(matrix)

绘制 5x5 点阵。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| matrix | list | 5x5 点阵数组 |

---

## dfck.display_img(name)

显示板载图片。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| name | str | 图片名称 |

### 示例

```python
dfck.display_img("picture1")
```

---

## dfck.close_img()

关闭图片显示。

---

# RGB 彩灯

## dfck.set_all_rgb(rgb, brightness)

设置全部 RGB 灯。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| rgb | list | RGB 颜色 |
| brightness | int | 亮度 0-100 |

---

## dfck.set_single_rgb(index, rgb, brightness)

设置单个 RGB 灯。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| index | int | 灯编号 1-8 |
| rgb | list | RGB 颜色 |
| brightness | int | 亮度 |

---

## dfck.set_flowing_light(rgb, brightness, delay)

流水灯效果。

---

## dfck.set_breathing_light(rgb, brightness, delay)

呼吸灯效果。

---

## dfck.set_blink_light(rgb, brightness, on_time, off_time)

闪烁灯效果。

---

## dfck.led_thread_stop()

停止所有灯效。

---

## dfck.set_highlight_mode(state)

设置高亮模式。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| state | bool | 是否启用 |

---

# 扩展端口

支持端口：

- P1
- P2

---

## dfck.get_digital(port)

读取数字输入。

### 返回值

| 值 | 说明 |
|---|---|
| 0 | LOW |
| 1 | HIGH |

---

## dfck.get_analog(port)

读取模拟输入。

### 返回值

| 类型 | 范围 |
|---|---|
| int | 0-2048 |

---

## dfck.set_digital(port, value)

设置数字输出。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| value | int | 0 或 1 |

---

## dfck.set_analog(port, value)

设置 PWM 输出。

### 参数

| 参数 | 类型 | 范围 |
|---|---|---|
| value | int | 0-100 |

---

# WiFi

## dfck.wifi_connect(ssid, password)

连接 WiFi。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| ssid | str | WiFi 名称 |
| password | str | WiFi 密码 |

### 示例

```python
dfck.wifi_connect("MyWiFi", "12345678")
```

---

## dfck.wifi_is_connected()

获取 WiFi 连接状态。

### 返回值

| 类型 | 说明 |
|---|---|
| bool | 是否连接成功 |

---

## dfck.wifi_disconnect()

断开 WiFi。

---

# UDP 网络通信

## dfck.udp_mode_select(mode)

设置 UDP 模式。

### 支持模式

| 模式 | 说明 |
|---|---|
| standard_UDP | 标准模式 |
| broadcast_UDP | 广播模式 |

---

## dfck.udp_set_timeout(timeout)

设置 UDP 超时时间。

---

## dfck.udp_update_local_port(port)

设置本地端口。

---

## dfck.udp_recv()

接收 UDP 数据。

---

## dfck.udp_has_data()

检查是否收到数据。

### 返回值

| 类型 | 说明 |
|---|---|
| bool | 是否收到数据 |

---

## dfck.udp_get_data()

获取接收到的数据。

---

## dfck.udp_get_sender_ip()

获取发送方 IP 地址。

---

## dfck.udp_send(msg, target_ip, target_port)

发送 UDP 数据。

### 参数

| 参数 | 类型 | 说明 |
|---|---|---|
| msg | str | 发送内容 |
| target_ip | str | 目标 IP |
| target_port | int | 目标端口 |

---

# 控制语句

## break

跳出当前循环。

### 示例

```python
while True:
    break
```

---

## continue

跳过当前循环剩余部分并进入下一轮循环。

### 示例

```python
for i in range(10):
    if i == 5:
        continue

    print(i)
```

---

# MkDocs 项目初始化

## 安装依赖

```bash
pip install mkdocs-material
```

推荐额外安装：

```bash
pip install mkdocs-glightbox
pip install mkdocstrings[python]
pip install pymdown-extensions
```

---

## 创建项目

```bash
mkdocs new tianqi-docs
cd tianqi-docs
```

---

## 项目目录结构

```text
tianqi-docs/
├── docs/
│   ├── index.md
│   ├── getting-started/
│   │   ├── firmware.md
│   │   ├── thonny.md
│   │   └── filesystem.md
│   ├── api/
│   │   ├── time.md
│   │   ├── button.md
│   │   ├── imu.md
│   │   ├── display.md
│   │   ├── rgb.md
│   │   ├── wifi.md
│   │   └── udp.md
│   └── examples/
│       ├── blink.md
│       ├── oled.md
│       └── wifi.md
├── mkdocs.yml
└── requirements.txt
```

---

## requirements.txt

```text
mkdocs-material
mkdocs-glightbox
mkdocstrings[python]
pymdown-extensions
```

---

# mkdocs.yml 配置

```yaml
site_name: TianQi ESP32-S3 Docs
site_description: ESP32-S3 MicroPython SDK Documentation
site_author: DFCK

repo_name: tianqi-board

copyright: Copyright © TianQi

nav:
  - 首页: index.md

  - 快速开始:
      - 固件刷写: getting-started/firmware.md
      - Thonny: getting-started/thonny.md
      - 文件系统: getting-started/filesystem.md

  - API Reference:
      - 时间: api/time.md
      - 按键: api/button.md
      - IMU: api/imu.md
      - 屏幕: api/display.md
      - RGB: api/rgb.md
      - WiFi: api/wifi.md
      - UDP: api/udp.md

  - 示例:
      - 点灯: examples/blink.md
      - OLED: examples/oled.md
      - WiFi: examples/wifi.md

theme:
  name: material
  language: zh

  palette:
    - scheme: default
      primary: blue
      accent: light blue
      toggle:
        icon: material/weather-night
        name: Dark mode

    - scheme: slate
      primary: blue
      accent: light blue
      toggle:
        icon: material/weather-sunny
        name: Light mode

  features:
    - navigation.tabs
    - navigation.sections
    - navigation.expand
    - navigation.top
    - search.highlight
    - search.share
    - content.code.copy
    - content.tabs.link

markdown_extensions:
  - admonition
  - tables
  - attr_list
  - md_in_html

  - pymdownx.superfences
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.tabbed:
      alternate_style: true
  - pymdownx.details

plugins:
  - search
  - glightbox

extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/
```

---

## 启动文档服务器

```bash
mkdocs serve
```

浏览器访问：

```text
http://127.0.0.1:8000
```

---

## 构建静态站点

```bash
mkdocs build
```

生成目录：

```text
site/
```

可以直接部署到：

- GitHub Pages
- Vercel
- Netlify
- Nginx

---

## GitHub Pages 部署

```bash
mkdocs gh-deploy
```

---

# 推荐的首页 index.md

```markdown
# 天启 ESP32-S3 MicroPython SDK

基于 ESP32-S3-WROOM-1 的教育开发板 MicroPython SDK。

## 特性

- ESP32-S3
- MicroPython
- WiFi
- RGB LED
- 屏幕显示
- IMU
- 麦克风
- UDP 通信
- 板载音频

## 快速开始

1. 刷入 MicroPython
2. 使用 Thonny 连接开发板
3. 上传 dfck_block
4. 运行示例程序

## 示例

```python
from dfck_block import *

print("Hello TianQi")
```
```

---

# 推荐的 MkDocs 配置

```yaml
site_name: TianQi ESP32-S3 Docs

repo_name: tianqi-board

theme:
  name: material
  language: zh
  features:
    - navigation.tabs
    - navigation.sections
    - content.code.copy

markdown_extensions:
  - admonition
  - pymdownx.superfences
  - pymdownx.highlight
  - pymdownx.inlinehilite
  - pymdownx.tabbed

plugins:
  - search

nav:
  - 首页: index.md

  - API:
      - 时间: api/time.md
      - 按键: api/button.md
      - IMU: api/imu.md
      - RGB: api/rgb.md
      - 屏幕: api/display.md
      - WiFi: api/wifi.md
```

---

# 推荐的后续优化

建议后续逐步完善：

1. GPIO 映射表
2. I2C 地址表
3. 硬件原理图
4. 完整示例工程
5. 类型注解
6. PEP8 API 重构
7. Sphinx / mkdocstrings 自动 API 文档
8. SDK 分层结构
9. 驱动源码说明
10. 异步 asyncio 支持

