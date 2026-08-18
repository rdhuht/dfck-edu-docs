# AI 模块 API

> **模块名：** AI module
>
> **导入方式：**
> ```python
> from tqpy import *
> set_extend_board("E2")
> ```
>
> !!! info "连接说明"
>     AI 模块使用 I2C 接口，连接 E1/E2/E3 任一拓展板的 I2C 接口即可，无需选择 port 端口。

---

## 连接拓展板

### set_extend_board(board_name)

设置与 AI 模块连接的拓展板。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| board_name | str | `"E1"` `"E2"` `"E3"` |

---

## 补光灯

### ai_light.on()

打开补光灯。

---

### ai_light.off()

关闭补光灯。

---

### ai_light.set_color(color, level)

设置补光灯颜色、亮度。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| color | str | `"red"` `"black"` `"green"` `"yellow"` `"blue"` `"purple"` `"cyan"` `"white"` |
| level | int | 0-15 |

**示例：**

```python
ai_light.set_color("white", 8)
```

---

## 摄像头

### ai_camera.set_rotate(option)

设置摄像头是否反转。

**参数：** `option` - 整数，0 或 1

---

## 颜色识别

### ai_color.on()

打开颜色识别。

---

### ai_color.off()

关闭颜色识别。

---

### ai_color.set_grid(number, size)

颜色识别预置识别区域网格数量及大小。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| number | str | 水平 × 垂直网格：`"1x1"` `"2x2"` `"3x3"` `"4x4"` `"5x5"` `"1x10"` `"2x10"` `"6x1"` `"6x2"` |
| size | str | 水平 × 垂直像素：`"2x2"` `"4x4"` `"8x8"` `"16x16"` `"32x32"` |

---

### ai_color.get_value()

获取颜色识别全部信息，并在底层保存。

---

### ai_color.get_color_num(color)

获取颜色识别到指定颜色的数量。

**参数：** `color` - 指定颜色：`"red"` `"black"` `"green"` `"yellow"` `"blue"` `"white"`

**返回值：** `int` - 范围 0-25

---

### ai_color.is_detected_color(color, index)

判断是否检测到指定颜色。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| color | str | `"red"` `"black"` `"green"` `"yellow"` `"blue"` `"white"` |
| index | int | 0-25 |

**返回值：** `bool` - `True` 识别到了指定颜色，`False` 没有

---

### ai_color.detected_rgb_or_lable(RGB_COLOR, index)

获取检测到的具体的 R/G/B 值或具体的颜色。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| RGB_COLOR | str | `"R"` `"G"` `"B"` `"COLOR"` |
| index | int | 0-25 |

**返回值：** 识别到的具体 RGB 值或颜色名

---

## 色块识别

### ai_blob.on()

色块识别打开。

---

### ai_blob.off()

色块识别关闭。

---

### ai_blob.set_performance(level)

设置色块识别性能。

**参数：** `level` - 字符串：`"speed"`（灵敏）、`"balance"`（均衡）、`"accuracy"`（准确）

---

### ai_blob.set_max_num(number)

设置色块识别最大数量。

**参数：** `number` - 整数，1-5

---

### ai_blob.set_detect_color(color)

设置色块识别可识别的颜色。

**参数：** `color` - 字符串：`"red"` `"black"` `"green"` `"yellow"` `"blue"` `"white"`

---

### ai_blob.set_detect_min_size(size)

设置色块识别最小范围。

**参数：** `size` - 字符串：`"2x2"` `"4x4"` `"8x8"` `"16x16"` `"32x32"` `"64x64"` `"128x128"`

---

### ai_blob.get_value()

获取色块识别全部信息，并在底层保存。

---

### ai_blob.is_detected_color(color)

判断检测到的色块颜色是否和指定的颜色一致。

**参数：** `color` - 字符串：`"red"` `"black"` `"green"` `"yellow"` `"blue"` `"white"`

---

### ai_blob.get_blob_num()

获取色块识别检测到的数量。

**返回值：** `int` - 范围 0-10

---

### ai_blob.detection_blob(type, index)

获取色块识别的指定信息。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| type | str | 标签：`"l"`，宽度：`"w"`，高度：`"h"`，x 坐标：`"x"`，y 坐标：`"y"` |
| index | int | 0-9 |

