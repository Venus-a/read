# docker命令

## 常用命令

docker ps 查看容器

docker ps -a 查看所有容器（包含已经停止的）

docker run \stop\start 容器

docker rm -f 强制删除容器

docker rm -f $(docker ps -aq) 直接删除所有容器（包含运行中的）



docker logs 查看容器日志

docker logs --tail 100 myapp  查看最后 100 行日志



docker images 查看镜像



## 一、容器生命周期管理

| 命令                                          | 说明                                                    |
| :-------------------------------------------- | :------------------------------------------------------ |
| `docker run -d --name myapp -p 8080:80 nginx` | 启动容器（`-d` 后台运行，`--name` 命名，`-p` 端口映射） |
| `docker start myapp`                          | 启动已停止的容器                                        |
| `docker stop myapp`                           | 停止运行中的容器                                        |
| `docker restart myapp`                        | 重启容器                                                |
| `docker rm myapp`                             | **删除已停止的容器**（加 `-f` 强制删除运行中的容器）    |
| `docker exec -it myapp /bin/bash`             | 进入运行中的容器（`-it` 交互模式）                      |
| `docker pause/unpause myapp`                  | 暂停/恢复容器进程                                       |

## 二、镜像管理

| 命令                               | 说明                                              |
| :--------------------------------- | :------------------------------------------------ |
| `docker pull nginx:latest`         | 拉取镜像（不指定标签默认 `latest`）               |
| `docker build -t my-image:1.0 .`   | 构建镜像（`-t` 指定名称，`.` 为 Dockerfile 目录） |
| `docker images`                    | 查看本地镜像列表                                  |
| `docker rmi my-image:1.0`          | 删除镜像（需先删除依赖容器）                      |
| `docker push my-repo/my-image:1.0` | 推送镜像到仓库                                    |

## 三、查看信息

| 命令                   | 说明                                 |
| :--------------------- | :----------------------------------- |
| `docker ps`            | 查看**运行中**的容器                 |
| `docker ps -a`         | 查看所有容器（包括已停止的）         |
| `docker logs myapp`    | 查看容器日志（加 `-f` 实时跟踪）     |
| `docker inspect myapp` | 查看容器/镜像的详细信息（JSON 格式） |
| `docker stats`         | 实时监控容器资源使用（CPU/内存）     |

## 四、数据管理

| 命令                                             | 说明             |
| :----------------------------------------------- | :--------------- |
| `docker volume create my-vol`                    | 创建数据卷       |
| `docker run -v my-vol:/app/data nginx`           | 挂载数据卷到容器 |
| `docker run -v /host/path:/container/path nginx` | 绑定宿主机目录   |

## 五、网络管理

| 命令                                | 说明               |
| :---------------------------------- | :----------------- |
| `docker network ls`                 | 查看网络列表       |
| `docker network create my-net`      | 创建自定义网络     |
| `docker run --network=my-net nginx` | 将容器加入指定网络 |

## 六、清理资源

| 命令                     | 说明                                   |
| :----------------------- | :------------------------------------- |
| `docker system prune`    | 清理停止的容器、未使用的网络和构建缓存 |
| `docker system prune -a` | **彻底清理**（包括未使用的镜像）       |
| `docker volume prune`    | 清理未使用的数据卷                     |

