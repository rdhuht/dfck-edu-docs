# 2.0 主板 API

> 模块名：`dfck_block`
>
> 导入方式：`from dfck_block import *`
>
> 端口：P1, P2

---

## 串口输出

### print()

串口输出字符串。

**示例：**

```python
print("Hello World")
```

---

## 时间类

### dfck.get_ticks_ms()

获取主板运行时间（毫秒）。

**返回值：** `int` - 主板运行时间（ms）

**示例：**

```python
start = dfck.get_ticks_ms()
print(start)
```

---

### dfck.get_ticks_diff(start, end)

计算两个时间戳之间的差值，等价于 `end - start`。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| start | int | 起始时间 |
| end | int | 结束时间 |

**返回值：** `int` - 时间差（ms）

**示例：**

```python
start = dfck.get_ticks_ms()
# some code
end = dfck.get_ticks_ms()
print(dfck.get_ticks_diff(start, end))
```

---

## 按键

### @dfck.when_button_pressed(button)

按键事件回调。当指定按键被按下时自动执行函数。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| button | str | 按键编号：`A` `B` `C` `D` |

**示例：**

```python
@dfck.when_button_pressed("A")
def on_button_a_pressed():
    print("Button A pressed")
```

---

### dfck.button_is_pressed(button)

获取按键当前状态。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| button | str | 按键编号 |

**返回值：** `bool` - True 表示按下

**示例：**

```python
if dfck.button_is_pressed("A"):
    print("Pressed")
```

---

## 姿态与 IMU

### dfck.get_gyro_accel_state(state)

获取主板当前姿态状态。

**支持状态：**

| 状态 | 说明 |
|------|------|
| shake | 摇晃 |
| face up | 正面朝上 |
| face down | 正面朝下 |
| up | 向上 |
| down | 向下 |
| left | 左倾 |
| right | 右倾 |
| upright | 正立 |
| handstand | 倒立 |

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| state | str | 姿态名称 |

**返回值：** `bool` - 当前是否处于指定状态

**示例：**

```python
if dfck.get_gyro_accel_state("shake"):
    print("Device shaking")
```

---

### dfck.get_acceleration(axis)

获取加速度值。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| axis | str | `x` `y` `z` |

**返回值：** `float` - 当前轴向加速度

**示例：**

```python
x = dfck.get_acceleration("x")
y = dfck.get_acceleration("y")
z = dfck.get_acceleration("z")
print(f"X: {x}, Y: {y}, Z: {z}")
```

---

### dfck.get_gyroscope(axis)

获取角速度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| axis | str | `x` `y` `z` |

**返回值：** `float` - 当前轴向角速度

**示例：**

```python
pitch = dfck.get_gyroscope("x")
roll = dfck.get_gyroscope("y")
yaw = dfck.get_gyroscope("z")
print(f"Pitch: {pitch}, Roll: {roll}, Yaw: {yaw}")
```

---

### dfck.get_pitch()

获取俯仰角（主板与 XOY 平面的夹角）。

**返回值：** `float` - 俯仰角（弧度，范围：-π/2 ~ π/2）

**示例：**

```python
pitch = dfck.get_pitch()
print(f"Pitch: {pitch}")
```

---

### dfck.get_roll()

获取横滚角（主板与 XOZ 平面的夹角）。

**返回值：** `float` - 横滚角（弧度，范围：-π ~ π）

**示例：**

```python
roll = dfck.get_roll()
print(f"Roll: {roll}")
```

---

## 磁敏传感器

### dfck.get_magnetic_state()

检测是否存在磁场。

**返回值：** `bool` - 是否检测到磁铁

**示例：**

```python
if dfck.get_magnetic_state():
    print("Magnet detected")
```

---

### @dfck.when_magnetic_detected()

磁场检测事件回调。

**示例：**

```python
@dfck.when_magnetic_detected()
def on_magnet():
    print("Magnet detected")
```

---

## 环境传感器

### dfck.get_light_value(sensor)

获取光照值。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| sensor | str | `left` 或 `right` |

**返回值：** `int` - 范围 0-1023

**示例：**

```python
left_light = dfck.get_light_value("left")
right_light = dfck.get_light_value("right")
print(f"Left: {left_light}, Right: {right_light}")
```

---

### dfck.get_temperature_value()

获取温度值。

**返回值：** `float` - 范围 -40℃ ~ 80℃

**示例：**

```python
temp = dfck.get_temperature_value()
print(f"Temperature: {temp}℃")
```

---

### dfck.get_humidity_value()

获取湿度值。

**返回值：** `float` - 范围 0%RH ~ 100%RH

**示例：**

```python
humidity = dfck.get_humidity_value()
print(f"Humidity: {humidity}%RH")
```

---

## 麦克风与语音识别