**返回值：** 数字，范围 0-10

---

## 线条识别

### ai_line.on()

线条识别打开。

---

### ai_line.off()

线条识别关闭。

---

### ai_line.set_performance(level)

设置线条识别性能。

**参数：** `level` - 字符串：`"speed"` `"balance"` `"accuracy"`

---

### ai_line.set_max_num(number)

设置线条识别最大数量。

**参数：** `number` - 整数，1-5

---

### ai_line.get_value()

获取线条识别全部信息，并在底层保存。

---

### ai_line.detection_line(type, index)

获取线条识别的指定信息。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| type | str | 起点 x：`"x_start"`，终点 x：`"x_end"`，起点 y：`"y_start"`，终点 y：`"y_end"`，倾斜角度：`"angle"` |
| index | int | 0-4 |

**返回值：** 数字，范围 0-10

---

## 二维码识别

### ai_qrcode.on()

二维码识别打开。

---

### ai_qrcode.off()

二维码识别关闭。

---

### ai_qrcode.get_value()

获取二维码识别全部信息，并在底层保存。

---

### ai_qrcode.is_detected_symbol(sign)

判断二维码识别是否包含指定符号。

**参数：** `sign` - ASCII 码表中的符号，如 `"!"` `"#"` `"%"` 等

**返回值：** `bool`

---

### ai_qrcode.is_detected_number(num)

判断二维码识别是否包含指定数字。

**参数：** `num` - 数字，0-9

**返回值：** `bool`

---

### ai_qrcode.is_detected_lowercase(letter)

判断二维码识别是否包含指定小写英文字母。

**参数：** `letter` - 小写字母，如 `"a"` `"b"` `"c"` 等

**返回值：** `bool`

---

### ai_qrcode.is_detected_capital(letter)

判断二维码识别是否包含指定大写英文字母。

**参数：** `letter` - 大写字母，如 `"A"` `"B"` `"C"` 等

**返回值：** `bool`

---

### ai_qrcode.detection_qrcode(sign)

获取二维码识别的指定符号的具体信息值。

**参数：** `sign` - 信息值：`"r"`（结果）、`"l"`（字符长度）、`"w"`（宽度）、`"h"`（高度）、`"x"`（坐标 x）、`"y"`（坐标 y）

**返回值：** 字符串或数字，具体的信息值

---

## 标签识别

### ai_apriltag.on()

标签识别打开。

---

### ai_apriltag.off()

标签识别关闭。

---

### ai_apriltag.set_performance(level)

设置标签识别性能。

**参数：** `level` - 字符串：`"speed"` `"balance"` `"accuracy"`

---

### ai_apriltag.get_value(type)

获取标签识别全部信息，并在底层保存。

**参数：** `type` - 字符串：`"16H5"` `"25H9"` `"36H11"`

---

### ai_apriltag.is_detected_16h5(index)

获取标签识别 16H5 编码检测 ID。

**参数：** `index` - 整数，0-29

**返回值：** `bool` - `True` 识别到了指定 ID，`False` 没有

---

### ai_apriltag.is_detected_25h9(index)

获取标签识别 25H9 编码检测 ID。

**参数：** `index` - 整数，0-29

**返回值：** `bool`

---

### ai_apriltag.is_detected_36h11(index)

获取标签识别 36H11 编码检测 ID。

**参数：** `index` - 整数，0-29

**返回值：** `bool`

---

### ai_apriltag.get_apriltag_num(type)

获取标签识别检测到的结果数量。

**参数：** `type` - 字符串：`"16H5"` `"25H9"` `"36H11"`

**返回值：** `int` - 范围 0-25

---

### ai_apriltag.detection_apriltag(type, index)

获取标签识别的指定信息。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| type | str | 标签：`"l"`，宽度：`"w"`，高度：`"h"`，x 坐标：`"x"`，y 坐标：`"y"`，起点 x：`"x_start"`，终点 x：`"x_end"`，起点 y：`"y_start"`，终点 y：`"y_end"`，倾斜角度：`"angle"` |
| index | int | 0-24 |

**返回值：** 字符串或数字，具体的信息值

---

## 深度学习

### ai_learn.on()

深度学习打开。

---

### ai_learn.off()

