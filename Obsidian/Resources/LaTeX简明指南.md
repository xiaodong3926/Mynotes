## 一.前言部分(Preamble) 

`\document[a4paper, 12pt]{...}` latex的第一句，通常用来指定文章类型，如article,report,book,beamer(幻灯片),方括号内的文本指定了一些选项——示例
中它设置纸张大小为 A4，主要文字大小为 12pt

`\usepackage{...}` 导入包，如`\usepackage[UTF-8]{ctex}` 用来导入中文，而编码是用来告诉ctex包这篇文章是UTF-8编码，防止中文乱码。**注意：一个语句只能导入一个包，多个包要写多个命令**

一篇latex文章通常包含下面几个信息:
- `\title{标题}` 
- `\author{作者}`
- `\date{\today}` \today也是个命令，用来显示当前日期

## 二.正文(Body)

`\begin{document}` 从这行命令开始，所有东西都会显示在文章中

`\maketitle` 在这行命令的位置，将前言部分的标题，作者，日期都显示出来

`\end{document}` 文章结束
#### 1.文字处理

`\textbf{...}`  Bold Font 将文字加粗

`\textit{...}` Italic 斜体文字

`underline{...}` 下划线

#### 2.内容结构

按照块大小进行排序:

`\part{篇名}`
	`\chapter{章名}`
		`\section{节名}` article类型，最高级就是section
			`\subsection{小节}`	
				`\subsubsection{小小节}`

#### 3.插入图片（需导入包{graphicx}

在一个块内对图片进行处理:
`\begin{figure}` 

`\centering` 将图片居中

`\includegraphics[width=0.8\textwidth]{图片名}` 导入图片，并将图片宽度设为文章的80%

`\caption{图片标题}` 

`\end{figure}` 结束

#### 4.列表

`\begin{itemize}` 无序表格，有序表格需要替换为`enumerate`

`\item` 项1
`\item` 项2
......

`\end{itemize}` 结束

#### 5.表格

`\begin{table}` 

`\center`

`\begin{tabular}{|l|r|c|}`  l:靠左对齐,r:靠右对齐,c:居中对齐,|:给表格加竖直方向边框
	\hline(添加水平方向边框)
	格1 & 格2 &格3 \\(分割每行)
	\hline
	格4 & 格5 &格6
	\hline
`end{tabular}`表格内容编辑结束

`\caption{标题}`

`\end{table}` 表格样式编辑结束

#### 6.公式
**行内公式**:`$E=mc^2$`  可与文字一起排版

**独立公式** ：
`\begin{equation}` 可简写为`\[`

E = mc^2

`emd{equation}` `\]`

[在线latex公式编辑](https://www.latexlive.com/)