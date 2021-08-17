# APS期刊投稿准备: REVTex格式

APS是American Physics Society的简称。旗下比较有影响力的期刊有: "pra, prb, prc, prd, pre, prl, prstab, prstper, or rmp". 在旗下期刊的投稿中需遵循一套APS自己的风格。具体的要求详见这个网站：https://journals.aps.org/prl/authors . 这里并不会把网站的英文说明翻译一遍，大家看原文的要求可能能准确些。这里主要总结一下自己在准备APS投稿论文中遇到的一些问题。

- Latex or Word
APS接受的论文格式有Word和Latex格式。其中Word格式就不多讲了，只要使用微软正版的Office套装，相信问题都不大，但注意不能使用Word自带的数学公式编辑器，必须使用MathType插件输入公式才可以。接下来的内容会重点介绍APS对Latex投稿的格式要求。
- REVTex
REVTex是APS自己定义的一个latex文档规格，一般最新的Texlive发行版都是默认内置的。所以平时如果习惯用Texlive码字，基本上不用自己再重新安装配置REVTex环境。只要将Documentclass[]更换成REVTex对应环境即可。一个最小的文档例子如下：

```
%\documentclass[aps,prl,reprint,superscriptaddress,showpacs]{revtex4-1}
\documentclass[%
reprint, %preprint, twocolumn% 其中reprint提供双栏最接近出版论文的格式，preprint显示的字体和行距则相对大一些，是方便审稿人将论文打印出来仔细阅读的，twocolumn选项与此类似。
superscriptaddress, %groupedaddress,% 现在通用是前一种作者名录格式，这样在显示多个作者或者一个作者从属于多个机构时比较紧凑方便。
showpacs,% 显示PACS代码
amsmath, amssymb, %都是用于显示数学公式环境
aps, %这个是指APS风格，另一个可选项应该是AIP
prl,%pra, prb, rmp, % 这里是对不同期刊的选择
]{revtex4-1}% 这个格式就是APS对应的latex文档格式
\usepackage{graphicx}% Include figure files
\usepackage{dcolumn}% Align table columns on decimal point
\usepackage{bm}% bold math
\usepackage{hyperref}% add hypertext capabilities
\hypersetup{colorlinks=true, citecolor=blue, urlcolor=blue, linkcolor=blue}
\bibliographystyle{apsrev4-1.bst}% 注意这个.bst风格文件是需要从官网单独下载的，可以控制文章末尾参考文献的现实风格。下载之后放到工作目录下即可(即.tex文档所在的目录)
\begin{document}
\title{Manuscript Title}% Force line breaks with \\
%\thanks{A footnote to the article title}%
\author{First Author}% You, the writer of this paper. 第一作者
\altaffiliation{Physics Department, XYZ University.}
\author{Second Author}% Boss with communication email 通讯作者，注意这里的Email一定要放在通讯作者后的第一个位置，这样邮箱地址的链接才会正确显示。
\email{Second.Author@institution.edu}
\affiliation{Authors' institution and/or address}
\author{Third Author} % 一个作者有多个单位
\homepage{http://www.Second.institution.edu/~Charlie.Author}
\affiliation{Second institution and/or address}%
\affiliation{Third institution, the second for Charlie Author}
\date{\today}%This date can be changed.
\bagin{abstract}% 摘要
An article usually includes an abstract, a concise summary of the work
covered at length in the main body of the article...
\end{abstract}
\pacs{Valid PACS appear here}% PACS, the Physics and Astronomy
%\keywords{Suggested keywords}% Not always required.
\maketitle
...
Main body of this paper...
...
\bibliography{References.bib}% Produces the bibliography via BibTeX. 这个包含引用文献的.bib文件是需要自己根据所引用的文章用文献管理工具或者自己手工生成的。
\end{document}
```

## 字数限制：
APS中Review性质的期刊一般只刊载本领域最新的进展，所以都是评论快报的形式，比较短小。一般的文章都控制在4页纸的长度左右，不会像有些期刊一样，一篇文章动辄几十上百页的规模。以prl为例，其正文的字数限制是3750，评论的限制是800左右。
相关的小技巧
REVTex的安装包 revtex4-1.zip可以从官网https://journals.aps.org/revtex下载到，但已经装好Texlive却不需要再重复安装。但是其中有些文件却有很大的帮助。例如：
/Downloads/revtex4-1/revtex4-1-tds/doc/latex/revtex/sample/aps/
apssamp.tex% 这个是REVTex的一个现成的完整的例子，里面有公式，图表等各种使用的范例。
apstemplate.tex% 这个是个空白的文档，没有什么内容，可以复制出来直接添加修改成自己的文章。其中很多地方都有注释后的提示，也很有帮助。
/Downloads/revtex4-1/revtex4-1-tds/bibtex/bst/revtex
这个目录下面则有各种现成的.bst文件，可以直接复制出来放到工作目录中调用。
aipauth4-1.bst aipnum4-1.bst apsrev4-1.bst apsrmp4-1.bst
其中apsrev4-1.bst就是prl对应的引文格式。

## 关于参考文献格式
从期刊网站上下载的文献一般不方便直接使用，因为不同期刊的格式有些混乱，所以要人工做些处理。目前我只保留bibtex中7条有用的信息，其它信息一般用不到。只有对于一些没有DOI的文献，可以加入URL信息提供文献的电子链接。但是DOI和URL最好不用同时出现，否则会引起混乱，一般有DOI就不用再加入URL了。
```
@article{Granetz_2014_POP,
	author = {Granetz, R. S. and Esposito, B. and Kim, J. H. and others},
	journal = {Phys. Plasmas},
	year = {2014},
	volume = {21},
	pages = {072506},
	title = {An ITPA joint experiment to study runaway electron generation and suppression},
	doi = {10.1063/1.4886802},
}
```
需要注意的是对REVTex的引文格式，在作者列表中"and others"是个关键词，使用它可以生成.et al，也就是更多作者的缩略[1]。一般可以在.bib文件中手工改一改，把超过3个作者的名字都删掉，替换成and others，这样文章末尾的文献列表就会短很多，不那么占地方了，如下图所示。

## 提交论文的最终版本
最终需要提交的文件只有.tex论文的latex源代码文件和.eps图片。之前我们都是利用.bib文件来生成参考文献的，等到编译好pdf文件的同时，会生成一个.bbl文件，这个文件里包含的就是包括完整引文格式和信息的参考文献代码：
```
\begin{thebibliography}{39}%
... ...
\end{thebibliography}%
```
所以只要把这个文件里的代码复制后粘贴到.tex的文档末尾，就可以将原来调用.bib引文文件和.bst引文格式文件的代码行注释掉。之后只需要.tex文件和.eps图片就可以以较快的速度编译生成.pdf论文文档了。

参考：
[1]https://tex.stackexchange.com/questions/123600/latex-doesnt-recognize-et-al-in-the-bibliography
[2]https://tex.stackexchange.com/questions/57743/how-to-write-ä-and-other-umlauts-and-accented-letters-in-bibliography
[3]https://www.cnblogs.com/docnan/p/8406929.html
