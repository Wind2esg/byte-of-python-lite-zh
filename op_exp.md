# 运算符与表达式 Operators and Expressions {#op-exp}

大多数你写的语句都含有 _表达式_ 。`2 + 3` 就是个简单的表达式。表达式可以拆分为运算符 (operators) 和操作数 (operands)。


_Operators_ are functionality that do something and can be represented by symbols such as `+` or by special keywords. Operators require some data to operate on and such data is called _operands_. In this case, `2` and `3` are the operands.

_运算符_ 是具有某些功能的，它的形式可以是符号如 `+` ，或者特殊关键词。运算符需要有数据去运算，这些数据称为 _操作数_。

## 运算符 Operators

我们可以先简单看看运算符和它们的使用方法。

你看，你能使用互动解释器命令行来计算例子中给出的表达式。例如，试试  `2 + 3` ：

```python
>>> 2 + 3
5
>>> 3 * 5
15
>>>
```

运算符快速一览表：

- `+` （加）
    - `'a' + 'b'` 得到 `'ab'` ，。
    > python 中当操作数是字符串式，`+` 可以省略，即 `'a''b'` 得到 `'ab'`

- `-` （减）

- `*` （乘）
    - `2 * 3` 得到 `6` 。 `'la' * 3` 得到 `'lalala'` 。

- `**` （幂）
    - 返回 x 的 y 次幂
    - `3 ** 4` 得到 `81` （即 `3 * 3 * 3 * 3` ）。

- `/` （除）
    - `13 / 3` 得出 `4.333333333333333`

- `//` （除并且向下取整）
    - x 被 y 除，并且取小于结果的最大整数作为答案。请注意，如果其中某个值是浮点数，那么你就会得到浮点数的结果。 
    - `13 // 3` 得出 `4`
    - `9//1.81` 得出 `4.0`

- `%` （模）
    - 返回除的余数
    - `13 % 3` 得出 `1` 。 `-25.5 % 2.25` 得出 `1.5` 。

- `<<` （左移位）
    - 将数字的二进制位向左移动若干位（每一个数字在内存中都是使用二进制数 0 或 1 表示）。
    - `2 << 2` 得出 `8` 。 `2` 的二进制数是 `10` 。左移位 2 位得出 `1000` 即 `8` 。

- `>>` （右移位）

- `&` （按位与）
    - 将数字的二进制数对应位想比较，同为 1 则那一位结果为 1 ，否则为 0 。
    - `5 & 3` gives `1`.

- `|` （按位或）
    - 将数字的二进制数对应位想比较，同为 0 则那一位结果为 0 ，否则为 1 。
    - `5 | 3` gives `7`

- `^` （按位异或）
    - 将数字的二进制数对应位想比较，这两位相同则那一位结果为 0 ，否则为 1 。
    - `5 ^ 3` gives `6`

- `~` （按位取反）
    - x 的按位翻转得到的是 -(x+1) 。
    - `~5` 得出 `-6` 。http://stackoverflow.com/a/11810203 能够给你详细的信息。

- `<` （小于）

- `>` （大于）

- `<=` （小于等于）

- `>=` （大于等于）

- `==` （等于）

- `=` （赋值）
    - 将又侧的值赋给左侧的变量。
    > 注意它和 `==` 的区别。

- `!=` （不等于）

- `not` （布尔 非）
    - 如果 x 是 `True` ，返回 `False` 。 如果 x is `False` ，返回 `True` 。

- `and` （布尔 与）
    - `x and y` x 和 y 都为 `True` 时，返回 `True` 否则为 `False` 。
    - 如果 python 发现表达式左侧是 `False` ，那么它就不会看右侧。这叫做短路计算。

