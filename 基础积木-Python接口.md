# <font style="color:rgb(38, 38, 38);">控制类</font>
## 时间 time
### 延时/秒
函数用法：time.sleep(seconds) 

<font style="color:#262626;background-color:#FFFFFF;">功能描述：延时指定秒数</font>

输入参数：

<font style="color:#262626;background-color:#FFFFFF;">seconds：延时秒数（>=0，可为整数、小数）</font>

## 循环 while/for
### 重复执行/次
函数用法：for count in range(times)：

功能描述：循环/次

输入参数：

times：循环次数<font style="color:#262626;background-color:#FFFFFF;">（>=0，整数）</font>

### 无限循环
函数用法：while True：pass

功能描述：循环

输入参数：无

### 等待
函数用法：while not bool(True):pass

功能描述：待条件被满足后，执行后面的代码

输入参数：

True：不为0/False/null(字符串为空)的条件

pass：为固定字段

### 重复执行直到
函数用法：while not bool(True)：Function

功能描述：重复执行循环内的代码，直到条件满足，跳出循环

输入参数：

True：不为0/False/null(字符串为空)的条件

Function：需要循环执行的代码

## 条件判断 if
### 如果
函数用法：if ...

功能描述：如果条件被满足，执行程序

### 如果...否则...
函数用法：if  ... else  ...

功能描述：如果条件被满足，<font style="color:rgb(65, 70, 75);">执行程序，否则执行另一程序</font>

# <font style="color:rgb(65, 70, 75);">运算类</font>
## 运算符
### 数学运算符
数学运算符用于执行各种数学运算。

| 符号 | 算法 | 示例 | 所得值 |
| --- | --- | --- | --- |
| + | 加 | 2+3 | 5 |
| - | 减 | 7-4 | 3 |
| * | 乘 | 2*4 | 8 |
| / | 除 | 9/3 | 3 |


:::info
与数学一样，表达式中的运算符也有优先级，并且优先级与数学计算类似，先执行优先级较高的运算，再从左向右依次计算，同样的，也可以用括号改变计算优先级。

:::

### 条件运算符
条件运算符确定在各值之间进行何种类型的比较 。

| 符号 | 说明 |
| --- | --- |
| == | 等于 |
| != | 不等于 |
| < | 小于 |
| > | 大于 |
| <= | 小于等于 |
| >= | 大于等于 |


:::info
不可将数值与字符串类型数据进行比较

:::

### 逻辑运算符
逻辑运算符用于组合多个布尔表达式。

| 符号 | 说明 |
| --- | --- |
| and | "和"比较，当两个布尔值同时为True时，求值结果才为Ture。 |
| or | "或"比较，比较的两个布尔值，只要有一个为True,那么该比较求值即为True。 |
| not | "非"操作符，仅作用于一个布尔值，求值原布尔值的相反值。 |


## 字符串
### 连接两个字符串
用法：str('苹果 ') + str('香蕉')

功能描述：<font style="color:#333333;">将两个字符串连接为一个字符串</font>

<font style="color:#262626;background-color:#ffffff;">输入</font><font style="color:#333333;">参数：</font>

<font style="color:#333333;">num1：字符串</font>

<font style="color:#333333;">num2：字符串</font>

<font style="color:#262626;background-color:#ffffff;">返回值：连接后的字符串</font>

### 获取第N个字符
用法：'str'[n-1]

功能描述：通过索引获取字符串中字符

备注：在python中，索引是从0开始，直到序列长度减1,例如想要获取第1个字符，即n为1时，对应代码为'str'[0]。

<font style="color:#262626;background-color:#ffffff;">输入</font><font style="color:#333333;">参数：</font>

<font style="color:#333333;">str：字符串</font>

<font style="color:#333333;">n：整数（最大值为字符串长度减1，最小值为0）</font>

<font style="color:#262626;background-color:#ffffff;">返回值：当前字符串的第n个字符</font>

### 获取字符串字符数量
用法：len('str')

功能描述：获取字符串中包含的字符数量

<font style="color:#262626;background-color:#ffffff;">输入</font><font style="color:#333333;">参数：</font>

<font style="color:#333333;">str：字符串</font>

<font style="color:#262626;background-color:#ffffff;">返回值：当前字符串包含的字符数量</font>

### 检测是否包含
用法：str('str').find(str('s')) > -1

功能描述：检测字符串中是否包含某个字符

<font style="color:#262626;background-color:#ffffff;">输入</font><font style="color:#333333;">参数：</font>

<font style="color:#333333;">str：字符串</font>

<font style="color:#333333;">s：字符/字符串</font>

<font style="color:#262626;background-color:#ffffff;">返回值：True/False</font>

## 高级数学运算
### <font style="color:#262626;background-color:#ffffff;">取随机数</font>
<font style="color:#262626;background-color:#ffffff;">函数用法：</font><font style="color:#333333;">random.randint(num1, num2)</font>

<font style="color:#262626;background-color:#ffffff;">功能描述：</font><font style="color:#333333;">取num1和num2之间的随机整数</font>

