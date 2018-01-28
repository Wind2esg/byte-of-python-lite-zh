# 异常 exception

当程序中发生**意料之外**的事时，异常 (exception) 就产生了。例如，你要读取一个文件，但这个文件并不存在时会怎样？或者在程序运行时，你不小心删掉了它的话会怎样？这种情况都交由**异常**处理。

类似的，你的程序有不合法语句时会怎样？python 会这样处理，抬起它的手，然后告诉你这有个**错误 (error)** 。

## 错误 error

设想一个简单的 `print` 函数调用。你错将 `print` 写成 `Print` 的话会怎么样？请注意这个大写。本例中，python **抛出 (raise)** 一个语法错误。

> raise 译作“抛出”，是因为通常我们都习惯说**抛出**异常或错误。
```python
>>> Print("Hello World")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'Print' is not defined
>>> print("Hello World")
Hello World
```

仔细看，一个 `NameError` 被抛出，它的位置也被侦测到并打印出来。这是此错误的**错误句柄 (error handler)** 的作用。

## 异常

我们将要**试着**读取用户输入。键入下例中的第一行，然后按下 `Enter` 键。当你机器的命令行提示符等待你输入的时候，按下相应的终止热键，看看会发生什么。

```python
>>> s = input('Enter something --> ')
Enter something --> Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
EOFError
```

python 抛出了叫做 `EOFError` 的错误，最主要是说在它不期望看到**文件结尾**的地方，发现了**EOF**符号。

> EOF 不陌生吧？

## 异常处理

我们可以使用 `try..except` 语句来处理异常。我们主要是将我们普通语句放入 try-block 然后将所有的错误句柄放在 except-block 中。

> try catch 更常见。

请看示例 `exceptions_handle.py` ：

<pre><code class="lang-python">{% include "./programs/exceptions_handle.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/exceptions_handle.txt" %}</code></pre>

**它是怎样做的**

我们将所有可能抛出异常或者错误的语句都放入 `try` 块中，然后将相应的句柄放在 `except` 语句或块里。`except` 语句会处理被特指某个错误或异常，或者一括号的错误或者异常列表。如果没有为这些错误和异常提供名称，它就会处理**所有**的错误和异常。

每个 `try` 语句都至少得有一个 `except` 语句与其相关联。否则 try 的意义何在？

如果有错误和异常是没有被处理的，python 默认的句柄就会被调用，它会停止程序运行并且打印错误消息。这些行为我们在上面已经见过了。

你还可以在 `try..except` 这使用 `else` 语句。如果没有异常产生，`else` 语句会被执行。

在下个例子中，你会看到怎样取得异常对象，通过它来获取更多信息。

## 抛出异常

你可以使用 `rasie` 语句，提供错误或者异常的名称以及异常对象来**抛出**异常。

你要抛出的错误或者异常必须直接和间接的继承自 `Exception` 类。

请看示例 `exceptions_raise.py` ：

<pre><code class="lang-python">{% include "./programs/exceptions_raise.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/exceptions_raise.txt" %}</code></pre>

**它是怎样做的**

在这里，我们创建了我们自己的异常类型。这个新异常类型叫做 `ShortInputException`。它有两个字段，`length` 是给定输入的长度，`atleast` 是程序要求的最小长高度。

在 `except` 语句中，我们指明这个类，它的相应对象，储存在 `as` 后的变量名中。这就如同函数调用中的参数 (parameters 和 arguments) 。在特定的 `except` 语句中，我们使用异常对象的 `length` 和 `atleast` 字段来打印正确信息给用户。

> 异常处理这块我们可以多谈谈。
> 现在已经有一些禁用 try catch 的声音了。
> 根据 try except 或 catch 的特性和继承的特性，我们得知异常处理时指定的类范围过大，这将会屏蔽应有的错误提示，这是编程不友好的。另外它们的消耗也不小，这是性能不友好。
> 但是我并不推荐禁用。它的本意有两点，第一是用户友好，防止程序出现异常或者错误而崩溃。第二，提供自定义的抛出处理机制。不能把使用者的笨拙怪罪于刀，对吧。

## Try ... Finally {#try-finally}

假设你打的程序读取一个文件。无论有无异常，你怎么来确保文件对象被正确关闭？你可以使用 `finally` 块。

请看示例 `exceptions_finally.py` ：

<pre><code class="lang-python">{% include "./programs/exceptions_finally.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/exceptions_finally.txt" %}</code></pre>

**它是怎样做的**

我们像平常那样做文件读取，但我们使用 `time.sleep` 函数来使程序每打印一行后睡眠 2 秒，这样程序的运行就慢下来了。当程序运行的时候，按 `ctrl + c` 能打断或者取消程序。

仔细观察 `KeyboardInterrupt` 异常被抛出，程序退出了。但是，在程序退出之前，finally 语句在执行了，文件对象总能关闭。

请注意，一个变量被赋值 0 或者 `None` ，或者一个变量引用空的序列或者集合在 python 中被看做是 `False` 。这也是我们在上述代码中使用 `if: f` 的原因。

还请注意，在 `print`之后我们还使用了 `sys.stdout.flush()` ，来使其能立即打印到屏幕上。

## with {#with}

在 `try` 块内获取一个资源接着在 `finally` 块中释放这个资源是一个很常见的模式。因此，这还有一个 `with` 语句能利索的完成这件事。

请看示例 `exceptions_using_with.py` ：

<pre><code class="lang-python">{% include "./programs/exceptions_using_with.py" %}</code></pre>

**它是怎样做的**

输出同前例一样。不同的是我们在 `open` 函数中使用 `with` 语句——我们可以将文件的关闭交由 `with open` 自动完成。

在表面之下是 `with` 语句使用了一个协议。它通过 `open` 语句的返回获取对象，在此例中让我们称之为“thefile”。

`thefile.__enter__` 函数总在 `with` 之后的代码块开始前被调用。`thefile.__exit__` 函数总在这个代码块结束之后被调用。

所以我们写在 `finally` 块中的代码会被 `__exit__` 方法自动处理。这能帮助我们避免在必须重复显式使用 `try..finally` 语句。

关于这个话题的更多讨论略微超出本书范围，[PEP 343](http://www.python.org/dev/peps/pep-0343/) 能够给出更全面的解释。

## 总结

我们已经讨论了 `try..except` 和 `try..finally` 语句的使用。我们了解到了怎样创建我们自己的异常类型，以及怎样抛出异常。

接着，我们会探索标准库 (Python Standard Library) 。
