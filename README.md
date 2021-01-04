# docker-hadoop-spark-hive

docker-hadoop-spark-hive 快速构建你的大数据环境

这是一个 基于docker 构建的 一键启停 大数据 学习平台

- hadoop 2.8
- hive 2.3.2
- spark 2.1.0

要用到docker 你可能需要使用虚拟环境 这里 我用的是 virtualbox 

我研究了一段时间，才配置成功了各项参数。

所有软件访问需要预先 配置的端口，都已经 一一映射！

其中 hadoop , spark , hive 均可以在 我的windows 连接哦。很nice

接下来 介绍一下 如何使用

## 1、安装docker 

```shell
sudo apt install docker.io
```

## 2、安装 docker-compose

```shell
sudo apt install docker-compose
```

## 3、开始你的表演

```shell
# 进入 docker-compose.yml 的目录
./run.sh

# 如果发现存在没有成功启动的 容器 （状态为 exited ）
docker ps -a

# 手动重启下
docker-compose up -d 

# 如果需要停掉
./stop.sh

# 如果需要设置一些 环境变量

vim *.env

这里需要注意，环境变量 基本不需要设置。

# 如果需要修改 docker 容器 运行的一些选项
vim docker-compose.yml

```

## 4、环境验证
### 4.1 browser访问spark hadoop es kibana等

本机访问如下几个地址：

```tex
localhost:8080	-- spark
localhost:50070 -- hadoop NN
localhost:9200	-- ES
localhost:5601	-- Kibana
```

如果可以正确打开则没问题。

### 4.2 进入hive：

进入容器

bash前面的是你的容器ID，通过`docker ps`可以看到。

```shell
docker exec -it b002969ab690 bash
```

进入beeline

```shell
beeline -u jdbc:hive2://localhost:10000
```
至此已经进入Hive环境，可以自行尝试hive的语句。
