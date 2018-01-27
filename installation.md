# 安装 {#installation}

本书中提到 python 3 一般是指高于 [python {{ book.pythonVersion }}](https://www.python.org/downloads/) 的版本

## Windows 安装

到官网 [https://www.python.org/](https://www.python.org/downloads/) 下载合适的版本安装包。将 python 目录添加到环境变量 PATH 中。之后就直接在命令行环境中直接使用 python 命令运行 python 解释器。

## Mac OS X 安装

[Homebrew](http://brew.sh) 帮你解决， `brew install python3` 。一般来说，你需要在bash环境中在环境变量的末尾追加来实现对默认编译器版本的更改。

## GNU/Linux 安装

yum ， apt 等相应的包管理器能够轻松为你安装python，某些发行版本会内置 python，他们的版本未必是你想要的，你可以使用 alternatives 等版本管理工具来切换 python 命令默认的解释器。

由于这些安装是全局的，切换默认版本也许会带来问题。我建议使用绝对路径来运行你的解释器。

## 总结

shell 中输入 python 或者 python3 ，如果你看到一系列python相关信息，并且提示符变为 >>>，这代表你成功进入解释器命令行，你已安装成功。exit() 即可退出。

国际惯例，`print("Hello World!")` 。
