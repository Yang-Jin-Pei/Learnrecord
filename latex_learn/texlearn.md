# $\LaTeX$ 记录
# 1 导言区
首先定义类型 `\documentclass{}`。
```latex
\documentclass{article}
```
## 1.1 中文显示
```latex
\usepackage{ctex} % 中文显示
```

## 1.2 颜色
```latex
\usepackage{xcolor} % 颜色
```

## 1.3 图
```latex
\usepackage{graphicx} % 添加图片
\usepackage{tikz} % 绘制矢量图
\usepackage{subcaption} % 子图
```

## 1.4 表格
```latex
\usepackage{booktabs​} % 表格
\usepackage{multirow​} % 多行，包括合并的表格
```

## 1.5 数学公式
```latex
\usepackage{amsmath} % 数学公式
\usepackage{amssymb} % 数学符号
\usepackage{amsfonts} % 数学字体
\usepackage{bm} % 粗体
\usepackage{algorithm2e} % 算法显示
```

## 1.6 超链接
一般放在最后。
```latex
\usepackage[colorlinks, linkcolor=blue, citecolor=blue, urlcolor=blue]{hyperref} % 链接为蓝色
```

# 2 内容
```latex
\begin{document}
...
\end{document}
```
## 2.0 注释
注释为百分号 `%` ，输入百分号的方法是输入 `\%` 。
```latex
%
\%
```
## 2.1 正文之前

### 2.1.1 标题
```latex
\title{Title is Here}
```

### 2.1.2 作者

```latex
\author{Author is Here}
```

### 2.1.3 日期
这里 `\today` 是当天运行日期。
```latex
\date{\today}
```
### 2.1.4 输出标题等信息
采用 `\maketitle` 语句。
```latex
\maketitle
```

## 2.2 正文
正文内容包括文字，图，表格，
### 2.2.1 章节标题
```latex
\section{一级标题}           % 用于 article
\subsection{二级标题}
\subsubsection{三级标题}

\chapter{章}                % 用于 report 和 book
```

### 2.2.2 文本格式
```latex
\textbf{粗体文本}
\textit{斜体文本}
\underline{下划线}

{\Large 大号字体}  % 相对大小命令：\tiny, \small, \normalsize, \large, \Large, \LARGE, \huge, \Huge

\begin{center}
这是居中的文本。
\end{center}
```
### 2.2.3 列表
```latex
% 无序列表
\begin{itemize}
  \item 第一项
  \item 第二项
        \begin{itemize}
          \item 子项一
          \item 子项二
        \end{itemize}
\end{itemize}

% 有序列表
\begin{enumerate}
  \item 第一步
  \item 第二步
\end{enumerate}
```

### 2.2.4 数学公式
```latex
行内公式：勾股定理 $a^2 + b^2 = c^2$ 非常著名。

行间公式（带编号）：
\begin{equation}
E = mc^2
\label{eq:emc2} % 用于交叉引用
\end{equation}

多行对齐公式（不带编号）：
\[
\begin{aligned}
f(x) &= (x+1)^2 \\
     &= x^2 + 2x + 1
\end{aligned}
\]
```

### 2.2.5 插入图片
首先需要再导言区添加对应的包
```latex
\usepackage{graphicx} % 记得在导言区加载
```
正文部分插入图片
```latex
\begin{figure}[htbp] % h: here, t: top, b: bottom, p: page
  \centering
  \includegraphics[width=0.8\textwidth]{example-image.png} % 宽度设为文本宽度的80%
  \caption{图片的标题}
  \label{fig:my_image} % 用于交叉引用
\end{figure}
```

### 2.2.6 表格
```latex
\begin{table}[htbp]
  \centering
  \caption{表格标题}
  \begin{tabular}{|l|c|r|} % l: 左对齐, c: 居中, r: 右对齐, | 表示竖线
    \hline
    姓名 & 分数 & 等级 \\ \hline %\hline表示横线
    张三 & 95 & A \\ \hline
    李四 & 87 & B+ \\ \hline
  \end{tabular}
  \label{tab:score}
\end{table}
```

### 2.2.7 交叉引用
```latex
如第\ref{sec:intro}节中图\ref{fig:arch}所示，公式(\ref{eq:main})是核心。
```

### 2.2.8 特殊字符
```latex
\%，\$，\&，\_
```

### 2.2.9 空格与换行
- **多个空格**​ 会被视为一个空格。
- **换行符**​ 被视为一个空格。要开始新的段落，使用一个空行或者 `\par`
- **强制换行**​ 使用 `\\` 或 `\newline`（在表格、公式等环境中常用，正文中尽量避免）。
- **禁止换行**​ 使用波浪号 `~`，例如 `Prof.~Smith` 可以防止 `"Prof."` 和 `"Smith"` 被分在两行。

### 2.2.10 颜色
```latex
\textcolor{red}{这段文字是红色的}
{\color{blue} 这段文字是蓝色的}
\colorbox{yellow}{这个文本有黄色背景}
\fcolorbox{red}{white}{这个文本有红色边框和白色背景}
```

## 2.3 参考文献
### 2.3.1 注意事项
- **使用** `BibTeX` 或更现代的 `BibLaTeX`。
- **创建**一个 `.bib` 文件管理所有文献。
- 在文中使用 `\cite{key}` **引用**。
- **编译**顺序：`LaTeX-> BibTeX-> LaTeX-> LaTeX`（确保交叉引用正确）。
### 2.3.2 BibTex 引用
#### 2.3.2.1 导言区
```latex
\usepackage{natbib}
\addbibresource{references.bib}
\usepackage{hyperref} % 建议最后加载
```
#### 2.3.2.2 内容引用
- `\cite{key}`：生成一个数字标签，如 [1]。
- `\citeauthor{key}`：只显示作者，如 Einstein。
- `\citeyear{key}`：只显示年份，如 1905。
- `\citet{key}`：生成 "作者 (年份)" 格式（需要 `natbib` 宏包），如 Einstein (1905)。
- `\citep{key}`：生成 "(作者, 年份)" 格式（需要 `natbib` 宏包），如 (Einstein, 1905)。
- **引用多个文献**：用逗号分隔，如 \cite{einstein1905, vaswani2017}生成 [1, 3]
#### 2.3.2.3 末尾
```latex
\bibliography{references} % 使用传统 BibTeX
\bibliographystyle{plain}       % 基本数字编号
```

