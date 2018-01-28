# 标准库 standard library {#stdlib}

python 标准库包含了海量的实用模块，并且它已继承在 python 的安装中。熟悉标准库是至关重要的，因为如果你熟悉这些库的范围的话，问题能够很快得到解。

我们会探索更多库中常用的模块。['Library Reference' section](http://docs.python.org/3/library/) 能够找到 python 标准库中的所有模块的全部详细信息。

让我们探索一些实用模块。

> 请注意：如果你感觉本章的话题有些超前，你可以略过本章。但是，我强烈推荐当你熟悉 python 编程后回顾本章。

## `sys` 模块 {#sys}

`sys` 模块包含了系统性的功能。我们已经看到了 `sys.argv` 列表包含了命令行参数。

假设我们想要检测当前使用的 python 软件版本，`sys` 模块能够给我们信息。

<!-- The output should match pythonVersion variable in book.json -->
```python
>>> import sys
>>> sys.version_info
sys.version_info(major=3, minor=6, micro=0, releaselevel='final', serial=0)
>>> sys.version_info.major == 3
True
```

**它是怎样做的**

`sys` 模块有个 `version_info` 元组可以给出版本信息。第一个入口是主要版本。我们可以拉出这些信息来使用它。

## `logging` 模块 {#logging}

如果你想将一些调试消息或者重要信息储存起来，再根据它们来看看程序是否如你所想的那样运行的时候该怎么办？你该如何将这些消息**储存起来**？`logging` 模块可以实现这点。

请看示例 `stdlib_logging.py` ：

<pre><code class="lang-python">{% include "./programs/stdlib_logging.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/stdlib_logging.txt" %}</code></pre>

命令行中使用的 `cat` 命令来读取 `test.log` 文件。如果 `cat` 命令不可用，你可以使用文本编辑器来打开 `test.log` 文件。

**它是怎样做的**

我们使用了三个标准库模块。`os` 模块与系统互动，`platform` 模块是有关于平台即操作系统信息的，`logging` 模块是操作**日志**信息的。

首先，我们使用 `platform.platform()` 返回的字符串来检测当前操作系统。如果是 Windows，我们要找出 home 驱动器，home 文件夹以及我们想要储存信息的文件的名称。将这三个部分放在一起，我们能得到文件的完整路径。对于其他系统，我们只要知道用户的 home 文件夹就能得到文件的完整路径。

我们使用 `os.path.join()` 函数来将三个位置放在一起。使用一个特定的函数而不是仅仅将字符串加在一起是因为这个函数会确保完整的路径能匹配操作系统要求的格式。

我们配置了 `logging` 模块来将所有信息写入到我们指定的文件中。

最后，我们能把这些信息用作调试，信息，警告或者某些关键消息。一旦程序运行了，我们就检查这个文件，就算在程序运行途中没有任何信息显示给用户，我们也会知道程序中发生了什么。

## Module of the Week 系列 {#motw}

标准库有更多内容可以探索，如[调试 debugging](http://docs.python.org/3/library/pdb.html) ，[处理命令行选项 handling command line options](http://docs.python.org/3/library/argparse.html) ，[正则表达式regular expressions](http://docs.python.org/3/library/re.html) 等等。

学习标准库的最佳方法是拜读 Doug Hellmann 的著作 [Python Module of the Week](http://pymotw.com/2/contents.html) 系列，以及阅读 [Python documentation](http://docs.python.org/3/) 。

## 总结

我们探索了标准库中某些模块的功能。强烈推荐好好浏览 [Python Standard Library documentation](http://docs.python.org/3/library/) 对所有可用模块有个了解。

接着，我们会涉及到其他多个能帮助我们**完善** python 之旅的方面。