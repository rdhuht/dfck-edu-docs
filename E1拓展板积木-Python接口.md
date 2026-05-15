## 注意事项
**<font style="color:#DF2A3F;">模块名</font>**<font style="color:#DF2A3F;">:</font><font style="color:#DF2A3F;"> </font>

E1

**<font style="color:#DF2A3F;">导入方式</font>**<font style="color:#DF2A3F;">：</font>

from tqpy import *

set_extend_board("E1")

**<font style="color:#DF2A3F;">port：</font>**

由于类型比较多，输入Pin口时，需要完整输入：例如D0/P0/S0

数字类：P0-P5

模拟类：P0-P5

IIC：P6-P8（不用写Pin口）

## 传感器
### 数字类
#### 按钮传感器
函数用法：button.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">检测按钮是否按下</font>

输入参数：<font style="color:#333333;">字符串，接口"P0"~"P5"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：检测到按下</font>

<font style="color:#333333;">False：未检测到按下</font>

#### 人体红外传感器
函数用法：PIR.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">红外传感器是否检测到人</font>

输入参数：<font style="color:#333333;">字符串，接口"P0"~"P5"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：传感器检测到</font><font style="color:#333333;"></font>

<font style="color:#333333;">False：传感器未检测到</font>

### 模拟类
#### 声音传感器
函数用法：voice.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">获取声音传感器的声音强度</font>

输入参数：

<font style="color:#333333;">port：字符串，接口"P0" "P1" "P2" "P3" "P4" "P5"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font><font style="color:#333333;">整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">光线传感器</font>
函数用法： light.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取光线传感器的检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3" "P4" "P5"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">旋钮传感器</font>
<font style="color:#333333;">函数用法： uv.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取紫外线传感器的检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3" "P4" "P5"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">土壤湿度传感器</font>
函数用法：soilHumidity.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取土壤湿度传感器检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3" "P4" "P5"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">温湿度传感器</font>
函数用法：DHT.get_value("temperature")

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取温湿度检测到的值</font>

输入参数：<font style="color:#333333;">字符串</font>

<font style="color:#333333;">温度："</font>temperature"

<font style="color:#333333;">湿度："</font>humidity"

<font style="color:#333333;">读值范围：</font><font style="color:rgb(0, 0, 0);">湿度0-100%RH，温度-40~+120℃</font>

<font style="color:#333333;">返回值：小数</font>

### 数字类/PWM脉冲驱动
#### <font style="color:#1a1a1a;">超声波传感器</font>
函数用法： ultrasonic.get_distance(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取超声波传感器检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口 "P0" "P1" "P2" "P3" "P4" "P5"</font>

<font style="color:#333333;">返回值：整数</font>

<font style="color:#333333;">障碍物的距离：2-250cm</font>

## 执行器
### 数字类
#### 全彩灯
函数用法：rgb.set_color(<font style="color:#333333;">port</font>, [0, 255, 0], 50)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">控制加湿器开关</font>

输入参数：

<font style="color:#333333;">port：字符串，接口P0-P5</font>

<font style="color:#333333;">R,G,B</font><font style="color:#333333;">：整数，</font><font style="color:#333333;">三原色， 每个元素的范围0-255</font>

<font style="color:#333333;">brightness</font><font style="color:#333333;">：0-100</font>

#### <font style="color:#1a1a1a;">LED</font>
函数用法：led.set_state(<font style="color:#333333;">port，state</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">单色led灯</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P5</font>

<font style="color:#333333;">state：字符串，点亮：on；熄灭：off</font>

### 数字类/PWM脉冲驱动
#### <font style="color:#1a1a1a;">Geekservo舵机</font>
函数用法：geekServo.set_angle(<font style="color:#333333;">port,angle</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置舵机角度</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P5</font>

<font style="color:#333333;">a</font>**<font style="color:#333333;">ngle：</font>****0-270**

#### <font style="color:#1a1a1a;">数字舵机</font>
函数用法：servo.set_angle(<font style="color:#333333;">port,angle</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置舵机角度</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P5</font>

<font style="color:#333333;">angle：</font>**0-180**

#### <font style="color:#1a1a1a;">蜂鸣器模块（音乐）</font>
函数用法：buzzer.play_music(<font style="color:#000000;">port,num</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">播放蜂鸣器内置音乐</font>

输入参数：

<font style="color:#333333;">port：整数，接口P1-P3</font>

<font style="color:#000000;">num：整数，音乐序号：1-5</font>

<font style="color:#000000;">1：生日快乐</font>

<font style="color:#000000;">2：欢乐颂</font>

<font style="color:#000000;">3：葫芦娃</font>

<font style="color:#333333;">4：两只老虎</font>

<font style="color:#333333;">5：警鸣声</font>

#### <font style="color:#1a1a1a;">风扇模块</font>
函数用法： fan.set_speed(<font style="color:#333333;">port,speed</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置风扇的转速</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P3</font>

<font style="color:#333333;">speed：0-100</font>

### 2.3 IIC类
#### 2.3.1  时钟数码管
##### 2.3.1.1  时钟数码管启用
函数用法：clockDigitalTube.on()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管启用，除停用、清屏、设置亮度外，其他函数中均包含此函数</font>

输入参数：无

##### 2.3.1.2  时钟<font style="color:#1a1a1a;">数码管停用</font>
函数用法：clockDigitalTube.off()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管停用，停用不清除内存</font>

输入参数：无

##### 2.3.1.3  时钟<font style="color:#1a1a1a;">数码管清屏</font>
函数用法：clockDigitalTube.clear()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管清屏，清除掉内存并黑屏</font>

输入参数：无

##### 2.3.1.4  时钟<font style="color:#1a1a1a;">数码管设置亮度</font>
函数用法：clockDigitalTube.set_brightness(value)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管设置亮度</font>

输入参数：整数

value：1-15

##### 2.3.1.5  时钟<font style="color:#1a1a1a;">数码管显示整数</font>
函数用法：clockDigitalTube.display(<font style="color:#333333;">info</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示整数、小数、字符串</font>

输入参数：整数（int()）、小数（float()）、字符串（str()）

##### 2.3.1.6  时钟数码管在指定位置显示数字
函数用法：clockDigitalTube.display_place(seat,num)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示数字</font>

输入参数：

seat：整数，1-4

num：整数，0-9

##### 2.3.1.7  时钟数码管在指定位置点亮小数点
函数用法：clockDigitalTube.displayDP(seat,bool)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示数字</font>

输入参数：

seat：整数，1-4

bool：布尔值，真/假

##### 2.3.1.8  时钟<font style="color:#1a1a1a;">数码管显示时间</font>
函数用法：clockDigitalTube.display_time(hour,minute)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示时间，不支持自计时，需要添加变量；右对齐</font>

输入参数：

hour：整数，0-23

minute：整数，0-59





<font style="color:rgb(38, 38, 38);"></font>

