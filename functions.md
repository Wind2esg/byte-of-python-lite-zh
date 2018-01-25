# 函数 Functions

函数是可复用的代码段。它们允许你为代码块命名，并且允许你使用指定的名称在程序其他任何地方不限次数的使用。这就是函数的**调用**。我们已经使用了许多内置函数如 `len` 和 `range` 。

在任何语言编写的正规程序里，函数概念是**最重要**的基础块。

函数使用关键字 `def` 定义。关键字之后就是这个函数的**标识符**名称，然后是包含变量的括号，最后行末尾就是分号。接下来的语句块也是函数的组成部分。下面这个例子会让你明白实际上这很简单 `function1.py` ：

<pre><code class="lang-python">{% include "./programs/function1.py" %}</code></pre>

输出为:

<pre><code>{% include "./programs/function1.txt" %}</code></pre>

**它是怎样做的**

按照之前讲的语法，我们定义了叫做 `say_hello` 的函数。这个函数没有参数，因此在括号内没有声明任何变量。函数的参数是函数接受的输入，我们可以在传递各种各样的值给它并能得到正确的相应的结果。

可以看到，我们两次调用了这个函数，而不需重复写代码。

## 参数 Parameters

函数有参数，它们是我们提供给函数的各种值，通过参数，函数就能做各种各样的事情了。这些参数很像变量，但它们的值是在我们调用函数时定义的，当函数运行时它们已然被赋值了。

参数在函数定义中的括号内指定，并且由逗号 `,` 分割。当我们调用函数时，我们以相同的方式为它们提供值。请注意这里的术语--函数定义里的参数叫做 *parameters* 。而调用函数时我们提供的那些参数称为 *arguments* 。

请看示例 `function_param.py` ：

<pre><code class="lang-python">{% include "./programs/function_param.py" %}</code></pre>

输出为：

<pre><code>{% include "./programs/function_param.txt" %}</code></pre>

**它是怎样做的**

在这，我们定义了 `print_max` 函数，并有两个参数 `a` 和 `b` 。我们通过一个简单的 `if..else` 找出较大的数并打印。 

第一次调用 `print_max` ，我们直接提供了参数。第二例中，我们调用了将改变量作为参数的函数。`print_max(x, y)` 将参数 `x` 值赋给参数 `a` ，`y` 赋给 `b` 。`print_max` 函数在两个例子中作用相同。

## 局部变量 Local Variables

When you declare variables inside a function definition, they are not related in any way to other variables with the same names used outside the function - i.e. variable names are *local* to the function. This is called the *scope* of the variable. All variables have the scope of the block they are declared in starting from the point of definition of the name.

当你在函数定义内声明变量时，它们与函数外的同名变量是毫不相关的--即对函数来说，变量名是**局部的 (local)** 。这叫做变量的**作用域 (scope)** 。变量的作用域起于它们声明之处，止于包含他们块结尾。

请看示例 `function_local.py` ：

<pre><code class="lang-python">{% include "./programs/function_local.py" %}</code></pre>

输出为:

<pre><code>{% include "./programs/function_local.txt" %}</code></pre>

**它是怎样做的**

我们第一次打印 `X` 的值是在函数体的第一行，python 使用了主块内函数定义之前定义的参数的值。

接着，我们把 `2` 赋给 `x` 。`X` 是我们函数的局部变量。因此，当我们在函数内改变 `x` 的值的时候，主块内定义的 `x` 不会发生改变。 

With the last `print` statement, we display the value of `x` as defined in the main block, thereby confirming that it is actually unaffected by the local assignment within the previously called function.
最后的 `print` 语句显示出主块内定义的 `x` 的值，因此，可以确认在调用的函数中的局部变量的赋值确实不会有任何影响。 

## 全局 global {#global-statement}

If you want to assign a value to a name defined at the top level of the program (i.e. not inside any kind of scope such as functions or classes), then you have to tell Python that the name is not local, but it is *global*. We do this using the `global` statement. It is impossible to assign a value to a variable defined outside a function without the `global` statement.

You can use the values of such variables defined outside the function (assuming there is no variable with the same name within the function). However, this is not encouraged and should be avoided since it becomes unclear to the reader of the program as to where that variable's definition is. Using the `global` statement makes it amply clear that the variable is defined in an outermost block.

Example (save as `function_global.py`):

<pre><code class="lang-python">{% include "./programs/function_global.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_global.txt" %}</code></pre>

**How It Works**

The `global` statement is used to declare that `x` is a global variable - hence, when we assign a value to `x` inside the function, that change is reflected when we use the value of `x` in the main block.

You can specify more than one global variable using the same `global` statement e.g. `global x, y, z`.

## Default Argument Values {#default-arguments}

For some functions, you may want to make some parameters *optional* and use default values in case the user does not want to provide values for them. This is done with the help of default argument values. You can specify default argument values for parameters by appending to the parameter name in the function definition the assignment operator (`=`) followed by the default value.

Note that the default argument value should be a constant. More precisely, the default argument value should be immutable - this is explained in detail in later chapters. For now, just remember this.

Example (save as `function_default.py`):

<pre><code class="lang-python">{% include "./programs/function_default.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_default.txt" %}</code></pre>

**How It Works**

The function named `say` is used to print a string as many times as specified. If we don't supply a value, then by default, the string is printed just once. We achieve this by specifying a default argument value of `1` to the parameter `times`.

