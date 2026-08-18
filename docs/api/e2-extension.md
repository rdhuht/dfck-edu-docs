# E2 拓展板 API

> **模块名：** `tqpy`
>
> **导入方式：**
> ```python
> from tqpy import *
> set_extend_board("E2")
> ```
>
> **端口格式：** 由于类型比较多，输入 Pin 口时需要完整输入，例如 `D0`、`P0`、`S0`
>
> | 类型 | 端口 |
> |------|------|
> | 数字类 | `D0` - `D7` |
> | 舵机 | `S0` - `S7` |
> | 模拟类 | `P0` - `P3` |
> | IIC | `P4` - `P7`（不用写 Pin 口） |
> | 电机 | `M0` - `M7` |

---

## 传感器

### 数字类

#### magnetometer.get_state(port)

磁敏传感器。检测是否有磁铁。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 检测到磁铁，`False` 未检测到

**示例：**

```python
if magnetometer.get_state("D0"):
    print("Magnet detected")
```

---

#### generaltouch.get_state(port)

倾斜传感器。检测传感器是否倾斜。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 倾斜，`False` 不倾斜

---

#### collision.get_state(port)

碰撞传感器。检测传感器是否被碰撞。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 被碰撞，`False` 没有被碰撞

---

#### obstacle.get_state(port)

红外测障传感器。检测传感器前方是否有障碍。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 前方有障碍，`False` 前方没有障碍

---

#### PIR.get_state(port)

人体红外传感器。一定范围内是否检测到人。

!!! info "感应范围"
    上电需静置 10s；感应距离 6m 左右，感应角度 100°。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 检测到人，`False` 未检测到

---

#### touch.get_state(port)

触摸传感器。获取触摸传感器状态。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 触摸到，`False` 没有触摸到

---

#### button.get_state(port)

按钮传感器。判断按钮是否被按下。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 被按下，`False` 未按下

---

#### trace.get_state(port, dir, color)

双路循迹传感器。获取双路循迹传感器检测状态。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"D0"` ~ `"D7"` |
| dir | int | 左路：0；右路：1 |
| color | int | 黑色：0；白色：1 |

**返回值：** `bool` - `True` 检测到对应颜色，`False` 未检测到

!!! info "探测距离"
    探头底部离地距离 1-5cm（0.5cm 以下为盲区），推荐 1-2.5cm。

**示例：**

```python
if trace.get_state("D0", 0, 0):
    print("Left sensor detected black")
```

---

#### single_trace.get_state(port)

循迹传感器。获取循迹传感器检测状态。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 检测到对应颜色，`False` 未检测到

!!! info "探测距离"
    探头底部离地距离 1-5cm（0.5cm 以下为盲区），推荐 1-2.5cm。

---

#### DigitalRainSensor.get_state(port)

数字水滴传感器。获取数字水滴传感器检测状态。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 检测到水滴，`False` 未检测到水滴

---

#### digitalFan.set_state(port, state)

数字风扇。控制风扇开关。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"D0"` ~ `"D7"` |
| state | str | `"on"` 或 `"off"` |

**示例：**

```python
digitalFan.set_state("D0", "on")
time.sleep(2)
digitalFan.set_state("D0", "off")
```

---

### 模拟类

#### smokeSensor.get_value(port)

烟雾传感器（值）。获取烟雾传感器检测到的烟雾浓度。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### smokeSensor.get_state(port)

烟雾传感器（状态）。检测是否有烟雾。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `bool` - `True` 检测到烟雾，`False` 未检测到烟雾

---

#### filmPressure.get_value(port)

薄膜压力传感器。获取薄膜压力传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### joystick.get_value(port, left_or_right)

摇杆传感器。获取摇杆传感器检测状态。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| left_or_right | int | 左路：0；右路：1 |

**返回值：** `int` - 范围 0-1023

---

#### light.get_intensity(port)

光线传感器。获取光线传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### rotarySwitch.get_value(port)

旋钮传感器。获取旋钮传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### uv.get_value(port)

紫外线传感器。获取紫外线传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### flameSensor.get_value(port)

火焰传感器（值）。获取火焰传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### flameSensor.get_state(port)

