# 函数 Function

函数是可复用的代码段。它们允许你为代码块命名，并且允许你使用指定的名称在程序其他任何地方不限次数的使用。这就是函数的**调用**。我们已经使用了许多内置函数如 `len` 和 `range` 。

在任何语言编写的正规程序里，函数概念是**最重要**的基础块。

函数使用关键字 `def` 定义。关键字之后就是这个函数的**标识符**名称，然后是包含变量的括号，最后行末尾就是分号。接下来的语句块也是函数的组成部分。下面这个例子会让你明白实际上这很简单 `function1.py` ：

<pre><code class="lang-python">{% include "./programs/function1.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function1.txt" %}</code></pre>

**它是怎样做的**

按照之前讲的语法，我们定义了叫做 `say_hello` 的函数。这个函数没有参数，因此在括号内没有声明任何变量。函数的参数是函数接受的输入，我们可以在传递各种各样的值给它并能得到正确的相应的结果。

可以看到，我们两次调用了这个函数，而不需重复写代码。

## 参数 Parameter

函数有参数，它们是我们提供给函数的各种值，通过参数，函数就能做各种各样的事情了。这些参数很像变量，但它们的值是在我们调用函数时定义的，当函数运行时它们已然被赋值了。

参数在函数定义中的括号内指定，并且由逗号 `,` 分割。当我们调用函数时，我们以相同的方式为它们提供值。请注意这里的术语——函数定义里的参数叫做 *parameters* 。而调用函数时我们提供的那些参数称为 *arguments* 。

请看示例 `function_param.py` ：

<pre><code class="lang-python">{% include "./programs/function_param.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_param.txt" %}</code></pre>

**它是怎样做的**

在这，我们定义了 `print_max` 函数，并有两个参数 `a` 和 `b` 。我们通过一个简单的 `if..else` 找出较大的数并打印。 

第一次调用 `print_max` ，我们直接提供了参数。第二例中，我们调用了将改变量作为参数的函数。`print_max(x, y)` 将参数 `x` 值赋给参数 `a` ，`y` 赋给 `b` 。`print_max` 函数在两个例子中作用相同。

## 局部变量 Local Variable

当你在函数定义内声明变量时，它们与函数外的同名变量是毫不相关的——即对函数来说，变量名是**局部的 (local)** 。这叫做变量的**作用域 (scope)** 。变量的作用域起于它们声明之处，止于包含他们块结尾。

请看示例 `function_local.py` ：

<pre><code class="lang-python">{% include "./programs/function_local.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_local.txt" %}</code></pre>

**它是怎样做的**

我们第一次打印 `X` 的值是在函数体的第一行，python 使用了主块内函数定义之前定义的参数的值。

接着，我们把 `2` 赋给 `x` 。`X` 是我们函数的局部变量。因此，当我们在函数内改变 `x` 的值的时候，主块内定义的 `x` 不会发生改变。 

最后的 `print` 语句显示出主块内定义的 `x` 的值，因此，可以确认在调用的函数中的局部变量的赋值确实不会有任何影响。 

## 全局 global {#global-statement}

当你处在某函数或者类的作用域中时，如果你想为在程序的最顶层（也就是不在任何函数或者类的作用域中）定义的变量赋值，你得告诉 python 这个变量名称不是局部的，它是**全局的 (global)** 。`global` 语句是做成这件事的唯一途径。

我们可以直接使用那些定义在在函数之外的变量的值（假定函数内不存在与这些变量同名的局部变量）。但是通常我们不鼓励这么做并且你应该尽量避免这么做，因为它使得程序读起来不那么清晰明了，变量在何处定义会干扰程序代码的阅读。使用 `global` 语句能够清楚明白的告知变量定义在最外层。

请看示例 `function_global.py` ：

<pre><code class="lang-python">{% include "./programs/function_global.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_global.txt" %}</code></pre>

**它是怎样做的**

`global` 语句声明 `x` 是一个全局变量——因此，当我们在函数内为 `x` 赋值时，当我们在主块中使用 `x` 的值得时候，这个改变就反映出来。

一行 `global` 语句可以指定不止一个全局变量，例如 `global x, y, z` 。

## 位置参数 Positional Argument

函数调用时，我们提供一些值。例如:

```python
def test(a,b)
    print(a)
    print(b)

test(1,2)
```

位置参数 (Positional Argument) 指的就是如同 `1` ，`2` 这样的参数，按照位置与声明函数时的参数对应。

## 默认参数值 Default Argument Value {#default-arguments}

对一些函数来说，你也许想要某些参数是**可选的**并且当用户不想为他们提供值时使用默认的值。默认参数值能够得到。在函数定义时，你可以用某些值为参数赋值，这些值就是默认参数值。

有一点你必须记好，默认参数值必须是常量。更准确的说，默认参数值是不可变的——在之后的章节会对此做更多的解释。现在，记住它就是。

请看示例 `function_default.py` ：

<pre><code class="lang-python">{% include "./programs/function_default.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_default.txt" %}</code></pre>

**它是怎样做的**

`say` 函数打印某字符串指定次。如果我没没有提供这个值，默认的，这字符串只打印一次。我们通过指定参数 `times` 的默认参数值为 `1` 完成这些。 

`say` 首次调用，我们仅仅提供了字符串，这个字符串打印了一次。我们再次调用时，我们提供了字符串的同时还提供了参数 `5` 声明我们要**说**这个字符串五次。

> **请注意**
> 
> 在参数列表中，有默认参数值的参数不得位于无默认参数值的参数之前。例如 `def func(a,b=5)` 是可以的, 但是 `def func(a=5, b)` **不行**。
> 
> 原因在于**如果** `def func(a=5, b, c=7)` 是合法的，那么调用 `func(6,8)` 时，python 无法确定该如何去为 `a` ，`b` ，`c` 赋值。

