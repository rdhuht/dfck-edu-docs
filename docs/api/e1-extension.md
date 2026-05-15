# E1 拓展板 API

> 导入方式：
> ```python
> from tqpy import *
> set_extend_board("E1")
> ```
>
> 端口格式：需要完整输入，例如 `D0`、`P0`、`S0`
>
> | 类型 | 端口 |
> |------|------|
> | 数字类 | P0-P5 |
> | 模拟类 | P0-P5 |
> | IIC | P6-P8（不用写 Pin 口）|

---

## 传感器

### 数字类传感器

#### button.get_state(port)

检测按钮是否按下。

**参数：** `port` - 字符串，接口 `"P0"` ~ `"P5"`

**返回值：** `bool` - True 表示检测到按下

**示例：**

```python
if button.get_state("P0"):
    print("Button pressed")
```

---

#### PIR.get_state(port)

人体红外传感器是否检测到人。

**参数：** `port` - 字符串，接口 `"P0"` ~ `"P5"`

**返回值：** `bool` - True 表示检测到

**示例：**

```python
if PIR.get_state("P0"):
    print("Person detected")
```

---

### 模拟类传感器

#### voice.get_value(port)

获取声音传感器的声音强度。

**参数：** `port` - 字符串，接口 `"P0"` ~ `"P5"`

**返回值：** `int` - 范围 0-1023

**示例：**

```python
level = voice.get_value("P0")
print(f"Sound level: {level}")
```

---

#### light.get_value(port)

获取光线传感器的数值。

**参数：** `port` - 字符串，接口 `"P0"` ~ `"P5"`

**返回值：** `int` - 范围 0-1023

**示例：**

```python
light_value = light.get_value("P0")
print(f"Light: {light_value}")
```

---

#### uv.get_value(port)

获取旋钮传感器的数值。

**参数：** `port` - 字符串，接口 `"P0"` ~ `"P5"`

**返回值：** `int` - 范围 0-1023

**示例：**

```python
value = uv.get_value("P0")
print(f"UV value: {value}")
```

---

#### soilHumidity.get_value(port)

获取土壤湿度传感器的数值。

**参数：** `port` - 字符串，接口 `"P0"` ~ `"P5"`

**返回值：** `int` - 范围 0-1023

**示例：**

```python
humidity = soilHumidity.get_value("P0")
print(f"Soil humidity: {humidity}")
```

---

#### DHT.get_value(type)

获取温湿度传感器的值。

**参数：** `type` - 字符串
- `"temperature"` - 温度
- `"humidity"` - 湿度

**返回值：** `float`
- 湿度范围：0-100%RH
- 温度范围：-40~+120℃

**示例：**

```python
temp = DHT.get_value("temperature")
humidity = DHT.get_value("humidity")
print(f"Temperature: {temp}℃, Humidity: {humidity}%RH")
```

---

### 数字类/PWM脉冲驱动

#### ultrasonic.get_distance(port)

获取超声波传感器检测到的距离。

**参数：** `port` - 字符串，接口 `"P0"` ~ `"P5"`

**返回值：** `int` - 障碍物的距离（2-250cm）

**示例：**

```python
distance = ultrasonic.get_distance("P0")
print(f"Distance: {distance}cm")
```

---

## 执行器

### 数字类

#### rgb.set_color(port, [r, g, b], brightness)

控制全彩灯。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 P0-P5 |
| [r, g, b] | list | RGB 颜色，每个元素范围 0-255 |
| brightness | int | 亮度 0-100 |

**示例：**

```python
# 设置 P0 端口的全彩灯为红色，亮度 50
rgb.set_color("P0", [255, 0, 0], 50)

# 绿色
rgb.set_color("P0", [0, 255, 0], 50)

# 蓝色
rgb.set_color("P0", [0, 0, 255], 50)
```

---

#### led.set_state(port, state)

控制单色 LED 灯。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 P0-P5 |
| state | str | `"on"` 点亮，`"off"` 熄灭 |