火焰传感器（状态）。检测是否有火焰。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `bool` - `True` 检测到火焰，`False` 未检测到火焰

---

#### rainSensor.get_value(port)

水滴传感器（值）。获取水滴传感器检测到的水滴量数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### rainSensor.get_state(port)

水滴传感器（状态）。检测是否有水滴。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `bool` - `True` 检测到水滴，`False` 未检测到水滴

---

#### waterLevel.get_value(port)

水位高度传感器。获取水位高度传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### soilHumidity.get_value(port)

土壤湿度传感器。获取土壤湿度传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

**示例：**

```python
humidity = soilHumidity.get_value("P0")
print(f"Soil humidity: {humidity}")
```

---

#### alcohol.get_value(port)

酒精传感器（值）。获取酒精传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### alcohol.get_state(port)

酒精传感器（状态）。检测是否有酒精。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `bool` - `True` 检测到酒精，`False` 未检测到酒精

---

#### co.get_value(port)

一氧化碳传感器（值）。获取一氧化碳传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### co.get_state(port)

一氧化碳传感器（状态）。检测是否有一氧化碳。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `bool` - `True` 检测到一氧化碳，`False` 未检测到

---

#### co2.get_value(port)

二氧化碳传感器（值）。获取二氧化碳传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### co2.get_state(port)

二氧化碳传感器（状态）。检测是否有二氧化碳。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `bool` - `True` 检测到二氧化碳，`False` 未检测到

---

#### trace.get_value('P1', 0)

双路循迹传感器（值）。获取双路循迹传感器检测到的灰度值。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P1"` ~ `"P3"` |
| left_or_right | int | 左路：0；右路：1 |

**返回值：** 检测到的灰度值

!!! info "探测距离"
    探头底部离地距离 1-5cm（0.5cm 以下为盲区），推荐 1-2.5cm。

---

#### voice.get_value(port)

声音传感器（值）。获取声音传感器检测到的音量。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** 声音音量值

---

#### sgm58031.get_data(index)

模数转换。获取指定端口的模拟值。

**参数：** `index` - 字符串，接口 `"A0"` `"A1"` `"A2"` `"A3"`

**返回值：** 端口的模拟值

---

### IIC 类

#### temperature.get_temp()

温度传感器。获取温度检测到的值。

**参数：** 无

**读值范围：** 温度 -40 ~ +120℃

**返回值：** `float`

---

#### DHT.get_value(type)

温湿度传感器。获取温湿度检测到的值。

**参数：** `type` - 字符串

- `"temperature"` - 温度
- `"humidity"` - 湿度

**读值范围：** 湿度 0-100%RH，温度 -40 ~ +120℃

**返回值：** `float`

**示例：**

```python
temp = DHT.get_value("temperature")
humidity = DHT.get_value("humidity")
print(f"Temp: {temp}℃, Humidity: {humidity}%RH")
```

---

#### colorSensor.get_color(color)

颜色识别传感器（R/G/B 值）。检测 R/G/B 的值。

**参数：** `color` - 字符串：`"R"` `"G"` `"B"`

**返回值：** `int` - 范围 0-255

---

#### colorSensor.is_color(color)

颜色识别传感器（检测颜色）。检测是否是所选颜色。

**参数：** `color` - 字符串：`"red"`、`"orange"`、`"yellow"`、`"green"`、`"bule"`、`"purple"`

可检测的颜色：红、橙、黄、绿、蓝、紫。

**返回值：** `bool` - `True` 物体颜色是所选颜色，`False` 不是

---

#### four_trace.get_state(index, option)

四路巡线传感器。获取对应引脚识别颜色。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| index | str | `"T0"` ~ `"T3"` |
| option | int | 黑色：1，白色：0 |

**返回值：** `bool` - `True` 物体颜色是所选的测试颜色，`False` 不是

---

### 串口类

#### beidou.Get_latitude(port)

北斗导航传感器（获取纬度）。获取当前传感器位置所在纬度。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** 列表

---

#### beidou.Get_longitude(port)

北斗导航传感器（获取经度）。获取当前传感器位置所在经度。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** 列表

---

