## 注意事项
**<font style="color:#DF2A3F;">模块名</font>**<font style="color:#DF2A3F;">:</font><font style="color:#DF2A3F;"> </font>

E2

**<font style="color:#DF2A3F;">导入方式</font>**<font style="color:#DF2A3F;">：</font>

from tqpy import *

set_extend_board("E2")

**<font style="color:#DF2A3F;">port：</font>**

由于类型比较多，输入Pin口时，需要完整输入：例如D0/P0/S0

数字类：D0-D7

舵机：S0-S7

模拟类：P0-P3

IIC：P4-P7（不用写Pin口）

## 传感器
### 数字类
#### 磁敏传感器
函数用法：magnetometer.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">检测是否有磁铁</font>

输入参数：<font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：检测到磁铁</font>

<font style="color:#333333;">False：未检测到磁铁</font>

#### 倾斜传感器
函数用法：generaltouch.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">检测传感器是否倾斜</font>

输入参数：<font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：传感器</font><font style="color:#333333;">倾斜</font>

<font style="color:#333333;">False：传感器不</font><font style="color:#333333;">倾斜</font>

#### 碰撞传感器
函数用法：collision.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">检测传感器是否被碰撞</font>

输入参数：<font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：传感器</font><font style="color:#333333;">被碰撞</font>

<font style="color:#333333;">False：传感器没有</font><font style="color:#333333;">被碰撞</font>

#### <font style="color:#333333;">红外测障传感器</font>
<font style="color:#333333;">函数用法：obstacle.get_state(</font><font style="color:#333333;">port</font><font style="color:#333333;">)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">检测传感器前方是否有障碍</font>

<font style="color:#333333;">输入参数：</font><font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：传感器</font><font style="color:#333333;">前方有障碍</font>

<font style="color:#333333;">False：传感器</font><font style="color:#333333;">前方</font><font style="color:#333333;">没有</font><font style="color:#333333;">障碍</font>

#### 人体红外传感器
函数用法：PIR.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">在一定范围内，是否检测到人</font>

<font style="color:rgb(0, 0, 0);">感应范围：（上电需静置10s）感应距离6m左右，感应角度100°</font>

输入参数：<font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：检测到人</font>

<font style="color:#333333;">False：未检测到人</font>

#### 触摸传感器
函数用法：touch.get_state(<font style="color:#333333;">port</font>) 

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取触摸传感器状态</font>

输入参数：<font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True，触摸到了</font>

<font style="color:#333333;">False，没有触摸到</font>

#### 按钮传感器
函数用法：button.get_state(<font style="color:#333333;">port</font>) 

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">判断按钮传感器是否被按下</font>

输入参数：<font style="color:#333333;">字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：被按下</font>

<font style="color:#333333;">False ：未按下</font>

#### 双路循迹传感器
函数用法：trace.get_state(<font style="color:#333333;">port,</font>dir,color)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">获取双路循迹传感器检测状态</font>

输入参数：

<font style="color:#333333;">port：字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">dir：整数</font>

<font style="color:#262626;background-color:#FFFFFF;">获取哪一路的状态：左路：0；右路：1</font>

<font style="color:#333333;">color：黑色：0；白色：1</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：检测到对应颜色</font>

<font style="color:#333333;">False：未检测到对应颜色</font>

:::info
<font style="color:rgb(0, 0, 0);">探测距离（探头底部离地距离）：1-5cm（0.5cm以下为盲区），推荐1-2.5cm</font>

:::

#### 循迹传感器
函数用法：single_trace.get_state(port)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">获取循迹传感器检测状态</font>

输入参数：

<font style="color:#333333;">port：字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：检测到对应颜色</font>

<font style="color:#333333;">False：未检测到对应颜色</font>

:::info
<font style="color:rgb(0, 0, 0);">探测距离（探头底部离地距离）：1-5cm（0.5cm以下为盲区），推荐1-2.5cm</font>

:::

#### 数字水滴传感器
函数用法：DigitalRainSensor.get_state(port)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">获取数字水滴传感器检测状态</font>

输入参数：

<font style="color:#333333;">port：字符串，接口"D0"~"D7"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：检测到水滴</font>

<font style="color:#333333;">False：未检测到水滴</font>

#### 数字风扇
函数用法：digitalFan.set_state(port,state)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">控制风扇打到相应的状态</font>

