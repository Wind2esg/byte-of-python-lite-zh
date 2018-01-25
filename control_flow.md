# 控制流 Control Flow {#control-flow}

迄今，我们所看到的程序中，基本都是一系列的语句，由 python 准确的按照从上至下的顺序执行。如果你想改变这个执行顺序，该怎么做？例如，你想要程序能够做出选择，根据不同的情况采取不同的行为，例如，根据当前时间打印“早上好”或“晚上好”？

也行正如你猜想的那样，这可正是控制流语句的用武之地。python 中有三种控制流语句--`if` ，`for` 和 `while` 。

## if else

`if` 语句能检查某条件：**如果**这条件是真的，我们运行被称为 _if-block_ 的语句块，`else` **否则**我们执行被称为 _else-block_ 的语句块。*else* 语句是可选的。

请看示例 `if.py` ：

<!-- 在代码块中的标签并未展开 https://github.com/GitbookIO/gitbook/issues/707 -->
<pre><code class="lang-python">{% include "./programs/if.py" %}</code></pre>

输出为:

<pre><code>{% include "./programs/if.txt" %}</code></pre>

**它是怎样做的**

本程序中，我们得到用户的猜测的数字并且检查是否是我们已选的数字。我们将变量 `number` 设为任意整数，如 `23` 。然后，我们使用 `input()` 函数得到用户输入的猜测数字。函数是可复用的程序段。我们将在[下一章](./functions.md#functions)中更多的了解它们。

我们为内置的 `input` 函数提供一个字符串。`input` 会将这个字符串打印到屏幕上，并且等待用户的输入。当我们输入完，并且按下 `[enter]` 键，`input` 函数将返回保存我们输入的字符串。之后，我们使用 `int` 将此字符串转换为整数再将之储存在变量 `guess` 中。实际上，`int` 是一个类 (class) 但现在你所要知道的就是你可以用它将字符串转换为整数（前提是这个字符串是某个有效整数的文本形式)。

下面，我们比较用户猜测的数字以及我们所选的数字。如果它们相等，就打印成功的信息。请注意，我们使用缩进层次来告知 python 哪个语句归属于哪个块。这也是为何缩进在 pyuthon 中如此重要。我希望你能坚持“一致缩进”的准则。你会的，对吧？

然后，我们检查猜测的数字是否小于已选数字，如果是，我们通知用户他们必须往大点猜。这里的 `elif` 语句实际上是将 `if else if else` 合并成 `if elif else` 的简写。这使得程序更简化并且能适度减少所需要的缩进量。

`elif` 和 `else` 语句必须在逻辑行的末尾使用分号，并在之后接相应的语句块（当然，要有正确的缩进）。

你也可以在某个 `if` 的 if-block 中使用另一个 `if` 语句甚至依此循环--这叫做嵌套 `if` 语句。

请记好， `elif` 和 `else` 都是可选的。`if` 语句的最简短形式类似这样的：

```python
if True:
    print('Yes, it is true')
```

python 执行完 `if` 语句以及它相关联的 `elif` 和 `else` 语句之后，它会接着执行包含了 `if` 语句的块之后的语句。前例中，也就是主块（程序的起始之处），之后的语句是 `print('Done')` 语句。这之后，python 看到了程序的结尾，就结束了。

尽管这是个非常简单的程序，我还是要指出很多你需要注意的地方。所有这些都是很通俗易懂的（对那些有 c 或 c++ 背景的出奇的容易）。初期，你需要了解这许多东西，但经过一系列练习之后，你就会熟悉它们，那时你会感觉很舒适，很自然。

