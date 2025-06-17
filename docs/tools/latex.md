# LaTex


<!-- ## Overleaf

[Overleaf](https://www.overleaf.com/) 是一个在线 LaTeX 编辑器。投稿前请让我新建 project 并分享给你。 -->

## Tips

### 使用`input`组织文档结构

不要把所有内容都写在一个 `.tex` 文件中。可以使用 `\input` 命令将不同的章节或部分分成不同的文件。这样可以更好地组织文档结构。

文档结构示例：

```bash
/My-Best-Paper
|-- main.tex
|-- preamble.tex  # optional, for all your packages and commands
|-- references.bib # Your BibTeX bibliography file
|-- /sections
|   |-- 0_abastract.tex
|   |-- 1_introduction.tex
|-- /figures
|   |-- fig_methodology.pdf
|   |-- fig_results.png
```

> [!NOTE]
> 对使用标准 ACM 和 IEEE 模板的论文，**不要**把`acmart.cls`和`IEEEtran.cls`等模板文件放在项目目录下。它们会自动通过`\usepackage`加载。

`main.text`示例：

```tex
% Set the document class and options.
\documentclass[sigplan,nonacm,screen,review]{acmart} % or \documentclass{IEEEtran}

% --- PREAMBLE ---
\input{preamble} % optional

\begin{document}
\title{My Best Paper}
\author{Your Name}

% --- SECTIONS ---
% Input the content from the 'sections' directory. This creates the paper's flow.
\input{sections/0_abstract} % abstract
\input{sections/1_introduction} % introduction

\end{document}
```

### 修改 documentclass 选项

问其他同学，或者自己看[文档](https://mirror.las.iastate.edu/tex-archive/macros/latex/contrib/acmart/acmart.pdf)第 2.1 章。

### 使用`preamble.tex`自定义包和命令

在 `preamble.tex` 文件中，可以放置所有的包和自定义命令。这样可以使主文档更简洁。

添加包的时候，参考 ACM 可接受的 [列表](https://authors.acm.org/proceedings/production-information/accepted-latex-packages)。

示例：

```tex
\usepackage{microtype}
\usepackage[capitalize]{cleveref}
\usepackage[obeyFinal]{changes}
\usepackage{enumitem}
\usepackage{graphicx}
\usepackage{subcaption}
\usepackage{siunitx}
```

定义自定义命令也可以放在 `main.tex`开头或者`preamble.tex` 中。例如：

```tex
\newcommand*{\game}{元神}
\newcommand{\scam}{Super-Cognitive Architecture Model (SCAM)}
\newcommand{\vect}[1]{\mathbf{#1}} % Defines a command for vectors
```

在正文中使用：

```tex
\game 是一款由哈米游开发并发行的开放世界玩法的冒险类角色扮演游戏。
In this section, we discuss the \scam. The \scam is ...
Let the vector be $\vect{v}$. The relationship is $\vect{a} = \vect{F}/\vect{m}$.
```

### 标点符号

- 三种横线
    - `-`（短横线）：连字符，比如 `state-of-the-art`
    - `--`（长横线）：数字区间，比如 `page 1--10`
    - `---`（破折号）：表示停顿或插入语，比如 `This is a test---a very important one.`
- 引号
    - 单引号：`` ` ``和`` ' ``
    - 双引号分别用` `` `和`` '' ``
- 省略号： `\ldots`

### 数学符号

- `$The result is x$`： "The result is" 会被当作一连串的数学变量 (`T*h*e*...`) 来处理
    - 使用 `amsmath` 提供的 `\text{...}` 命令来插入正常的文本。
- `$sin(x)$` 或 `$log(y)$`： "sin" 和 "log" 会渲染成三个斜体的变量 (`s*i*n` 和 `l*o*g`)
    - 使用预设的函数/符号，例如：`$\sin(x)$` 和 `$\log(y)$`。
    - 对于未预设的函数/变量名，使用 `\DeclareMathOperator` 自行定义。例如`\DeclareMathOperator{\Tr}{Tr}`

### 使用 `cleveref` 引用

[clevref](https://ctan.org/pkg/cleveref) 可以自动识别引用的类型，如“定理”、“引理”、“图”、“表”等，并自动添加对应的前缀。命令为`\cref`

```tex
\cref{fig:my-figure} % Figure 1
\Cref{sec:my-section} % Section 1.2
\cref{thm:my-theorem} % Theorem 1
```

### 使用 `changes` 标记修改

[changes](https://ctan.org/pkg/changes) 可以标记出文档中的修改，如增加、删除、替换等。命令为`\added`，`\deleted`，`\replaced`，`\comment`，`\highlight`。

```tex
\added{这是新增的内容。}
\deleted{这是删除的内容。}
\replaced{这是替换后的内容。}{这是替换前的内容。}
\comment{这是注释内容。}
\highlight{这是高亮的内容。}
```

### 使用 `enumitem` 调整 bullets 间距

[enumitem](https://ctan.org/pkg/enumitem) 可以自定义列表的样式和间距。

### 使用 `minipage` 和 `subcaption` 创建并排的图表

[subcaption](https://ctan.org/pkg/subcaption) 提供了更好的支持和更多的功能。

```tex
\begin{figure}[htbp]
    \centering
    \begin{minipage}{0.45\textwidth}
        \centering
        \includegraphics[width=\linewidth]{figures/fig_methodology.pdf}
        \caption{Methodology}
        \label{fig:methodology}
    \end{minipage}
   \hfill
    \begin{minipage}{0.45\textwidth}
        \centering
        \includegraphics[width=\linewidth]{figures/fig_results.png}
        \caption{Results}
        \label{fig:results}
    \end{minipage}
\end{figure}
```

> [!NOTE]
> **不要**使用 `subfigure`，`subfig`，或`wrapfig`。

### 使用 `siunitx` 处理单位

[siunitx](https://ctan.org/pkg/siunitx) 提供了一个一致的方式来处理单位和数字。可以使用 `\SI` 命令来格式化单位。

```tex
One thousand bytes is \SI{1}{\kilo\byte}. % 1 KB
One thousand and twenty-four bytes is \SI{1}{\kibi\byte}. % 1 KiB
```
