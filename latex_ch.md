# 快速使用LaTex编辑中文([原文链接](http://www.sharelatex.com/learn/Chinese ))

------

LaTex通过一些特殊的包支持世界上的一些其他语言。本文中，我们将介绍如何通过这些包创建**中文**文档。

------

## 导论

由于中文的编码和字体与英文非常不同，因此需要使用的特殊的文类（document class）。

```latex
\documentclass{ctexart}
 
\setCJKmainfont{simsun.ttf}
\setCJKsansfont{simhei.ttf}
\setCJKmonofont{simfang.ttf}
 
\begin{document}
 
\tableofcontents
 
\begin{abstract}
这是在文件的开头的介绍文字.本文的主要话题的简短说明.
\end{abstract}
 
\section{ 前言 }
在该第一部分中的一些额外的元素可以被添加。巴贝尔包将采取的翻译服务.
 
\section{关于数学部分}
在本节中的一些数学会使用数学模型含中文字符显示。
 
這是一個傳統的中國文字
 
\end{document}
```
 
**ctexart**（Chinese Tex Article）是创建中文文档的推荐方式，但是它有它的局限性，也不是唯一的方式。下面的章节我们这些LaTex中文文类环境。

----

## 使用ctexart输入简体中文
现代计算机系统支持通过键盘直接输入中文。为了在LaTex中使用中文，我们可以使用**ctexart**文类。

`\documentclass{ctexart}`

这个文类就像是中文的*圣经*，你不仅可以直接输入中文，而且摘要（Abstract）、目录（Table of Contents）等也已经翻译好了。但是缺点需要指出：文类定义的其他参数，如页面的大小，是受限制的。但是，你可以使用[geometry package](http://www.sharelatex.com/learn/Page_size_and_margins)定义自己文档大小。
该文类支持使用外部字体，你可以使用系统字体，也可以将你下载的字体放置在你的LaTex文档相同的目录。例如，如果你的计算机上安装了 *IPAGothic* 字体，你可以使用如下命令使用该字体，
`\setCJKmainfont{IPAGothic}`
当然，其他的字体样式也可以设置。你可以使用`\setCJKsansfont{}`设置**sans**风格的字体样式，使用\setCJKmonofont{}设置等宽字体。**如果使用外部字体，你必须使用XeLaTex编译**。
 

---

## 使用CJK包编辑繁体中文，简体中文文档

如导论中所说，你可以使用其他包来设置中文环境，当然你也可以在同一个文件中同时输入繁体中文、简体中文和拉丁字符。

### XeLaTex
创建中文文档的另一个方式是使用**xeCJK**包，并设置你喜欢的中文字体。

```latex
\documentclass{article}
 
\usepackage{xeCJK}
 
\setCJKmainfont{simsun.ttf}
\setCJKsansfont{simhei.ttf}
\setCJKmonofont{simfang.ttf}
 
\begin{document}
 
\section{前言}
在该第一部分中的一些额外的元素可以被添加。巴贝尔包将采取的翻译服务.
 
\section{关于数学部分}
在本节中的一些数学会使用数学模型含中文字符显示。
 
\vspace{0.5cm}
 
這是一個傳統的中國文字
\end{document}
```


**xeCJk**包允许使用外部字体，语法与使用**ctexart**文类相同。同时，该包支持繁体中文。

使用该包时编译与使用**ctexart**文类不同，并且最终的编译结果可能会存在锯齿。但是，该包你可以自由选择文类（如，book，report）等。
**编译，xeCJK包必须使用XeLaTex。**

### pdfLaTex

CJTK包可以使用pdfLaTex编译。使用该包不允许使用外部字体，但是可以同时使用繁体中文、简体中文和拉丁字符，非常适合编辑包含少数中文的英文文档。

```latex
\documentclass{article}
\usepackage{CJKutf8}
 
\begin{document}
 
\begin{CJK*}{UTF8}{gbsn}
 
\section{前言}
在该第一部分中的一些额外的元素可以被添加。巴贝尔包将采取的翻译服务.
 
\section{关于数学部分}
在本节中的一些数学会使用数学模型含中文字符显示。
 
\end{CJK*}
 
\vspace{0.5cm} % A white space
 
\noindent
You can also insert Latin text in your document
 
\vspace{0.5cm}
 
\noindent
\begin{CJK*}{UTF8}{bsmi}
這是一個傳統的中國文字
\end{CJK*}
 
\end{document}
```

**\usepackage{CJKutf8}**启用utf8编码。
使用这个包时，所有的中文必须包含在**\begin{CJK*}{UTF8}{gbsm}**环境中，其中UTF8表示编码，gbsm是使用的字体。简体中文可以使用  gbsm 和 gkai 字体，繁体中文可以使用 bmsi 和 bkai 字体.