<font style="color:#262626;background-color:#ffffff;">输入</font><font style="color:#333333;">参数：</font>

<font style="color:#333333;">num1：数字</font>

<font style="color:#333333;">num2：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：取随机整数结果</font>

### 四舍五入
用法：round(num)

功能描述：<font style="color:#262626;background-color:#ffffff;">四舍五入取整</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：取整结果</font>

### 绝对值
函数用法：<font style="color:#262626;background-color:#ffffff;">math.abs(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算数字绝对值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：绝对值结果</font>

### 向上取整
函数用法：<font style="color:#262626;background-color:#ffffff;">math.ceil(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">向上舍入取整</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：取整结果</font>

### 向下取整
函数用法：<font style="color:#262626;background-color:#ffffff;">math.floor(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">向下舍入取整</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：取整结果</font>

### <font style="color:#262626;background-color:#ffffff;">平方根</font>
函数用法：<font style="color:#262626;background-color:#ffffff;">math.sqrt(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算平方根值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：平方根结果</font>

### sin函数
函数用法：<font style="color:#262626;background-color:#ffffff;">math.sin(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算sin值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：sin结果</font>

### cos函数
函数用法：<font style="color:#262626;background-color:#ffffff;">math.cos(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算cos值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：cos结果</font>

### tan函数
函数用法：<font style="color:#262626;background-color:#ffffff;">math.tan(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算tan值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：tan结果</font>

### asin函数
函数用法：<font style="color:#262626;background-color:#ffffff;">math.asin(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算asin值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：asin结果</font>

### acos函数
函数用法：<font style="color:#262626;background-color:#ffffff;">math.acos(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算acos值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：acos结果</font>

### atan函数
函数用法：<font style="color:#262626;background-color:#ffffff;">math.atan(num)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算atan值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：atan结果</font>

### ln函数
功能描述：函数用法：<font style="color:#262626;background-color:#ffffff;">math.log(num1)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算log值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num1：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：以e为基数的num1的对数</font>

### log函数
功能描述：函数用法：<font style="color:#262626;background-color:#ffffff;">math.log(num1，10)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算log值</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num1：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：是以10为基数的num1的对数</font>

### e^函数
函数用法：math.exp(num)

功能描述：<font style="color:#262626;background-color:#ffffff;">计算指数函数的值；</font><font style="color:rgb(51, 51, 51);">e = 2.71828183</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：平方结果</font>

### 10^函数
函数用法：<font style="color:#262626;background-color:#ffffff;">math.pow(10, num1)</font>

功能描述：<font style="color:#262626;background-color:#ffffff;">计算10的num1次方</font>

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num1：数字</font>

<font style="color:#262626;background-color:#ffffff;">返回值：幂结果</font>

# 变量类
## 变量
> 使用前先新增一个变量variable
>

### 赋值
用法：variable = num

功能描述：将<font style="color:#262626;background-color:#ffffff;">变量</font>variable赋值为num

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字or字符串</font>

### 申明为全局变量
用法：gloable** **variable

功能描述：<font style="color:#262626;background-color:#ffffff;">将变量</font>**variable**申明为全局变量

<font style="color:#262626;background-color:#ffffff;">输入参数：无</font>

### 将变量增加
用法：variable += num

功能描述：<font style="color:#262626;background-color:#ffffff;">将变量</font>variable增加num

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

## 列表
> 使用前先新增一个列表mtlist
>

### 列表赋值
用法：mylist.append(element)

功能描述：给列表中新增元素element

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">element：数字or字符串</font>

### 列表删除第num项
用法：mylist.pop(int(<font style="color:#262626;background-color:#ffffff;">num</font>))

功能描述：指定删除列表的第num项

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字or字符串</font>

### 删除列表所有项
用法：mylist.clear()

功能描述：删除列表的所有项元素

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">无</font>

### 列表插入
用法：mylist.insert(int(num), element)

功能描述：在列表的第num项前插入新的元素element

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">element：数字or字符串</font>

### 列表替换
用法：mylist[int(num)] =element

功能描述：用新的元素element替换第num项的元素

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

<font style="color:#262626;background-color:#ffffff;">element：数字or字符串</font>

### 列表的第几项
用法：mylist[int(num)]

功能描述：列表的第num项

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">num：数字</font>

### 查找列表中某个元素第一次出现时的编号
用法：mylist.index(element) + 1

功能描述：查找元素element在列表mylist中第一次出现的位置

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">element：数字or字符串</font>

<font style="color:#262626;background-color:#ffffff;">返回值：数字编号</font>

### 获取列表长度
用法：len(mylist)

功能描述：获取列表长度的值

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">无</font>

<font style="color:#262626;background-color:#ffffff;">返回值：列表长度</font>

### 判断列表是否包含元素element
用法：element in mylist

功能描述：判断元素element是否存在在列表mylist中

<font style="color:#262626;background-color:#ffffff;">输入参数：</font>

<font style="color:#262626;background-color:#ffffff;">ement：数字or字符串</font>

<font style="color:#262626;background-color:#ffffff;">返回值：True/False</font>