深度学习关闭。

---

### ai_learn.get_value()

获取深度学习全部信息，并在底层保存。

---

### ai_learn.is_detected(index)

获取深度学习检测的 ID。

**参数：** `index` - 整数，1-25

**返回值：** `bool` - `True` 识别到了指定 ID，`False` 没有

---

### ai_learn.delete_or_train(type, index)

删除或者对某个 ID 重新训练。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| type | str | 删除：`"delete"`，训练：`"train"` |
| index | int | 1-25 |

---

## 卡片识别

### ai_card.vision_card(type)

卡片识别开关。打开或关闭卡片识别。

**参数：** `type` - 字符串，打开：`"on"`，关闭：`"off"`

---

### ai_card.get_value()

获取卡片识别全部信息，并在底层保存。

---

### ai_card.detected_traffic_signs(type)

卡片识别到交通标示。

**参数：** `type` - 分类标签，见下表

| 标签 | 英文标识 | 中文含义 | 标签 | 英文标识 | 中文含义 |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | Forward | 前进 | 2 | Left | 左转 |
| 3 | Right | 右转 | 4 | Turn Around | 掉头 |
| 5 | Park | 停车 | 6 | Green | 绿灯 |
| 7 | Red | 红灯 | 8 | Speed 40 | 限速 40 |
| 9 | Speed 60 | 限速 60 | 10 | Speed 80 | 限速 80 |

**返回值：** `bool` - `True` 识别到了指定 ID，`False` 没有

---

### ai_card.detected_graphical_symbol(type)

卡片识别到圆形符号。

**参数：** `type` - 分类标签，见下表

| 标签 | 英文标识 | 中文含义 | 标签 | 英文标识 | 中文含义 |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 11 | Check | 对号 | 12 | Cross | 叉号 |
| 13 | Circle | 圆形 | 14 | Square | 方形 |
| 15 | Triangle | 三角形 | 16 | Plus | 加号 |
| 17 | Minus | 减号 | 18 | Divide | 除号 |

**返回值：** `bool`

---

### ai_card.detected_number(type)

卡片识别到数字。

**参数：** `type` - 分类标签，见下表

| 标签 | 英文标识 | 中文含义 | 标签 | 英文标识 | 中文含义 |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 20 | Num 0 | 数字 0 | 21 | Num 1 | 数字 1 |
| 22 | Num 2 | 数字 2 | 23 | Num 3 | 数字 3 |
| 24 | Num 4 | 数字 4 | 25 | Num 5 | 数字 5 |
| 26 | Num 6 | 数字 6 | 27 | Num 7 | 数字 7 |
| 28 | Num 8 | 数字 8 | 29 | Num 9 | 数字 9 |

**返回值：** `bool`

---

### ai_card.get_card_num()

获取卡片识别检测到的结果数量。

**参数：** 无

**返回值：** `int` - 范围 0-10

---

### ai_card.detection_blob(type, index)

获取卡片识别的指定信息。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| type | str | 标签：`"l"`，宽度：`"w"`，高度：`"h"`，x 坐标：`"x"`，y 坐标：`"y"` |
| index | int | 0-9 |

**返回值：** 数字，范围 0-10

---

## 人脸识别

### ai_face.on()

人脸识别打开。

---

### ai_face.off()

人脸识别关闭。

---

### ai_face.get_value()

获取人脸识别全部信息，并在底层保存。

---

### ai_face.is_detected(index)

获取人脸识别检测的 ID。

**参数：** `index` - 整数，1-25

**返回值：** `bool` - `True` 识别到了指定 ID，`False` 没有

---

### ai_face.delete_or_train(type, index)

删除或者对某个 ID 重新训练。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| type | str | 删除：`"delete"`，训练：`"train"` |
| index | int | 1-25 |

---

### ai_face.get_face_num()

获取人脸识别检测到的结果数量。

**参数：** 无

**返回值：** `int` - 范围 0-10

---

### ai_face.detection_face(sign, index)

获取人脸识别检测到的指定标签的全部信息。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| sign | str | `"l"`（标签）、`"w"`（宽度）、`"h"`（高度）、`"x"`（坐标 x）、`"y"`（坐标 y） |
| index | int | 0 |

**返回值：** 字符串或数字，具体的信息值