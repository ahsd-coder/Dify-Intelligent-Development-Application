# 步骤 1: 租赁阿里云 ECS

- 选择**香港地区**（Dify 安装插件需要外网权限）
- 选择需要公网 IP
- 设置 root 密码

> https://ecs-buy.aliyun.com/ecs#/custom/prepay/cn-hongkong

![阿里云ECS租赁步骤](./image1.png)

# 步骤 2: 安装 Docker 环境

```shell
# 更新包管理工具
sudo apt-get update

# 添加Docker软件包源
sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common

# 安装Docker社区版本，容器运行时containerd.io，以及Docker构建和Compose插件
sudo curl -fsSL http://mirrors.cloud.aliyuncs.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository -y "deb [arch=$(dpkg --print-architecture)] http://mirrors.cloud.aliyuncs.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get -y install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 启动Docker
sudo systemctl start docker

# 设置Docker守护进程在系统启动时自动启动
sudo systemctl enable docker

# 确认docker环境
sudo docker -v

```



# 步骤 3: 安装 Dify

参考步骤：https://docs.dify.ai/zh-hans/getting-started/install-self-hosted/docker-compose

启动完成后，需要确定实例的安全组，打开 80 端口

访问：http://公网ip/install