#### beidou.Get_value(port, index)

串口寻迹传感器。获取对应引脚识别是否是黑色。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| index | str | `"T0"` ~ `"T3"` |

**返回值：** `bool` - `True` 引脚识别为黑色，`False` 引脚识别不为黑色

---

#### offlineVoice.get_instructions(port)

离线语音识别传感器。获取传感器货物全部指令。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

---

#### offlineVoice.dete_instructions(port, num)

离线语音识别传感器（检测指令）。获取传感器识别的指令。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| num | int | 指令代表的数字 |

**返回值：** `bool` - `True` 传感器识别到指令，`False` 传感器未识别到指令

---

#### windSpeed.get_speed(port)

风速传感器（风速值）。获取当前风速值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### windSpeed.get_level(port)

风速传感器（风速等级）。获取当前风速等级。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-12

---

#### finger.Auto_register(port)

指纹识别模块（注册）。注册指纹。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** 数字，指纹注册 ID

---

#### finger.Verify(port)

指纹识别模块（识别是否存在）。识别指纹是否存在。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `bool` - `True` 识别成功，`False` 识别失败

---

#### finger.Get_verify_id(port)

指纹识别模块（识别 ID）。识别指纹所代表的 ID。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** 数字，指纹注册 ID

---

### 数字类 / PWM 脉冲驱动

#### ultrasonic.get_distance(port)

超声波传感器。获取超声波传感器检测到的距离。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 障碍物的距离，2-250cm

**示例：**

```python
distance = ultrasonic.get_distance("P0")
print(f"Distance: {distance}cm")
```

---

### 遥控器

#### remote.key_press(button_name)

2.4G 遥控器按钮检测。获取 2.4G 遥控器按钮是否按下的结果。

**参数：** `button_name` - 按钮名，`"A"` `"B"` `"C"` `"D"`

**返回值：** `bool` - `True` 按下，`False` 没有按下

---

#### remote.get_direction(direction)

2.4G 遥控器摇杆方向检测。获取 2.4G 遥控器摇杆推向哪个方向。

**参数：** `direction` - 摇杆方向，`"UP"` `"DOWN"` `"LEFT"` `"RIGHT"`

**返回值：** `bool` - `True` 摇杆推向指定方向，`False` 没有

---

#### rrc16.is_key_press(button_name)

16 通道遥控器按钮检测。获取 16 通道遥控器按钮是否按下的结果。

**参数：** `button_name` - 按钮名，1-8

**返回值：** `bool` - `True` 按下，`False` 没有按下

---

#### rc16.get_joystick_left(direction)

16 通道遥控器左摇杆方向检测。获取 16 通道遥控器左摇杆推向哪个方向。

**参数：** `direction` - 摇杆方向，`"W"` `"A"` `"S"` `"D"`

**返回值：** `bool` - `True` 左摇杆推向指定方向，`False` 没有

---

#### rc16.get_joystick_right(direction)

16 通道遥控器右摇杆方向检测。获取 16 通道遥控器右摇杆推向哪个方向。

**参数：** `direction` - 摇杆方向，`"I"` `"J"` `"K"` `"L"`

**返回值：** `bool` - `True` 右摇杆推向指定方向，`False` 没有

---

## 执行器

### 数字类

#### humidifier.set_state(port, state)

加湿器。控制加湿器开关。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"D0"` ~ `"D7"` |
| state | str | 打开：`"on"`；关闭：`"off"` |

---

#### activeBuzzer.set_state(port, state)

有源蜂鸣器。设置有源蜂鸣器状态。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"D0"` ~ `"D7"` |
| state | str | 打开：`"on"`；关闭：`"off"` |

---

#### led.set_state(port, state)

LED。单色 LED 灯。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"D0"` ~ `"D7"` |
| state | str | 点亮：`"on"`；熄灭：`"off"` |

---

#### lightStrip.set_state(port, state)

灯串模块。点亮 / 熄灭灯串。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"D0"` ~ `"D7"` |
| state | str | 点亮：`"on"`；熄灭：`"off"` |

---

### 数字类 / PWM 脉冲驱动

#### geekServo.angle(port, angle)

