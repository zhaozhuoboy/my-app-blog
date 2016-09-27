# 在linux服务器上部署代码

1. 上传代码  ssh  git  github

  `scp -r test zhaozhuo.club ` 通过ssh协议 将本地项目拷贝到服务器上（域名可以是ip）

2. 登录到服务器 ssh ip/域名

  `ssh zhaozhuo.club/IP`

3. 安装（软件）服务器 nginx

  `sudo apt-get install nginx`

4. 配置服务器nginx

  ```
  cd /etc/nginx/   软件安装目录

  cd sites-enabled/       打开添加新网站的配置文件夹

  sudo touch test.conf    创建新站点的配置文件

  ```

  _修改配置文件 `sudo vim test.conf `   使用`vim`修改配置文件_

  `test.conf:`文件内容

  ```
  server{
    listen 80;
    server_name zhaozhuo.club;  //访问地址
    root /home/zhaozhuo/test;    //入口文件位置
  }

  ```

  > 修改配置文件之后 重启服务器   sudo service nginx reload

  `sudo nginx -t`   查看重启服务器报错信息

  `logout` 退出登录远程服务器   快捷键：`ctrl+D`


  # 局域网内模拟部署过程

  1 查看作为服务器 机器的 ip `ifconfig`

  2 用自己的电脑ping一下服务器的ip 查看是否能连通

  3 在服务器上安装 ssh server

  `sudo apt-get install openssh-server`

  开放机器，使别的计算机能够远程登陆这台服务器

  4 登陆服务器

   ` ssh zhaozhuo@ip` 然后输入远程服务器的登陆密码


  5 上传代码 ssh  git   github

  `scp -r test username@ip:`

  scp 是基于 ssh 的

  : 必须有最后的冒号

  最后会拷贝到目标机器的用户主目录 `/home/username`

  6 剩下步骤 参考上边 配置服务器nginx
