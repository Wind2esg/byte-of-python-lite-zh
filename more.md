# 更多

至今为止，我们已经学习了大多数将要用到的知识。在本章节，我们会了解那些能让我们的 python 知识更加圆满的知识。

## 传递元组

你想过从一个函数中返回两种不同的值吗？你可以的。你要做的就是使用一个元组。

```python
>>> def get_error_details():
...     return (2, 'details')
...
>>> errnum, errstr = get_error_details()
>>> errnum
2
>>> errstr
'details'
```

请注意 `a, b = <some expression>` 的作用是将表达式的结果转换为带两个值元组。

这也意味着在 python 中最快交换两个变量的方法是：

```python
>>> a = 5; b = 8
>>> a, b
(5, 8)
>>> a, b = b, a
>>> a, b
(8, 5)
```

> 这还是很有意思的。不需中间变量或者 `a = a + b; b = a - b; a = a - b;` 。

## 特殊方法

有一些特定的方法例如 `__init__` 和 `__del__` 方法在类中有特殊的意义。

特殊方法是用来模拟特定内置类型行为的。例如，如果你想在类中使用 `x[key]` 索引操作符，就像你在列表和元组中使用的那样，你索要做的就是实现 `__getitem__()` 方法。深入思考，实则这就是 python 在 `list` 类中的做法。

一些实用的特殊方法罗列如下表。如果你想知道更多关于特殊方法的信息，[请看手册](http://docs.python.org/3/reference/datamodel.html#special-method-names)。

- `__init__(self, ...)`
    - 在对象创建前调用，返回被创建的对象，以供使用。

- `__del__(self)`
    - 对象销毁前调用（可能会产生不可预计的问题，所以尽量避免使用）。

- `__str__(self)`
    - 当我们使用 `print` 函数或者 `str()` 的时候调用。

- `__lt__(self, other)`
    - < 被使用时调用。类似的，其他操作符如 + ，> 等也有相应的特殊方法。

- `__getitem__(self, key)`
    - 当 `x[key]` 这样的索引操作使用时调用。

- `__len__(self)`
    - 当对序列对象使用内置 `len()` 函数是调用。

## 单语句块

我们看到每个语句块都通过它的缩进等级来和其他语句块区分。这有个要注意的点。如果你的语句块仅包含单个语句，你可以在同一行指定它。如条件语句或循环语句。下面这个示例能更清晰的说明：

```python
>>> flag = True
>>> if flag: print('Yes')
...
Yes
```

请注意，在那使用的单个语句并不是被当做独立的块。尽管，你可以这样做来使你的程序更**短**，我强烈推荐你不要这么做，除非是为了检查错误。主要是因为如果你使用正确的缩进，再添加语句是很容易的。

## Lambda

`lambda` 语句能够用来创建新的函数对象。`lambda` 在本质上是一个参数，后面接一个表达式。`lambda` 变为函数的主体。表达式的值就是新函数的返回值。

请看示例 `more_lambda.py` ：

<pre><code class="lang-python">{% include "./programs/more_lambda.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/more_lambda.txt" %}</code></pre>

**它是怎样做的**

请注意，`list` 的 `sort` 方法所带的那个 `key` 参数能决定列表被如何排序（通常我们仅用升 (ascending) 序和降 (descending) 序）。本例中，我们想要使用自定义的排序，为此，我们必须写出这个函数。与其为一个仅在这里一次性使用的函数写一个独立的 `def` 块，我们更乐意使用 lambda 来创建这个新函数。

## 列表推导 list comprehensions

列表推导能够从已有列表中衍生出新列表。假设你有一个数字的列表，如果你想得到一个相应的新列表，它将已有列表中大于 2 的数字乘以 2 。列表推导就是这种情况下的理想选择。

请看示例 `more_list_comprehension.py` ：

<pre><code class="lang-python">{% include "./programs/more_list_comprehension.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/more_list_comprehension.txt" %}</code></pre>

**它是怎样做的**

在这里，我们通过条件 `if i > 2` 满足时执行乘 `2*i` 来衍生新列表。请记住，原列表保持原样不变。

使用列表推导的一大好处是减少我们使用循环处理列表中的每一个元素然后将其储存到新列表中时所需的样板 (boilerplate) 代码数量。

> 确实 python 此点更灵活，我们不需要总是循环遍历。

## 在函数中接收元组与字典

There is a special way of receiving parameters to a function as a tuple or a dictionary using the `*` or `**` prefix respectively. This is useful when taking variable number of arguments in the function.
这有一个特殊的方法能使函数接收元组或字典作为参数，那就是使用`*` 或 `**` 前缀。当函数中需要不定数量的变量时，这是相当有用的。

```python
>>> def powersum(power, *args):
...     '''Return the sum of each argument raised to the specified power.'''
...     total = 0
...     for i in args:
...         total += pow(i, power)
...     return total
...
>>> powersum(2, 3, 4)
25
>>> powersum(2, 10)
100
```

因为我们的 `args` 变量有 `*` 前缀，所有传递给函数的额外的参数都储存在 `args` 元祖中。如果使用的是 `**` 前缀，那么额外的参数就被认为是字典中的键值对。

## assert {#assert}

The `pop()` method removes and returns the last item from the list.
`assert` 语句是用来断言 (assert) 某事物是真的。例如，如果你很确定你将使用的列表中至少含有一个元素，并且你想检测一下它，如果它不为真，就抛出错误。`assert` 语句就是这种情况下的理想之选。当断言语句失败的时候，`AssertionError` 被抛出。

```python
>>> mylist = ['item']
>>> assert len(mylist) >= 1
>>> mylist.pop()
'item'
>>> assert len(mylist) >= 1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError
```

`assert` 语句应该被明智的使用。大多时候，最好还是捕获异常，而不是将问题交给用户，或者显示错误信息给用户，之后再退出程序。

## 装饰器 decorator {#decorator}

装饰器是封装函数的快捷方式。这对使用相同代码重复包装功能来说是很有用的。例如，我自己创建了一个 `rettry` 装饰器，我可以将它应用在任何函数上，只要在运行过程中有异常被抛出。它会一直重试，直到达到最大次数 5 并且每次重试间都会有个延迟。在你尝试通过网络调用远程计算机的情况下，这尤其有用：

<pre><code class="lang-python">{% include "./programs/more_decorator.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/more_decorator.txt" %}</code></pre>

**它是怎样做的**

请看：

- http://www.ibm.com/developerworks/linux/library/l-cpdecor.html
- http://toumorokoshi.github.io/dry-principles-through-python-decorators.html

## python 2 与 3 的差异 {#two-vs-three}

如果你想了解这其中的差异，请观看：

- ["Six" library](http://pythonhosted.org/six/)
- [Porting to Python 3 Redux by Armin](http://lucumr.pocoo.org/2013/5/21/porting-to-python-3-redux/)
- [Python 3 experience by PyDanny](http://pydanny.com/experiences-with-django-python3.html)
- [Official Django Guide to Porting to Python 3](https://docs.djangoproject.com/en/dev/topics/python3/)
- [Discussion on What are the advantages to python 3.x?](http://www.reddit.com/r/Python/comments/22ovb3/what_are_the_advantages_to_python_3x/)

## 总结

在本章中，我们涉及到 python 的一些特性，虽然仍有很多特性我们并未了解。但是，在这个阶段，这些已经足够你实践使用了。

下面，我们讨论如何继续深入 python 。
