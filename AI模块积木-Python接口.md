## 注意事项
**<font style="color:#DF2A3F;">模块名</font>**<font style="color:#DF2A3F;">:</font><font style="color:#DF2A3F;"> </font>

AI module

**<font style="color:#DF2A3F;">导入方式</font>**<font style="color:#DF2A3F;">：</font>

通过积木导入

from tqpy import *

set_extend_board("E2")

:::info
<font style="color:rgb(38, 38, 38);">E1/E2/E3都可以连接，AI模块均为I2C,连接I2C接口即可,无需选择port端口</font>

:::

# 连接拓展板
## 设置连接拓展板
函数用法：set_extend_board(board_name)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置与AI模块连接的拓展板</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">board_name：字符串，"E1" "E2" "E3"</font>

# 补光灯
## 补光灯打开
函数用法：ai_light.on(<font style="color:#333333;"></font>)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开补光灯</font>

## <font style="color:#333333;">补光灯关闭</font>
<font style="color:#333333;">函数用法：ai_light.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭补光灯</font>

## <font style="color:#333333;">设置补光灯颜色、亮度</font>
<font style="color:#333333;">函数用法：ai_light.set_color(color,level)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置补光灯颜色、亮度</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">color:字符串,补光灯颜色,红色:"red",黑色:"black",绿色:"green",黄色:"yellow",蓝色:"blue",紫色:"purple", 青色:"cyan", 白色:"white"</font>

<font style="color:#333333;">level:数字:0-15</font>

# 摄像头
## 设置摄像头反转
函数用法：ai_camera.set_rotate(option)

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置摄像头是否反转</font>

<font style="color:#333333;">输入参数：</font>

<font style="color:#333333;">option：0或1</font>

# <font style="color:#333333;">颜色识别</font>
## 颜色识别打开
函数用法：ai_color.on()

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开颜色识别</font>

## <font style="color:#333333;">颜色识别关闭</font>
<font style="color:#333333;">函数用法：ai_color.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭颜色识别</font>

## <font style="color:#333333;">颜色识别预置识别区域网格数量及大小</font>
<font style="color:#333333;">函数用法：ai_color.set_grid(number, size)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置颜色识别网格数量与大小</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">number:字符串,网格数量,</font><font style="color:rgb(51, 51, 51);">水平方向数量 x 垂直方向数量：1x1、2x2、3x3、4x4、5x5、1x10、2x10、6x1、6x2</font>

<font style="color:rgb(51, 51, 51);">size:字符串,网格大小,水平方向像素 x 垂直方向像素:2x2、4x4、8x8、16x16、32x32</font>

## <font style="color:#333333;">获取颜色识别全部信息</font>
<font style="color:#333333;">函数用法：ai_color.get_value()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的颜色的全部信息，并在底层保存</font>



## <font style="color:#333333;">获取颜色识别到颜色的数量</font>
<font style="color:#333333;">函数用法：ai_color.get_color_num(color)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取指定颜色检测到的具体数量</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">color:指定颜色:</font><font style="color:#333333;">红色:"red",黑色:"black",绿色:"green",黄色:"yellow",蓝色:"blue", 白色:"white"</font>

返回值:

数字:范围:<font style="color:rgb(51, 51, 51);">0-25</font>

