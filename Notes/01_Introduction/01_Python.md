[目录](../Contents.md) \| [下一节 (1.2 A First Program)](02_Hello_world.md)

# 1.1 Python

### Python 是什么?

Python是一种解释型高级编程语言。它通常被归类为[“脚本语言”](https://en.wikipedia.org/wiki/Scripting_language)，并被认为是类似于Perl、Tcl或Ruby之类的语言。Python的语法受到了C编程元素的启发。

Python是由Guido van Rossum在1990年左右创建的，他为纪念Monty Python而如此命名这门语言。

### 从哪里获取Python?

您可以在官网[Python.org](https://www.python.org/)下载Python。学习本课程，您只需要安装Python本体。建议安装Python 3.6或更新版本。课程的在Notes和Solutions中使用的是Python 3.6。

### Python 为何而生?

Python的作者如是说：

> My original motivation for creating Python was the perceived need
> for a higher level language in the Amoeba [Operating Systems]
> project. I realized that the development of system administration
> utilities in C was taking too long. Moreover, doing these things in
> the Bourne shell wouldn't work for a variety of reasons. ... So,
> there was a need for a language that would bridge the gap between C
> and the shell.
>
> - Guido van Rossum

### 我的机器从哪运行Python ?

虽然有许多环境可以运行Python，但Python通常作为从终端(terminal)或命令shell运行的程序安装在您的机器上。在终端中，你应该可以像这样输入`python`：

```
bash $ python
Python 3.8.1 (default, Feb 20 2020, 09:29:22)
[Clang 10.0.0 (clang-1000.10.44.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> print("hello world")
hello world
>>>
```

如果您是第一次使用Shell或者Terminal，或许你应该先完成一个简单的相关学习然后再回来继续。

尽管有许多非shell环境可以让你编写Python代码，但如果你能够在终端上运行、调试并与Python交互，你将会成为一个更强大的Python程序员。这是Python的原生环境。如果你能在这里使用Python，你就能在其他地方使用它。

## 练习题

### 练习 1.1: 将Python作为计算器使用

在你的机器上，运行Python并将其作为计算器解决以下的问题。

幸运的拉里以每股235.14美元的价格购买了75股谷歌的股票。现在谷歌的股价为711.25美元。使用Python的交互模式作为计算器，计算出如果现在Larry卖掉他所有的股份，他将获得多少利润。

```python
>>> (711.25 - 235.14) * 75
35708.25
>>>
```

进阶技巧：使用下划线(\_)变量来使用上次计算的结果。 例如，在他的代理拿走20%的佣金后拉里赚了多少钱?

```python
>>> _ * 0.80
28566.600000000002
>>>
```

### 练习 1.2: 获取帮助信息

使用 `help()` 命令获取 `abs()` 函数的帮助信息。然后使用`help()` 获取 `round()` 函数信息。 只输入 `help()` 而不带参数将会进入帮助交互界面。

需要注意的是`help()`无法用于Python的基础语句，像`for`, `if`, `while`语句以及更多的其他基础语句（也就是说，当你输入`help(for)`时会得到一个语法错误）。你可以尝试加上引号比如`help("for")`，如果还是不行，那你只能使用网络查询了。

后续：访问<http://docs.python.org>并找到`abs()`函数的文档。（提示：这是内建函数相关库里的函数）。

### 练习 1.3: 剪切与粘贴

本课程的结构是一系列传统网页，鼓励您尝试交互式Python代码示例并**通过手敲键盘输入**完成。如果你是第一次学习Python，鼓励这种“缓慢的方法”。通过放慢速度、输入内容、思考自己在做什么，你会对这门语言有更好的感觉。

如果您一定要“剪切并粘贴”代码示例，请“>>>”提示符之后的代码剪切，注意不要超过第一个空行或下一个“>>>”提示符(以先出现的为准)。然后在浏览器中选择“复制”，进入Python窗口，选择“粘贴”，将其复制到Python shell中。要使代码运行，您可能需要在粘贴代码之后点击回车键。

在本会话中使用剪切-粘贴来执行Python语句：

```python
>>> 12 + 20
32
>>> (3 + 4
         + 5 + 6)
18
>>> for i in range(5):
        print(i)

0
1
2
3
4
>>>
```

警告：一次不能粘贴多个Python命令(出现在' >>> '之后的语句)到基本的Python shell中。您必须一次粘贴一个命令。

现在您已经完成了这一步，请记住，通过缓慢地输入代码并思考它，而不是剪切和粘贴，您将从这个传统方法中获得更多的东西。


### 练习 1.4: 我的公共汽车到哪了 ？

试试更高级的方法，输入以下语句，让我们看看在芝加哥克拉克街(Clark street)和巴尔莫勒尔街(Balmoral)的拐角处等下一辆北上的CTA \#22 公共汽车的人需要等多久:


```python
>>> import urllib.request
>>> u = urllib.request.urlopen('http://ctabustracker.com/bustime/map/getStopPredictions.jsp?stop=14791&route=22')
>>> from xml.etree.ElementTree import parse
>>> doc = parse(u)
>>> for pt in doc.findall('.//pt'):
        print(pt.text)

6 MIN
18 MIN
28 MIN
>>>
```

没错，在这大约6行代码中，你只是下载了一个网页，解析了一个XML文档，并提取一些有用的信息。 你获取的数据你实际上是网站 <http://ctabustracker.com/bustime/home.jsp> 提供的。 再试一次，看看预测的变化。

注意：此服务只报告接下来30分钟内的到达时间。如果你在不同的时区，恰好是芝加哥凌晨3点，你可能不会得到任何输出。你可以使用上面的链接进行检查。

如果第一个import语句`import urllib.request` 失败，那您可能使用的是python2。对于本课程，您需要确保使用的是Python 3.6或更新版本。如果你需要，请到<https://www.python.org>下载。

如果您的工作环境需要使用HTTP代理服务器，您可能需要设置`HTTP_PROXY`环境变量，以使练习的这一部分工作。例如:

```python
>>> import os
>>> os.environ['HTTP_PROXY'] = 'http://yourproxy.server.com'
>>>
```

如果这个示例您无法运行，也不用担心。本课程的其余部分与解析XML无关。

[目录](../Contents.md) \| [下一节 (1.2 A First Program)](02_Hello_world.md)

