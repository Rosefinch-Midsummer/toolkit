# 编辑器 (Vim)

[编辑器 (Vim)来源地址](https://missing-semester-cn.github.io/2020/editors/)

写作和写代码其实是两项非常不同的活动。当我们编程的时候，会经常在文件间进行切换、阅读、浏览和修改代码，而不是连续编写一大段的文字。因此代码编辑器和文本编辑器是很不同的两种工具（例如微软的 Word 与 Visual Studio Code）。

作为程序员，我们大部分时间都花在代码编辑上，所以花点时间掌握某个适合自己的编辑器是非常值得的。通常学习使用一个新的编辑器包含以下步骤：

- 阅读教程（比如这节课以及我们为您提供的资源）
- 坚持使用它来完成你所有的编辑工作（即使一开始这会让你的工作效率降低）
- 随时查阅：如果某个操作看起来像是有更方便的实现方法，一般情况下真的会有

如果您能够遵循上述步骤，并且坚持使用新的编辑器完成您所有的文本编辑任务，那么学习一个复杂的代码编辑器的过程一般是这样的：头两个小时，您会学习到编辑器的基本操作，例如打开和编辑文件、保存与退出、浏览缓冲区。当学习时间累计达到20个小时之后，您使用新编辑器的效率应该已经和使用老编辑器一样快。在此之后，其益处开始显现：有了足够的知识和肌肉记忆后，使用新编辑器将大大节省你的时间。而现代文本编辑器都是些复杂且强大的工具，永远有新东西可学：学的越多，效率越高。

<!-- toc -->

# 该学哪个编辑器？

程序员们对自己正在使用的文本编辑器通常有着 [非常强的执念](https://zh.wikipedia.org/wiki/%E7%BC%96%E8%BE%91%E5%99%A8%E4%B9%8B%E6%88%98)。

现在最流行的编辑器是什么？[Stack Overflow 的调查](https://insights.stackoverflow.com/survey/2019/#development-environments-and-tools)（这个调查可能并不如我们想象的那样客观，因为 Stack Overflow 的用户并不能代表所有程序员）显示，[Visual Studio Code](https://code.visualstudio.com/) 是目前最流行的代码编辑器。而 [Vim](https://www.vim.org/) 则是最流行的基于命令行的编辑器。

## Vim

这门课的所有教员都使用 Vim 作为编辑器。Vim 有着悠久历史；它始于 1976 年的 Vi 编辑器，到现在还在 不断开发中。Vim 有很多聪明的设计思想，所以很多其他工具也支持 Vim 模式（比如，140 万人安装了 [Vim emulation for VS code](https://github.com/VSCodeVim/Vim)）。即使你最后使用 其他编辑器，Vim 也值得学习。

由于不可能在 50 分钟内教授 Vim 的所有功能，我们会专注于解释 Vim 的设计哲学，教你基础知识， 并展示一部分高级功能，然后给你掌握这个工具所需要的资源。

# Vim 的哲学

在编程的时候，你会把大量时间花在阅读/编辑而不是在写代码上。所以，Vim 是一个_多模态_编辑 器：它对于插入文字和操纵文字有不同的模式。Vim 是可编程的（可以使用 Vimscript 或者像 Python 一样的其他程序语言），Vim 的接口本身也是一种程序语言：键入操作（以及其助记名） 是命令，这些命令也是可组合的。Vim 避免了使用鼠标，因为那样太慢了；Vim 甚至避免用 上下左右键因为那样需要太多的手指移动。

这样的设计哲学使得 Vim 成为了一个能跟上你思维速度的编辑器。

# 编辑模式

Vim 的设计以大多数时间都花在阅读、浏览和进行少量编辑改动为基础，因此它具有多种操作模式：

- **正常模式**：在文件中四处移动光标进行修改
- **插入模式**：插入文本
- **替换模式**：替换文本
- **可视化模式**（一般，行，块）：选中文本块
- **命令模式**：用于执行命令

在不同的操作模式下，键盘敲击的含义也不同。比如，`x` 在插入模式会插入字母 `x`，但是在正常模式 会删除当前光标所在的字母，在可视模式下则会删除选中文块。

在默认设置下，Vim 会在左下角显示当前的模式。Vim 启动时的默认模式是正常模式。通常你会把大部分 时间花在正常模式和插入模式。

你可以按下 `<ESC>`（退出键）从任何其他模式返回正常模式。在正常模式，键入 `i` 进入插入 模式，`R` 进入替换模式，`v` 进入可视（一般）模式，`V` 进入可视（行）模式，`<C-v>` （Ctrl-V, 有时也写作 `^V`）进入可视（块）模式，`:` 进入命令模式。

因为你会在使用 Vim 时大量使用 `<ESC>` 键，所以可以考虑把大小写锁定键重定义成 `<ESC>` 键（[MacOS 教程](https://vim.fandom.com/wiki/Map_caps_lock_to_escape_in_macOS)）。

# 基本操作

## 插入文本

在正常模式，键入 `i` 进入插入模式。现在 Vim 跟很多其他的编辑器一样，直到你键入 `<ESC>` 返回正常模式。你只需要掌握这一点和上面介绍的所有基础知识就可以使用 Vim 来编辑文件了 （虽然如果你一直停留在插入模式内不一定高效）。

## 缓存， 标签页， 窗口

Vim 会维护一系列打开的文件，称为“缓存”。一个 Vim 会话包含一系列标签页，每个标签页包含 一系列窗口（分隔面板）。每个窗口显示一个缓存。跟网页浏览器等其他你熟悉的程序不一样的是， 缓存和窗口不是一一对应的关系；窗口只是视角。一个缓存可以在多个窗口打开，甚至在同一个标签页内的多个窗口打开。这个功能其实很好用，比如在查看同一个文件的不同部分的时候。

Vim 默认打开一个标签页，这个标签也包含一个窗口。

## 命令行

在正常模式下键入 `:` 进入命令行模式。 在键入 `:` 后，你的光标会立即跳到屏幕下方的命令行。 这个模式有很多功能，包括打开，保存，关闭文件，以及 [退出 Vim](https://twitter.com/iamdevloper/status/435555976687923200)。

- `:q` 退出（关闭窗口）
- `:w` 保存（写）
- `:wq` 保存然后退出
- `:e {文件名}` 打开要编辑的文件
- `:ls` 显示打开的缓存
- `:help {标题}` 打开帮助文档
    - `:help :w` 打开 `:w` 命令的帮助文档
    - `:help w` 打开 `w` 移动的帮助文档

# Vim 的接口其实是一种编程语言

Vim 最重要的设计思想是 Vim 的界面本身是一种程序语言。键入操作（以及他们的助记名） 本身是命令，这些命令可以组合使用。这使得移动和编辑更加高效，特别是一旦形成肌肉记忆。

## 移动

多数时候你会在正常模式下，使用移动命令在缓存中导航。在 Vim 里面移动也被称为 “名词”， 因为它们指向文字块。

- 基本移动: `hjkl` （左， 下， 上， 右）
- 词： `w` （下一个词）， `b` （词初）， `e` （词尾）
- 行： `0` （行初）， `^` （第一个非空格字符）， `$` （行尾）
- 屏幕： `H` （屏幕首行）， `M` （屏幕中间）， `L` （屏幕底部）
- 翻页： `Ctrl-u` （上翻）， `Ctrl-d` （下翻）
- 文件： `gg` （文件头）， `G` （文件尾）
- 行数： `:{行数}<CR>` 或者 `{行数}G` ({行数}为行数)
- 杂项： `%` （找到配对，比如括号或者 /* */ 之类的注释对）
- 查找： `f{字符}`， `t{字符}`， `F{字符}`， `T{字符}`
    - 查找/到 向前/向后 在本行的{字符}
    - `,` / `;` 用于导航匹配
- 搜索: `/{正则表达式}`, `n` / `N` 用于导航匹配

## 选择

可视化模式:

- 可视化：`v`
- 可视化行： `V`
- 可视化块：`Ctrl+v`

可以用移动命令来选中。

## 编辑

所有你需要用鼠标做的事， 你现在都可以用键盘：采用编辑命令和移动命令的组合来完成。 这就是 Vim 的界面开始看起来像一个程序语言的时候。Vim 的编辑命令也被称为 “动词”， 因为动词可以施动于名词。

- `i` 进入插入模式
    - 但是对于操纵/编辑文本，不单想用退格键完成
- `O` / `o` 在之上/之下插入行
- `d{移动命令}` 删除 {移动命令}
    - 例如，`dw` 删除词, `d$` 删除到行尾, `d0` 删除到行头。
- `c{移动命令}` 改变 {移动命令}
    - 例如，`cw` 改变词
    - 比如 `d{移动命令}` 再 `i`
- `x` 删除字符（等同于 `dl`）
- `s` 替换字符（等同于 `xi`）
- 可视化模式 + 操作
    - 选中文字, `d` 删除 或者 `c` 改变
- `u` 撤销, `<C-r>` 重做
- `y` 复制 / “yank” （其他一些命令比如 `d` 也会复制）
- `p` 粘贴
- 更多值得学习的: 比如 `~` 改变字符的大小写

## 计数

你可以用一个计数来结合“名词”和“动词”，这会执行指定操作若干次。

- `3w` 向后移动三个词
- `5j` 向下移动5行
- `7dw` 删除7个词

## 修饰语

你可以用修饰语改变“名词”的意义。修饰语有 `i`，表示“内部”或者“在内”，和 `a`， 表示“周围”。

- `ci(` 改变当前括号内的内容
- `ci[` 改变当前方括号内的内容
- `da'` 删除一个单引号字符串， 包括周围的单引号

# 演示

这里是一个有问题的 [fizz buzz](https://en.wikipedia.org/wiki/Fizz_buzz) 实现：

```python
def fizz_buzz(limit):
    for i in range(limit):
        if i % 3 == 0:
            print('fizz')
        if i % 5 == 0:
            print('fizz')
        if i % 3 and i % 5:
            print(i)

def main():
    fizz_buzz(10)
```

我们会修复以下问题：

- 主函数没有被调用
- 从 0 而不是 1 开始
- 在 15 的整数倍的时候在不同行打印 “fizz” 和 “buzz”
- 在 5 的整数倍的时候打印 “fizz”
- 采用硬编码的参数 10 而不是从命令控制行读取参数
    
- 主函数没有被调用
    - `G` 文件尾
    - `o` 向下打开一个新行
    - 输入 “if **name** …”
- 从 0 而不是 1 开始
    - 搜索 `/range`
    - `ww` 向后移动两个词
    - `i` 插入文字， “1, “
    - `ea` 在 limit 后插入， “+1”
- 在新的一行 “fizzbuzz”
    - `jj$i` 插入文字到行尾
    - 加入 “, end=’’”
    - `jj.` 重复第二个打印
    - `jjo` 在 if 打开一行
    - 加入 “else: print()” ❗ 🔄
- fizz fizz
    - `ci'` 变到 fizz
- 命令控制行参数
    - `ggO` 向上打开
    - “import sys” 
    - `/10`
    - `ci(` to “int(sys.argv[1])” 

```python
import sys
def fizz_buzz(limit):
    for i in range(limit):
        if i % 3 == 0:
            print('fizz')
        if i % 5 == 0:
            print('buzz')
        if i % 3 and i % 5:
            print(i)

def main():
    fizz_buzz(int(sys.argv[1]))

if __name__ == '__main__':
	main()
```

展示详情请观看课程视频。比较上面用 Vim 的操作和你可能使用其他程序的操作。 值得一提的是 Vim 需要很少的键盘操作，允许你编辑的速度跟上你思维的速度。

# 自定义 Vim

Vim 由一个位于 `~/.vimrc` 的文本配置文件（包含 Vim 脚本命令）。你可能会启用很多基本 设置。

我们提供一个文档详细的基本设置，你可以用它当作你的初始设置。我们推荐使用这个设置因为 它修复了一些 Vim 默认设置奇怪行为。 **在[这儿](https://missing-semester-cn.github.io/2020/files/vimrc) 下载我们的设置，然后将它保存成 `~/.vimrc`.**

Vim 能够被重度自定义，花时间探索自定义选项是值得的。你可以参考其他人的在 GitHub 上共享的设置文件，比如，你的授课人的 Vim 设置 ([Anish](https://github.com/anishathalye/dotfiles/blob/master/vimrc), [Jon](https://github.com/jonhoo/configs/blob/master/editor/.config/nvim/init.vim) (uses [neovim](https://neovim.io/)), [Jose](https://github.com/JJGO/dotfiles/blob/master/vim/.vimrc))。 有很多好的博客文章也聊到了这个话题。尽量不要复制粘贴别人的整个设置文件， 而是阅读和理解它，然后采用对你有用的部分。

# 扩展 Vim

Vim 有很多扩展插件。跟很多互联网上已经过时的建议相反，你_不_需要在 Vim 使用一个插件 管理器（从 Vim 8.0 开始）。你可以使用内置的插件管理系统。只需要创建一个 `~/.vim/pack/vendor/start/` 的文件夹，然后把插件放到这里（比如通过 `git clone`）。

以下是一些我们最爱的插件：

- [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim): 模糊文件查找
- [ack.vim](https://github.com/mileszs/ack.vim): 代码搜索
- [nerdtree](https://github.com/scrooloose/nerdtree): 文件浏览器
- [vim-easymotion](https://github.com/easymotion/vim-easymotion): 魔术操作

我们尽量避免在这里提供一份冗长的插件列表。你可以查看讲师们的开源的配置文件 ([Anish](https://github.com/anishathalye/dotfiles), [Jon](https://github.com/jonhoo/configs), [Jose](https://github.com/JJGO/dotfiles)) 来看看我们使用的其他插件。 浏览 [Vim Awesome](https://vimawesome.com/) 来了解一些很棒的插件。 这个话题也有很多博客文章：搜索 “best Vim plugins”。

# 其他程序的 Vim 模式

很多工具提供了 Vim 模式。这些 Vim 模式的质量参差不齐；取决于具体工具，有的提供了 很多酷炫的 Vim 功能，但是大多数对基本功能支持的很好。

## Shell

如果你是一个 Bash 用户，用 `set -o vi`。如果你用 Zsh：`bindkey -v`。Fish 用 `fish_vi_key_bindings`。另外，不管利用什么 shell，你可以 `export EDITOR=vim`。 这是一个用来决定当一个程序需要启动编辑时启动哪个的环境变量。 例如，`git` 会使用这个编辑器来编辑 commit 信息。

## Readline

很多程序使用 [GNU Readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 库来作为它们的命令控制行界面。Readline 也支持基本的 Vim 模式， 可以通过在 `~/.inputrc` 添加如下行开启：

```
set editing-mode vi
```

比如，在这个设置下，Python REPL 会支持 Vim 快捷键。

## 其他

甚至有 Vim 的网页浏览快捷键 [browsers](http://vim.wikia.com/wiki/Vim_key_bindings_for_web_browsers), 受欢迎的有 用于 Google Chrome 的 [Vimium](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb?hl=en) 和用于 Firefox 的 [Tridactyl](https://github.com/tridactyl/tridactyl)。 你甚至可以在 [Jupyter notebooks](https://github.com/lambdalisue/jupyter-vim-binding) 中用 Vim 快捷键。 [这个列表](https://reversed.top/2016-08-13/big-list-of-vim-like-software) 中列举了支持类 vim 键位绑定的软件。

# Vim 进阶

这里我们提供了一些展示这个编辑器能力的例子。我们无法把所有的这样的事情都教给你，但是你 可以在使用中学习。一个好的对策是: 当你在使用你的编辑器的时候感觉 “一定有更好的方法来做这个”， 那么很可能真的有：上网搜寻一下。

## 搜索和替换

`:s` （替换）命令（[文档](http://vim.wikia.com/wiki/Search_and_replace)）。

- `%s/foo/bar/g`
    - 在整个文件中将 foo 全局替换成 bar
- `%s/\[.*\](\(.*\))/\1/g`
    - 将有命名的 Markdown 链接替换成简单 URLs

## 复制粘贴

vim中的复制和粘贴命令分别是y和p，在不需要和系统交互剪贴板数据时还好，一旦要复制外部数据到vim中或者将vim中的数据复制到外部，这两个命令就无效了，只能用鼠标选中再右键复制粘贴。虽然和windows下的Ctrl C、Ctrl V不同，但vim可以通过配置实现和系统剪贴板的“沟通”。
需要注意的是Ctrl y和Ctrl p在 vim 中有特殊含义，使用以下设置后会覆盖默认设置。

前提
开始前需要先查看vim是否已经支持clipboard功能，使用vim --version | grep clipboard命令查看，有+clipboard说已经支持clipboard功能。

```
-clipboard         +keymap            +printer           +vertsplit
+eval              -mouse_jsbterm     -sun_workshop      -xterm_clipboard
```

如果其前为-号，执行sudo apt install vim-gtk安装vim-gtk即可（或者安装gvim，非debian系的系统不是用apt命令，根据系统变动就行，都差不多），安装完成后再执行vim --version | grep clipboard此时应该已经支持clipboard功能。

配置vim

此时如果在vim外复制了文本，要粘贴到打开的vim文件内，只需在normal模式下（如果不知道当前在哪个模式就先按一次ESC键）执行"\*p，注意是三个键连续输入，由于要输入双引号和星号，因此需要先按下Shift键，再分别按下" \*（过程中Shift不要放下），最后按下p（小写，此时不要按Shift），如果没问题应该可以将系统剪贴板数据粘贴到vim中；

类似的，要将vim中的数据复制到vim外，需要回到normal模式先按v进入visual模式，移动光标选中目标文本后，在visua模式下执行" + y即可将vim数据复制到系统剪贴板，在vim外执行Ctrl V即可完成数据粘贴。

vim支持自定义快捷键，使用vim打开~/.vimrc文件这是当前用户的vim配置文件，vim会读取配置文件中的内容完成相应的配置，在这个配置文件中添加（中文前的“号是注释）

```
vnoremap <C-y> "+y   "支持在Visual模式下，通过C-y复制到系统剪切板
nnoremap <C-p> "*p   "支持在normal模式下，通过C-p粘贴系统剪切板
```

添加完成后按ESC回到normal模式输入:wq保存并退出，此后就可以像Ctrl C、Ctrl V那样愉快地使用Ctrl y和Ctrl p进行复制粘贴了。


## 多窗口

- 用 `:sp` / `:vsp` 来分割窗口
- 同一个缓存可以在多个窗口中显示。

[来源](https://zhuanlan.zhihu.com/p/337157587)

Vim分屏功能是通过分割窗口来实现的，这是提高工作效率的一大利器。无论我们想同时显示两个文件，或者同时显示一个文件的两个不同的位置，又或者并排比较两个文件，等等，这些都能通过分屏来实现，这样子很方便代码的比对和复制粘贴

**水平方向分屏打开新文件**

:sp linuxmi.py

或者

:split linuxmi.py

这个命令把窗口横向切分为两个窗口，并把光标置于上面的窗口中。

**垂直方向分屏打开新文件**

:vsp linux.py

:vsplit linux.py

:sview linux.py ->只读分屏打开文件

另外，要打开窗口编辑一个新的文件时，可以用以下命令：

:new

**从命令行直接打开多个文件且是分屏**

vim -On file1, file2 ... ->垂直分屏

vim -on file1, file2 ... ->水平分屏

linuxmi@linuxmi:~/[http://www.linuxmi.com](https://link.zhihu.com/?target=http%3A//www.linuxmi.com)$ vim -O3 linux.py linuxmi.py linuxmi.cpp

![](https://pic3.zhimg.com/80/v2-2fbea6832d96ea4ca18d8c8fc6aa76a2_1440w.webp)

注：-O垂直分屏，-o水平分屏，n表示分几个屏  

**实时调整当前窗口的宽度**  
ctrl-w > //向右加宽，默认值为1  
ctrl-w N > //向右加宽宽度N  
ctrl-w < // 同理

**横屏/竖屏分屏打开当前文件**

ctrl+w s  
ctrl+w v

**切换分屏**

ctrl+w h,j,k,l  
ctrl+w 上下左右键

crtl+w进行分屏窗口的切换 按完以后再按一个w

crtl+w进行分屏窗口的切换 按完以后再按一个r 互换窗口

crtl+w进行分屏窗口的切换 按完以后再按一个c 关闭窗口

**关闭分屏**

关闭窗口有以下几个个命令：

ctrl+W c 关闭当前窗口

ctrl+w q 关闭当前窗口，若只有一个分屏且退出vim

:only 仅保留当前分屏  
:hide 关闭当前分屏

**调整分屏的大小（宽度与高度）**

ctrl+w = 所有分屏都统一高度  
ctrl+w + 增加高度，默认值为1  
ctrl+w - 减少高度  
10 ctrl+w + 增加10行高度  
ctrl-w N + //当前屏高度加N

使用指定当前屏的调整高度  
: resize N

示例：

:resize 30

**移动分屏**

ctrl+W H,J,K,L

**将屏幕移动到最顶端**  
ctrl-w + K

**将屏幕移动到最低端**  
ctrl-w + J

**将屏幕移动到最左边**  
ctrl-w + H

**将屏幕移动到最右边**  
ctrl-w + L
## 宏

- `q{字符}` 来开始在寄存器`{字符}`中录制宏
- `q`停止录制
- `@{字符}` 重放宏
- 宏的执行遇错误会停止
- `{计数}@{字符}`执行一个宏{计数}次
- 宏可以递归
    - 首先用`q{字符}q`清除宏
    - 录制该宏，用 `@{字符}` 来递归调用该宏 （在录制完成之前不会有任何操作）
- 例子：将 xml 转成 json ([file](https://missing-semester-cn.github.io/2020/files/example-data.xml))
    - 一个有 “name” / “email” 键对象的数组
    - 用一个 Python 程序？
    - 用 sed / 正则表达式
        - `g/people/d`
        - `%s/<person>/{/g`
        - `%s/<name>\(.*\)<\/name>/"name": "\1",/g`
        - …
    - Vim 命令 / 宏
        - `ggdd`, `Gdd` 删除第一行和最后一行
        - 格式化最后一个元素的宏 （寄存器 `e`）
            - 跳转到有 `<name>` 的行
            - `qe^r"f>s": "<ESC>f<C"<ESC>q`
        - 格式化一个的宏
            - 跳转到有 `<person>` 的行
            - `qpS{<ESC>j@eA,<ESC>j@ejS},<ESC>q`
        - 格式化一个标签然后转到另外一个的宏
            - 跳转到有 `<person>` 的行
            - `qq@pjq`
        - 执行宏到文件尾
            - `999@q`
        - 手动移除最后的 `,` 然后加上 `[` 和 `]` 分隔符

# 扩展资料

- `vimtutor` 是一个 Vim 安装时自带的教程
- [Vim Adventures](https://vim-adventures.com/) 是一个学习使用 Vim 的游戏
- [Vim Tips Wiki](http://vim.wikia.com/wiki/Vim_Tips_Wiki) 
- [Vim Advent Calendar](https://vimways.org/2019/) 有很多 Vim 小技巧
- [Vim Golf](http://www.vimgolf.com/) 是用 Vim 的用户界面作为程序语言的 [code golf](https://en.wikipedia.org/wiki/Code_golf)
- [Vi/Vim Stack Exchange](https://vi.stackexchange.com/) 
- [Vim Screencasts](http://vimcasts.org/)
- [Practical Vim](https://pragprog.com/titles/dnvim2/)（书籍） 

# 课后练习

[习题解答](https://missing-semester-cn.github.io/missing-notes-and-solutions/2020/solutions//editors-solution)

1. 完成 `vimtutor`。备注：它在一个 [80x24](https://en.wikipedia.org/wiki/VT100)（80 列，24 行） 终端窗口看起来效果最好。
2. 下载我们提供的 [vimrc](https://missing-semester-cn.github.io/2020/files/vimrc)，然后把它保存到 `~/.vimrc`。 通读这个注释详细的文件 （用 Vim!）， 然后观察 Vim 在这个新的设置下看起来和使用起来有哪些细微的区别。
3. 安装和配置一个插件： [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim).
    1. 用 `mkdir -p ~/.vim/pack/vendor/start` 创建插件文件夹
    2. 下载这个插件： `cd ~/.vim/pack/vendor/start; git clone https://github.com/ctrlpvim/ctrlp.vim`
    3. 阅读这个插件的 [文档](https://github.com/ctrlpvim/ctrlp.vim/blob/master/readme.md)。 尝试用 CtrlP 来在一个工程文件夹里定位一个文件，打开 Vim, 然后用 Vim 命令控制行开始 `:CtrlP`.
    4. 自定义 CtrlP：添加 [configuration](https://github.com/ctrlpvim/ctrlp.vim/blob/master/readme.md#basic-options) 到你的 `~/.vimrc` 来用按 Ctrl-P 打开 CtrlP
4. 练习使用 Vim, 在你自己的机器上重做 [演示](https://missing-semester-cn.github.io/2020/editors/#demo)。
5. 下个月用 Vim 完成_所有的_文件编辑。每当不够高效的时候，或者你感觉 “一定有一个更好的方式”时， 尝试求助搜索引擎，很有可能有一个更好的方式。如果你遇到难题，可以来我们的答疑时间或者给我们发邮件。
6. 在其他工具中设置 Vim 快捷键 （见上面的操作指南）。
7. 进一步自定义你的 `~/.vimrc` 和安装更多插件。
8. （高阶）用 Vim 宏将 XML 转换到 JSON ([例子文件](https://missing-semester-cn.github.io/2020/files/example-data.xml))。 尝试着先完全自己做，但是在你卡住的时候可以查看上面[宏](https://missing-semester-cn.github.io/2020/editors/#macros) 章节。



# Solution-编辑器 (Vim)

1. 完成 vimtutor。 备注： 它在一个 80x24（80 列，24 行） 终端窗口看起来最好。
    
    ```
      vimtutor
    ```
    
2. 下载我们的[vimrc](https://missing-semester-cn.github.io/2020/files/vimrc)，然后把它保存到 `~/.vimrc`。 通读这个注释详细的文件 （用 Vim!）， 然后观察 Vim 在这个新的设置下看起来和使用起来有哪些细微的区别。
3. 安装和配置一个插件： `ctrlp.vim`.
    1. 用 `mkdir -p ~/.vim/pack/vendor/start` 创建插件文件夹
    2. 下载这个插件： `cd ~/.vim/pack/vendor/start; git clone https://github.com/ctrlpvim/ctrlp.vim`  
        下载后需要在~/.vimrc 中添加如下设置，参考[这里](http://ctrlpvim.github.io/ctrlp.vim/#installation)
        
        ```
         set runtimepath^=~/.vim/pack/vendor/start/ctrlp.vim 
        ```
        
    3. 请阅读这个插件的[文档](https://github.com/ctrlpvim/ctrlp.vim/blob/master/readme.md)。 尝试用 CtrlP 来在一个工程文件夹里定位一个文件， 打开 Vim, 然后用 Vim 命令控制行开始 :CtrlP.![1.png](https://missing-semester-cn.github.io/missing-notes-and-solutions/2020/solutions/images/3/1.png)
    4. 自定义 CtrlP： 添加 [configuration](https://github.com/ctrlpvim/ctrlp.vim/blob/master/readme.md#basic-options) 到你的 ~/.vimrc 来用按 Ctrl-P 打开 CtrlP
        
        ```
         let g:ctrlp_map ='<c-p>' 
         let g:ctrlp_cmd = 'CtrlP'
         let g:ctrlp_working_path_mode = 'ra' #设置默认路径为当前路径
        ```
        
        ![1.png](https://missing-semester-cn.github.io/missing-notes-and-solutions/2020/solutions/images/3/2.png)
        
4. 练习使用 Vim, 在你自己的机器上重做演示。
5. 下个月用 Vim 完成_所有_的文件编辑。每当不够高效的时候，或者你感觉 “一定有一个更好的方式”， 尝试求助搜索引擎，很有可能有一个更好的方式。如果你遇到难题， 来我们的答疑时间或者给我们发邮件。
6. 在你的其他工具中设置 Vim 快捷键 （见上面的操作指南）。
7. 进一步自定义你的 ~/.vimrc 和安装更多插件。 安装插件最简单的方法是使用 Vim 的包管理器，即使用 vim-plug 安装插件：
    1. 安装 vim-plug
        
        ```
         $ curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
        https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
        ```
        
    2. 修改 ~/.vimrc
        
        ```
         call plug#begin()
         Plug 'preservim/NERDTree' #需要安装的插件 NERDTree
         Plug 'wikitopian/hardmode'  #安装 hardmode
         ..... # 更多插件
         call plug#end()
        ```
        
    3. 在 vim 命令行中执行 `:PlugInstall`![1.png](https://missing-semester-cn.github.io/missing-notes-and-solutions/2020/solutions//images/3/3.png)
8. (高阶)用 Vim 宏将 XML 转换到 JSON ([例子文件](https://missing-semester-cn.github.io/2020/files/example-data.xml))。 尝试着先完全自己做，但是在你卡住的时候可以查看上面 [宏](https://missing-semester-cn.github.io/2020/editors/#macros) 章节。
    
    可以先查看[转化后的JSON文件](https://missing-semester-cn.github.io/missing-notes-and-solutions/2020/solutions/demoCode/3/example-data.json)，了解最终的转换效果。
    
    ```
    vim example-data.xml
    ```
    
    在`vim`编辑页面中执行以下步骤：
    
    1. 删除首尾两行
        - `Gdd`：跳转到最后一行，并删除该行
        - `ggdd`： 跳转到第一行，并删除该行
    2. 录制寄存器`e`，实现对`<name>`标签的处理
        
        - `/<name>`，再键入`Enter`，然后键入`N`：查找`<name>`并跳转到文件的最后一个`<name>`
        - 接下来，录制宏（即寄存器`e`）：
        
        - `qe`：即将录制名为`e`的宏
        - `^r"`：`^`跳转到当前行的首个非空字符，即`<name>`的`<`，`r"`将`<`替换为`"`
        - `f>s": "`：`f>`查找`>`，此处即匹配刚才的`<name>`的`>`；`s"`将`>`替换为`": "`
        - `<Esc>`：回到正常模式
        - `f<C"`：查找下一个`<`，由于xml文件的特征，此时匹配到的是刚才修改的`<name>`对应的`</name>`的`<`；然后，将当前位置到本行末尾的内容删除，同时插入`"`
        - `<Esc>`：回到正常模式
        - `q`：停止录制，寄存器`e`完成
            - 寄存器`e`的效果示例：将`<name>Mike</name>`修改为`"name": "Mike"`
    3. 录制寄存器`p`，实现对`<person>`标签的处理
        
        - `gg`：跳转到文件开头（本例中，正好处于一个`<person>`标签）
        - 接下来，录制宏（寄存器`p`）
        
        - `qp`：即将录制宏`p`
        - `S{`：将当前行删除，并替换为`{`
        - `<Esc>`：回到正常模式
        - `j@e`：移到下一行，并执行宏`e`（因为本例的xml文件中，`<person>`的下一行为`<name>`）
        - `A,`：在本行的末尾添加上`,`
        - `<Esc>`
        - `j@e`：移到下一行，并执行宏`e`（本例中，完成对`<email>`标签行的处理，其处理与`<name>`标签行的一致）
        - `jS},`：跳转到下一行，并删除整行，同时添加上`},`（本例中该行内容为：`</person>`）
        - `<Esc>q`：回到正常模式，并停止录制，完成宏`p`
    4. 录制寄存器`q`，实现从一个`<person>`标签到另一个`<person>`标签的跳转
        - `/<person>`：从第三步的位置开始查找下一个`<person>`标签
        - `qq`：开始录制宏`q`
        - `@p`：执行宏`p`，可以将这一组`<person>`标签包含的内容修改为json格式
        - `jq`：移到下一行，并停止录制，完成宏`q`（此时，刚好处于下一个`<person>`标签行）
    5. 执行宏`q`到文件尾
        - `999@q`：执行999次宏`q`（本文档总行数为1002行，执行999次能确保到达文件末尾）
    6. 手动修改文件内容
        - `gg`
        - `O`：（大写的`o`）在开头插入如下内容
            
            ```
            {
            "people": {
                "person": [
            ```
            
        - `<Esc>`
        - `/<email>`：跳转到文件末尾唯一未处理的`<email>`标签行
        - `@e`：对该标签行进行处理
        - `jS}`：移到下一行，删除`</person>`标签
        - `<Esc>`
        - `o`：在文件末尾插入以下内容
            
            ```
                ]
            }
            }
            ```




