### dfck.wwe_get_command()

获取当前语音识别结果。

**返回值：** `str` - 识别到的命令

**示例：**

```python
command = dfck.wwe_get_command()
print(f"Command: {command}")
```

---

### dfck.wwe_dete_command(command)

判断语音识别结果是否匹配。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| command | str | 待匹配命令（拼音）|

**返回值：** `bool` - 是否匹配

**示例：**

```python
if dfck.wwe_dete_command("kai deng"):
    print("Command matched: kai deng")
```

---

### dfck.wwe_add_command(command)

新增语音命令。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| command | str | 拼音命令 |

**示例：**

```python
dfck.wwe_add_command("kai deng")
dfck.wwe_add_command("guan deng")
dfck.wwe_add_command("hong se")
```

---

### dfck.wwe_get_sound_level()

获取声音强度。

**返回值：** `int` - 范围 0-1023

**示例：**

```python
level = dfck.wwe_get_sound_level()
print(f"Sound level: {level}")
```

---

## 喇叭与音频

### dfck.buzzer_set_note(freq, sec)

播放指定频率音调。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| freq | int | 音调频率 |
| sec | float | 节拍长度 |

**示例：**

```python
# 播放标准音调 A4 (440Hz)，持续 0.5 秒
dfck.buzzer_set_note(440, 0.5)
```

---

### dfck.buzzer_play_music(music, threaded)

播放内置音乐。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| music | str | 音乐名称 |
| threaded | bool | 是否后台播放 |

**示例：**

```python
# 播放内置音乐
dfck.buzzer_play_music("happy", False)
```

---

### dfck.tts_play_chinese(message)

语音合成播放（拼音文本）。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| message | str | 拼音文本 |

**示例：**

```python
dfck.tts_play_chinese("ni hao")
```

---

### dfck.pb_player_start(path)

播放音频文件。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| path | str | 文件路径 |

**示例：**

```python
dfck.pb_player_start("/sdcard/audio/1.mp3")
```

---

### dfck.pb_player_stop()

停止音频播放。

**示例：**

```python
dfck.pb_player_stop()
```

---

## 屏幕显示

### dfck.screen_clear()

清空屏幕缓冲区。

**示例：**

```python
dfck.screen_clear()
```

---

### dfck.screen_flush()

刷新显示内容。

!!! warning "注意"
    修改屏幕内容后必须调用 `screen_flush()` 才会真正显示。

**示例：**

```python
dfck.screen_clear()
dfck.draw_text("Hello", 10, 20, [255, 255, 255])
dfck.screen_flush()
```

---

### dfck.draw_text(text, x, y, rgb)

绘制文本。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| text | str | 显示文本 |
| x | int | X 坐标 |
| y | int | Y 坐标 |
| rgb | list | RGB 颜色 |

**示例：**

```python
dfck.screen_clear()
dfck.draw_text("Hello DFCK", 10, 20, [255, 255, 255])
dfck.screen_flush()
```

---

### dfck.draw_matrix(matrix)

绘制 5x5 点阵。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| matrix | list | 5x5 点阵数组 |

**示例：**

```python
# 心形点阵
heart = [
    [0,1,0,1,0],
    [1,0,1,0,1],
    [1,0,0,0,1],
    [0,1,0,1,0],
    [0,0,1,0,0]
]
dfck.draw_matrix(heart)
dfck.screen_flush()
```

---

### dfck.display_img(name)

显示板载图片。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| name | str | 图片名称，如 `"picture1"` |

**示例：**

```python
dfck.display_img("picture1")
```

---

### dfck.close_img()

关闭图片显示。

**示例：**

```python
dfck.close_img()
```

---

## RGB 彩灯

### dfck.set_all_rgb(rgb, brightness)

设置全部 RGB 灯。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| rgb | list | RGB 颜色，如 `[255, 0, 0]` |
| brightness | int | 亮度 0-100 |

**示例：**

```python
# 设置所有灯为红色，亮度 50
dfck.set_all_rgb([255, 0, 0], 50)
```

---

### dfck.set_single_rgb(index, rgb, brightness)

设置单个 RGB 灯。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| index | int | 灯编号 1-8 |
| rgb | list | RGB 颜色 |
| brightness | int | 亮度 0-100 |

**示例：**

```python
# 设置第 1 盏灯为绿色，亮度 80
dfck.set_single_rgb(1, [0, 255, 0], 80)
```

---

### dfck.set_flowing_light(rgb, brightness, delay)

流水灯效果。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| rgb | list | RGB 颜色 |
| brightness | int | 亮度 0-100 |
| delay | int | 延时时间（毫秒）|

**示例：**

```python
dfck.set_flowing_light([255, 0, 0], 50, 100)
```

---

### dfck.set_breathing_light(rgb, brightness, delay)

