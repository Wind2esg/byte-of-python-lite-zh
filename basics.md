# 基础

`hellow world` 肯定满足不了你。要编写更复杂有趣的程序，我们需要学习更多的知识。

## 注释 comment

**注释** 是指某行内位于符号 `#` 之后的文本。

例如：

```python
print('hello world') # Note that print is a function
```

或者：

```python
# Note that print is a function
print('hello world')
```

**注释** 在程序运行时，会被解释器忽略掉。因此它主要用来：

- 为程序的阅读者提供更多信息。
- 调试代码时迅速屏蔽代码。

如果你初次接触编程，你可以去看下原著作者提供的[**代码告诉你如何，注释告诉你为何**](http://www.codinghorror.com/blog/2006/12/code-tells-you-how-comments-tell-you-why.html)。良好的编程习惯，这绝对是重要的。写天书与读天书，你即使现在不懂，以后也会懂的。

## 字面常量 literal constant

数字如 `5` ，`1.23` ，或者字符串如 `'This is a string'` ，`"It's a string!"` 都是字面常量的例子。

“字面”指的是它的字面意思就是实际意义，`2` 永远就是数字 2 ，不会代表任何其他意义。“常量”，提起变量就比较容易理解，指的是值不会发生变化。

## 数字 number

数字主要有两种——整数 (integers) 和浮点数 (floats)

整数的例子是 `2` 。

浮点数的例子是 `3.23` 和 `52.3E-4` 。标记 `E` 表示 10 的指数。`52.3E-4` 就是 `52.3 * 10^-4^` 。

> python 仅有 `int` ，它可以是任意大小的整数。  
> 没有 `short` ，`long` ，`unsign short` ，`unsign long` 诸如此类。

## 字符串 string

字符串是一串字符 (characters) 的序列 (sequence) 。

你在写 python 程序时基本都会用到字符串，所以下面的部分要多上心。

### 单引号

你可以使用单引号指定字符串如 `'Quote me on this'` 。

所有的在单引号中的空白诸如空格或者制表符都会保持原样。

### 双引号

与单引号完全相同

> 请注意，python 中，单引号双引号完全相同。

### 三引号 {#triple-quotes}

你可以用三引号 `"""` 或 `'''` 来指定多行字符串。在其中你可以任意使用双引号和单引号。例如

```python
'''This is a multi-line string. This is the first line.
This is the second line.
"What's your name?," I asked.
He said "Bond, James Bond."
'''
```

### 字符串是不可变的

也就是说一旦你创建了字符串，你就不能更改它。尽管这看起来不太好，但实际上并不糟。我们之后会在各种各样的程序样例中搞清楚这不会使我们碍手碍脚的原因。

> 这也没有什么 `char`、 在 python 中我们确实不需要它，我非常肯定你不会想念它。
>
> 也许你也会想到 python 的基本数据类型如此精简，那么当我们与其他实体互动时，如操作数据库会不会有很多麻烦？

### format 方法

有时，我们想使用其他信息来创建字符串，这正是 format() 一展身手之处。

将下面这些保存为 `str_format.py` ：

```python
age = 20
name = 'Swaroop'

print('{0} was {1} years old when he wrote this book'.format(name, age))
print('Why is {0} playing with that python?'.format(name))
```

输出为：

```
$ python str_format.py
Swaroop was 20 years old when he wrote this book
Why is Swaroop playing with that python?
```

**它是怎样做的**

字符串可以使用特定的格式，接着，`format` 方法会使用它的相应的参数来替换那些特定格式。

看看我们初次使用 `{0}` 的地方，它对应着 format 方法的第一个参数，`name` 变量。类似的，下一个，`{1}` 对应着  `age` 。注意 python 从 0 开始计数，即第一个位置是在索引 0 处，第二个在索引 1 ，以此类推。

当然，我们也可以使用连接字符串来达到同样的效果。

```python
name + ' is ' + str(age) + ' years old'
```

但是这看起来并不友好，而且容易出错。再者，`format` 方法能自动完成成字符串，不需显式的指定转换至字符串。最后，当时用 `format` 方法时，我们能够更改消息而不需顾虑变量，反之亦然。

`{}` 中数字是可选的，所以我们写成这样：

```python
age = 20
name = 'Swaroop'

print('{} was {} years old when he wrote this book'.format(name, age))
print('Why is {} playing with that python?'.format(name))
```

结果一模一样。

`format` 方法的原理是用每一个参数的值去替换格式所在的位置。这其中还有更加详细的格式，比如：

```python
# decimal (.) precision of 3 for float '0.333'
print('{0:.3f}'.format(1.0/3))
# fill with underscores (_) with the text centered
# (^) to 11 width '___hello___'
print('{0:_^11}'.format('hello'))
# keyword-based 'Swaroop wrote A Byte of Python'
print('{name} wrote {book}'.format(name='Swaroop', book='A Byte of Python'))
```

输出为：

```
0.333
___hello___
Swaroop wrote A Byte of Python
```

由于我们正在讨论格式化相关问题，就要注意 `print` 总是以隐藏的换行符 `\n` 结尾，所以每次调用 `print` 都会新起一行。你可以指定以空白来 `end` 来避免这个换行符被打印。

```python
print('a', end='')
print('b', end='')
```

输出为：

```
ab
```

或者你可以用一个空格来 `end` ：

```python
print('a', end=' ')
print('b', end=' ')
print('c')
```

输出为：

```
a b c
```

### 转义序列 escape sequence

假设，你想要一个包含一个单引号 `'` 的字符串，你该如何来指定这个字符串？例如，这个字符串是 `"What's your name?"` 。你没法指定 `'What's your name?'` 因为 python 会困惑于字符串的起止位置。所以，你必须指定这个单引号并不表示字符串的结尾。转义序列 (escape sequence) 能够帮助我们。你可以指定单引号为 `\'` ：记好这个反斜杠 `\` 。现在，你可以这雅漾指定这个字符串 `'What\'s your name?'` 。

还有一种指定这个字符串的方式 `"What's your name?"` ，如此例，使用双引号。类似的，你在双引号指定的字符串中必须使用转义序列来指定字符串中的双引号。你也可以使用转义序列指定反斜杠 `\\` 。

如果你想要指定一个两行的字符串时，该怎么做？使用三引号 [previously](#triple-quotes) 或者使用换行符的转义序列 `\n` 来说明要新起一行。一个例子是：

```python
'This is the first line\nThis is the second line'
```
另一个很有用的转义序列是制表符 `\t` 。转义序列实在很多，在此我仅提到最常用的几个。

有件事值得注意，在字符串中，行末尾的单独的反斜杠说明此行并未结束，下行接续，并没有新起一行。例如：

```python
"This is the first sentence. \
This is the second sentence."
```

等同于：

```python
"This is the first sentence. This is the second sentence."
```

### 原字符串 raw string

如果你需要指定某些不需如转义序列等特殊处理的字符串，你需要使用 `r` 或 `R` 前缀来指定原 (raw) 字符串。例如：

```python
r"Newlines are indicated by \n"
```

> 使用正则表达式的时候最好总使用原字符串。否则，你需要使用太多的反斜杠了。例如反向引用如 `'\\1'` 或 `r'\1'` 。

## 变量 variable

仅使用字面常量很快就会感到无聊——我们需要一些能够存储信息并对它们做一些操作的手段。变量 (variables) 应运而生。变量名副其实——他们的值是可变的，如同例子中那样，你可以使用变量存储任何东西。变量是你电脑中为你储存信息的内存的一部分。不同于字面常量，你需要一些方法来访问这些变量，因此，你需要为他们命名。

## 标识符命名 identifier naming

变量是一种标识符 (identifier) 。**标识符**是用来标示**某事物**的名称。这有一些你必须遵守的命名标识符的准则：

- 标识符的首字符必须是字母表中的字母（大小写 ASCII 字符或者 Unicode 字符）或者是下划线 `_` 。
- 余下可以由字母，下划线或者数字 (0-9) 组成。
- 标识符名称是大小写敏感的。例如，`myname` 和 `myName` 是**不同的** 。注意前面的是小写 `n` ，而后面的是大写 `N` 。
- **正确的**标识符名称如 `i` ，`name_2_3` 。像 `2things` ，`this is spaced out` ，`my-name` 和 `>a1b2_c3` 都是**不正确的**。

## 数据类型 data type

变量可保存不同类型的值，这些类型叫做**数据类型**。基本的类型是我们之前讨论过的数字和字符串。在之后的章节里，我们能够看到如何使用 [类 (classes)](./oop.md#classes) 来创建我们自己的变量。


## 对象 object

请记住，python 中一切皆为**对象**。这是一般意义上的说法。我们会将**某些东西**称作**对象**。

> python 中一切皆为对象，包括数字，字符串和函数。

我们将要看到变量与字面常量如何联动。保存并运行下面的这些示例程序。

### 例：使用变量与字面常量

输入，运行以下程序：

```python
# Filename : var.py
i = 5
print(i)
i = i + 1
print(i)

s = '''This is a multi-line string.
This is the second line.'''
print(s)
```

输出为：

```
5
6
This is a multi-line string.
This is the second line.
```

**它是怎样做的**

在这说明这段程序如何工作的。首先，我们使用赋值运算符 `=` 将字面常量 `5` 赋值给变量 `i` 。这一行称作语句 (statement) 因为它声明某些事情将要完成，在本例中，我们将变量名 `i` 与值 `5` 相连接。 接着，我们使用 `print` 语句来打印 `i` 的值，毫无意外的，变量的值在屏幕上被打印出来。

然后，我们将 `i` 中储存的值加 `1` 再存回 `1` 。我们接着打印它，正如所料，我们得到了值 `6` 。

类似的，我们赋值变量 `s` 然后打印它。

> python 中，变量的使用方式仅仅是赋值给他们。声明或者数据类型定义完全是不需要的。

## 逻辑与物理行 logical and physical line

物理行 (physical line) 是写程序时**你看到的**。逻辑行 (logical line) 是 **python 看到的**单个语句。python 隐式的假定每行物理行对应一行逻辑行。

像 `print 'hello world'` 的这样的一条语句就是逻辑行的例子——如果它本身就占一行（正如你在编辑器里看到的那样），它也对应一行物理行。

隐式的，python 鼓励每行使用单独的一条语句，如此会使代码可读性更高。

如果你想要在一行物理行中指定多行逻辑行，你必须显示的使用分号 `;` 来指明语句的结束。例如：

```python
i = 5
print(i)
```

等于

```python
i = 5;
print(i);
```

等同于

```python
i = 5; print(i);
```

与之相等的还有

```python
i = 5; print(i)
```

但是，我**强烈推荐**你恪守**每物理行仅有一逻辑行**。也就是说，你永远也用不上分号。实际上，我**从未**用过也未从 python 程序中见过分号。

当你有一行很长的代码需要使用反斜杠将其分成若干物理行的时候，你会发现这个概念非常着实有用。

这引出了**显式行连接**：

```python
s = 'This is a string. \
This continues the string.'
print(s)
```

输出为：

```
This is a string. This continues the string.
```

相似的,

```python
i = \
5
```

等同于

```python
i = 5
```

有时，也有一种隐式的假设，你不需要使用反斜杠。这种情况是逻辑行开头使用了左括号 `(` ，左中括号 `[` 或者左花括号 `{` 。这叫做**隐式行连接**。你能在后面章节中我们使用 [列表 (list)](./data_structures.md#lists) 写程序的时候看到这种行为。

## 缩进 indentation

python 中空白 (whitespace) 是很重要的。实际上，*在行开头的空白是很重要的*。这叫做**缩进 (indentation)**。逻辑行开头的空白（空格或者制表符）有着决定逻辑行缩进层次的作用，而逻辑行的层次会决定语句的分组。

这意味着同组语句**必须**有着相同的缩进。语句的集合称作*块*。我们再后面的章节的例子中可以看到块是多么的重要。

你应该记住的一件事是错误的缩进会产生错误 (error) 。例如：

```python
i = 5
# Error below! Notice a single space at the start of the line
 print('Value is', i)
print('I repeat, the value is', i)
```

当你运行它的时候，你会得到如下错误：

```python
  File "whitespace.py", line 3
    print('Value is', i)
    ^
IndentationError: unexpected indent
```

请注意，第二行开头有一个空格。python 指出这个错误来告诉我程序的语法有误。如前例，程序的编写不正确。于你而言，这意味着**你无法随意创建新的语句块**（当然，除了你一直使用的主语句块）。何种情形下你能使用新语句块在后续章节如 [控制流 (control flow)](./control_flow.md#control_flow) 中会有较详尽的描述。

> **如何缩进**
>
> 使用4个空格缩进。这是 python 语言的官方推荐方式。一些较友好的编辑器会自动帮你完成它。请你确认使用了一致数量的空格来缩进，否则你的程序将无法运行或者得出意外的结果。
>
> python 会一直使用缩进来指明块，并且永不使用花括号。有没有想到在[关于 python](./about_python.md#about_python) 中我的吐槽？如有兴趣可运行 `from __future__ import braces` 了解更多。

## 总结

你已然掌握了诸多具体本质细节，我们可以接着学习更有趣的内容如控制流语句等。请确保你可以对本章节内容游刃有余。