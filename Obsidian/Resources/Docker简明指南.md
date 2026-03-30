## 一.容器
##### 镜像就相当于一个模板，当你用镜像来创建好一个容器后你就可以来修改它
#### 创建一个容器
简单来说就一个命令:`docker run (参数) （镜像名） （命令）` 参数就比如“-i -t -d -p”(-i 终端，-t 允许进行交互,-d 后台运行,-p 5000:5000 映射端口，前一个是主机端口，后一个是容器端口) ，镜像名可以在Docker Hub上找一个，命令比如`bash`--进入容器的bash shell，运行结束后会打印出一个很长的ID

这一行命令包含了三个步骤：

1.`docker pull (name)` 命令允许你从Docker Hub上下载一个镜像（官网会有详细的拉取介绍）

2.`docker create --name (name1) (name2)` 来创建一个容器（不运行）， 第一个名字是你给你的容器创建的名字，第二个名字是Docker Hub上的镜像名，官网要求镜像名必须全小写

3.`docker start (name1)` 命令来启动这个容器，再使用`docker exec -it （name1）（命令）` 来进入这个容器并与之交互(`docker attach`也可以进入运行的容器但退出时会自动关闭容器)

在shell界面可以用`exit`或Ctal+D来退出容器

## 二.容器基本操作
#### 1.创建(Status:Created)

#### 2. 启动(Status:Running)
`docker run (...)` 可以运行容器但是只适合第一次创建的时候用，当你已经有容器了，用
`docker start (name)` 来启动

#### 2.冻结(Status:Paused)
`docker pause (name)` 允许你冻结某个容器，可以用
`docker unpause (name)` 来恢复

#### 3.停止 (Status:Exited)
`docker stop (name)` 可以让你关闭一个容器，不可恢复！！

`docker kill (name)` 强行关闭，适合容器出现异常的情况

#### 4.删除
`docker rm (name)` 删除已经停止的容器，加参数`-f`来强行删除正在运行的容器

#### 5.查看
`docker logs (name)` 加`-f`(`tail -f`)参数来实时输出容器内的日志

用参数`--tail 5` 来输出最近的5条日志