输入参数：

<font style="color:#333333;">port：字符串，接口"D0"~"D7"</font>

<font style="color:#333333;">state：字符串，on或者off</font>

### 模拟类
#### 烟雾传感器(值)
函数用法：smokeSensor.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取烟雾传感器检测到的烟雾浓度</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### 烟雾传感器(状态)
函数用法：smokeSensor.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">检测是否有烟雾</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：布尔值</font>

<font style="color:#333333;">True：检测到烟雾</font>

<font style="color:#333333;">False：未检测到烟雾</font>

#### <font style="color:#1a1a1a;">薄膜压力传感器</font>
函数用法： filmPressure.get_value("P0")

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取薄膜压力传感器的检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#DF2A3F;">返回值：整数，0-1023</font>

#### 摇杆传感器
函数用法：joystick.get_value(port, left_or_right)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">获取摇杆传感器检测状态</font>

输入参数：

<font style="color:#333333;">port：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#262626;background-color:#FFFFFF;">left_or_right：整数</font>

<font style="color:#262626;background-color:#FFFFFF;">获取哪一路的状态：左路：0；右路：1</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font><font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">光线传感器</font>
函数用法： light.get_intensity(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取光线传感器的检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">紫外线传感器</font>
<font style="color:#333333;">函数用法： rotarySwitch.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取旋钮传感器的检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">旋钮传感器</font>
<font style="color:#333333;">函数用法： uv.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取紫外线传感器的检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#1a1a1a;">火焰传感器（值）</font>
函数用法：flameSensor.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取火焰传感器检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">火焰传感器（状态）</font>
函数用法：flameSensor.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">检测是否有火焰</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：布尔值</font>

<font style="color:#333333;">True：检测到火焰</font>

<font style="color:#333333;">False：未检测到火焰</font>

#### <font style="color:#1a1a1a;">水滴传感器（值）</font>
函数用法：rainSensor.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取水滴传感器检测到的水滴量数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">水滴传感器（状态）</font>
函数用法：rainSensor.get_state(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">检测是否有水滴</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">True：检测到水滴</font>

<font style="color:#333333;">False：未检测到水滴</font>

#### <font style="color:#333333;"></font><font style="color:#1a1a1a;">水位高度传感器</font>
<font style="color:#333333;">函数用法： waterLevel.get_value(</font><font style="color:#333333;">port</font><font style="color:#333333;">)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取水位高度传感器检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">土壤湿度传感器</font>
函数用法：soilHumidity.get_value(<font style="color:#333333;">port</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取土壤湿度传感器检测到的数值</font>

输入参数：<font style="color:#333333;">字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">酒精传感器（值）</font>
<font style="color:#333333;">函数用法： alcohol.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取酒精传感器检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">酒精传感器（状态）</font>
<font style="color:#333333;">函数用法：alcohol.get_state(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">检测是否有酒精</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">True：检测到酒精</font>

<font style="color:#333333;">False：未检测到酒精</font>

#### <font style="color:#1a1a1a;">一氧化碳传感器（值）</font>
<font style="color:#333333;">函数用法： co.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取一氧化碳传感器检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">一氧化碳传感器（状态）</font>
<font style="color:#333333;">函数用法：co.get_state(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">检测是否有一氧化碳</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">True：检测到</font><font style="color:#1a1a1a;">一氧化碳</font>

<font style="color:#333333;">False：未检测到</font><font style="color:#1a1a1a;">一氧化碳</font>

#### <font style="color:#1a1a1a;">二氧化碳传感器（值）</font>
<font style="color:#333333;">函数用法： co2.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取二氧化碳传感器检测到的数值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0-1023</font>

#### <font style="color:#1a1a1a;">二氧化碳传感器（状态）</font>
<font style="color:#333333;">函数用法：co2.get_state(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">检测是否有二氧化碳</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">True：检测到</font><font style="color:#1a1a1a;">二氧化碳</font>

<font style="color:#333333;">False：未检测到</font><font style="color:#1a1a1a;">二氧化碳</font>

#### <font style="color:#1a1a1a;">双路循迹传感器（值）</font>
<font style="color:#1a1a1a;">函数用法：trace.get_value('P1', 0)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">获取双路循迹传感器检测到的灰度值</font>

<font style="color:#1a1a1a;">输入参数：</font>

<font style="color:#333333;">port：字符串，接口"P1"~"P3"</font>

<font style="color:#262626;background-color:#FFFFFF;">left_or_right：左路：0；右路：1</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font><font style="color:#000000;">检测到的灰度值</font>

:::info
<font style="color:rgb(0, 0, 0);">探测距离（探头底部离地距离）：1-5cm（0.5cm以下为盲区），推荐1-2.5cm</font>

:::

#### <font style="color:#1a1a1a;">声音传感器（值）</font>
<font style="color:#333333;">函数用法：voice.get_value(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">检测是否有二氧化碳</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回：</font>

<font style="color:#333333;">True：检测到的音量</font>

#### <font style="color:#1a1a1a;">模数转换</font>
<font style="color:#333333;">函数用法：sgm58031.get_data(index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取指定端口的模拟值</font>

<font style="color:#333333;">输入参数：字符串，接口"A0" "A1" "A2" "A3"</font>

<font style="color:#333333;">返回：端口的模拟值</font>

### IIC类
#### <font style="color:#1a1a1a;">温度传感器</font>
<font style="color:#333333;">函数用法：temperature.get_temp()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取温度检测到的值</font>

<font style="color:#333333;">输入参数：无</font>

<font style="color:#333333;">读值范围：</font><font style="color:rgb(0, 0, 0);">温度-40~+120℃</font>

<font style="color:#333333;">返回值：小数</font>

#### <font style="color:#1a1a1a;">温湿度传感器</font>
函数用法：DHT.get_value("temperature")

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取温湿度检测到的值</font>

输入参数：<font style="color:#333333;">字符串</font>

<font style="color:#333333;">温度："</font>temperature"

<font style="color:#333333;">湿度："</font>humidity"

<font style="color:#333333;">读值范围：</font><font style="color:rgb(0, 0, 0);">湿度0-100%RH，温度-40~+120℃</font>

<font style="color:#333333;">返回值：小数</font>

#### <font style="color:#1a1a1a;">颜色识别传感器（R/G/B值）</font>
函数用法： colorSensor.get_color(<font style="color:#333333;">color</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">检测R/G/B的值</font>

输入参数：<font style="color:#333333;">字符串</font>

<font style="color:#333333;">color："R" "G" "B"</font>

<font style="color:#333333;">返回值：整数，0-255</font>

#### <font style="color:#1a1a1a;">颜色识别传感器（检测颜色）</font>
函数用法： colorSensor.is_color(<font style="color:#333333;">color</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">检测是否是所选颜色</font>

输入参数：<font style="color:#333333;">字符串</font>

<font style="color:#333333;">color：</font><font style="color:#333333;">“red”、"orange" 、“yellow”、“green”、“bule” 、“purple”</font>

<font style="color:#333333;">可以检测的颜色值是：红、橙、黄、绿、蓝、紫</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：布尔值</font>

<font style="color:#333333;">True：</font><font style="color:#333333;">物体颜色【是】所选的测试颜色</font>

<font style="color:#333333;">False：物体颜色【不是】所选的测试颜色</font>

#### <font style="color:#1a1a1a;">四路巡线传感器</font>
<font style="color:#333333;">函数用法： four_trace.get_state(self, index, option)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取对应引脚识别颜色</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">index: 字符串: "T0"-"T3"</font>

<font style="color:#333333;">option:数字:黑-1, 白-0</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：布尔值</font>

<font style="color:#333333;">True：</font><font style="color:#333333;">物体颜色【是】所选的测试颜色</font>

<font style="color:#333333;">False：物体颜色【不是】所选的测试颜色</font>

### <font style="color:#333333;">串口类</font>
#### 北斗导航传感器(获取纬度)
<font style="color:#333333;">函数用法：beidou.Get_latitude(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取当前传感器位置所在纬度</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值:列表</font>

#### <font style="color:#333333;">北斗导航传感器(获取经度)</font>
<font style="color:#333333;">函数用法：beidou.Get_longitude(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">获取当前传感器位置所在</font><font style="color:#333333;">经度</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值:列表</font>

#### <font style="color:#333333;">串口寻迹传感器</font>
<font style="color:#333333;">函数用法：beidou.Get_value(port,index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取对应引脚识别是否是黑色</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">index: 字符串: "T0"-"T3"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：引脚识别为黑色</font>

<font style="color:#333333;">False：引脚识别不为黑色</font>

#### 离线语音识别传感器
<font style="color:#333333;">函数用法：offlineVoice.get_instructions(port,)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">传感器货物全部指令</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

#### <font style="color:#333333;">离线语音识别传感器（检测指令）</font>
<font style="color:#333333;">函数用法：offlineVoice.dete_instructions(port, num)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取传感器识别的指令</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">index: 指令代表的数字</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：</font>

<font style="color:#333333;">True：传感器识别到指令</font>

<font style="color:#333333;">False：传感器未识别到指令</font>

#### 风速传感器(风速值)
<font style="color:#333333;">函数用法：windSpeed.get_speed(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取当前风速值</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">1023</font>

#### <font style="color:#262626;background-color:#FFFFFF;">风速传感器(风速等级)</font>
<font style="color:#333333;">函数用法：windSpeed.get_level(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取当前风速等级</font>

<font style="color:#333333;">输入参数：字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值：整数，0</font><font style="color:#000000;">-</font><font style="color:#333333;">12</font>

#### <font style="color:#262626;background-color:#FFFFFF;">指纹识别模块(注册)</font>
<font style="color:#333333;">函数用法：finger.Auto_register(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">注册指纹</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port:字符串，接口"P0" "P1" "P2" "P3"</font>

返回值:

数字:指纹注册ID

#### <font style="color:#262626;background-color:#FFFFFF;">指纹识别模块(识别是否存在)</font>
<font style="color:#333333;">函数用法：finger.Verify(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">识别指纹</font><font style="color:#262626;background-color:#FFFFFF;">是否存在</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port:字符串，接口"P0" "P1" "P2" "P3"</font>

<font style="color:#333333;">返回值:</font>

<font style="color:#333333;">True：识别成功</font>

<font style="color:#333333;">False：识别失败</font>

#### <font style="color:#262626;background-color:#FFFFFF;">指纹识别模块(识别ID)</font>
<font style="color:#333333;">函数用法：finger.Get_verify_id(port)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">识别指纹所代表的ID</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port:字符串，接口"P0" "P1" "P2" "P3"</font>

返回值:

数字:指纹注册ID

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

#### 16通道遥控器按钮检测
函数用法：rrc16.is_key_press(button_name) 

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取16通道遥控器按钮是否按下的结果</font>

输入参数：<font style="color:#333333;">按钮名，1-8</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：布尔值</font>

<font style="color:#333333;">True，按下</font>

<font style="color:#333333;">False，没有按下</font>

#### <font style="color:#333333;">16通道遥控器摇杆左摇杆推向检测</font>
<font style="color:#333333;">函数用法：rc16.get_joystick_left(direction) </font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取16通道遥控器左摇杆推向哪一个方向</font>

<font style="color:#333333;">输入参数：遥杆推向，"W" "A" "S" "D"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：布尔值</font>

<font style="color:#333333;">True，左遥感推向指定方向了</font>

<font style="color:#333333;">False，左遥感没有推向指定方向</font>

#### <font style="color:#333333;">16通道遥控器摇杆右摇杆推向检测</font>
<font style="color:#333333;">函数用法：rc16.get_joystick_right(direction) </font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">获取16通道右遥控器摇杆推向哪一个方向</font>

<font style="color:#333333;">输入参数：遥杆推向，"I" "J" "K" "L"</font>

<font style="color:#262626;background-color:#FFFFFF;">返回值：布尔值</font>

<font style="color:#333333;">True，右遥感推向指定方向了</font>

<font style="color:#333333;">False，右遥感没有推向指定方向</font>

## 执行器
### 数字类
#### 加湿器
函数用法：humidifier.set_state(<font style="color:#333333;">port，state</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">控制加湿器开关</font>

输入参数：

<font style="color:#333333;">port：整数，接口D0-D7</font>

<font style="color:#333333;">state：字符串，打开：on；关闭：off</font>

#### <font style="color:#333333;">有源蜂鸣器</font>
<font style="color:#333333;">函数用法：activeBuzzer.set_state(port，state)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置有源蜂鸣器状态</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port：整数，接口D0-D7</font>

<font style="color:#333333;">state：字符串，打开：on；关闭：off</font>

#### <font style="color:#1a1a1a;">LED</font>
函数用法：led.set_state(<font style="color:#333333;">port，state</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">单色led灯</font>

输入参数：

<font style="color:#333333;">port：整数，接口D0-D7</font>

<font style="color:#333333;">state：字符串，点亮：on；熄灭：off</font>

#### <font style="color:#1a1a1a;">灯串模块</font>
函数用法：lightStrip.set_state(<font style="color:#333333;">port，state</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">点亮/熄灭灯串</font>

输入参数：

<font style="color:#333333;">port：整数，接口D0-D7</font>

<font style="color:#333333;">state：字符串，点亮：on；熄灭：off</font>



### 数字类/PWM脉冲驱动
#### <font style="color:#1a1a1a;">Geekservo舵机</font>
函数用法：geekServo.angle(<font style="color:#333333;">port,angle</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置舵机角度</font>

输入参数：

<font style="color:#333333;">port：整数，接口S0-S7</font>

<font style="color:#333333;">angle：</font>**<font style="color:#DF2A3F;">0-270</font>**

#### <font style="color:#1a1a1a;">蜂鸣器模块（音调）</font>
函数用法：buzzer.set_note(<font style="color:#000000;">port,tone, duration</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#000000;">蜂鸣器播放指定音调</font>

输入参数：

<font style="color:#333333;">port：整数，接口P1-P3</font>

<font style="color:#000000;">tone：整数，E5-B8：3-28</font>

<font style="color:#000000;">duration：整数：1/4：4；1/2：8；1：16；2：32</font>

<font style="color:#000000;">持续几个base（拍音调持续时间， base时间是1/4拍，125ms）</font>

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

#### <font style="color:#1a1a1a;">电动推杆</font>
函数用法： pushRod.set_speed(port, dir, speed)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置电动推杆的方向与速度</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P3</font>

<font style="color:#333333;">dir:	0 正转   1 反转</font>

<font style="color:#333333;">speed:  1 低速   2 中速   3 高速</font>

#### <font style="color:#1a1a1a;">电磁铁</font>
函数用法：electromagnet.set_state(<font style="color:#333333;">port,state</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置直流电机转向和转速</font>

输入参数：

<font style="color:#333333;">port：整数，接口M0-M7</font>

state:字符串,打开:"on",关闭:"off"

#### <font style="color:#1a1a1a;">风扇模块</font>
函数用法： fan.set_speed(<font style="color:#333333;">port,speed</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置风扇的转速</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P3</font>

<font style="color:#333333;">speed：0-100</font>

#### <font style="color:#1a1a1a;">直流电机</font>
函数用法：motor.speed(<font style="color:#333333;">port,dir,speed</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置直流电机转向和转速</font>

输入参数：

<font style="color:#333333;">port：整数，接口M0-M7</font>

<font style="color:#333333;">dir：顺时针：0；逆时针：1</font>

<font style="color:#333333;">speed：0-100</font>

#### <font style="color:#1a1a1a;">数字舵机</font>
函数用法：servo.angle(<font style="color:#333333;">port,angle</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置舵机角度</font>

输入参数：

<font style="color:#333333;">port：字符串，接口S0-S7</font>

<font style="color:#333333;">angle：</font>**<font style="color:#DF2A3F;">0-180</font>**

#### <font style="color:#1a1a1a;">继电器</font>
<font style="color:#333333;">函数用法：relay.set_state(port, state)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#1a1a1a;">设置继电器状态</font>

<font style="color:#333333;">输入参数：字符串，P0-P3,D0-D7</font>

### 串口类
#### <font style="color:#333333;">TTS语音合成模块(控制功能)</font>
<font style="color:#333333;">函数用法：voicetts.control(port, function)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">控制TTS语音合成模块播放功能</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port：字符串，接口P0-P3</font>

<font style="color:#333333;">function：字符串,想要控制的功能,打开:"on",关闭:"off",暂停:"pause"</font>

#### <font style="color:#333333;">TTS语音合成模块(音量,语音速度,语调设置)</font>
<font style="color:#333333;">函数用法：voicetts.set_function(port, vol, speed, tone)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">控制TTS语音合成模块的音量,语音速度,语调</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port：字符串，接口P0-P3</font>

<font style="color:#333333;">vol：数字,0-9,音量大小</font>

<font style="color:#333333;">speed:数字,0-9,播音速度</font>

<font style="color:#333333;">tone:语调,数字,0-9,播放声音语调</font>

#### <font style="color:#333333;">TTS语音合成模块(播放内置音频)</font>
<font style="color:#333333;">函数用法：voicetts.send_bell_tone(port,index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">控制TTS语音合成模块播放内置铃声</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port：字符串，接口P0-P3</font>

<font style="color:#333333;">index：数字 ,1-15,播放内置音频编号</font>

#### <font style="color:#333333;">TTS语音合成模块(播放语音)</font>
<font style="color:#333333;">函数用法：voicetts.text_to_speech(port, message)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">控制TTS语音合成模块播放合成文字</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">port：字符串，接口P0-P3</font>

<font style="color:#333333;">message：字符串,想要播放的文字</font>

#### 
### 数字类/单总协议输出
#### <font style="color:#1a1a1a;">全彩灯模块</font>
函数用法：RGB.set_color(<font style="color:#333333;">port,R,G,B,brightness</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置全彩灯颜色和亮度</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P3</font>

<font style="color:#333333;">R,G,B</font><font style="color:#333333;">：整数，</font><font style="color:#333333;">三原色， 每个元素的范围0-255</font>

<font style="color:#333333;">brightness</font><font style="color:#333333;">：0-100</font>

#### 4*4点阵灯（每个灯可亮不同颜色）
函数用法：ledMatrix.show(<font style="color:#333333;">port,brightness,image</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">显示指定图案（不同色）</font>

输入参数：

<font style="color:#333333;">port：字符串，接口P0-P3</font>

<font style="color:#333333;">brightness</font><font style="color:#333333;">：0-100</font>

<font style="color:#333333;">image：一个三基色RGB标识一个点，image 是一个二维列表</font>

<font style="color:#333333;">image = </font>

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2023/png/10390217/1677056652424-977b0dd5-fb21-4d0b-85fa-f0295fd9f70d.png)

#### 2.3.2  4*4点阵灯（统一颜色）
函数用法：ledMatrix.show_uniformcolor(<font style="color:#333333;">port,color,brightness,image</font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">显示自定义图案（同色）</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P3</font>

<font style="color:#333333;">color：整数，</font><font style="color:#333333;">三原色， 每个元素的范围0-255</font>

<font style="color:#333333;">brightness</font><font style="color:#333333;">：0-100</font>

<font style="color:#333333;">image：列表，</font><font style="color:#000000;">['0000','0000','0000','0000']</font>

<font style="color:#333333;">熄灭：0；点亮：1</font>



#### 2.3.3 12灯灯带
函数用法：RGBStrip.set_color_separate(port, <font style="color:#333333;">brightness</font>, [[<font style="color:#333333;">color1</font>],[<font style="color:#333333;">color2</font>],[<font style="color:#333333;">color3</font>],[<font style="color:#333333;">color4</font>],[<font style="color:#333333;">color5</font>],[<font style="color:#333333;">color6</font>],[<font style="color:#333333;">color7</font>],[<font style="color:#333333;">color8</font>],[<font style="color:#333333;">color9</font>],[<font style="color:#333333;">color10</font>],[<font style="color:#333333;">color11</font>],[<font style="color:#333333;">color12</font>]])

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">显示自定义灯串图案</font>

输入参数：

<font style="color:#333333;">port：整数，接口P0-P3</font>

<font style="color:#333333;">color：整数，</font><font style="color:#333333;">三原色， 每个元素的范围0-255</font>

<font style="color:#333333;">brightness：0-100</font>

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

#### 2.4.2  OLED显示屏
##### 2.4.2.1  显示屏启用
函数用法：oled.on()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管启用，除停用、清屏外，其他函数中均包含此函数</font>

输入参数：无

##### 2.4.2.2  显示屏<font style="color:#1a1a1a;">停用</font>
函数用法：oled.off()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管停用，停用不清除内存</font>

输入参数：无

##### 2.4.2.3  显示屏<font style="color:#1a1a1a;">清屏</font>
函数用法：oled.clear()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟</font><font style="color:#333333;">数码管清屏，清除掉内存并黑屏</font>

输入参数：无

##### 2.4.2.4  显示屏在指定坐标显示文本
函数用法：oled.draw_text(text, x, y)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：时钟数码管显示数字</font>

输入参数：

text：字符串，str()

x：整数，x坐标

y：整数，y坐标

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