In the first usage of `say`, we supply only the string and it prints the string once. In the second usage of `say`, we supply both the string and an argument `5` stating that we want to *say* the string message 5 times.

> *CAUTION*
> 
> Only those parameters which are at the end of the parameter list can be given default argument
> values i.e. you cannot have a parameter with a default argument value preceding a parameter without
> a default argument value in the function's parameter list.
> 
> This is because the values are assigned to the parameters by position. For example,`def func(a,
> b=5)` is valid, but `def func(a=5, b)` is *not valid*.

## Keyword Arguments

If you have some functions with many parameters and you want to specify only some of them, then you can give values for such parameters by naming them - this is called *keyword arguments* - we use the name (keyword) instead of the position (which we have been using all along) to specify the arguments to the function.

There are two advantages - one, using the function is easier since we do not need to worry about the order of the arguments. Two, we can give values to only those parameters to which we want to, provided that the other parameters have default argument values.

Example (save as `function_keyword.py`):

<pre><code class="lang-python">{% include "./programs/function_keyword.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_keyword.txt" %}</code></pre>

**How It Works**

The function named `func` has one parameter without a default argument value, followed by two parameters with default argument values.

In the first usage, `func(3, 7)`, the parameter `a` gets the value `3`, the parameter `b` gets the value `7` and `c` gets the default value of `10`.

In the second usage `func(25, c=24)`, the variable `a` gets the value of 25 due to the position of the argument. Then, the parameter `c` gets the value of `24` due to naming i.e. keyword arguments. The variable `b` gets the default value of `5`.

In the third usage `func(c=50, a=100)`, we use keyword arguments for all specified values. Notice that we are specifying the value for parameter `c` before that for `a` even though `a` is defined before `c` in the function definition.

## VarArgs parameters

Sometimes you might want to define a function that can take _any_ number of parameters, i.e. **var**iable number of **arg**uments, this can be achieved by using the stars (save as `function_varargs.py`):

<pre><code class="lang-python">{% include "./programs/function_varargs.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_varargs.txt" %}</code></pre>

**How It Works**

When we declare a starred parameter such as `*param`, then all the positional arguments from that point till the end are collected as a tuple called 'param'.

Similarly, when we declare a double-starred parameter such as `**param`, then all the keyword arguments from that point till the end are collected as a dictionary called 'param'.

We will explore tuples and dictionaries in a [later chapter](./data_structures.md#data-structures).

## The `return` statement {#return-statement}

The `return` statement is used to *return* from a function i.e. break out of the function. We can optionally *return a value* from the function as well.

Example (save as `function_return.py`):

<pre><code class="lang-python">{% include "./programs/function_return.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_return.txt" %}</code></pre>

**How It Works**

The `maximum` function returns the maximum of the parameters, in this case the numbers supplied to the function. It uses a simple `if..else` statement to find the greater value and then *returns* that value.

Note that a `return` statement without a value is equivalent to `return None`. `None` is a special type in Python that represents nothingness. For example, it is used to indicate that a variable has no value if it has a value of `None`.

Every function implicitly contains a `return None` statement at the end unless you have written your own `return` statement. You can see this by running `print(some_function())` where the function `some_function` does not use the `return` statement such as:

```python
def some_function():
    pass
```

The `pass` statement is used in Python to indicate an empty block of statements.

> TIP: There is a built-in function called `max` that already implements the 'find maximum' functionality, so use this built-in function whenever possible.

## DocStrings

Python has a nifty feature called *documentation strings*, usually referred to by its shorter name *docstrings*. DocStrings are an important tool that you should make use of since it helps to document the program better and makes it easier to understand. Amazingly, we can even get the docstring back from, say a function, when the program is actually running!

Example (save as `function_docstring.py`):

<pre><code class="lang-python">{% include "./programs/function_docstring.py" %}</code></pre>

Output:

<pre><code>{% include "./programs/function_docstring.txt" %}</code></pre>

**How It Works**

A string on the first logical line of a function is the *docstring* for that function. Note that DocStrings also apply to [modules](./modules.md#modules) and [classes](./oop.md#oop) which we will learn about in the respective chapters.

The convention followed for a docstring is a multi-line string where the first line starts with a capital letter and ends with a dot. Then the second line is blank followed by any detailed explanation starting from the third line. You are *strongly advised* to follow this convention for all your docstrings for all your non-trivial functions.

We can access the docstring of the `print_max` function using the `__doc__` (notice the *double underscores*) attribute (name belonging to) of the function. Just remember that Python treats *everything* as an object and this includes functions. We'll learn more about objects in the chapter on [classes](./oop.md#oop).

If you have used `help()` in Python, then you have already seen the usage of docstrings! What it does is just fetch the `__doc__` attribute of that function and displays it in a neat manner for you. You can try it out on the function above - just include `help(print_max)` in your program. Remember to press the `q` key to exit `help`.

Automated tools can retrieve the documentation from your program in this manner. Therefore, I *strongly recommend* that you use docstrings for any non-trivial function that you write. The `pydoc` command that comes with your Python distribution works similarly to `help()` using docstrings.

## Summary

We have seen so many aspects of functions but note that we still haven't covered all aspects of them. However, we have already covered most of what you'll use regarding Python functions on an everyday basis.

Next, we will see how to use as well as create Python modules.