**示例：**

```python
led.set_state("P0", "on")   # 点亮
led.set_state("P0", "off")  # 熄灭
```

---

### 数字类/PWM脉冲驱动

#### geekServo.set_angle(port, angle)

控制 Geekservo 舵机角度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 P0-P5 |
| angle | int | 角度 0-270 |

**示例：**

```python
# 将 Geekservo 转到 90 度位置
geekServo.set_angle("P0", 90)

# 转到 180 度
geekServo.set_angle("P0", 180)
```

---

#### servo.set_angle(port, angle)

控制数字舵机角度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 P0-P5 |
| angle | int | 角度 0-180 |

**示例：**

```python
# 将数字舵机转到 90 度位置
servo.set_angle("P0", 90)
```

---

#### buzzer.play_music(port, num)

播放蜂鸣器内置音乐。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 P1-P3 |
| num | int | 音乐序号 1-5 |

| 序号 | 音乐 |
|------|------|
| 1 | 生日快乐 |
| 2 | 欢乐颂 |
| 3 | 葫芦娃 |
| 4 | 两只老虎 |
| 5 | 警鸣声 |

**示例：**

```python
# 播放 P1 端口的生日快乐
buzzer.play_music("P1", 1)

# 播放警鸣声
buzzer.play_music("P1", 5)
```

---

#### fan.set_speed(port, speed)

设置风扇的转速。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 P0-P3 |
| speed | int | 转速 0-100 |

**示例：**

```python
# 全速运转
fan.set_speed("P0", 100)

# 半速运转
fan.set_speed("P0", 50)

# 停止
fan.set_speed("P0", 0)
```

---

### IIC 类

#### clockDigitalTube.on()

时钟数码管启用。

除停用、清屏、设置亮度外，其他函数中均包含此函数。

**示例：**

```python
clockDigitalTube.on()
```

---

#### clockDigitalTube.off()

时钟数码管停用（停用不清除内存）。

**示例：**

```python
clockDigitalTube.off()
```

---

#### clockDigitalTube.clear()

时钟数码管清屏（清除内存并黑屏）。

**示例：**

```python
clockDigitalTube.clear()
```

---

#### clockDigitalTube.set_brightness(value)

设置时钟数码管亮度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| value | int | 亮度 1-15 |

**示例：**

```python
clockDigitalTube.set_brightness(8)
```

---

#### clockDigitalTube.display(info)

时钟数码管显示内容。

**参数：** `info` - 整数(int)、小数(float)、字符串(str)

**示例：**

```python
clockDigitalTube.on()
clockDigitalTube.display(1234)      # 显示整数
clockDigitalTube.display(12.34)     # 显示小数
clockDigitalTube.display("OPEN")    # 显示字符串
```

---

#### clockDigitalTube.display_place(seat, num)

在指定位置显示数字。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| seat | int | 位置 1-4 |
| num | int | 数字 0-9 |

**示例：**

```python
clockDigitalTube.on()
clockDigitalTube.display_place(1, 1)  # 第 1 位显示 1
clockDigitalTube.display_place(2, 2)  # 第 2 位显示 2
clockDigitalTube.display_place(3, 3)  # 第 3 位显示 3
clockDigitalTube.display_place(4, 4)  # 第 4 位显示 4
```

---

#### clockDigitalTube.displayDP(seat, bool)

在指定位置点亮小数点。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| seat | int | 位置 1-4 |
| bool | bool | True/False |

**示例：**

```python
clockDigitalTube.on()
clockDigitalTube.display_place(1, 1)
clockDigitalTube.displayDP(1, True)  # 第 1 位小数点点亮
```

---

#### clockDigitalTube.display_time(hour, minute)

显示时间（不支持自计时，需要添加变量，右对齐）。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| hour | int | 小时 0-23 |
| minute | int | 分钟 0-59 |

**示例：**

```python
clockDigitalTube.on()
clockDigitalTube.display_time(12, 30)  # 显示 12:30
```
