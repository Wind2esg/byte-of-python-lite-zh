# 安装 {#installation}

本书中提到 python 3 一般是指高于 [python {{ book.pythonVersion }}](https://www.python.org/downloads/) 的版本

## windows 安装

到官网 [https://www.python.org/](https://www.python.org/downloads/) 下载合适的版本安装包。将 python 目录添加到环境变量 PATH 中。之后就直接在命令行环境中直接使用 python 命令运行 python 解释器。

## Mac OS X 安装

[Homebrew](http://brew.sh) 帮你解决， `brew install python3` 。一般来说，你需要在bash环境中在环境变量的末尾追加来实现对默认编译器版本的更改。

## GNU/Linux 安装

yum ， apt 等相应的包管理器能够轻松为你安装python，某些发行版本会内置 python，他们的版本未必是你想要的，你可以使用 alternatives 之类版本管理工具来切换 python 命令默认的解释器，但我建议使用绝对路径来运行你要的解释器。

# 使用编辑器

相对于命令行，一般我们都会使用更友好的开发工具，毕竟我们不总是要面临服务器编程的情况。

熟悉 Visual Studio 的我对 VisualStudioCode 一见倾心。VSCode 难以置信的轻量，功能强劲，集成 Git ，终端，调试框架，插件也应有尽有。 ctrl + shfit + x 搜索 python插件，安装。ctrl + shfit + p ,呼出命令面板，输入 se 即可看到选择解释器的智能提示，选择你默认的。连版本管理都有了，比 alternatives 之类版本管理工具方便多了吧？ ctrl + shfit + d ， debug 多种配置预置，F5 直接起航！简直不要再美，值得一试！

当然，个别默认快捷键根据系统有所不同，你可以使用组合键 ctrl + k ctrl + s 来查看默认的一些快捷键设置。

## 总结

hellow world ， NOW!
