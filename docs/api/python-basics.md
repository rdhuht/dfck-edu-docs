# Python 基础

> 适用于 MicroPython 开发板的 Python 基础语法参考。

---

## 时间与延时

### time.sleep(seconds)

延时指定秒数。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| seconds | float | 延时秒数（>=0，可为整数或小数）|

**示例：**

```python
time.sleep(1)       # 延时 1 秒
time.sleep(0.5)     # 延时 0.5 秒
```

---

## 循环

### for 循环

```python
for count in range(times):
    # 循环体
```

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| times | int | 循环次数（>=0）|

**示例：**

```python
for i in range(5):
    print(i)  # 输出 0, 1, 2, 3, 4
```

---

### while 无限循环

```python
while True:
    # 循环体
```

---

### while 条件循环

```python
while condition:
    # 循环体
```

当条件为 True 时重复执行。

---

### while 等待条件

```python
while not condition:
    pass
```

等待条件被满足后执行后面的代码。

---

## 条件判断

### if 语句

```python
if condition:
    # 代码块
```

---

### if...else 语句

```python
if condition:
    # 条件满足时执行
else:
    # 条件不满足时执行
```

---

## 运算符

### 数学运算符

| 符号 | 算法 | 示例 | 结果 |
|------|------|------|------|
| + | 加 | 2 + 3 | 5 |
| - | 减 | 7 - 4 | 3 |
| * | 乘 | 2 * 4 | 8 |
| / | 除 | 9 / 3 | 3 |

!!! info "优先级"
    表达式中的运算符有优先级，与数学计算类似，可以用括号改变计算优先级。

---

### 条件运算符

| 符号 | 说明 |
|------|------|
| == | 等于 |
| != | 不等于 |
| < | 小于 |
| > | 大于 |
| <= | 小于等于 |
| >= | 大于等于 |

!!! warning "注意"
    不可将数值与字符串类型数据进行比较。

---

### 逻辑运算符

| 符号 | 说明 |
|------|------|
| and | "和"比较，两个布尔值同时为 True 时结果才为 True |
| or | "或"比较，只要有一个为 True 结果即为 True |
| not | "非"操作符，取原布尔值的相反值 |

---

## 字符串

### 连接字符串

```python
str1 + str2
```

**示例：**

```python
result = "苹果 " + "香蕉"  # "苹果 香蕉"
```

---

### 获取第 N 个字符

```python
"string"[n-1]
```

!!! warning "索引从 0 开始"
    Python 中索引从 0 开始。想获取第 1 个字符，应使用 `"string"[0]`。

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| n | int | 字符位置（最小值 0，最大值 字符串长度-1）|

**示例：**

```python
s = "Hello"
print(s[0])  # H
print(s[4])  # o
```

---

### 获取字符串长度

```python
len("string")
```

**返回值：** 字符数量

---

### 检测是否包含

```python
"string".find("substring") > -1
```

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| substring | str | 要查找的字符或字符串 |

**返回值：** `bool` - True 表示包含

---

## 高级数学运算

> 使用前需导入：`import math`

### random.randint(num1, num2)

取 num1 和 num2 之间的随机整数。

```python
import random

result = random.randint(1, 10)  # 1 到 10 之间的随机整数
```

---

### round(num)

四舍五入取整。

```python
round(3.7)   # 4
round(3.3)   # 3
```

---

### math.abs(num)

计算绝对值。

```python
import math

math.abs(-5)   # 5
```

---

### math.ceil(num)

向上取整。

```python
import math

math.ceil(3.1)   # 4
```

---

### math.floor(num)

向下取整。

```python
import math

math.floor(3.9)   # 3
```

---

### math.sqrt(num)

计算平方根。

```python
import math

math.sqrt(9)   # 3.0
```

---

### 三角函数

```python
import math

math.sin(x)    # sin 值
math.cos(x)    # cos 值
math.tan(x)    # tan 值
math.asin(x)   # asin 值
math.acos(x)   # acos 值
math.atan(x)   # atan 值
```

---

### math.log(num)

计算对数。

```python
import math

math.log(num)       # 以 e 为基数
math.log(num, 10)   # 以 10 为基数
```

---

### math.exp(num)

计算指数函数的值（e = 2.71828183）。

```python
import math

math.exp(2)   # e^2
```

---

### math.pow(10, num)

计算 10 的 num 次方。

```python
import math

math.pow(10, 3)   # 1000
```

---

## 变量

> 使用前先声明变量

### 赋值

```python
variable = value
```

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| value | int/float/str | 数字或字符串 |

---

### 声明全局变量

```python
global variable
```

---

### 变量自增

```python
variable += num
```

---

## 列表

> 使用前先创建列表

### 添加元素

```python
mylist.append(element)
```

---

### 删除第 N 项

```python
mylist.pop(int(num))
```

---

### 清空列表

```python
mylist.clear()
```

---

### 插入元素

```python
mylist.insert(int(num), element)
```

在第 num 项前插入新元素。

---

### 替换元素

```python
mylist[int(num)] = element
```

---

### 获取第 N 项

```python
mylist[int(num)]
```

!!! warning "索引从 0 开始"
    Python 列表索引从 0 开始。

---

### 查找元素位置

```python
mylist.index(element) + 1
```

返回元素第一次出现的位置（从 1 开始编号）。

---

### 获取列表长度

```python
len(mylist)
```

---

### 判断是否包含元素

```python
element in mylist
```

**返回值：** `bool` - True 表示包含

---
