# 工欲善其事

通过 Hello World 你已经认识了**解释器命令行**，并体验了它如何运行 python 代码。

python 程序的运行还可以**通过解释器来运行源代码文件**，将之前的代码保存到 HelloWorld.py 文件中，shell 切换到文件所在目录，输入 `python HelloWorld.py`。

## 使用编辑器

相对于命令行，一般我们都会使用更友好的开发工具，毕竟我们不总是要面临服务器编程的情况。

原著作者推荐的编辑器 [PyCharm Educational Edition](https://www.jetbrains.com/pycharm-edu/)

我个人对 [VisualStudioCode](https://code.visualstudio.com) 更青睐，它是微软出品的集成开发环境。

它难以置信的轻便迅捷，能量强大，集成 Git 和调试框架，还内置了插件商店与管理器。

在界面左侧图标中寻找并切换到 Extension 插件面板，搜索安装 python 插件。在界面顶端菜单点击 View -> command palettte ，输入 `python:select interpreter` 根据智能提示选择即可。Git 面板提供了 UI 操作，为了能正常使用它，你可能需要在用户设置中添加 git 的执行路径。在顶端菜单 File -> preference -> setting 在右面添加，`"git path": "yourGitPath"` 。 调试框架也很容易使用，初次调试的话仅需要按提示单击，添加预置的配置文件。基本配置就已完毕，**可用 F5 在调试框架内运行程序**。

解释型语言没有狭义的静态编译过程，一般我们都会使用其他工具来帮助我们检查语法。如果你有兴趣探索一下用户设置，Python Configuration 有着丰富的内容。想必你会注意到 linting 这个关键词。这就是目前支持的语法检查工具的相关设置了。我们可以看到有 flake8 ，mypy ，pep8等。想要使用他们我们可以试着在插件商店搜索，或者自行安装后，增添配置，是否启用，路径等等。配置完毕就可以在 command palette 调用他们。formatting 有 autopep8 ，yapf 它们可以帮助我们整理源代码排版，增加可读性。

如果你对 VSCode 满意，可以探索更高级些的使用方式如快捷键，命令面板和终端等的使用。

你非常有兴趣的话，可以到 github 去研究它。采用 MIT LIcense 许可开源，[https://github.com/microsoft/vscode](https://github.com/microsoft/vscode) 。

## 帮助文档 help

对任何开发来说，帮助文档都是必要的工具。

除了官方文档 [https://www.python.org/doc/](https://www.python.org/doc/) , 解释器命令行下的 `help` 也是必不可少的利器。一般直接用 `help(object)` ，这里的 object 可以是任何东西，比如 `help('help')` 。

## 总结

你已能使用合适的工具来编写，保存 python 程序了，并且也掌握了三种运行它们的方式。

接下来我们学习一些 ptyhon 中的概念。
