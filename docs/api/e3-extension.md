# E3 拓展板 API

> **模块名：** `tqpy`
>
> **导入方式：**
> ```python
> from tqpy import *
> set_extend_board("E3")
> ```
>
> **端口格式：** 由于类型比较多，输入 Pin 口时需要完整输入，例如 `D0`、`P0`、`S0`
>
> | 类型 | 端口 |
> |------|------|
> | 编码电机类 | `EM0`、`EM1` |
> | 舵机 | `S0` - `S3` |
> | 模拟类 | `P0` - `P3` |
> | IIC | 不用写 Pin 口 |

---

## 传感器

### 数字类

#### PIR.get_state(port)

人体红外传感器。在一定范围内是否检测到人。

!!! info "感应范围"
    上电需静置 10s；感应距离 6m 左右，感应角度 100°。

**参数：** `port` - 字符串，接口 `"D0"` ~ `"D7"`

**返回值：** `bool` - `True` 检测到人，`False` 未检测到

---

### 模拟类

#### uv.get_value(port)

紫外线传感器。获取紫外线传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

#### soilHumidity.get_value(port)

土壤湿度传感器。获取土壤湿度传感器检测到的数值。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 范围 0-1023

---

### 数字类 / PWM 脉冲驱动

#### ultrasonic.get_distance(port)

超声波传感器。获取超声波传感器检测到的距离。

**参数：** `port` - 字符串，接口 `"P0"` `"P1"` `"P2"` `"P3"`

**返回值：** `int` - 障碍物的距离，2-250cm

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

## 执行器

### 数字类 / PWM 脉冲驱动

#### servo.angle(port, angle)

数字舵机。设置舵机角度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"S0"` ~ `"S7"` |
| angle | int | **0-180** |

**示例：**

```python
servo.angle("S0", 0)
time.sleep(1)
servo.angle("S0", 90)
```

---

#### servo.set_all_angle(angle1, angle2, angle3, angle4)

数字舵机批量设置（S0-S3）。一次设置 S0-S3 四个舵机角度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| angle1 | int | **0-180**，对应 S0 |
| angle2 | int | **0-180**，对应 S1 |
| angle3 | int | **0-180**，对应 S2 |
| angle4 | int | **0-180**，对应 S3 |

**示例：**

```python
servo.set_all_angle(0, 90, 180, 90)
```

---

### 数字类 / 单总线协议输出

#### rgb.set_color(port, R, G, B, brightness)

全彩灯模块。设置全彩灯颜色和亮度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| port | str | 接口 `"P0"` `"P1"` `"P2"` `"P3"` |
| R, G, B | int | 三原色，每个元素范围 0-255 |
| brightness | int | 0-100 |

**示例：**

```python
rgb.set_color("P0", 255, 0, 0, 50)
```

---

### IIC 类

#### clockDigitalTube.on()

时钟数码管启用。

!!! info "提示"
    除停用、清屏、设置亮度外，其他函数中均包含此函数。

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

五路巡线传感器颜色校准。

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

IC 卡写入数据。

**参数：** `number` - 整数，0-9

---

#### IC.read_data()

IC 卡读取数据。

**参数：** 无

**返回值：** IC 卡数据

---

### 串口类 — 编码电机

#### ECMotor.set_chassis_pwm(speed)

控制小车速度。设置小车的移动速度（PWM 调速）。

**参数：** `speed` - 整数，0-100

---

#### ECMotor.set_motor_power(motor_id, speed)

编码电机功率。设置指定编码电机的功率。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| motor_id | str | `"EM0"` 或 `"EM1"` |
| speed | int | 0-100 |

---

#### ECMotor.set_chassis_speed(speed)

设置小车转速（脉冲）。设置小车的轮胎转速。

**参数：** `speed` - 整数，-4000 到 4000

---

#### ECMotor.set_chassis_turn_angle(angle, speed)

设置小车原地转向（脉冲）。设置小车原地转向的角度和转动速度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| angle | int | -32768 ~ 32768 |
| speed | int | 正数 |

---

#### ECMotor.set_chassis_move_distance(distance_cm, speed)

控制小车行驶（脉冲）。控制小车以指定速度行驶指定距离。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| distance_cm | int | 1-30000 |
| speed | int | -200 ~ 200 |

---

#### ECMotor.set_motor_speed(motor_id, speed)

编码电机转速。设置指定编码电机的转速。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| motor_id | str | `"EM0"` 或 `"EM1"` |
| speed | int | -4000 ~ 4000 |

---

#### ECMotor.set_motor_angle(motor_id, speed, time)

编码电机在指定时间内转动。控制编码电机以指定速度转动指定时间。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| motor_id | str | `"EM0"` 或 `"EM1"` |
| speed | int | -4000 ~ 4000 |
| time | int | 0 ~ 32768 |

**示例：**

```python
from tqpy import *

set_extend_board("E3")

# 控制小车前进 20cm
ECMotor.set_chassis_move_distance(20, 100)

# 控制小车原地转向 90 度
ECMotor.set_chassis_turn_angle(90, 100)
```