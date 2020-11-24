## 1. 注释

- 单行注释
使用 `//`，其注释内容从 `//` 开始到本行结尾。

- 多行注释
使用 `/*` 和 `*/`将一段比较长的注释括起来，还可以在每行的注释前面标记 `//`。

- 文档注释
这种注释以`/**`开始，以 `*/`结束。

>在Java中，`/* */`注释不能嵌套。也就是说，不能简单地代码用 `/*` 和 `*/`括起来作为注释，因为这段代码本身可能也包含一个 `*/`

## 2. 数据类型

Java是一种强类型语言。在Java中，一共有8种基本类型，其中4种整型、2种浮点类型、1种由于表示Unicode编码地字符单元地字符类型`char`和1种用于表示真挚的`boolean`类型。

这八种基本类型都有对应的包装类分别为：Byte、Short、Integer、Long、Float、Double、Character、Boolean

#### 2.1 整型

| 类型 | 存储需求 | 取值范围 |
| :----: | :----: | :----: |
| byte | 1字节 | -2<sup>7</sup> ~ 2<sup>7</sup>+1 |
| short | 2字节 | -2<sup>15</sup> ~ +2<sup>15</sup>+1 | 
| int | 4字节 | -2<sup>31</sup> ~ 2<sup>31+1 |
| long | 8字节 | -2<sup>63</sup> ~ 2<sup>63</sup>+1 |

>Java 里使用 long 类型的数据一定要在数值后面加上 L，否则将作为整型解析

>注意：Java没有任何无符号（unsigned）形式地整型数据。

#### 2.2 浮点类型

float类型地数据地数值有一个后缀F或f，没有后缀F或f的浮点数值默认为`double`类型.
所有的浮点数值计算都遵循`IEEE 754`规范.下面是表示溢出和出错情况的三个特殊的浮点数值：

- 正无穷大
- 负无穷大
- NaN（不是一个数字）

#### 2.3 char 类型

`char`类型的字面量值要用单引号括起来。双引号括起来的是一个字符串。

```java
char a = 'h'
String a = "h"
```

>强烈建议不要在程序中使用`char`类型，除非确实需要处理UTF-16代码单元。最好将字符串作为抽象数据类型处理。

#### 2.4 boolean 类型

`boolean`（布尔）类型有两个值：false 和 true，用来判断逻辑条件。

整型值和布尔值之间不能进行相互转换。

## 3. 变量

在Java中，每个变量都有一个类型。在声明变量时，变量的类型位于变量名之前。例如：

```java
double salary;
int vacationarys;
```

变量名必须是一个以字母开头并由<font color='red'>字母和数字</font>构成的序列。变量名中所有的字符都是有意义的，并且大小写敏感。

另外，不能使用Java关键字作为变量名.

##### Java中常见的关键字

| 访问控制 | private | protected | public |   |   |   |   |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  类，方法和变量修饰符 | abstact | class | extends | final | implements | interface | native |
|   | new | static | strictfp | synchronized | transient | volatile |   |
| 程序控制 | break | continue | return | do | while | if | else |
|  | for | instanceof | switch | case | default |   |   |
| 错误处理 | try | catch | throws | finally |   |   |
| 包相关 | import | package |   |   |   |   |   |
| 基本类型 | boolean | byte | char | double | float | int | long |
|   | short | null | true | false |   |   |   |
| 变量引用 | super | this | void |   |   |   |   |
| 保留字 | goto | const |   |   |   |   |   |

#### 3.1 变量初始化

声明一个变量之后，必须用赋值语句对变量进行显式初始化。也可以将变量的声明和初始化放在同一行。

```java
int i = 10;
```

>在Java中，变量的声明尽可能靠近变量第一次使用的地方，这是一种良好的程序编写风格。

#### 3.2 常量

在Java中，利用关键字`final`指示常量。

关键字`final`表示这个变量只能被赋值一次，一旦赋值之后，就不能再更改了。

习惯上，变量名使用全大写。