## <font style="color:#333333;">获取</font><font style="color:rgb(51, 51, 51);">是否检测到指定颜色</font>
<font style="color:#333333;">函数用法：ai_color.is_detected_color(color,index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">判断是否检测到指定颜色</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">color:指定颜色:</font><font style="color:#333333;">红色:"red",黑色:"black",绿色:"green",黄色:"yellow",蓝色:"blue", 白色:"white"</font>

<font style="color:#333333;">index:0-25</font>

返回值:

true:识别到了指定颜色

false:没有识别到指定颜色

## <font style="color:#333333;">获取检测到的具体的R\G\B值或者具体的颜色</font>
<font style="color:#333333;">函数用法：ai_color.ai_color.detected_rgb_or_lable(RGB_COLOR, index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">返回检测到的具体的R\G\B值或者具体的颜色</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">RGB_COLOR:字符串:R或G或B或COLOR</font>

<font style="color:#333333;">index:范围:</font><font style="color:rgb(51, 51, 51);">0-25</font>

返回值:

true:识别到了指定颜色

false:没有识别到指定颜色

# <font style="color:#333333;">色块识别</font>
## <font style="color:#333333;">色块</font><font style="color:rgb(51, 51, 51);">识别打开</font>
<font style="color:rgb(51, 51, 51);">函数用法：ai_blob.on()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开颜色识别</font>

## <font style="color:#333333;">色块</font><font style="color:#333333;">识别关闭</font>
<font style="color:#333333;">函数用法：ai_blob.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭颜色识别</font>

## <font style="color:#333333;">设置</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别性能</font>
<font style="color:#333333;">函数用法：ai_blob.set_performance(level)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置色块识别性能</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">level:字符串,灵敏:"speed",均衡:"balance",准确:"accuracy"</font>

## <font style="color:#333333;">设置</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别最大数量</font>
<font style="color:#333333;">函数用法：ai_blob.set_max_num(number)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置色块识别可识别到的最大数量</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">number:数字,1-5</font>

## <font style="color:#333333;">设置</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别颜色</font>
<font style="color:#333333;">函数用法：ai_blob.set_detect_color(color)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置色块识别可识别到的颜色</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:rgb(51, 51, 51);">color:指定颜色:</font><font style="color:#333333;">红色:"red",黑色:"black",绿色:"green",黄色:"yellow",蓝色:"blue", 白色:"white"</font>

## <font style="color:#333333;">设置</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别最小范围</font>
<font style="color:#333333;">函数用法：ai_blob.set_detect_color(size)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置色块识别最小范围</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">size</font><font style="color:rgb(51, 51, 51);">:最小范围设置:2x2、4x4、8x8、16x16、32x32,64x64,128x128</font>

## <font style="color:#333333;">获取</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别全部信息</font>
<font style="color:#333333;">函数用法：ai_blob.get_value()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的</font><font style="color:#333333;">色块</font><font style="color:rgb(51, 51, 51);">的全部信息，并在底层保存</font>

## <font style="color:#333333;">获取</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别的颜色</font>
<font style="color:#333333;">函数用法：ai_blob.is_detected_color(color)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">判断视觉模块检测到的色块颜色是否和指定的颜色一致</font>

输入参数:

color:<font style="color:rgb(51, 51, 51);">指定颜色:</font><font style="color:#333333;">红色:"red",黑色:"black",绿色:"green",黄色:"yellow",蓝色:"blue", 白色:"white"</font>

## <font style="color:#333333;">获取</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别检测到的数量</font>
<font style="color:#333333;">函数用法：ai_blob.get_blob_num()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的</font><font style="color:#333333;">色块</font><font style="color:rgb(51, 51, 51);">的全部信息，并在底层保存</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:rgb(51, 51, 51);">数字,范围:0-10</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">色块</font><font style="color:#333333;">识别</font><font style="color:rgb(51, 51, 51);">的指定信息</font>
<font style="color:#333333;">函数用法：ai_blob.detection_blob(type,index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的色块的指定信息</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">type:字符串,标签:"l",宽度:"w",高度:"h",坐标x:"x",坐标y:"y"</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 0-9</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:rgb(51, 51, 51);">数字,范围:0-10</font>

# 线条识别
## <font style="color:#333333;">线条</font><font style="color:rgb(51, 51, 51);">识别打开</font>
<font style="color:rgb(51, 51, 51);">函数用法：ai_blob.on()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开颜色识别</font>

## <font style="color:#333333;">线条</font><font style="color:#333333;">识别关闭</font>
<font style="color:#333333;">函数用法：ai_blob.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭颜色识别</font>

## <font style="color:#333333;">设置</font><font style="color:#333333;">线条</font><font style="color:#333333;">识别性能</font>
<font style="color:#333333;">函数用法：ai_line.set_performance(level)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置</font><font style="color:#333333;">线条</font><font style="color:#333333;">识别性能</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">level:字符串,灵敏:"speed",均衡:"balance",准确:"accuracy"</font>

## <font style="color:#333333;">设置</font><font style="color:#333333;">线条</font><font style="color:#333333;">识别最大数量</font>
<font style="color:#333333;">函数用法：ai_line.set_max_num(number)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置</font><font style="color:#333333;">线条</font><font style="color:#333333;">识别可识别到的最大数量</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">number:数字,1-5</font>

## <font style="color:#333333;">获取</font><font style="color:#333333;">线条</font><font style="color:#333333;">识别全部信息</font>
<font style="color:#333333;">函数用法：ai_line.get_value()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的</font><font style="color:#333333;">线条</font><font style="color:rgb(51, 51, 51);">的全部信息，并在底层保存</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">线条</font><font style="color:#333333;">识别</font><font style="color:rgb(51, 51, 51);">的指定信息</font>
<font style="color:#333333;">函数用法：ai_line.detection_line(type,index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的线条的指定信息</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">type:字符串,</font>起点x坐标:"x_start",<font style="color:rgb(51, 51, 51);">终点x坐标:"x_end",起点y坐标:"y_start",终点y坐标:"y_end",倾斜角度:"angle"</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 0-4</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:rgb(51, 51, 51);">数字,范围:0-10</font>

# 二维码识别
## <font style="color:#333333;">二维码</font><font style="color:rgb(51, 51, 51);">识别打开</font>
<font style="color:rgb(51, 51, 51);">函数用法：ai_qrcode.on()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开二维码识别</font>

## <font style="color:#333333;">二维码</font><font style="color:#333333;">识别关闭</font>
<font style="color:#333333;">函数用法：ai_qrcode.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭二维码识别</font>

## <font style="color:#333333;">二维码识别全部信息</font>
<font style="color:#333333;">函数用法：ai_qrcode.get_value()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置</font><font style="color:#333333;">线条</font><font style="color:#333333;">识别性能</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">二维码</font><font style="color:#333333;">识别</font><font style="color:rgb(51, 51, 51);">的指定符号</font>
<font style="color:#333333;">函数用法：ai_qrcode.is_detected_symbol(sign)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的二维码的指定信息</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">sign：符号，ASCLL码表中的符号，如"!" "#" "%"等</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">信息</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定信息</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">二维码</font><font style="color:#333333;">识别</font><font style="color:rgb(51, 51, 51);">的指定数字</font>
<font style="color:#333333;">函数用法：ai_qrcode.is_detected_number(num)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的二维码的指定信息</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">num：数字，0-9</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">信息</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定信息</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">二维码</font><font style="color:#333333;">识别</font><font style="color:rgb(51, 51, 51);">的指定小写英文字母</font>
<font style="color:#333333;">函数用法：ai_qrcode.is_detected_lowercase(letter)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的二维码的指定小写英文字母</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">sign：符号，ASCLL码表中的小</font><font style="color:rgb(51, 51, 51);">写英文字母</font><font style="color:#333333;">，如"a" "b" "c"等</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">信息</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定信息</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">二维码</font><font style="color:#333333;">识别</font><font style="color:rgb(51, 51, 51);">的指定大写英文字母</font>
<font style="color:#333333;">函数用法：ai_qrcode.is_detected_capital(letter)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的二维码的指定大写英文字母</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">sign：符号，ASCLL码表中的大</font><font style="color:rgb(51, 51, 51);">写英文字母</font><font style="color:#333333;">，如"A" "B" "C"等</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">信息</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定信息</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">二维码</font><font style="color:#333333;">识别</font><font style="color:rgb(51, 51, 51);">的指定符号的具体信息值</font>
<font style="color:#333333;">函数用法：ai_qrcode.detection_qrcode(sign)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的二维码的指定符号的具体信息值</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">sign：信息值，"结果r" "字符长度l" "宽度w" "高度h" "坐标x" "坐标y" </font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:rgb(51, 51, 51);">字符串或数字，具体的信息值</font>

# <font style="color:#333333;">标签识别</font>
## <font style="color:#333333;">标签</font><font style="color:rgb(51, 51, 51);">识别打开</font>
<font style="color:rgb(51, 51, 51);">函数用法：ai_apriltag.on()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开标签识别</font>

## <font style="color:#333333;">标签识别关闭</font>
<font style="color:#333333;">函数用法：ai_apriltag.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭标签识别</font>

## <font style="color:#333333;">设置标签识别性能</font>
<font style="color:#333333;">函数用法：ai_apriltag.set_performance(level)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">设置标签识别性能</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">level:字符串,灵敏:"speed",均衡:"balance",准确:"accuracy"</font>

## <font style="color:#333333;">获取标签识别全部信息</font>
<font style="color:#333333;">函数用法：ai_apriltag.get_value(type)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的</font><font style="color:#333333;">标签</font><font style="color:rgb(51, 51, 51);">的全部信息，并在底层保存</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">type:字符串:"16H5","25H9","36H11"</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">标签识别</font><font style="color:rgb(51, 51, 51);">16H5编码检测ID</font>
<font style="color:#333333;">函数用法：ai_apriltag.is_detected_16h5(index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取标签识别16H5编码检测ID</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 0-29</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

true:识别到了指定<font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">标签识别</font><font style="color:rgb(51, 51, 51);">25H9编码检测ID</font>
<font style="color:#333333;">函数用法：ai_apriltag.is_detected_25h9(index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取标签识别25H9编码检测ID</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 0-29</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">标签识别</font><font style="color:rgb(51, 51, 51);">36H11编码检测ID</font>
<font style="color:#333333;">函数用法：ai_apriltag.is_detected_36h11(index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取标签识别36H11编码检测ID</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 0-29</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">标签识别</font><font style="color:rgb(51, 51, 51);">检测到的结果数量</font>
<font style="color:#333333;">函数用法：ai_apriltag.get_apriltag_num(type)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取标签识别检测到的结果数量</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">type:字符串:"16H5","25H9","36H11"</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

数字:<font style="color:rgb(51, 51, 51);">0-25</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">签识识别</font><font style="color:rgb(51, 51, 51);">的指定信息</font>
<font style="color:#333333;">函数用法：ai_apriltag.detection_apriltag(type,index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的线条的指定信息</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">type:字符串,</font><font style="color:#333333;">起点x坐标:"x_start",</font><font style="color:rgb(51, 51, 51);">终点x坐标:"x_end",起点y坐标:"y_start",终点y坐标:"y_end",倾斜角度:"angle"</font>

<font style="color:rgb(51, 51, 51);">type:字符串,标签:"l",宽度:"w",高度:"h",坐标x:"x",坐标y:"y"</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 0-24</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:rgb(51, 51, 51);">字符串或数字，具体的信息值</font>

# <font style="color:#333333;">深度学习</font>
## 深度学习<font style="color:rgb(51, 51, 51);">打开</font>
<font style="color:rgb(51, 51, 51);">函数用法：ai_learn.on()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开深度学习</font>

## <font style="color:#333333;">深度学习关闭</font>
<font style="color:#333333;">函数用法：ai_learn.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭深度学习</font>

## <font style="color:#333333;">获取深度学习全部信息</font>
<font style="color:#333333;">函数用法：ai_learn.get_value()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的</font><font style="color:#333333;">深度学习</font><font style="color:rgb(51, 51, 51);">的全部信息，并在底层保存</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">深度学习检测的ID</font>
<font style="color:#333333;">函数用法：ai_apriltag.is_detected(index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取深度学习检测ID</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 1-25</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## 删除或者对某个ID重新训练
<font style="color:#333333;">函数用法：ai_learn.delete_or_train("type",index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">删除或者对某个ID重新训练</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">type:类型:删除:"delete",训练:"train"</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 1-25</font>

# <font style="color:#333333;">卡片识别</font>
## <font style="color:#333333;">卡片识别</font><font style="color:rgb(51, 51, 51);">开关</font>
<font style="color:rgb(51, 51, 51);">函数用法：ai_card.vision_card(type)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开或关闭卡片识别</font>

<font style="color:#333333;">输入参数:</font>

<font style="color:#333333;">type:打开:"on"关闭:"off"</font>

## <font style="color:#333333;">获取卡片识别全部信息</font>
<font style="color:#333333;">函数用法：</font><font style="color:rgb(51, 51, 51);">ai_card</font><font style="color:#333333;">.get_value()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的</font><font style="color:#333333;">卡片识别</font><font style="color:rgb(51, 51, 51);">的全部信息，并在底层保存</font>

## <font style="color:#333333;">卡片识别到交通标示</font>
<font style="color:#333333;">函数用法：ai_card.detected_traffic_signs(type)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取卡片识别到的交通标示</font>

<font style="color:#262626;background-color:#FFFFFF;">输入参数:</font>

<font style="color:#262626;background-color:#FFFFFF;">type:</font>

| **<font style="color:rgb(33, 37, 41);">分类标签</font>** | **<font style="color:rgb(33, 37, 41);">英文标识</font>** | **<font style="color:rgb(33, 37, 41);">中文含义</font>** | **<font style="color:rgb(33, 37, 41);">分类标签</font>** | **<font style="color:rgb(33, 37, 41);">英文标识</font>** | **<font style="color:rgb(33, 37, 41);">中文含义</font>** |
| :---: | :---: | :---: | :---: | :---: | :---: |
| <font style="color:rgb(33, 37, 41);">1</font> | <font style="color:rgb(33, 37, 41);">Forward</font> | <font style="color:rgb(33, 37, 41);">前进</font> | <font style="color:rgb(33, 37, 41);">2</font> | <font style="color:rgb(33, 37, 41);">Left</font> | <font style="color:rgb(33, 37, 41);">左转</font> |
| <font style="color:rgb(33, 37, 41);">3</font> | <font style="color:rgb(33, 37, 41);">Right</font> | <font style="color:rgb(33, 37, 41);">右转</font> | <font style="color:rgb(33, 37, 41);">4</font> | <font style="color:rgb(33, 37, 41);">Turn Around</font> | <font style="color:rgb(33, 37, 41);">掉头</font> |
| <font style="color:rgb(33, 37, 41);">5</font> | <font style="color:rgb(33, 37, 41);">Park</font> | <font style="color:rgb(33, 37, 41);">停车</font> | <font style="color:rgb(33, 37, 41);">6</font> | <font style="color:rgb(33, 37, 41);">Green</font> | <font style="color:rgb(33, 37, 41);">绿灯</font> |
| <font style="color:rgb(33, 37, 41);">7</font> | <font style="color:rgb(33, 37, 41);">Red</font> | <font style="color:rgb(33, 37, 41);">红灯</font> | <font style="color:rgb(33, 37, 41);">8</font> | <font style="color:rgb(33, 37, 41);">Speed 40</font> | <font style="color:rgb(33, 37, 41);">限速40</font> |
| <font style="color:rgb(33, 37, 41);">9</font> | <font style="color:rgb(33, 37, 41);">Speed 60</font> | <font style="color:rgb(33, 37, 41);">限速60</font> | <font style="color:rgb(33, 37, 41);">10</font> | <font style="color:rgb(33, 37, 41);">Speed 80</font> | <font style="color:rgb(33, 37, 41);">限速80</font> |


<font style="color:#333333;">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## <font style="color:#333333;">卡片识别到圆形符号</font>
<font style="color:#333333;">函数用法：ai_card.detected_graphical_symbol(type)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取卡片识别到的圆形符号</font>

<font style="color:#262626;background-color:#FFFFFF;">输入参数:</font>

<font style="color:#262626;background-color:#FFFFFF;">type:</font>

| **<font style="color:rgb(33, 37, 41);">分类标签</font>** | **<font style="color:rgb(33, 37, 41);">英文标识</font>** | **<font style="color:rgb(33, 37, 41);">中文含义</font>** | **<font style="color:rgb(33, 37, 41);">分类标签</font>** | **<font style="color:rgb(33, 37, 41);">英文标识</font>** | **<font style="color:rgb(33, 37, 41);">中文含义</font>** |
| :---: | :---: | :---: | :---: | :---: | :---: |
| <font style="color:rgb(33, 37, 41);">11</font> | <font style="color:rgb(33, 37, 41);">Check</font> | <font style="color:rgb(33, 37, 41);">对号</font> | <font style="color:rgb(33, 37, 41);">12</font> | <font style="color:rgb(33, 37, 41);">Cross</font> | <font style="color:rgb(33, 37, 41);">叉号</font> |
| <font style="color:rgb(33, 37, 41);">13</font> | <font style="color:rgb(33, 37, 41);">Circle</font> | <font style="color:rgb(33, 37, 41);">圆形</font> | <font style="color:rgb(33, 37, 41);">14</font> | <font style="color:rgb(33, 37, 41);">Square</font> | <font style="color:rgb(33, 37, 41);">方形</font> |
| <font style="color:rgb(33, 37, 41);">15</font> | <font style="color:rgb(33, 37, 41);">Triangle</font> | <font style="color:rgb(33, 37, 41);">三角形</font> | <font style="color:rgb(33, 37, 41);">16</font> | <font style="color:rgb(33, 37, 41);">Plus</font> | <font style="color:rgb(33, 37, 41);">加号</font> |
| <font style="color:rgb(33, 37, 41);">17</font> | <font style="color:rgb(33, 37, 41);">Minus</font> | <font style="color:rgb(33, 37, 41);">减号</font> | <font style="color:rgb(33, 37, 41);">18</font> | <font style="color:rgb(33, 37, 41);">Divide</font> | <font style="color:rgb(33, 37, 41);">除号</font> |


<font style="color:#333333;">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## <font style="color:#333333;">卡片识别到数字</font>
<font style="color:#333333;">函数用法：ai_card.detected_number(type)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：获取卡片识别到的圆形符号</font>

<font style="color:#262626;background-color:#FFFFFF;">输入参数:</font>

<font style="color:#262626;background-color:#FFFFFF;">type:</font>

| **<font style="color:rgb(33, 37, 41);">分类标签</font>** | **<font style="color:rgb(33, 37, 41);">英文标识</font>** | **<font style="color:rgb(33, 37, 41);">中文含义</font>** | **<font style="color:rgb(33, 37, 41);">分类标签</font>** | **<font style="color:rgb(33, 37, 41);">英文标识</font>** | **<font style="color:rgb(33, 37, 41);">中文含义</font>** |
| :---: | :---: | :---: | :---: | :---: | :---: |
| <font style="color:rgb(33, 37, 41);">20</font> | <font style="color:rgb(33, 37, 41);">Num 0</font> | <font style="color:rgb(33, 37, 41);">数字0</font> | <font style="color:rgb(33, 37, 41);">21</font> | <font style="color:rgb(33, 37, 41);">Num 1</font> | <font style="color:rgb(33, 37, 41);">数字1</font> |
| <font style="color:rgb(33, 37, 41);">22</font> | <font style="color:rgb(33, 37, 41);">Num 2</font> | <font style="color:rgb(33, 37, 41);">数字2</font> | <font style="color:rgb(33, 37, 41);">23</font> | <font style="color:rgb(33, 37, 41);">Num 3</font> | <font style="color:rgb(33, 37, 41);">数字3</font> |
| <font style="color:rgb(33, 37, 41);">24</font> | <font style="color:rgb(33, 37, 41);">Num 4</font> | <font style="color:rgb(33, 37, 41);">数字4</font> | <font style="color:rgb(33, 37, 41);">25</font> | <font style="color:rgb(33, 37, 41);">Num 5</font> | <font style="color:rgb(33, 37, 41);">数字5</font> |
| <font style="color:rgb(33, 37, 41);">26</font> | <font style="color:rgb(33, 37, 41);">Num 6</font> | <font style="color:rgb(33, 37, 41);">数字6</font> | <font style="color:rgb(33, 37, 41);">27</font> | <font style="color:rgb(33, 37, 41);">Num 7</font> | <font style="color:rgb(33, 37, 41);">数字7</font> |
| <font style="color:rgb(33, 37, 41);">28</font> | <font style="color:rgb(33, 37, 41);">Num 8</font> | <font style="color:rgb(33, 37, 41);">数字8</font> | <font style="color:rgb(33, 37, 41);">29</font> | <font style="color:rgb(33, 37, 41);">Num 9</font> | <font style="color:rgb(33, 37, 41);">数字9</font> |


<font style="color:#333333;">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">卡片识别</font><font style="color:rgb(51, 51, 51);">检测到的结果数量</font>
<font style="color:#333333;">函数用法：ai_card.get_card_num()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取卡片识别检测到的结果数量</font>

<font style="color:rgb(51, 51, 51);">输入参数:无</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">数字:</font><font style="color:rgb(51, 51, 51);">0-10</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">卡片识别</font><font style="color:rgb(51, 51, 51);">的指定信息</font>
<font style="color:#333333;">函数用法：ai_card.detection_blob(type,index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取并返回视觉模块检测到的色块的指定信息</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">type：字符串,标签:"l",宽度:"w",高度:"h",坐标x:"x",坐标y:"y"</font>

<font style="color:rgb(51, 51, 51);">index：数字:范围 0-9</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:rgb(51, 51, 51);">数字,范围:0-10</font>

<font style="color:#333333;"></font>

# <font style="color:#333333;">人脸识别</font>
## 人脸识别<font style="color:rgb(51, 51, 51);">打开</font>
<font style="color:rgb(51, 51, 51);">函数用法：ai_face.on()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">打开人脸识别</font>

## <font style="color:#333333;">人脸识别关闭</font>
<font style="color:#333333;">函数用法：ai_face.off()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:#333333;">关闭人脸识别</font>

## <font style="color:#333333;">获取人脸识别全部信息</font>
<font style="color:#333333;">函数用法：ai_face.get_value()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取到视觉模块检测到的</font><font style="color:#333333;">人脸识别</font><font style="color:rgb(51, 51, 51);">的全部信息，并在底层保存</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">人脸识别检测的ID</font>
<font style="color:#333333;">函数用法：ai_face.is_detected(index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">人脸识别</font><font style="color:rgb(51, 51, 51);">检测ID</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 1-25</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">true:识别到了指定</font><font style="color:rgb(51, 51, 51);">ID</font>

<font style="color:rgb(51, 51, 51);">false:没有识别到指定ID</font>

## 删除或者对某个ID重新训练
<font style="color:#333333;">函数用法：ai_face.delete_or_train("type",index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">删除或者对某个ID重新训练</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">type:类型:删除:"delete",训练:"train"</font>

<font style="color:rgb(51, 51, 51);">index:数字:范围 1-25</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">人脸识别</font><font style="color:rgb(51, 51, 51);">检测到的结果数量</font>
<font style="color:#333333;">函数用法：ai_face.get_face_num()</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取人脸识别检测到的结果数量</font>

<font style="color:rgb(51, 51, 51);">输入参数:无</font>

<font style="color:rgb(51, 51, 51);">返回值:</font>

<font style="color:#333333;">数字:</font><font style="color:rgb(51, 51, 51);">0-10</font>

## <font style="color:rgb(51, 51, 51);">获取</font><font style="color:#333333;">人脸识别</font><font style="color:rgb(51, 51, 51);">检测到的指定标签的全部信息</font>
<font style="color:#333333;">函数用法：ai_face.detection_face(sign, index)</font>

<font style="color:#262626;background-color:#FFFFFF;">功能描述：</font><font style="color:rgb(51, 51, 51);">获取人脸识别检测到的指定标签</font>

<font style="color:rgb(51, 51, 51);">输入参数:</font>

<font style="color:#333333;">sign：信息值，"标签l" "宽度w" "高度h" "坐标x" "坐标y" </font>

<font style="color:#333333;">index</font><font style="color:rgb(51, 51, 51);">：数字:0</font>

返回值：

<font style="color:rgb(51, 51, 51);">字符串或数字，具体的信息值</font>