- `or` (布尔 或）
    - x 与 y 皆为 `False` 时，返回 `False` 否则为 `True` 。
    - `x = True; y = False; x or y` 返回 `True` 。这也适用短路计算。

## 数学运算符同赋值符的简写

对某个变量使用数学运算符并且将运算结果再赋值给这个变量实在太常见了，因此对于此类表达式有了如下的简写：

```python
a = 2
a = a * 3
```

可写作：

```python
a = 2
a *= 3
```

请注意，`var = var operation expression` 变成了 `var operation= expression` 。

## Evaluation Order

If you had an expression such as `2 + 3 * 4`, is the addition done first or the multiplication? Our high school maths tells us that the multiplication should be done first. This means that the multiplication operator has higher precedence than the addition operator.

The following table gives the precedence table for Python, from the lowest precedence (least binding) to the highest precedence (most binding). This means that in a given expression, Python will first evaluate the operators and expressions lower in the table before the ones listed higher in the table.

The following table, taken from the [Python reference manual](http://docs.python.org/3/reference/expressions.html#operator-precedence), is provided for the sake of completeness. It is far better to use parentheses to group operators and operands appropriately in order to explicitly specify the precedence. This makes the program more readable. See [Changing the Order of Evaluation](#changing-order-of-evaluation) below for details.

- `lambda` : Lambda Expression
- `if - else` : Conditional expression
- `or` : Boolean OR
- `and` : Boolean AND
- `not x` : Boolean NOT
- `in, not in, is, is not, <, <=, >, >=, !=, ==` : Comparisons, including membership tests and identity tests
- `|` : Bitwise OR
- `^` : Bitwise XOR
- `&` : Bitwise AND
- `<<, >>` : Shifts
- `+, -` : Addition and subtraction
- `*, /, //, %` : Multiplication, Division, Floor Division and Remainder
- `+x, -x, ~x` : Positive, Negative, bitwise NOT
- `**` : Exponentiation
- `x[index], x[index:index], x(arguments...), x.attribute` : Subscription, slicing, call, attribute reference
- `(expressions...), [expressions...], {key: value...}, {expressions...}` : Binding or tuple display, list display, dictionary display, set display

The operators which we have not already come across will be explained in later chapters.

Operators with the _same precedence_ are listed in the same row in the above table. For example, `+` and `-` have the same precedence.

## Changing the Order Of Evaluation {#changing-order-of-evaluation}

To make the expressions more readable, we can use parentheses. For example, `2 + (3 * 4)` is definitely easier to understand than `2 + 3 * 4` which requires knowledge of the operator precedences. As with everything else, the parentheses should be used reasonably (do not overdo it) and should not be redundant, as in `(2 + (3 * 4))`.

There is an additional advantage to using parentheses - it helps us to change the order of evaluation. For example, if you want addition to be evaluated before multiplication in an expression, then you can write something like `(2 + 3) * 4`.

## Associativity

Operators are usually associated from left to right. This means that operators with the same precedence are evaluated in a left to right manner. For example, `2 + 3 + 4` is evaluated as `(2 + 3) + 4`.

## Expressions

Example (save as `expression.py`):

```python
length = 5
breadth = 2

area = length * breadth
print('Area is', area)
print('Perimeter is', 2 * (length + breadth))
```

Output:

```
$ python expression.py
Area is 10
Perimeter is 14
```

**How It Works**

The length and breadth of the rectangle are stored in variables by the same name. We use these to calculate the area and perimeter of the rectangle with the help of expressions. We store the result of the expression `length * breadth` in the variable `area` and then print it using the `print` function. In the second case, we directly use the value of the expression `2 * (length + breadth)` in the print function.

Also, notice how Python _pretty-prints_ the output. Even though we have not specified a space between `'Area is'` and the variable `area`, Python puts it for us so that we get a clean nice output and the program is much more readable this way (since we don't need to worry about spacing in the strings we use for output). This is an example of how Python makes life easy for the programmer.

## Summary

We have seen how to use operators, operands and expressions - these are the basic building blocks of any program. Next, we will see how to make use of these in our programs using statements.
