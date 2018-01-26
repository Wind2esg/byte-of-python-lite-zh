# 数据结构 Data Structures {#data-structures}

数据结构 (data structure) 是能够储存**数据**的**结构**。换句话说，它们是储存相关数据的集合。

python 有四种数据结构——**列表 (list) ，元组 (tuple) ，字典 (dictionary) 和集合 (set)** 。我们将看到它们如何发挥作用。

## 列表 List

`list` 这种数据结构是一种有序集合，即你可以将**序列**储存在列表里。这不难理解，如果你能想到购物清单。当然，这其中可能也存在差异，你的购物清单可能是每行一项，而 python 中，你使用逗号 `,` 来隔开那些项。

列表中的项应该包含在中括号内，python 就能明白你要指定一个列表。在列表中可以添加，移除和搜索项。由于我们能能够添加和移除项，我们称列表为**可变**数据类型，即这种类型是可以更改的。

## 速览对象与类

尽管到现在我们还要推迟对象和类的相关讨论，但你还是需要一些解释来帮助理解列表。我们会在[后面的章节](./oop.md#oop)里继续探索这个话题。

列表是对象和类的用法的实例之一。当我们使用变量 `i` 并为它赋值，比如说赋值为整数 `5` 的时候，你可以把这想做创建一个**类**（即类型）`int` 的**对象**（即实例）`i`。实际上，阅读 `help(int)` 可以帮助你了解。

类还可以有**方法 (method)** 即专属该类的函数。只有该类的对象可以使用这些方法。例如，python 为 ` list` 提供的 `append` 方法，该方法是的你可以在列表的末尾追加项。注意访问对象的方法使用的是点标记法。

一个类还能有**字段**，字段是专属该类的变量。只有该类的对象可以使用这些变量或名称。字段也使用点标记法访问，例如 `mylist.field` 。

请看示例 `ds_using_list.py` ：

<pre><code class="lang-python">{% include "./programs/ds_using_list.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/ds_using_list.txt" %}</code></pre>

**它是怎么做的**

变量 `shoplist` 是某兄台去市场购物的清单。在 `shoplist` 中，我们仅储存那些我们要买的项的名称。但是你可以添加**任意对象**到这个列表里，可以是数字，甚至是其他列表。

我们还使用了 `for..in` 循环来迭代列表中项。到此，你一定意识到列表也是序列。序列的特殊之处在[下面的部分](#sequence)会作更多探讨。

请注意，在 `print` 函数调用中的 `end` 参数说明我们用一个空格来做输出的结尾，而不是换行符。

接着，如我们前面所讲，我们使用列表对象的 `append` 方法向列表中添加项。然后，我们通过打印列表中的内容来检测这个项是否真的添加到了列表之中。要实现这个目的，我们只需将列表传递给 `print` 函数，它就能轻松的被打印出来。

再之后，我们使用列表的 `sort` 方法来将列表排序。一定要理解这个方法影响这个列表本身，而不是另造一个列表——这与字符串是不同的。这也是为何我们说列表是**可变的**，而字符串是**不可变的**。

最后，当我们在市场里购买完某项时，我们将之从列表中移除。使用 `del` 语句即可。在这里，我们要留意 `del` 语句会将为我们想要移除的那个项从列表中移除。我们指定想要移除的项是列表中的第一项，因此我们用 `del shoplist[0]`（请记住 python 从 0 开始计数）。

如果你下那个知道列表对象所有的方法，看看 `help(list)` 。

## 元组 Tuple

元组用以储存在一起的多个对象。它们和列表很像，只是没有列表类给你的那些伸缩方法。元组的一个主要特性就是**不可变**如同字符串那样。你不能修改元组。

元组的定义方法是在括号内指定项，这些项由逗号分隔。这里的括号是可选的。

如果能确定某语句或者某用户定义的函数的值得集合不会发生改变，通常我们使用元组。

请看示例 `ds_using_tuple.py` ：

<pre><code class="lang-python">{% include "./programs/ds_using_tuple.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/ds_using_tuple.txt" %}</code></pre>

**它是怎样做的**

变量 `zoo` 指的是一些项的元组。我们见到 `len` 函数可以用来获取元组的长度。这也说明了元组也是[序列 sequence](#sequence) 。

现在，由于老动物园关闭，我们将这些动物转移到新动物园里。因此，`new_zoo` 元组中包含了原本就在那的动物以及从老动物园带过来的动物。回归现实，请注意在被元组内的元组仍是元组。

就像在列表中那样，我们可以通过在一对中括号内指定项的位置来访问元组中的项。这种使用形式被称作**索引 (indexing)** 运算符。我们使用 `new_zoo[2]` 指定 `new_zoo` 的第三项，用 `new_zoo[2][2]` 来指定 `new_zoo` 元组的第三项内的第三项。如果你明白这个用法，这还是很简单的。

> **没有或者仅有一项的元组**
> 
> 空元组通过一对内中为空的括号构造，如 `myempty = ()` 。但是，当元组仅有一个项时，就没那么简单了。你不许使用一个逗号在这仅有的项之后，以求 python 能去分辨是一个元组还是某表达式中包围对象的一对括号，也就是说，如果你想要一个仅包含一个项 `2` 的元组，你必须像 `singleton = (2 , )` 这样来指定它。
> 这是我首次见到这样的语法。

<!-- -->

> 被包含在列表之内的列表不会失去它的身份指的是列表不会像在 Perl 中那样被摊平。这个道理同样适用于元祖中的元组，或列表中的元组，或元祖中的列表等。python 看来，它们只是储存在其他对象中的对象。仅此而已。

## 字典 Dictionary

字典有些像地址簿，你只需知道他或她的名称，就能找到这个人的地址或者详细联系方式，也就是说，我们将**键 (key)** 与**值**相联系。请记好，键必须是唯一的，就好像如果你的地址簿有重名的两个人，你就没法确认信息。

还要注意对于字典的键只能使用不可变对象如字符串，对于值，可变不可变皆可。也就是说你仅能使用简单对象作为键。

在字典中指定键值对 (pair) 使用的标记如 `d = {key1 : value1, key2 : value2 }` 。请注意，键和值使用冒号 `:` 隔开，本身是被逗号隔开，所有这些都包含在一对花括号内。

请记住，字典中的键值对是无序的。如果你想要其呈现出某种顺序，你必须在使用前对它们自行排序。

你使用的字典是 `dict` 类的对象或实例。

请看示例 `ds_using_dict.py` ：

<pre><code class="lang-python">{% include "./programs/ds_using_dict.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/ds_using_dict.txt" %}</code></pre>

**它怎样做到的**

我们使用之前探讨过的标记方式创建了字典 `ab` 。接着我们再在通过列表和元组内容中讲过的索引操作符中指定键来访问其中的键值对。看看这语法多简单。

我们使用老朋友—— `del` 语句来删除键值对。我们简单的指定字典，在索引操作符中指定想要移除的那个键值对的键，将其传递给 `del` 语句。整个操作中，我们不需知晓与此键相对应的值是什么。

接着，我们使用字典中的 `item` 方法来遍历字典中的每一对键值对。`items` 方法返回一个元组的列表，内中每一个元组都包含一对项——键与紧随其后的值。通过 `for..in` 循环，我们获取到每一对键值对并将其相应的赋值给变量 `name` 和 `address`，最后在 for-block 中打印。

增加新的键值对只需要使用索引操作符访问键并复制就可以，如我们在上例中对 Guido 的操作。

我们可以使用 `in` 操作符来检测某键值对是否存在。

`help(dict)` 可以给你 `dict` 类的方法列表。

> **关键字参数和字典**
> 
> 如果你再函数中使用了关键字参数，那么你已经使用过字典了。想想——你在函数定义的参数列表中指定了键值对，你在函数中访问那些变量，其实就是在访问字典的键（这在编译器设计术语中被称为**符号表 (symbol table)** ）

## 序列 Sequence

Lists, tuples and strings are examples of sequences, but what are sequences and what is so special about them?

The major features are *membership tests*, (i.e. the `in` and `not in` expressions) and *indexing operations*, which allow us to fetch a particular item in the sequence directly.

The three types of sequences mentioned above - lists, tuples and strings, also have a *slicing* operation which allows us to retrieve a slice of the sequence i.e. a part of the sequence.

Example (save as `ds_seq.py`):

<pre><code class="lang-python">{% include "./programs/ds_seq.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/ds_seq.txt" %}</code></pre>

**How It Works**

First, we see how to use indexes to get individual items of a sequence. This is also referred to as the _subscription operation_. Whenever you specify a number to a sequence within square brackets as shown above, Python will fetch you the item corresponding to that position in the sequence. Remember that Python starts counting numbers from 0. Hence, `shoplist[0]` fetches the first item and `shoplist[3]` fetches the fourth item in the `shoplist`sequence.

The index can also be a negative number, in which case, the position is calculated from the end of the sequence. Therefore, `shoplist[-1]` refers to the last item in the sequence and `shoplist[-2]` fetches the second last item in the sequence.

The slicing operation is used by specifying the name of the sequence followed by an optional pair of numbers separated by a colon within square brackets. Note that this is very similar to the indexing operation you have been using till now. Remember the numbers are optional but the colon isn't.

The first number (before the colon) in the slicing operation refers to the position from where the slice starts and the second number (after the colon) indicates where the slice will stop at. If the first number is not specified, Python will start at the beginning of the sequence. If the second number is left out, Python will stop at the end of the sequence. Note that the slice returned _starts_ at the start position and will end just before the _end_ position i.e. the start position is included but the end position is excluded from the sequence slice.

Thus, `shoplist[1:3]` returns a slice of the sequence starting at position 1, includes position 2 but stops at position 3 and therefore a *slice* of two items is returned.  Similarly, `shoplist[:]` returns a copy of the whole sequence.

You can also do slicing with negative positions. Negative numbers are used for positions from the end of the sequence. For example, `shoplist[:-1]` will return a slice of the sequence which excludes the last item of the sequence but contains everything else.

You can also provide a third argument for the slice, which is the _step_ for the slicing (by default, the step size is 1):

```python
>>> shoplist = ['apple', 'mango', 'carrot', 'banana']
>>> shoplist[::1]
['apple', 'mango', 'carrot', 'banana']
>>> shoplist[::2]
['apple', 'carrot']
>>> shoplist[::3]
['apple', 'banana']
>>> shoplist[::-1]
['banana', 'carrot', 'mango', 'apple']
```

Notice that when the step is 2, we get the items with position 0, 2,... When the step size is 3, we get the items with position 0, 3, etc.

Try various combinations of such slice specifications using the Python interpreter interactively i.e. the prompt so that you can see the results immediately. The great thing about sequences is that you can access tuples, lists and strings all in the same way!

## Set

Sets are _unordered_ collections of simple objects. These are used when the existence of an object in a collection is more important than the order or how many times it occurs.

Using sets, you can test for membership, whether it is a subset of another set, find the intersection between two sets, and so on.

```python
>>> bri = set(['brazil', 'russia', 'india'])
>>> 'india' in bri
True
>>> 'usa' in bri
False
>>> bric = bri.copy()
>>> bric.add('china')
>>> bric.issuperset(bri)
True
>>> bri.remove('russia')
>>> bri & bric # OR bri.intersection(bric)
{'brazil', 'india'}
```

**How It Works**

If you remember basic set theory mathematics from school, then this example is fairly self-explanatory.  But if not, you can google "set theory" and "Venn diagram" to better understand our use of sets in Python.

## References

When you create an object and assign it to a variable, the variable only _refers_ to the object and does not represent the object itself!  That is, the variable name points to that part of your computer's memory where the object is stored. This is called *binding* the name to the object.

Generally, you don't need to be worried about this, but there is a subtle effect due to references which you need to be aware of:

Example (save as `ds_reference.py`):

<pre><code class="lang-python">{% include "./programs/ds_reference.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/ds_reference.txt" %}</code></pre>

**How It Works**

Most of the explanation is available in the comments.

Remember that if you want to make a copy of a list or such kinds of sequences or complex objects (not simple _objects_ such as integers), then you have to use the slicing operation to make a copy. If you just assign the variable name to another name, both of them will ''refer'' to the same object and this could be trouble if you are not careful.

> **Note for Perl programmers**
> 
> Remember that an assignment statement for lists does **not** create a copy. You have to use slicing operation to make a copy of the sequence.

## More About Strings {#more-strings}

We have already discussed strings in detail earlier. What more can there be to know?  Well, did you know that strings are also objects and have methods which do everything from checking part of a string to stripping spaces?  In fact, you've already been using a string method... the `format` method!

The strings that you use in programs are all objects of the class `str`.  Some useful methods of this class are demonstrated in the next example. For a complete list of such methods, see `help(str)`.

Example (save as `ds_str_methods.py`):

<pre><code class="lang-python">{% include "./programs/ds_str_methods.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/ds_str_methods.txt" %}</code></pre>

**How It Works**

Here, we see a lot of the string methods in action. The `startswith` method is used to find out whether the string starts with the given string. The `in` operator is used to check if a given string is a part of the string.

The `find` method is used to locate the position of the given substring within the string; `find` returns -1 if it is unsuccessful in finding the substring. The `str` class also has a neat method to `join` the items of a sequence with the string acting as a delimiter between each item of the sequence and returns a bigger string generated from this.

## Summary

We have explored the various built-in data structures of Python in detail. These data structures will be essential for writing programs of reasonable size.

Now that we have a lot of the basics of Python in place, we will next see how to design and write a real-world Python program.