>需要注意：类常量的定义位于`main`方法的外部。因此，在同一个类的其他方法中也可以使用这个变量。如果一个常量被声明为`piblic`，那么其它类的方法也可以使用这个变量。

## 4. 运算符

#### 4.1 算术运算符

在Java中，使用算术运算符`+`、`-`、`*`、`/`表示加、减、乘、除运算。整数的求余（取模）操作用`%`表示。

当使用`/`运算的两个操作数都是整数时，表示整数除法；否则，表示浮点除法。

>注意：整数被0除将会产生一个异常，而浮点数被0除将会得到无穷大或者NaN结果。

#### 4.2 数学函数与常量

在Math类中，包含了各种各样的数学函数。

##### 常用的Math方法：
| 方法 | 功能 | 方法 | 功能 |
| :---: | :---: | :---: | :---: |
| sqrt | 开平方 | sin | 正弦函数 |
| pow | 幂运算 | cos | 余弦函数 |
| floorMod | 取模运算，余数>=0 | tan | 正切函数|
| atan | 反正切函数 | atan2 | 将笛卡尔坐标转换为极坐标，返回其角度值 |
| exp | 指数函数 | log | 自然对数 |
| log10 | 以10为底的对数 |

Java还提供了两个用于表示`∏`和`e`常量的近似值：
```java
Math.PI
Math.E
```

#### 4.3 数值类型之间的转换

