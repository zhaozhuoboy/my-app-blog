# Linux安装node

### 1. 首先安装nvm 用来安装nodejs的工具  可以安装多个版本node github上搜索nvm  从上边找到  安装命令代码
 ```
 curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.2/install.sh | bash

 ```

 *注意：安装完成之后要重启命令行生效*

 ### 2. 安装node.js

 `nvm ls-remote` 查看有哪些版本可以安装

 `nvm install v6.2.2` 这里我安装的是6.2.2版本

利用 nvm 可以在我们的机器上安装多个版本 node ，并且可以进行灵活的切换。下面将 6.2.2 这个 node 版本设置为默认。执行下面语句即可。重启 shell 之后，执行 node -v 可以查看当前的 node 版本。

`nvm alias defaule 6.2.2` 设置默认 node 版本