Geekservo 舵机。设置舵机角度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"S0"` ~ `"S7"` |
| angle | int | **0-270** |

**示例：**

```python
geekServo.angle("S0", 0)
time.sleep(1)
geekServo.angle("S0", 135)
```

---

#### buzzer.set_note(port, tone, duration)

蜂鸣器模块（音调）。蜂鸣器播放指定音调。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P1"` `"P2"` `"P3"` |
| tone | int | E5-B8：3-28 |
| duration | int | 1/4：4；1/2：8；1：16；2：32（base 时间为 1/4 拍，125ms） |

---

#### buzzer.play_music(port, num)

蜂鸣器模块（音乐）。播放蜂鸣器内置音乐。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P1"` `"P2"` `"P3"` |
| num | int | 音乐序号：1-5 |

| 序号 | 音乐 |
|------|------|
| 1 | 生日快乐 |
| 2 | 欢乐颂 |
| 3 | 葫芦娃 |
| 4 | 两只老虎 |
| 5 | 警鸣声 |

---

#### pushRod.set_speed(port, dir, speed)

电动推杆。设置电动推杆的方向与速度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| dir | int | 0 正转；1 反转 |
| speed | int | 1 低速；2 中速；3 高速 |

---

#### electromagnet.set_state(port, state)

电磁铁。设置电磁铁开关。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"M0"` ~ `"M7"` |
| state | str | 打开：`"on"`；关闭：`"off"` |

---

#### fan.set_speed(port, speed)

风扇模块。设置风扇的转速。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| speed | int | 0-100 |

**示例：**

```python
fan.set_speed("P0", 100)   # 全速
fan.set_speed("P0", 50)    # 半速
fan.set_speed("P0", 0)     # 停止
```

---

#### motor.speed(port, dir, speed)

直流电机。设置直流电机转向和转速。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"M0"` ~ `"M7"` |
| dir | int | 顺时针：0；逆时针：1 |
| speed | int | 0-100 |

---

#### servo.angle(port, angle)

数字舵机。设置舵机角度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"S0"` ~ `"S7"` |
| angle | int | **0-180** |

---

#### relay.set_state(port, state)

继电器。设置继电器状态。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` ~ `"P3"` 或 `"D0"` ~ `"D7"` |
| state | str | 打开：`"on"`；关闭：`"off"` |

---

### 串口类

#### voicetts.control(port, function)

TTS 语音合成模块（控制功能）。控制 TTS 模块播放功能。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| function | str | 打开：`"on"`；关闭：`"off"`；暂停：`"pause"` |

---

#### voicetts.set_function(port, vol, speed, tone)

TTS 语音合成模块（音量、速度、音调设置）。设置 TTS 模块的音量、播音速度和语调。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| vol | int | 0-9，音量大小 |
| speed | int | 0-9，播音速度 |
| tone | int | 0-9，播放声音语调 |

---

#### voicetts.send_bell_tone(port, index)

TTS 语音合成模块（播放内置音频）。控制 TTS 模块播放内置铃声。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| index | int | 1-15，内置音频编号 |

---

#### voicetts.text_to_speech(port, message)

TTS 语音合成模块（播放语音）。控制 TTS 模块播放合成文字。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| message | str | 想要播放的文字 |

---

### 数字类 / 单总线协议输出

#### RGB.set_color(port, R, G, B, brightness)

全彩灯模块。设置全彩灯颜色和亮度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| R, G, B | int | 三原色，每个元素范围 0-255 |
| brightness | int | 0-100 |

**示例：**

```python
RGB.set_color("P0", 255, 0, 0, 50)    # 红色
RGB.set_color("P0", 0, 255, 0, 50)    # 绿色
RGB.set_color("P0", 0, 0, 255, 50)    # 蓝色
```

---

#### ledMatrix.show(port, brightness, image)

4×4 点阵灯（每个灯可亮不同颜色）。显示指定图案（不同色）。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| brightness | int | 0-100 |
| image | list | 二维列表，每个元素是一个 RGB 三元组 |

---

#### ledMatrix.show_uniformcolor(port, color, brightness, image)

