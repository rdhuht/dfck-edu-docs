## 注意事项
**<font style="color:#DF2A3F;">模块名</font>**<font style="color:#DF2A3F;">:</font><font style="color:#DF2A3F;"> </font>

E3

**<font style="color:#DF2A3F;">导入方式</font>**<font style="color:#DF2A3F;">：</font>

from tqpy import *

set_extend_board("E3")

**<font style="color:#DF2A3F;">port：</font>**

由于类型比较多，输入Pin口时，需要完整输入：例如D0/P0/S0

编码电机类：EM0、EM1

舵机：S0-S3

模拟类：P0-P3

IIC：不用写Pin口

## 传感器
### 数字类
#### 人体红外传感器
函数用法：PIR.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">在一定范围内，是否检测到人</font>

<font style="color:rgb(0, 0, 0);">感应范围：（上电需静置10s）感应距离6m左右，感应角度100°</font>

输入参数：<font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：检测到人</font>

<font style="color:#333333;">False：未检测到人</font>

### 模拟类
#### <font style="color:#1a1a1a;">旋钮传感器</font>
<font style="color:#333333;">函数用法： uv.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取紫外线传感器的检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">土壤湿度传感器</font>
函数用法：soilHumidity.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取土壤湿度传感器检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

### 数字类/PWM脉冲驱动
#### <font style="color:#1a1a1a;">超声波传感器</font>
函数用法： ultrasonic.get_distance(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取超声波传感器检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口 "P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数</font>

<font style="color:#333333;">障碍物的距离：2-250cm</font>

### 遥控器
#### 2.4G遥控器按钮检测
函数用法：remote.key_press(button_name) 

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取2.4G遥控器按钮是否按下的结果</font>

输入参数：<font style="color:#333333;">按钮名，"A" "B" "C" "D"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：布尔值</font>

<font style="color:#333333;">True，按下</font>

<font style="color:#333333;">False，没有按下</font>

#### <font style="color:#333333;">2.4G遥控器摇杆推向检测</font>
<font style="color:#333333;">函数用法：remote.get_direction(direction) </font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取2.4G遥控器摇杆推向哪一个方向</font>

<font style="color:#333333;">输入参数：遥杆推向，"UP" "DOWN" "LEFT" "RIGHT"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：布尔值</font>

<font style="color:#333333;">True，遥感推向指定方向了</font>

<font style="color:#333333;">False，遥感没有推向指定方向</font>

## 执行器
### 数字类/PWM脉冲驱动
#### <font style="color:#1a1a1a;">数字舵机</font>
函数用法：servo.angle(<font style="color:#333333;">port,angle</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置舵机角度</font>

输入参数：

<font style="color:#333333;">port：字符串，接口S0-S7</font>

<font style="color:#333333;">angle：</font>**<font style="color:#DF2A3F;">0-180</font>**

#### <font style="color:#1a1a1a;">数字舵机（S0-S3）</font>
函数用法：servo.set_all_angle(angle1, angle2, angle3, angle4)

<font style="background-color:#FFFFFF;">功能描述：</font>设置舵机角度

输入参数<font style="background-color:#FFFFFF;">：</font>

<font style="color:#333333;">angle1：</font>**<font style="color:#DF2A3F;">0-180</font>**

<font style="color:#333333;">angle2：</font>**<font style="color:#DF2A3F;">0-180</font>**

<font style="color:#333333;">angle3：</font>**<font style="color:#DF2A3F;">0-180</font>**

<font style="color:#333333;">angle4：</font>**<font style="color:#DF2A3F;">0-180</font>**

### 数字类/单总协议输出
#### <font style="color:#1a1a1a;">全彩灯模块</font>
函数用法：rgb.set_color(<font style="color:#333333;">port,R,G,B,brightness</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置全彩灯颜色和亮度</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P3</font>

<font style="color:#333333;">R,G,B</font><font style="color:#333333;">：整数，</font><font style="color:#333333;">三原色， 每个元素的范围0-255</font>

<font style="color:#333333;">brightness</font><font style="color:#333333;">：0-100</font>

### 2.4 IIC类
#### 2.4.1  时钟数码管
##### 2.4.1.1  时钟数码管启用
函数用法：clockDigitalTube.on()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管启用，除停用、清屏、设置亮度外，其他函数中均包含此函数</font>

输入参数：无

##### 2.4.1.2  时钟<font style="color:#1a1a1a;">数码管停用</font>
函数用法：clockDigitalTube.off()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管停用，停用不清除内存</font>

输入参数：无

##### 2.4.1.3  时钟<font style="color:#1a1a1a;">数码管清屏</font>
函数用法：clockDigitalTube.clear()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管清屏，清除掉内存并黑屏</font>

输入参数：无

##### 2.4.1.4  时钟<font style="color:#1a1a1a;">数码管设置亮度</font>
函数用法：clockDigitalTube.set_brightness(value)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管设置亮度</font>

输入参数：整数

value：1-15

##### 2.4.1.5  时钟<font style="color:#1a1a1a;">数码管显示整数</font>
函数用法：clockDigitalTube.display(<font style="color:#333333;">info</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示整数、小数、字符串</font>

输入参数：整数（int()）、小数（float()）、字符串（str()）

##### 2.4.1.6  时钟数码管在指定位置显示数字
函数用法：clockDigitalTube.display_place(seat,num)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示数字</font>

输入参数：

seat：整数，1-4

num：整数，0-9

##### 2.4.1.7  时钟数码管在指定位置点亮小数点
函数用法：clockDigitalTube.displayDP(seat,bool)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示数字</font>

输入参数：

seat：整数，1-4

bool：布尔值，真/假

##### 2.4.1.8  时钟<font style="color:#1a1a1a;">数码管显示时间</font>
函数用法：clockDigitalTube.display_time(hour,minute)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示时间，不支持自计时，需要添加变量；右对齐</font>

输入参数：

hour：整数，0-23

minute：整数，0-59

#### 2.4.3  五路巡线传感器
##### 2.4.3.1  五路巡线传感器检测的所有状态
函数用法：five_trace.get_all_digital_data()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取到巡线传感器，五个探头检测到的所有的状态值</font>

输入参数：无

##### 2.4.3.2  五路巡线传感器指定探头的黑白检测
函数用法：five_trace.get_state(track,index)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：判断指定探头是否检测到指定颜色</font>

输入参数：

track：字符串，T0-T4

index：黑色或白色

##### 2.4.3.3  五路巡线传感器检测的所有模拟值
函数用法：five_trace.get_all_adc_data()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取到巡线传感器，五个探头检测到的所有的模拟值</font>

输入参数：无

##### 2.4.3.4  时钟<font style="color:#1a1a1a;">数码管设置亮度</font>
函数用法：five_trace.get_adc(track)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取到巡线传感器，五个探头检测到的指定探头的模拟值</font>

输入参数：

track：字符串，T0-T4

##### 2.4.3.5  <font style="color:#262626;background-color:#FFFFFF;">五路巡线传感器颜色较准</font>
函数用法：five_trace.calibrate_color()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：设置五路巡线传感器颜色较准</font>

输入参数：无

##### 2.4.3.6  五路巡线检测颜色平均值
函数用法：five_trace.get_color(color)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取五路巡线传感器的所有探头的颜色平均值</font>

输入参数：

color：字符串，"R" "G" "B"

##### 2.4.3.7  五路巡线传感器指定探头的指定颜色值
函数用法：five_trace.get_single_color(trace, color)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取五路巡线传感器指定探头的指定颜色值</font>

输入参数：

trace：字符串，T0-T4

color：字符串，"R" "G" "B"

##### 2.4.3.8  IC卡写入数据
函数用法：IC.write_data(number)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：控制IC卡写入数据</font>

输入参数：

number：整数，0-9

##### 2.4.3.9  IC卡写入数据
函数用法：IC.read_data()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：读取IC卡数据</font>

输入参数：无

返回：IC卡数据

<font style="color:rgb(38, 38, 38);"></font>

### 2.5 串口类
#### 2.5.1、编码电机
##### 2.4.1.1  控制小车速度
函数用法：ECMotor.set_chassis_pwm(speed)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：设置小车的移动速度</font>

输入参数：

speed：整数，0-100

##### 2.4.1.2  编码电机速度
函数用法：ECMotor.set_motor_power(motor_id, int(100))

<font style="color:#262626;background-color:#FFFFFF;">功能描述：设置小车的移动速度</font>

输入参数：

motor_id：字符串，EM0或EM1

speed：整数，0-100

##### 2.4.1.3  设置小车转速（脉冲）
函数用法：ECMotor.set_chassis_speed(speed)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：设置小车的轮胎的转速</font>

输入参数：

speed：整数，-4000到4000

##### 2.4.1.4  设置小车原地转向（脉冲）
函数用法：ECMotor.set_chassis_turn_angle(angle，speed)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：设置小车原地转向的角度和转动的速度（正数）</font>

输入参数：

angle：整数，-32768-32768

speed：正数

##### 2.4.1.5  控制小车行驶（脉冲）
函数用法：ECMotor.set_chassis_move_distance(distance_cm，speed)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：控制小车以指定速度行驶指定的距离</font>

输入参数：

distance_cm：整数，1-30000

speed：整数，-200-200

##### 2.4.1.6  编码电机转速
函数用法：ECMotor.set_motor_speed(motor_id，speed)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：控制小车以指定速度行驶指定的距离</font>

输入参数：

motor_id：字符串，EM0或EM1

speed：整数，-4000~4000

##### 2.4.1.7  编码电机在指定时间内转动
函数用法：ECMotor.set_motor_angle(motor_id，speed，time)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：控制小车以指定速度行驶指定的距离</font>

输入参数：

motor_id：字符串，EM0或EM1

speed：整数，-4000~4000

time：整数，0到32768

