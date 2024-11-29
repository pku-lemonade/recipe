# LaTex

LaTex 是一种文档排版系统。通常我们在写论文时会在[Overleaf](https://www.overleaf.com/)上用到。

## style guide

- 多换行。每个句子换一行。当句子接近编辑器宽度时（比如 80 字符）换一行。这样阅读起来更方便，报错时也更好定位。
- 在准备提交前，使用`\vspace{}`调整图片和文字之间的间距。

## packages

以下是一些常用的 package。

### clevref

[clevref](https://ctan.org/pkg/cleveref) 是一个用于交叉引用的 package。它可以自动识别引用的类型，如“定理”、“引理”、“图”、“表”等，并自动添加对应的前缀。命令为`\cref{}`和`\Cref{}`(大写第一个字母)。

### changes

[changes](https://ctan.org/pkg/changes) 是一个用于标记修改的 package。它可以标记出文档中的修改，如增加、删除、替换等。命令为`\added{}`，`\deleted{}`，`\replaced{}{}`，`\comment{}`，`\highlight{}`。
