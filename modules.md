# 模块 module

定义函数一次就可以在你程序中重用那部分代码。那么当你想在程序中重用大量函数时怎么办？也许你已经猜到了，答案就是模块 (module) 。

写模块有很多方式，最简单的就是创建一个包含函数与变量的扩展名为 `.py` 的文件。

另一个写模块的方法是使用编写 python 解释器的语言来编写。例如，你可以用 [c 语言](http://docs.python.org/3/extending/) 。它们在编译过后可以在 python 代码中使用。

模块能被**导入 (importe)** 到其他程序以复用它的功能。我们使用 python 标准库 (standard library) 也是同样道理。首先，让我们来看看如何使用标准库模块。

请看示例 `module_using_sys.py` ：

<pre><code class="lang-python">{% include "./programs/module_using_sys.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/module_using_sys.txt" %}</code></pre>

**它是怎么做的**

首先，我们使用 `import` 语句**导入** `sys` 模块。这告知 python 我们想要使用这个模块。`sys` 模块包含一些与 python 解释器和解释器运行环境即操作系统相关的功能。

当 python 执行 `import sys` 语句时，它会寻找 `sys` 模块。在本例中，它是内置模块之一，因此 python 知道在哪里能找到它。

如果它不是编译好的模块即该模块是用 python 写成的，python 解释器会在其 `sys.path` 变量保存的列表中的那些目录去搜寻它。如果找到，模块体中的语句就会运行，之后这模块就是**可用**的了。请注意，这个初始化仅发生在我们**首次**导入模块的时候。

`sys` 模块中的 `argv` 变量是使用点标记访问的即 `sys.argv` 。很明了，它是 `sys` 模块的一部分。这种方式的另一种好处是不会与你程序中的 `argv` 变量相冲突。

`sys.argv` 变量是一个字符串**列表**，列表在[之后的章节](./data_structures.md#data-structures)会作专门了解。`sys.argv` 包含了**命令行参数 (command line argumentss)** 列表，命令行参数即使用命令行传递给你程序的参数。

如果你正在使用 IDE 编写和运行程序，那么在菜单中你会找到指定命令行参数的方式。
在这里，当我们执行 `python module_using_sys.py we are arguments` 的时候，我们使用 `python` 命令运行 `module_using_sys.py` 模块，后面跟着的就是传递给程序的参数。python 将命令行参数储存在 `sys.argv` 变量中以待我们使用。

请记住，`sys.argv` 列表的首个元素是正在运行的脚本的名称。所以在本例中，我们会有：`sys.argv[0]` 是 `'module_using_sys.py'` ，`sys.argv[1]` 是 `'we'` ，`sys.argv[2]` 是 `'are'` ，`sys.argv[3]` 是 `'arguments'` 。请注意，python 的计数从 0 开始，而不是 1 。

`sys.path` 包含了记录模块从何处导入的目录的名称的列表。请看 `sys.path` 的首个字符串是空的——这个空字符串说明当前目录也是 `sys.path` 的一部分，`sys.path` 等同于环境变量 `PYTHONPATH` 。也就是说，你可以直接导入当前目录中的模块。否则，你必须将你的模块放到 `sys.path` 的列表中的某个目录之内。

请注意，当前目录是程序的启动目录。运行 `import os; print(os.getcwd())` 能找出你程序的当前目录。

## .pyc 文件 {#pyc}

导入模块有一定的消耗，所以 python 使用一些妙招来让优化。一个方法是创建拓展名为 `.pyc` 的**字节编译的 (Byte-compiled)** 文件，这是 python 将程序转化的那种字节代码（你一定会想起我们在[关于 python](./about_python.md#interpreted) 中关于编译型和解释型的那些探讨）。当你下次在其他程序中导入这个模块时，这个 `.pyc` 文件就发挥作用了——它的速度会更快一些，由于导入模块所需的处理的一部分已然完成。 这些 `.pyc` 文件同样是平台不依赖 (platform-independent) 的。

注意：这些 `.pyc` 文件通常创建在其相应的 `.py` 文件所在的目录中。如果 python 对那些目录和文件没有相应权限，那么 `.pyc` 文件就**不会**被创建。

> 不知你有没有想到之前谈到 python 特点是，在解释型那一块我们的一些探讨。

## from...import {#from-import-statement}

如果你将 `argv` 直接导入你的程序（而不是每次都输入 `sys.` ），你可以用 `from sys import argv` 语句。

> 注意，一般情况下，最好还是用 `import`，因为它能避免命名冲突，而且可读性更好。

例如：

```python
from math import sqrt
print("Square root of 16 is", sqrt(16))
```

## \_\_name\_\_ {#module-name}

每个模块都有它的名称，并且也有相应语句能找出这个名字。当你想区分这个模块是独立运行还是被导入到其他程序中之时是非常便利的。正如之前提到的那样，当一个模块首次导入时，内中代码已然执行。我们可利用这一点，根据模块是独立还是被导入来使其表现不同的行为。使用模块的 `__name__` 属性就可以。 

请看示例 `module_using_name.py` ：

<pre><code class="lang-python">{% include "./programs/module_using_name.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/module_using_name.txt" %}</code></pre>

**它是怎样做的**

每个 python 模块都有它的 `__name__` 。如果是 `'__main__'` ，就说明这个模块是独立运行的，我们就可以做出适当的行为了。

## 编写你自己的模块

创建你自己的模块蛮简单地，你其实一直都在做。每一个 python 程序都是一个模块。你只要确保它有 `.py` 的扩展名即可。下面的例子能做更好的说明。

请看示例 `mymodule.py` ：

<pre><code class="lang-python">{% include "./programs/mymodule.py" %}</code></pre>

这上面就是一个简单的**模块**。如你所见，与我们平常的 python 程序相比也没什么特别的。接着我们看如何在其他程序中使用这个模块。

请记住，模块要放在与程序所在目录或者是 `sys.path` 列表中的目录之内。

另一个模块 `mymodule_demo.py` ：

<pre><code class="lang-python">{% include "./programs/mymodule_demo.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/mymodule_demo.txt" %}</code></pre>

**它怎样工作的**

请看好，我们使用了相同的点标记来访问模块的成员。python 能很充分的利用相同的标记带给我们独特的 'pythonic' 感，我们不需不停地学习新的行事方式。

这是 `from...import` 语法的一个例子 `mymodule_demo2.py` ：

<pre><code class="lang-python">{% include "./programs/mymodule_demo2.py" %}</code></pre>

`mymodule_demo2.py` 的输出同 `mymodule_demo.py` 。

如果导入 mymodule 的模块内已声明了 `__version__` ，就会产生冲突。这种情况出现的可能性并不低，因为每个模块在它的名称中声明版本号这种行为还是较常见的。因此菜推荐你使用 `import` 语句，尽管它会让你的程序稍微长些。

你也可以这样用：

```python
from mymodule import *
```

这会导入所有如 `say_hi` 这种公有名称，但不会导入 `__version__` 因为它由双下划线开头。

> 注意：请记好，你应该避免使用 `from...import *` 。
> 看到这，我估计 python 中双下划线包裹表私有，其他皆为公有。

<!-- -->

> **python 奥义**
> 
> python 的一条指导原则是“显式优于隐式”。在 python 中运行 `import this` 能了解更多。

## dir() {#dir-function}

内置的 `dir()` 函数返回某对象的定义的名称的列表。如果这对象是个模块，那么这个列表将包含其内定义的函数，类，变量。

这个函数还能接受参数。如果参数是模块名称，那么函数就返回指定模块所含的定义的名称的列表。如果没有参数，函数就返回当前模块的名称的列表。

例如:

```python
$ python
>>> import sys

# get names of attributes in sys module
>>> dir(sys)
['__displayhook__', '__doc__',
'argv', 'builtin_module_names',
'version', 'version_info']
# only few entries shown here

# get names of attributes for current module
>>> dir()
['__builtins__', '__doc__',
'__name__', '__package__', 'sys']

# create a new variable 'a'
>>> a = 5

>>> dir()
['__builtins__', '__doc__', '__name__', '__package__', 'sys', 'a']

# delete/remove a name
>>> del a

>>> dir()
['__builtins__', '__doc__', '__name__', '__package__', 'sys']
```

**它是怎样做的**

首先，我们看到 `dir` 用在被导入 `sys` 模块上。我们看到它包含了属性的巨长列表。

接着，我们再次使用 `dir` 函数，不过这次没有给它传递参数。默认的，它返回了当前模块的属性的列表。注意看，被导入的模块的列表也是这个列表的一部分。

为了在行为层面上观察 `dir` ，我们定义了一个新变量 `a` 并且给它赋了个值。然后 `dir` 来看看这列表中追加了同样名称的值。我们使用 `del` 语句从当前模块中移除这个变量或者属性之后，`dir` 函数的输出能再次反映出这个变化。

关于 `del` ——这个语句多用来**删除**变量或名称。在语句运行之后，本例中是 `del a` ，你将无法再访问变量 `a` ——就如同它从未存在过。

还要看到 `dir()` 函数能用在**任何**对象上。例如，运行 `dir(str)` 能得到 `str` 类的属性。

这还有个 [`vars()`](http://docs.python.org/3/library/functions.html#vars)  函数，它也许能给你属性以及相应的值，但它并不对所有类都起作用。

## 包 package

迄今，你肯定已经开始观察你程序的组织加够了。变量通常在函数之内，函数和全局变量一般都在模块内。怎么组织模块呢？包 (package) 闪亮登场。

包就是有 `__init__.py` 这个特殊文件的模块的文件夹。这个文件会告诉 python 这个文件夹是特殊的，因为它含有 python 模块。 

假定你想创建一个名称为 'world' 的包，其下还有 'asia' ，'africa' 等子包。这些子包含有模块如 'india' ，'madagascar' 等。

你可以这样来构建你的文件夹：

```
- <some folder present in the sys.path>/
    - world/
        - __init__.py
        - asia/
            - __init__.py
            - india/
                - __init__.py
                - foo.py
        - africa/
            - __init__.py
            - madagascar/
                - __init__.py
                - bar.py
```

包就是模块组织架构的一种便捷方式。在[标准库 standard library](./stdlib.md#stdlib) 中，你会看到更多的范例。

## 总结

函数是代码块的重用，模块是程序的重用。包是模块的组织架构。python 标准库就是包与模块的集合的范例。

我们了解了如何使用模块，创建自己的模块。

下面，我们会了解一些更有趣的概念，数据结构