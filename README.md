# sdokio.github.io

### 说明
本分支为hexo博客框架源码，用于生成静态博客html。

每当本分支push时将触发本分支的workflow：生成静态博客html -> 强制push这些html到master分支。随后GitHub Pages检测到master分支有改动（之前GitHub Pages默认发布master分支，不可修改）将自动发布网页。

### 新机器使用方法
1. 安装 Git（已安装的跳过）
    1. CentOS: `sudo yum install git-core`
    1. Ubuntu: `sudo apt-get install git-core`

2. 安装 Node.js（已安装的跳过）

    `wget -qO- https://raw.github.com/creationix/nvm/v0.33.11/install.sh | sh`

    完成后，**重启**终端并执行:

    `nvm install stable`

3. 安装 hexo

    `npm install -g hexo-cli`

4. clone 项目

    `git clone -b hexo-src https://github.com/sdokio/sdokio.github.io.git`

5. npm安装依赖环境

    `cd blog && npm install`

6. 编译和本地部署

    `hexo g && hexo s`
