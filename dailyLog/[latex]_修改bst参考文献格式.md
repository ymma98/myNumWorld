# 通过修改 bst 文件修改参考文献的格式

我之前的参考文献的格式为:

```bash
[3] Steinhauer L C 2011 Phys. Plasmas 18 070501
```

现在需要做两点修改：

1. 在姓名缩写后面加上 `.`
2. 在年份后面添加文章的标题



在 .bst 文件里，找到 `FUNCTION` `article`:

```latex
FUNCTION {article}
```

然后在 `date.block` 后添加一行: `format.title "title" output.check`

```latex
{ output.bibitem
 format.authors "author" output.check
 format.date "year" output.check
 date.block
 crossref missing$
```

修改为:

```latex
{ output.bibitem
 format.authors "author" output.check
 format.date "year" output.check
 date.block
 format.title "title" output.check
 crossref missing$
```

解决方案来自：https://tex.stackexchange.com/questions/165011/help-with-editing-bst-file-to-output-article-titles-in-the-bibliography







修改标题:

找到 `format.names`:

```latex
FUNCTION {format.names}
{ 'bibinfo :=
 duplicate$ empty$ 'skip$ {
 's :=
 "" 't :=
 #1 'nameptr :=
 s num.names$ 'numnames :=
 numnames 'namesleft :=
   { namesleft #0 > }
   { s nameptr
    % "{vv~}{ll}{ jj}{ f.{~}}"  这一行修改为下一行
    "{vv~}{ll}{ jj}{ ff{~}}"
     format.name$
     %remove.dots  注释掉这个
     bibinfo bibinfo.check
```





修改 `et al.` 为 `et al`:

```latex
FUNCTION {bbl.etal}
{ "et~al" }
```