> python 中没有 `switch` 语句。你可以通过 `if` 和 `else` 语句的重复使用来完成同样的事情。（某些情形之下，使用 [字典 dictionary](./data_structures.md#dictionary) 会更快）

## while

`while` 语句，只要条件是真，那么你可以重复执行某语句块。`while` 是*循环 (looping)* 语句的实例之一。`while` 语句也可以有可选的 `else` 语句。

请看示例 `while.py`:

<pre><code class="lang-python">{% include "./programs/while.py" %}</code></pre>

输出为:

<pre><code>{% include "./programs/while.txt" %}</code></pre>

**它是怎样做的**

在这个程序中，我们接着玩猜数字的游戏，但是我们将它稍稍改进了一些，用户可以保留猜过的数字直到他猜对--我们不必像上一节中那样每次猜数都重新运行程序。这巧妙的阐释了 `while` 语句的作用。

我们将 `input` 和 `if` 语句放入 `while` 循环并在循环开始前将变量 `running` 设为 `True` 。我们先检测`running` 是否为 `True` ，然后执行相应的 *while-block* 。这个块执行之后，在此检测循环条件，本例中是 `running` 变量。如果它是真，那么我们再次执行 while-block ，不然我们接着执行可选的 else-block ，之后再顺次执行下面的语句。

当 `while` 的循环条件变为 `False` 时，`else` 块将会被执行--甚至初次检测循环条件时也如此。如果 `while` 循环有 `else` 语句，那么如果你不用 `break` 跳出循环的话，它总能得到执行。

`True` 与 `False` 被称为布尔 (Boolean) 类型，你可以把它们想象成值 `1` 与 `0`。

> 请记住，你的 `while` 循环也有 `else`
> Guido van Rossum 有点意思，他偏爱 `else`

## for

`for..in` 语句是另一种循环语句，它能在对象序列中进行*迭代 (iterate)*，即遍历序列中的每个项 (item) 。我们会从后面的章节 [序列 sequences](./data_structures.md#sequence) 做更多的了解。你现在仅需要知道序列是一些项的有序集合。

请看示例 `for.py`：

<pre><code class="lang-python">{% include "./programs/for.py" %}</code></pre>

输出为:

<pre><code>{% include "./programs/for.txt" %}</code></pre>

**它是怎样做的**

本示例中，我们打印出一个**序列**数字。我们使用内置的 `range` 函数来生成这个数字序列。

我们提供两个数，`range` 就能返回一个始于第一个数止于第二个数的数字序列。例如，`range(1,5)` 会得到 `1` , `2` , `3` , `4` 。默认的，`range` 取 1 作为步长 (step) 。如果我们给了 `range` 第三个数，那它就会使补偿。例如，`range(1,5,2)` 得出 `1` ,`3` 。一定要记好，`range` 的这个范围**止于**第二个数，也就是说**不包含**第二个数。

请注意 `range()` 每次只返回一个数，如果你想要所有数的列表，你可以在 `range()` 上调用 `list()` ，例如，`list(range(5))` 将会得到 `[0, 1, 2, 3, 4]` 。列表在 [数据结构 data structures](./data_structures.md#data-structures) 一章中会有更详细的解释。
 
`for` 循环会迭代指定的范围--`for i in range(1，5)` 等同于 `for i in [1, 2, 3, 4]` ，这好像是依次将序列中的数或者对象赋值给 i ，每次都执行一次语句块。本例中，我们仅将语句块中的值打印出来。

请记住 `else` 是可选的。当它存在时，如果没有 [break](#break-statement) 语句，它始终都会执行一次。

还有一点值得注意 `for..in` 循环能用于任何序列。在这里，我们是来生成数字列表，一般来说，我们可以使用各种对象的各样数列！这个观点我们会在之后章节里进行更多探索。

> python中 `for` 循环与 c 或 c++ 的 `for` 循环较大差异。c# 编程者会感到 与他们的 `foreach` 很相似。java 程序员也能发现其与 `for (int i : IntArray)` 的相似之处。

> 在 c 或 c++ 你需要这样写 `for (int i = 0; i < 5; i++)` ，而在 python 中，你仅需要  `for i in range(0,5)` 。如你所见，python 中的 `for` 循环更简单，更易理解，更健壮。

## break {#break-statement}

`break` 语句是用来**打破**循环的，即停止循环语句的执行，就算循环条件为真或者序列未迭代完也会停止。

非常重要一点是如果你**打破**了 `for` 或 `while` ，任何相应的循环的 `else` 块都**不会**执行的。

请看示例 `break.py` ：

<pre><code class="lang-python">{% include "./programs/break.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/break.txt" %}</code></pre>

**它是怎样做的**

此程序中，我们重复的获取用户的输入并且将其长度打印出来。我们提供了一个特定的条件来检测用户输入是否为 `'quit'` 来停止程序。我们**打破**循环，到达程序末尾来停止程序。

输入字符串的长度能够通过内置的 `len` 函数获得。

是的，`break` 语句也能在 `for` 循环中使用。

**Swaroop 的 Python 诗**

```
Programming is fun
When the work is done
if you wanna make your work also fun:
    use Python!
```

## continue {#continue-statement}

`continue` 语句用来告诉 python 跳过当前循环中的余下语句并且**继续**下一次循环的迭代。

请看示例 `continue.py` ：

<pre><code class="lang-python">{% include "./programs/continue.py" %}</code></pre>

输出为:

<pre><code>{% include "./programs/continue.txt" %}</code></pre>

**它是怎样做的**

本程序中，我们仅处理含有至少三个字符的用户输入字符串。所以，我们使用内置的 `len` 函数来获取长度，如果长度小于3， 我们使用 `continue` 略过余下语句，不然，循环中的余下语句就会执行。

当然，`continue` 语句也能在 `for` 循环中使用。

## 总结

我们已经看到如何使用 `if` ，`while` 与 `for` 三种控制流语句以及相关的 `break` 和 `continue` 语句。这些都是 python 中特别常用的。因此熟悉它们是必要的。

下面，我们来看看怎样创建和使用函数。