![数值类型之间的合法转换](https://github.com/ryanBert/JavaLearning/new/main/Java%E5%9F%BA%E7%A1%80/img/数值类型之间的合法转换.png)

<center>数值类型之间的合法转换</center>

在图中，6个实心箭头表示五信息丢失的转换；3个虚箭头表示可能有精度损失的转换。

#### 4.4 强制类型转换

在数值类型转换时，存在精度损失，这种情况下就要通过强制类型转换（cast）实现类型转换。强制类型转换的语法格式是在圆括号中给出想要转换的目标类型，后面紧跟转换的变量名。
```java
double x = 9.997;
int nx = (int)x;
```

><b><font color='black'>警告</font></b>：如果试图讲一个数值从一种类型强制转换为另一种类型，而又超出了目标类型的表示范围，结果就会截断成一个完全不同的值。例如，byte(300)实际值为44。

<font color='red'>注意:</font>不要在boolean类型与其他数值类型之间进行强制类型转换，这样可以发生错误。如果需要将布尔类型转换为数值类型，可以使用条件表达式。

#### 4.5 结合赋值和运算符

可以在赋值中使用二元运算符，例如：
```java
x += 4
```
等价于
```java
x = x + 4
```
(一般地，将运算符放在`=`左边，如`*=`或`%=`)

#### 4.6 自增与自减运算符

在Java中，借鉴了C和C++的作法，也提供了自增与自减运算符：n++将变量n的当前值加1，n--将n的当前值减1.

如下代码：

```java
int n = 12;
n++;        //n=13
```

自增与自减运算符有前缀和后缀两种形式：前缀形式先完成加1，后缀形式会使用变量原来的值。

```java
int m = 7;
int n = 7;
int a = 2 * ++m;  // a = 16, m = 8
int b = 2 * m++;  // b = 14, m = 8
```

>建议：代码中尽量不要使用自增与自减运算符，因为这样的代码容易让人困惑，产生不必要的bug

#### 4.7 关系和boolean运算符

关系运算符：`==`（等于）、`！=`（不等于）、`<`（小于）、`>`（大于）、`<=`（小于等于）、`>=`（大于等于）。

逻辑运算符：`&&`（逻辑与）、`||`（逻辑或）、`！`（逻辑非）。

Java支持三元运算符`?:`，如果条件为`true`，结果就为第一个表达式的值，否则为第二个表达式的值。形式如下：

```
condition ? expression1 : expression2;
```

#### 4.8 位运算符

| 符号 | 含义 | 符号 | 含义 |
| :---: | :---: | :---: | :---: |
| `&` | 位与 | `|` | 位或 |
| `^` | 位异或 | `~` | 位非 |
| `>>` | 位模式左移 | `<<` | 位模式右移 |
| `>>>`| 用0填充高位|  |  |

## 5. 字符串

从概念上讲，Java字符串就是Unicode字符序列。Java没有内置的字符串类型，而是在标准Java类库中提供了一个预定义类，很自然地叫做`String`。

```java
String s = ""; // an empty string
String greeting = "Hello";
```

#### 5.1 子串

`String`类中的`substring`方法可以从一个较大的字符串中提取出一个子串。

```java
String greeting = "Hello";
String s = greeting.substring(0, 3);  // s = "Hel"
```

`substring`方法有一个优点：容易计算字串的长度。字符串`s.substring(a,b)`的长度为b-a。

#### 5.2 拼接

Java语言允许使用 + 号拼接两个字符串。

```java
String expletive = "Expletive";
String PG13 = "PG13";
String message = expletive + PG13; // message = "ExpletivePG13"
```

当将一个字符串于一个非字符串的值进行拼接时，后者将被转换为字符串。

```java
int age = 13;
String rating = "PG" + age; // rating = "PG13"
```

如果需要把多个字符串放在一起，用一个分界符分割，可以使用join方法：
```java
String s = String.join("/", "123", "456"); // s = "123/456"
```

#### 5.3 不可变字符串

`String`类创建的字符串对象是不可修改的。

那么如何修改这个字符串呢？首先提取所需要的字符，然后再拼接上替换的字符串：

```java
String greeting = "Hello";
greeting = greeting.substring(0, 3) + "p"; // greeting = "Help"
```

#### 5.4 检测字符串是否相等

可以使用`equals`方法检测两个字符串是否相等。

```java
s.equals(t)
```

对于这个表达式，如果字符串s和t相等，则返回`true`；否则，返回`false`。

要想检测两个字符串是否相等，并不区分大小写，可以使用`equalsIgnoreCase`方法。

><font color='red'>一定不要使用`==`运算符来检测两个字符串是否相等！</font>这个字符串只能确定两个字符串是否放置在同一个位置上。

#### 5.5 空串与`Null`串

空串`""`是长度为0的字符串。空串是一个Java对象，有自己的串长度（0）和内容（空）。

可以调用下面代码检测一个字符串是否为空：

```java
if (str.length() == 0)
```
或
```java
if (str.equals(""))
```

`String`变量还可以存放一个特殊值：`null`，这表示目前没有任何对象与该变量关联。要检查一个字符串是否为`null`，可以使用以下条件：

```java
if (str == null)
```

有时需要检查一个字符串既不是`null`也不是空串，那么需要使用以下条件：

```java
if (str != null && str.length() != 0)
```

#### 5.6 String API

- `char charAt(int index)`
返回给定位置的代码单元。

<h></h>
- `int compareTo(String other)`
按照字典顺序，如果字符串位于other之前，返回一个负数；如果字符串位于other之后，返回一个正数；如果两个字符串相等，返回0。

<h></h>
- `boolean equals(Object other)`
如果字符串与other相等，返回true。

<h></h>
- `boolean equalIgnoreCase(String other)`
如果字符串与other相等（忽略大小写），返回true。

<h></h>
- `boolean startsWith(String prefix)`
- `boolean endsWith(String suffix)`
如果字符串以prefix开头或者以suffix结尾，返回true。

<h></h>
- `int indexOf(String str, int fromIndex)`
- `int indexOf(int cp, int fromIndex)`
返回与字符串 str 或代码点 cp 匹配的第一个子串的开始位置。这个位置从索引 0 或fromlndex 开始计算。 如果在原始串中不存在 str，返回 -1。

<h></h>
- `int lastIndexOf(String str, int fromIndex)`
- `int lastIndexOf(int cp, int fromIndex)`
返回与字符串 str 或代码点 cp 匹配的最后一个子串的开始位置。 这个位置从原始串尾
端或 fromlndex 开始计算。

<h></h>
- `int length()`
返回字符串的长度。

<h></h>
- `String replace(CharSequence oldString, CharSequence newString)`
返回一个新字符串。这个字符串用`newString`代替原始字符串中所有的`oldString`。

<h></h>
- `String toLowerCase()`
- `String toUpperCase()`
返回一个新字符串。 这个字符串将原始字符串中的大写字母改为小写，或者将原始字符串中的所有小写字母改成了大写字母。

<h></h>
- `String trim()`
返回一个新字符串。这个字符串将删除了原始字符串头部和尾部的空格。

<h></h>
- `String join(CharSequence delimiter, CharSequence ... elements)`
返回一个新字符串， 用给定的定界符`delimiter`连接所有元素。

<h></h>
>Java API文档可以在此网站详细查看：[https://docs.oracle.com/javase/8/docs/api/](https://docs.oracle.com/javase/8/docs/api/)

#### 5.7 构建字符串

在需要由较短的字符串构建字符串的时候，可以使用`StringBuilder`类来避免耗时、浪费空间的问题。

```java
StringBuilder builder = new StringBuilder();
```

当需要添加一部分内容时，可以调用`append`方法。

在需要构建字符串时，调用`toString`方法可以得到一个`String`对象。

```java
String s = builder.toString();
```

`StringBuilder`类中的重要方法：

- `StringBuilder()`
构造一个空的字符串构建器。

<h></h>
- `int length()`
返回构建器或缓冲器中的代码单元数量。

<h></h>
- `StringBuilder append()`
追加一个字符串或代码单元并返回this。

<h></h>
- `void setCharAt()`
将第i个代码单元设置为c。

<h></h>
- `StringBuilder insert(int offset, String str(Char c))`
在offset位置插入一个字符串或者代码单元并返回this。

<h></h>
- `StringBuilder delete(int startIndex, int endIndex)`
删除偏移量从startIndex到endIndex-1的代码单元并返回this。

<h></h>
- `String toString()`
返回一个与构建器或缓冲器内容相同的字符串。

## 6. 输入输出

#### 6.1 读取输入

要想通过控制台进行输入，首先需要构建一个Scanner对象，并与“标准输入流”`System.in`关联。

```java
Scanner in = new Scanner(System.in);
```

- `String nextLine()`
读取输入的下一行内容

<h></h>
- `String next()`
读取输入的下一个单词（以空格作为分隔符）

<h></h>
- `int nextInt()`
- `double nextDouble()`
读取并转换下一个表示整数或浮点数的字符序列。

<h></h>
- `boolean hasNext()`
检测输入中是否还有其他单词。

<h></h>
- `boolean hasNextInt()`
- `boolean hasNextDouble()`
检测是否还有表示整数或浮点数的下一个字符序列。

为了从控制台读取密码，Java SE 6引入了`Console`类。

```java
Console cons = System.console();
String username = cons.readLine("User name:");
char[] passwd = cons.readPassword("Password");
```

>注意：这个程序只能在控制台执行，否则会出现空指针错误。

#### 6.2 格式化输出

在Java SE 5.0沿用了C语言库函数中的`printf`方法的格式化。

下图给出了用于printf函数的所有转换符和标志：
![用于printf的转换符](https://github.com/ryanBert/JavaLearning/new/main/Java%E5%9F%BA%E7%A1%80/img/用于printf的转换符.png)

![用于printf的标志](https://github.com/ryanBert/JavaLearning/new/main/Java%E5%9F%BA%E7%A1%80/img/用于printf的标志.png)

>`printf`方法中日期与时间的格式化选项，推荐使用`java.time`包的方法。

#### 6.3 文件输入与输出

要想对文件进行读取，就需要一个用File对象构造一个`Scanner`对象，如下：

```java
Scanner in = new Scanner(Paths.get("myfile.txt"), "UTF-8");
```

要想写入文件，就需要构造一个PrintWriter对象。在构造器中，只需要提供文件名。如果文件不存在，创建该文件。

```java
PrintWriter out = new PrintWriter("myfile.txt", "UTF-8");
```

<h></h>
>在文件读写的过程中，建议使用异常处理。