## 关键字参数 Keyword Argument

如果你的函数带有很多参数，而你只想为其中的一些赋值，你可以命名他们来为这些参数指赋值——这叫做**关键字参数 (keyword arguments)** ——我们使用关键字而非位置来为函数指定参数。

这带来两个好处：一，我们不需顾虑参数顺序是的函数使用起来更加容易。二，我们可以仅为部分参数赋值，而其他的参数使用默认参数值。

请看示例 `function_keyword.py` ：

<pre><code class="lang-python">{% include "./programs/function_keyword.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_keyword.txt" %}</code></pre>

**它是怎样做的**

`func` 函数有一个没有默认参数值的参数，在它之后，有两个有默认参数值的参数。

首次调用 `func(3, 7)` ，参数 `a` 被赋值 `3` ，参数 `b` 被赋值 `7` ，`c` 被赋值默认值 `10` 。

第二次调用 `func(25, c=24)` ，变量 `a` 被位置参数 `25` 赋值。之后，参数 `c` 被关键字参数 `c=24`  赋值。变量 `b` 被赋默认值参数值 `5` 。

第三次 `func(c=50, a=100)` ，我们使用关键字参数来指定所有值。请注意，即使在函数定义中，`a` 在 `c` 之前定义，我们仍可以先为 `c` 赋值。

## 可变参数 VarArgs parameter

有时，你也许想要定义一个可以带**任意**参数的函数，即参数的数量是可变的。`*` 可以帮你实现。

请看示例 `function_varargs.py` ：

<pre><code class="lang-python">{% include "./programs/function_varargs.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_varargs.txt" %}</code></pre>

**它是怎样做的**

当我们声明一个带星号的参数如 `*param` 的时候，从它到末尾的所有的由参数位置指定的参数都被收在名称为 `param` 的元组中。

类似的，当我们声明一个带两个型号的参数如 `**param` 的时候，从它到末尾的所有关键字参数都被收在名称为 `param` 的字典里 (dictionary) 。

我们[之后的章节](./data_structures.md#data-structures)更多的探索元组和字典。

> 我想你已经想到了，位置参数要放在关键字参数之前。
> 不妨据此例展开一些练习。想想：
> `total(a=5,*numbers,**phonebook)` 何种情况下 `a` 的默认参数值能生效？
> `total(*numbers, a=5, **phonebook)` 此种情况下如何为 `a` 传递参数？

## return {#return-statement}

`return` 语句的作用是从函数中**返回**即从函数体中跳出。我们也可以从函数中**返回值**。

请看示例 `function_return.py` ：

<pre><code class="lang-python">{% include "./programs/function_return.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_return.txt" %}</code></pre>

**它是怎样做的**

`maximum` 函数返回参数中最大的那个。它使用一个简单的 `if..else` 语句来找到最大值，然后**返回**这个值。

请注意，`return` 语句后没有值得话就等同于 `return None` 。空 (None) 是 python 中一种特殊类型，表示不存在。例如，一个变量如果值为 `None` 意思是它的值是空。

> 这里要搞清楚空与未定义 (not defined) 的区别
> 未定义是没有对变量赋值过，是不合法的。
> 空是合法的，变量已被赋值，这不过这个值是不存在

除非你写出你自己的 `return` 语句，每个函数都隐式的在末尾包含一个 `return None` 语句。如果 `some_function` 没有 `return` 语句，那么 `print(some_function())` 可就以让你看到这些：

```python
def some_function():
    pass
```

`pass` 语句在 python 中用来表示语句块。

> python 中已内置了 `max` 函数，实现了找最大值得功能，所以尽可能的使用内置函数吧。

## 文档字符串 DocString

python 有种灵巧的特性叫做**文档字符串 (documentation strings)** ，我们通常使用它的简写**docstring**。文档字符串是很重要的工具，它能帮助你为程序做标注，使之更易读。你应该充分利用它。非常棒的是，我们甚至能从当前运行中的程序里得到它。

请看示例 `function_docstring.py` ：

<pre><code class="lang-python">{% include "./programs/function_docstring.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_docstring.txt" %}</code></pre>

**它是怎么做的**

函数的首个逻辑行的首个字符串就是这个函数的**文档字符串**。请注意稳当字符串也适用于[模块 modules](./modules.md#modules) 和[类 classes](./oop.md#oop) ，我们再后续章节中会作更多了解。

文档字符串的惯例格式是首字母大写，以点 `.` 结尾的多行字符串。然后，第二行留空，从第三行开始对函数的详细解释。在这，**强烈**推荐你写文档字符串的时候遵从这个格式。

我们使用函数的 `__doc__` (注意**双下划线 (double underscores)** )属性来获取 `print_max` 函数的文档字符串。记住，python 中一切皆为对象，函数也是对象。我们会在 [类 classes](./oop.md#oop) 章节中更多的了解对象。

如果你在 python 中使用过 `help()` ，那么你已经见过文档字符串了！它既是获取函数的 `__doc__` 属性然后将之友好的展现给你。你可以在上面的函数上试试——将 `help(print_max)` 放入你的程序中。记得按 `q` 键来退出 `help` 互动命令行。

既然我们有自动化工具能从你程序中获取文档。我**强烈推荐**你在正式函数中都要写文档字符串。`pydoc` 命令的作用类似于 `help()` 。

## 总结

尽管没有全部了解，但我们已经具备日常使用函数的基础。

下面的章节，我们会看看如何创建 python 模块。
