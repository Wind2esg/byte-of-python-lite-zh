# 控制流 Control Flow {#control-flow}

迄今，我们所看到的程序中，基本都是一系列的语句，由 python 准确的按照从上至下的顺序执行。如果你想改变这个执行顺序，该怎么做？例如，你想要程序能够做出选择，根据不同的情况采取不同的行为，例如，根据当前时间打印“早上好”或“晚上好”？

也行正如你猜想的那样，这可正是控制流语句的用武之地。python 中有三种控制流语句--`if` ，`for` 和 `while` 。

## `if` 

`if` 语句用来检查某条件：*if* 这条件是真的，我们运行被称为 _if-block_ 的语句块，*else* 我们执行被称为 _else-block_ 的语句块。 *else* 语句是可选的。

请看示例 `if.py` ：

<!-- 在代码块中的标签并未展开 https://github.com/GitbookIO/gitbook/issues/707 -->
<pre><code class="lang-python">{% include "./programs/if.py" %}</code></pre>

输出为:

<pre><code>{% include "./programs/if.txt" %}</code></pre>

**它怎样做的**

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

Even though this is a very simple program, I have been pointing out a lot of things that you should notice. All these are pretty straightforward (and surprisingly simple for those of you from C/C++ backgrounds). You will need to become aware of all these things initially, but after some practice you will become comfortable with them, and it will all feel 'natural' to you.
尽管这是个非常简单的程序，我还是要指出很多你需要注意的地方。所有这些都是很通俗易懂的（对那些有 c 或 c++ 背景的出奇的容易）。初期，你需要了解这许多东西，但经过一系列练习之后，你会熟悉它们，那是你会感觉很舒适，很自然。

> python 中没有 `switch` 语句。你可以通过 `if` 和 `else` 语句的重复使用来完成同样的事情。（某些情形之下，使用 [字典 dictionary](./data_structures.md#dictionary) 会更快）

## The while Statement

The `while` statement allows you to repeatedly execute a block of statements as long as a condition is true. A `while` statement is an example of what is called a *looping* statement. A `while` statement can have an optional `else` clause.

Example (save as `while.py`):

<pre><code class="lang-python">{% include "./programs/while.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/while.txt" %}</code></pre>

**How It Works**

In this program, we are still playing the guessing game, but the advantage is that the user is allowed to keep guessing until he guesses correctly - there is no need to repeatedly run the program for each guess, as we have done in the previous section. This aptly demonstrates the use of the `while` statement.

We move the `input` and `if` statements to inside the `while` loop and set the variable `running` to `True` before the while loop. First, we check if the variable `running` is `True` and then proceed to execute the corresponding *while-block*. After this block is executed, the condition is again checked which in this case is the `running` variable. If it is true, we execute the while-block again, else we continue to execute the optional else-block and then continue to the next statement.

The `else` block is executed when the `while` loop condition becomes `False` - this may even be the first time that the condition is checked. If there is an `else` clause for a `while` loop, it is always executed unless you break out of the loop with a `break` statement.

The `True` and `False` are called Boolean types and you can consider them to be equivalent to the value `1` and `0` respectively.

> **Note for C/C++ Programmers**
> 
> Remember that you can have an `else` clause for the `while` loop.

## The `for` loop

The `for..in` statement is another looping statement which *iterates* over a sequence of objects i.e. go through each item in a sequence. We will see more about [sequences](./data_structures.md#sequence) in detail in later chapters. What you need to know right now is that a sequence is just an ordered collection of items.

Example (save as `for.py`):

<pre><code class="lang-python">{% include "./programs/for.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/for.txt" %}</code></pre>

**How It Works**

In this program, we are printing a *sequence* of numbers. We generate this sequence of numbers using the built-in `range` function.

What we do here is supply it two numbers and `range` returns a sequence of numbers starting from the first number and up to the second number. For example, `range(1,5)` gives the sequence `[1, 2, 3, 4]`. By default, `range` takes a step count of 1. If we supply a third number to `range`, then that becomes the step count. For example, `range(1,5,2)` gives `[1,3]`. Remember that the range extends *up to* the second number i.e. it does *not* include the second number.

Note that `range()` generates only one number at a time, if you want the full list of numbers, call `list()` on the `range()`, for example, `list(range(5))` will result in `[0, 1, 2, 3, 4]`. Lists are explained in the [data structures chapter](./data_structures.md#data-structures).

The `for` loop then iterates over this range - `for i in range(1,5)` is equivalent to `for i in [1, 2, 3, 4]` which is like assigning each number (or object) in the sequence to i, one at a time, and then executing the block of statements for each value of `i`.  In this case, we just print the value in the block of statements.

Remember that the `else` part is optional. When included, it is always executed once after the `for` loop is over unless a [break](#break-statement) statement is encountered.

Remember that the `for..in` loop works for any sequence. Here, we have a list of numbers generated by the built-in `range` function, but in general we can use any kind of sequence of any kind of objects! We will explore this idea in detail in later chapters.

> **Note for C/C++/Java/C# Programmers**
> 
> The Python `for` loop is radically different from the C/C++ `for` loop. C# programmers will note that the `for` loop in Python is similar to the `foreach` loop in C#. Java programmers will note that the same is similar to `for (int i : IntArray)` in Java 1.5.
> 
> In C/C++, if you want to write `for (int i = 0; i < 5; i++)`, then in Python you write just `for i in range(0,5)`. As you can see, the `for` loop is simpler, more expressive and less error prone in Python.

## The break Statement {#break-statement}

The `break` statement is used to *break* out of a loop statement i.e. stop the execution of a looping statement, even if the loop condition has not become `False` or the sequence of items has not been completely iterated over.

An important note is that if you *break* out of a `for` or `while` loop, any corresponding loop `else` block is **not** executed.

Example (save as `break.py`):

<pre><code class="lang-python">{% include "./programs/break.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/break.txt" %}</code></pre>

**How It Works**

In this program, we repeatedly take the user's input and print the length of each input each
time. We are providing a special condition to stop the program by checking if the user input is
`'quit'`. We stop the program by *breaking* out of the loop and reach the end of the program.

The length of the input string can be found out using the built-in `len` function.

Remember that the `break` statement can be used with the `for` loop as well.

**Swaroop's Poetic Python**

The input I have used here is a mini poem I have written:

```
Programming is fun
When the work is done
if you wanna make your work also fun:
    use Python!
```

## The `continue` Statement {#continue-statement}

The `continue` statement is used to tell Python to skip the rest of the statements in the current loop block and to *continue* to the next iteration of the loop.

Example (save as `continue.py`):

<pre><code class="lang-python">{% include "./programs/continue.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/continue.txt" %}</code></pre>

**How It Works**

In this program, we accept input from the user, but we process the input string only if it is at least 3 characters long. So, we use the built-in `len` function to get the length and if the length is less than 3, we skip the rest of the statements in the block by using the `continue` statement. Otherwise, the rest of the statements in the loop are executed, doing any kind of processing we want to do here.

Note that the `continue` statement works with the `for` loop as well.

## Summary

We have seen how to use the three control flow statements - `if`, `while` and `for` along with their associated `break` and `continue` statements. These are some of the most commonly used parts of Python and hence, becoming comfortable with them is essential.

Next, we will see how to create and use functions.
