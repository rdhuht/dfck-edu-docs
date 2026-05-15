# 综合示例

> 以下示例展示了多个 API 的组合使用，具体函数的示例代码已放在各 API 文档下方。

---

## 2.0 主板综合示例

### 姿态检测与彩灯控制

```python
from dfck_block import *

while True:
    if dfck.get_gyro_accel_state("shake"):
        dfck.set_all_rgb([255, 0, 0], 50)  # 摇晃时红色
    elif dfck.get_gyro_accel_state("face up"):
        dfck.set_all_rgb([0, 255, 0], 50)   # 正面朝上时绿色
    elif dfck.get_gyro_accel_state("face down"):
        dfck.set_all_rgb([0, 0, 255], 50)   # 正面朝下时蓝色
```

---

### 环境监测

```python
from dfck_block import *

dfck.screen_clear()
dfck.draw_text("Environment", 10, 0, [255, 255, 255])
dfck.screen_flush()

while True:
    temp = dfck.get_temperature_value()
    humidity = dfck.get_humidity_value()
    light = dfck.get_light_value("left")

    print(f"Temp: {temp}C, Humidity: {humidity}%, Light: {light}")
    time.sleep(1)
```

---

### WiFi 与 UDP 通信

```python
from dfck_block import *

# 连接 WiFi
dfck.wifi_connect("MyWiFi", "12345678")

# 等待连接
while not dfck.wifi_is_connected():
    time.sleep(0.5)

print("WiFi connected!")

# 配置 UDP
dfck.udp_mode_select('standard_UDP')
dfck.udp_update_local_port(8888)
dfck.udp_set_timeout(30)

# 发送数据
dfck.udp_send("Hello from ESP32", "192.168.1.100", 8888)
```

---

### 语音控制彩灯

```python
from dfck_block import *

# 添加语音命令
dfck.wwe_add_command("kai deng")
dfck.wwe_add_command("guan deng")
dfck.wwe_add_command("hong se")
dfck.wwe_add_command("lv se")
dfck.wwe_add_command("lan se")

while True:
    command = dfck.wwe_get_command()

    if dfck.wwe_dete_command("kai deng"):
        dfck.set_all_rgb([255, 255, 255], 100)

    if dfck.wwe_dete_command("guan deng"):
        dfck.led_thread_stop()

    if dfck.wwe_dete_command("hong se"):
        dfck.set_all_rgb([255, 0, 0], 50)

    if dfck.wwe_dete_command("lv se"):
        dfck.set_all_rgb([0, 255, 0], 50)

    if dfck.wwe_dete_command("lan se"):
        dfck.set_all_rgb([0, 0, 255], 50)
```

---

### 屏幕点阵动画

```python
from dfck_block import *

heart = [
    [0,1,0,1,0],
    [1,0,1,0,1],
    [1,0,0,0,1],
    [0,1,0,1,0],
    [0,0,1,0,0]
]

smile = [
    [0,1,0,1,0],
    [0,1,0,1,0],
    [0,0,0,0,0],
    [1,0,0,0,1],
    [0,1,1,1,0]
]

while True:
    dfck.screen_clear()
    dfck.draw_matrix(heart)
    dfck.screen_flush()
    time.sleep(1)

    dfck.screen_clear()
    dfck.draw_matrix(smile)
    dfck.screen_flush()
    time.sleep(1)
```

---

## E1 拓展板综合示例

### 智能风扇

```python
from tqpy import *

set_extend_board("E1")

while True:
    temp = DHT.get_value("temperature")

    if temp > 30:
        fan.set_speed("P0", 100)
    elif temp > 25:
        fan.set_speed("P0", 50)
    else:
        fan.set_speed("P0", 0)

    print(f"Temperature: {temp}C")
    time.sleep(1)
```

---

### 超声波测距报警

```python
from tqpy import *

set_extend_board("E1")

while True:
    distance = ultrasonic.get_distance("P0")

    if distance < 10:
        buzzer.play_music("P1", 5)  # 警鸣声
        led.set_state("P0", "on")
    else:
        led.set_state("P0", "off")

    print(f"Distance: {distance}cm")
    time.sleep(0.5)
```

---

### 舵机控制

```python
from tqpy import *

set_extend_board("E1")

# Geekservo 舵机控制
geekServo.set_angle("P0", 0)
time.sleep(1)
geekServo.set_angle("P0", 90)
time.sleep(1)
geekServo.set_angle("P0", 180)
time.sleep(1)

# 数字舵机控制
servo.set_angle("P1", 0)
time.sleep(1)
servo.set_angle("P1", 90)
time.sleep(1)
servo.set_angle("P1", 180)
```

---

### 数码管时钟

```python
from tqpy import *

set_extend_board("E1")

clockDigitalTube.on()
clockDigitalTube.set_brightness(8)

hour = 12
minute = 30

clockDigitalTube.display_time(hour, minute)
```

---

### 土壤湿度监测

```python
from tqpy import *

set_extend_board("E1")

while True:
    soil = soilHumidity.get_value("P0")

    if soil < 30:
        print("Soil is too dry!")
        rgb.set_color("P0", [255, 0, 0], 50)  # 红色警告
    elif soil > 70:
        print("Soil is too wet!")
        rgb.set_color("P0", [0, 0, 255], 50)  # 蓝色警告
    else:
        print("Soil moisture is OK")
        rgb.set_color("P0", [0, 255, 0], 50)  # 绿色正常

    time.sleep(1)
```
