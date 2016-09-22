# MongoDB 安装


[参考资料](https://docs.mongodb.com/v3.0/tutorial/install-mongodb-on-ubuntu/)

1 导入的包管理系统使用的公钥。

  ```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
  ```

2 创建MongoDB的列表文件

```
echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list

```

3 刷新本地包数据库

```
sudo apt-get update

```

4 安装MongoDB的包

```
sudo apt-get install -y mongodb-org

```

验证一下 mongodb 有没有安装成功

```
//创建一个数据库 跑起来
mkdir data
mongod --dbpath=./data --port 27017

```

*执行上面命令后 如果停留在 `[initandlisten] waiting for …… 27017 证明mongod服务启动成功了*

```
sudo service mongod start //启动服务

sudo service mongod stop  //停止服务

sudo service mongod restart  //重启服务

```
