# soyadokio.github.io

本分支为hexo博客框架源码，用于生成静态博客html。

每当本分支push时将触发本分支的workflow：生成静态博客html -> 强制push这些html到master分支。随后GitHub Pages检测到master分支有改动（之前GitHub Pages默认发布master分支，不可修改）将自动发布网页。