呼吸灯效果。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| rgb | list | RGB 颜色 |
| brightness | int | 亮度 0-100 |
| delay | int | 延时时间（毫秒）|

**示例：**

```python
dfck.set_breathing_light([0, 255, 0], 50, 50)
```

---

### dfck.set_blink_light(rgb, brightness, on_time, off_time)

闪烁灯效果。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| rgb | list | RGB 颜色 |
| brightness | int | 亮度 0-100 |
| on_time | int | 亮灯持续时间（毫秒）|
| off_time | int | 灭灯持续时间（毫秒）|

**示例：**

```python
dfck.set_blink_light([0, 0, 255], 50, 500, 500)
```

---

### dfck.led_thread_stop()

停止所有灯效。

**示例：**

```python
dfck.led_thread_stop()
```

---

### dfck.set_highlight_mode(state)

设置高亮模式。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| state | bool | 是否启用 |

**示例：**

```python
dfck.set_highlight_mode(True)
```

---

## 扩展端口

支持端口：P1, P2

---

### dfck.get_digital(port)

读取数字输入。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 端口号 `P1` 或 `P2` |

**返回值：**

| 值 | 说明 |
|-----|------|
| 0 | LOW |
| 1 | HIGH |

**示例：**

```python
value = dfck.get_digital("P1")
print(f"Digital value: {value}")
```

---

### dfck.get_analog(port)

读取模拟输入。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 端口号 `P1` 或 `P2` |

**返回值：** `int` - 范围 0-2048

**示例：**

```python
value = dfck.get_analog("P1")
print(f"Analog value: {value}")
```

---

### dfck.set_digital(port, value)

设置数字输出。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 端口号 `P1` 或 `P2` |
| value | int | 0 或 1 |

**示例：**

```python
dfck.set_digital("P1", 1)  # 输出 HIGH
dfck.set_digital("P1", 0)  # 输出 LOW
```

---

### dfck.set_analog(port, value)

设置 PWM 输出。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 端口号 `P1` 或 `P2` |
| value | int | 0-100 |

**示例：**

```python
dfck.set_analog("P1", 50)  # 50% 占空比
```

---

## WiFi

### dfck.wifi_connect(ssid, password)

连接 WiFi。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| ssid | str | WiFi 名称 |
| password | str | WiFi 密码 |

**示例：**

```python
dfck.wifi_connect("MyWiFi", "12345678")
```

---

### dfck.wifi_is_connected()

获取 WiFi 连接状态。

**返回值：** `bool` - 是否连接成功

**示例：**

```python
if dfck.wifi_is_connected():
    print("WiFi connected")
else:
    print("WiFi not connected")
```

---

### dfck.wifi_disconnect()

断开 WiFi。

**示例：**

```python
dfck.wifi_disconnect()
```

---

## UDP 网络通信

### dfck.udp_mode_select(mode)

设置 UDP 模式。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| mode | str | `standard_UDP` 或 `broadcast_UDP` |

**示例：**

```python
dfck.udp_mode_select('standard_UDP')
```

---

### dfck.udp_set_timeout(timeout)

设置 UDP 超时时间。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| timeout | int | 超时时间（秒）|

**示例：**

```python
dfck.udp_set_timeout(30)
```

---

### dfck.udp_update_local_port(port)

设置本地端口。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | int | 端口号 |

**示例：**

```python
dfck.udp_update_local_port(8888)
```

---

### dfck.udp_recv()

开始接收 UDP 数据。

**示例：**

```python
dfck.udp_recv()
```

---

### dfck.udp_has_data()

检查是否收到数据。

**返回值：** `bool` - 是否收到数据

**示例：**

```python
if dfck.udp_has_data():
    print("Data received")
```

---

### dfck.udp_get_data()

获取接收到的数据。

**返回值：** 接收的数据

**示例：**

```python
if dfck.udp_has_data():
    data = dfck.udp_get_data()
    sender_ip = dfck.udp_get_sender_ip()
    print(f"From {sender_ip}: {data}")
```

---

### dfck.udp_get_sender_ip()

获取发送方 IP 地址。

**返回值：** `str` - 发送方 IP 地址

---

### dfck.udp_send(msg, target_ip, target_port)

发送 UDP 数据。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| msg | str | 发送内容 |
| target_ip | str | 目标 IP |
| target_port | int | 目标端口 |

**示例：**

```python
dfck.udp_send("Hello", "192.168.1.100", 8888)
```

---

## 控制语句

### break

跳出当前循环。

**示例：**

```python
while True:
    if dfck.button_is_pressed("A"):
        break
```

---

### continue

跳过当前循环剩余部分并进入下一轮循环。

**示例：**

```python
for i in range(10):
    if i == 5:
        continue
    print(i)
```
