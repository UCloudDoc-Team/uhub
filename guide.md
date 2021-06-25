# 操作指南



## 创建镜像仓库

在UCloud控制台，找到公共镜像库服务。

![image](/images/uhub_create_01.png)

或在产品与服务中找到UHub，然后点击进入后创建镜像仓库:

![image](/images/uhub_create_02.png)

输入镜像仓库名称以及备注，镜像仓库名称必须为全网唯一。镜像仓库默认为非公开，如果你希望自己镜像被平台内其他用户pull，可以将镜像仓库设置为公开。

在创建镜像仓库后，即可从docker client端镜像push镜像来创建镜像。

当前每个项目支持最多 5 个镜像仓库，如您需要多于 5 个镜像仓库，可在上传镜像时利用多级目录进行命名，如：

```
docker tag nginx:latest uhub.service.ucloud.cn/ucloud_test/xyz/123/nginx:latest
```

## 镜像库登录

在装有docker (版本要求1.10 以上版本) 机器上通过docker login执行登录。

登录镜像仓库，通过域名访问服务：

```
docker login uhub.service.ucloud.cn -u user@ucloud.cn
```

登录用户名为UCloud平台注册的邮箱，密码为控制台密码。

## 独立密码使用说明

1. 登录用户名为UCloud平台注册的邮箱，密码为设置的独立密码。

2. 独立密码根据登录用户名进行绑定，修改独立密码将适用于所有镜像仓库。

3. 独立密码支持在UCLoud内网和外网使用。

4. 暂不支持内网拉取镜像的地域：福建。请使用UCloud平台密码进行镜像拉取。

## push镜像

Step 1: 本地对镜像打一个tag:

    docker tag {本地镜像名} uhub.service.ucloud.cn/{已创建镜像仓库}/{镜像}:tag

Step2：提交镜像到仓库:

    docker push uhub.service.ucloud.cn/{已创建镜像仓库}/{镜像}:tag

## pull镜像

pull镜像

    docker pull uhub.service.ucloud.cn/{已创建镜像仓库}/{镜像}:tag

## 跨地域使用体验

UCloud公共镜像库为跨地域架构，在一个地域节点push的镜像，在其他地域的节点都可以通过内网镜像pull；
如在北京二可用区C，push镜像：

![image](/images/uhub_region_01.png)

在上海二地域也可pull到：

![image](/images/uhub_region_02.png)

只要镜像push完成，UCloud平台内所有内网已经覆盖的地域都可以通过内网pull到已经push的镜像。
