## vim的两种模式

vim有两种模式，命令模式和插入模式，两种不同的模式下，键盘的功能是不同的。

+ 命令模式：当键入命令进入编辑界面时就是处于命令模式，这时候键盘上的每一个按键都有它独有的命令
+ 插入模式：在插入模式时，键盘就是一个打字机，按下的每一个按键都会显示在显示屏上

### 两种模式间的切换

在命令模式下，可以通过插入命令进入插入模式，最常见的是使用`i`按钮来进入插入模式

在插入模式下，任何时间都可以使用`ESC`按钮进入插入模式。

## 保存和退出

### 保存

+ ZZ 保存并退出
+ :wq  等价于ZZ

### 放弃编辑

:e!   放弃本次的所有编辑，回到初始状态

:q!   放弃编辑，直接退出vim

上面两个命令都会导致本次所做的编辑丢失，vim不允许这样，加上！可以强制执行.

### 保存文件

:w 保存修改
:w newfile 将当前内容保存在文件newfile中

## 简单的编辑

上面提到过当处于插入模式下的适合于键盘相当于一个打字机，所以下面提到的操作没有特殊说明都是在命令模式下的。

### 移动光标

####单步移动

+ h 左移
+ l 右移
+ k 上移
+ j 下移

#### 数字参数

将数字与移动命令组合，像这样`4l`这相当于执行了四次右移，很多命令都可以这样使用。

#### 行内移动

+ 0: 数字0 可以将光标快速定位到行首
+ $: 美元符号，可以将光标快速定位到行尾

#### 按文本块移动

+ w:向后移动，移动的跨度为一个单词，标点符号被看作为一个单词。
+ W:同上，但是标点符号不被当作单词
+ b:向前移动
+ B:同上

上面这几个命令也可以和数字组合起来使用

#### 简单的编辑

#### 插入文本

+ i: 按下`i`后会进入插入模式，所有输入都会被插入到当前位置。
+ a: 追加，光标会向后移动一个字符然后进入插入模式。

#### 修改文本
 
修改现有的文本，使用命令`c` ,但是为了告诉vim要修改的范围，要使用下面这些命令

+ cw :将当前光标位置到当前单词词尾之间内容删除进入插入模式
+ c2b:这里b命令配合数字使用，将当前光标位置于前两个单词之间的内容删去，进入插入模式
+ c0:到行首
+ c$:到行尾

+ cc:删除当前行进入插入模式
+ C : 大写的C，删除当前位置至行尾，功能同c$

#### 替换文本

+ r:替换单个字母 
有时候输入错误了一个字母这个时候可以使用`r`命令(replace）按下r键会选中要替换的字母，按下需要替换的字母，就可以完成替换。在这以后，仍然是处于命令模式。
+ s:按下s命令后，会删除当前字符然后进入插入模式，不同于r的是，s可以用任意多的字符替换掉一个字母，而r则只是用一个字符替换一个字符
+ S:删除掉当前行进入插入模式，功能同cc
+ R:同其他编辑器按下了insert一样，按下R后输入的任何字符都会替换掉一个字符。
+ ~:波浪号，能够将当前光标下的字母转变为大写或者小写，取决于当前字母的是大写还是小写
#### 删除文本

使用d命令配合其他命令来删除文本，同上面的修改文本一样，需要确定一个删除范围。

+ dw : 删除光标所在位置至当前单词的词尾。
+ d$ : 删除到行尾
同样上面这些命令也可以配合数字来使用，像这样d2w删除当前光标位置后的两个单词。

+ dd：删除整行，不同于S或者cc，这些命令删除后会进入插入模式，而dd不会。同样可以使用3dd这样的命令来删除3行。

+ D：删除当前位置至行尾的内容，不进入插入模式，所以和c$与C是有区别的。

+ x: 删除单个字符，是在命令模式删除，所以是有别于在插入模式的backspace的。

#### 移动文本(复制粘贴）

+ dd
p:使用删除加粘贴，也就是剪切。当使用删除操作是vim会把最近9次删除的文本保存在缓冲区中，而使用y就是将最新的一次删除粘贴杂当前位置。

+ x p:x也是删除键，所以也可以像上面那样使用。

+ y p:上面两个都是剪切，这个是粘贴。使用y命令可以复制选中的内容，然后使用p命令，可以将复制的内容粘贴在光标所在位置。

而这里的y命令，和上面的修改命令一样也要选择一个范围。

+ yy:复制当前行
+ Y:同yy
+ y3w:复制光标后的三个单词。

#### 撤销操作

+ u:可以在命令模式下使用u来撤销最近一次的操作。
+ U:使用大写U来撤销对当前行的操作。

+ ctrl+r:当发现撤销时候多撤销了一步，可以使用ctrl+r来恢复。

#### 常用的插入文本方法

除了上面提到的i和a还有下面这些命令可以进入插入模式：

+ A:在当前行的末尾进行插入。
+ I:在行首进行插入。
+ o:在当前行下面新建一行进行插入。
+ O:在当前行上面新建一行，进行插入。当前行会下移。
+ s:使用输入的文本替换掉光标所在位置的字符。
+ S:使用输入的字符替换当前行。
+ R:使用新字符替换当前字符。

#### 合并短行

+ J:当需要合并当前行与下一行时，可以在当前行上使用J这样就可以将两行合并。

## 快速移动

### 按屏幕滚动

+ ctrl+f 向前滚动一屏
+ ctrl+b 向后滚动夷平
+ ctrl+d 向前滚动半屏
+ ctrl+u 向后滚动半屏

+ ctrl+e 向上滚动一行
+ ctrl+y 向下滚动一行

### 重定位屏幕

+ z return:按下z然后按回车键，将当前行定位到屏幕顶部
+ z . :按下z和小数点，将当前行定位到屏幕中间
+ z - :z和段横将当前行定位到屏幕底端

### 屏幕内移动

+ H:移动到屏幕首行起始位置
+ M:移动到屏幕中间行起始位置
+ L:移动到屏幕末行起始位置

+ nH:配合数字使用，移动到首行下面第n行
+ nL:移动到末行上面第n行

### 行内移动

+ ^:移动到当前行的第一个非空字符
+ 0:移动到当前行的第一个字符
+ n|:配合数字使用，移动到第n个字符


