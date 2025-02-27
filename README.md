# rosjava_bootstrap

修改了maven地址，用以生成java消息。目前使用的地址是私有的 http://192.168.3.109/rosjava
上面所有的私有的库都放到了 [rosjava_center](https://github.com/ceoifung/rosjava_center)

clone 上面的仓库到本地，然后启动一个http服务器，全局搜索代码中的http://192.168.3.109/rosjava
修改为自己的地址

目录结构如下：

```shell
rosjava-|
        ├─com
        │  └─google
        │      └─guava
        │          └─guava
        │              └─12.0
        ├─commons-pool
        │  └─commons-pool
        │      └─1.6
        ├─io
        │  └─netty
        │      └─netty
        │          └─3.5.2.Final
        └─org
            └─apache
                └─commons
                    ├─com.springsource.org.apache.commons.codec
                    │  └─1.3.0
                    ├─com.springsource.org.apache.commons.io
                    │  └─1.4.0
                    └─com.springsource.org.apache.commons.lang
                        └─2.4.0
```

## docker编译

用docker拉取一个我已经制作好的rosjava镜像

```shell
docker pull ceoifung/rosjava-ceoifung
```

然后clone仓库

```shell
mkdir ~/catkin_ws/src -p
cd ~/catkin_ws/src
git clone https://github.com/ceoifung/rosjava_bootstrap

# 将自己的message消息放到catkin_ws/src里面
# 启动docker
docker run --rm -it -v ~/catkin_ws:/home/catkin_ws rosjava-ceoifung:latest /bin/bash

# 进入镜像之后
cd /home/catkin_ws
catkin_make
# 编译成功之后，就可以在devel目录下找到编译出来的jar文件了
```

----
See [rosjava_core](https://github.com/rosjava/rosjava_core) readme.