4×4 点阵灯（统一颜色）。显示自定义图案（同色）。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| color | list | 三原色，每个元素范围 0-255 |
| brightness | int | 0-100 |
| image | list | 列表，格式 `['0000','0000','0000','0000']`，熄灭：0，点亮：1 |

---

#### RGBStrip.set_color_separate(port, brightness, colors)

12 灯灯带。显示自定义灯串图案。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| brightness | int | 0-100 |
| colors | list | 12 个颜色，格式 `[[color1],[color2],...,[color12]]` |

---

### IIC 类

#### clockDigitalTube.on()

时钟数码管启用。

!!! info "提示"
    除停用、清屏、设置亮度外，其他函数中均包含此函数。

**示例：**

```python
clockDigitalTube.on()
```

---

#### clockDigitalTube.off()

时钟数码管停用（停用不清除内存）。

---

#### clockDigitalTube.clear()

时钟数码管清屏（清除内存并黑屏）。

---

#### clockDigitalTube.set_brightness(value)

设置时钟数码管亮度。

**参数：** `value` - 整数，亮度 1-15

---

#### clockDigitalTube.display(info)

时钟数码管显示内容。

**参数：** `info` - 整数(int)、小数(float)、字符串(str)

**示例：**

```python
clockDigitalTube.on()
clockDigitalTube.display(1234)      # 整数
clockDigitalTube.display(12.34)     # 小数
clockDigitalTube.display("OPEN")    # 字符串
```

---

#### clockDigitalTube.display_place(seat, num)

在指定位置显示数字。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| seat | int | 位置 1-4 |
| num | int | 数字 0-9 |

---

#### clockDigitalTube.displayDP(seat, bool)

在指定位置点亮小数点。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| seat | int | 位置 1-4 |
| bool | bool | `True` / `False` |

---

#### clockDigitalTube.display_time(hour, minute)

显示时间（不支持自计时，需要添加变量，右对齐）。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| hour | int | 小时 0-23 |
| minute | int | 分钟 0-59 |

---

#### oled.on()

显示屏启用。

!!! info "提示"
    除停用、清屏外，其他函数中均包含此函数。

---

#### oled.off()

显示屏停用（停用不清除内存）。

---

#### oled.clear()

显示屏清屏（清除内存并黑屏）。

---

#### oled.draw_text(text, x, y)

显示屏在指定坐标显示文本。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| text | str | 字符串 |
| x | int | x 坐标 |
| y | int | y 坐标 |

**示例：**

```python
oled.on()
oled.draw_text("Hello", 0, 0)
```

---

#### five_trace.get_all_digital_data()

五路巡线传感器（所有状态）。获取五个探头检测到的所有状态值。

**参数：** 无

---

#### five_trace.get_state(track, index)

五路巡线传感器（指定探头的黑白检测）。判断指定探头是否检测到指定颜色。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| track | str | `"T0"` ~ `"T4"` |
| index | int | 黑色：1，白色：0 |

---

#### five_trace.get_all_adc_data()

五路巡线传感器（所有模拟值）。获取五个探头检测到的所有模拟值。

**参数：** 无

---

#### five_trace.get_adc(track)

五路巡线传感器（指定探头的模拟值）。获取指定探头检测到的模拟值。

**参数：** `track` - 字符串，`"T0"` ~ `"T4"`

---

#### five_trace.calibrate_color()

五路巡线传感器颜色校准。设置五路巡线传感器颜色校准。

**参数：** 无

---

#### five_trace.get_color(color)

五路巡线检测颜色平均值。获取所有探头的颜色平均值。

**参数：** `color` - 字符串，`"R"` `"G"` `"B"`

---

#### five_trace.get_single_color(trace, color)

五路巡线传感器（指定探头的指定颜色值）。获取指定探头的指定颜色值。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| trace | str | `"T0"` ~ `"T4"` |
| color | str | `"R"` `"G"` `"B"` |

---

#### IC.write_data(number)

IC 卡写入数据。控制 IC 卡写入数据。

**参数：** `number` - 整数，0-9

---

#### IC.read_data()

IC 卡读取数据。读取 IC 卡数据。

**参数：** 无

**返回值：** IC 卡数据