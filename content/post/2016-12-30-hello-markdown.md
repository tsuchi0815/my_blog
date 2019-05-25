---
date: "2016-12-30T21:49:57-07:00"
title: A Plain Markdown Post
---

これは、R Markdown（* .Rmd）ではなく、プレーン Markdown（* .md）で書かかれた投稿です。 主な違いは以下の通りです：

1. プレーン Markdown 文書では R コードを実行できませんが、一方で、R Markdown 文書では、R コードチャンク  (```` ```{r} ````) を埋め込むことができます。
2. プレーン Markdown 投稿 [Blackfriday](https://gohugo.io/overview/configuration/) を通してレンダリングされ、R Markdown文書は [**rmarkdown**](http://rmarkdown.rstudio.com) と [Pandoc](http://pandoc.org) によってコンパイルされます

Blackfriday の Markdown と Pandoc の Markdown の間には、構文に多くの違いがあります。例えば、Bl ackfriday を使用してタスクリストを作成できますが、Pandoc では作成できません：

- [x] Write an R package.
- [ ] Write a book.
- [ ] ...
- [ ] Profit!

逆に、Blackfriday は LaTeX の数式をサポートしておりませんが、Pandoc はサポートしています。
このテーマ ([hugo-lithium](https://github.com/yihui/hugo-lithium)) には MathJax  サポートを追加していますが、プレーン Markdown 投稿には注意が必要です：バッククォートで数式を囲む必要があります（インライン： `` `$ $` ``; 表示スタイル： `` `$$ $$` ``）、例えば、 `$S_n = \sum_{i=1}^n X_i$`.^[これは、数式が Markdown として解釈されないように保護する必要があるためです。 数学式にアンダースコアやアスタリスクのような特別な Markdown 構文が含まれていない場合は、バッククォートは不要ですが、常にバッククォートを使用する方が安全です。 同じ要素内に2つのドル記号がある場合は、1つのドル記号をエスケープすることができます。例えば、`\$50 and $100` は、"\$50 and $100" と表示されます] R Markdown の投稿の場合、Pandoc が 数式を識別して処理するため、バッククォートは必要ありません。

新しい投稿を作成するときは、投稿形式が Markdown か R Markdown かを決める必要があります。これは、 `blogdown::new_post()` 関数の `ext` 引数を使用して実行できます。例えば、

```r
blogdown::new_post("Post Title", ext = '.Rmd')
```
