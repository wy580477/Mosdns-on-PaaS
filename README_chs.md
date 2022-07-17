## 鸣谢

- [IrineSistiana/mosdns](https://github.com/IrineSistiana/mosdns) An advanced DNS forwarder.
- [v2fly](https://github.com/v2fly)

## 注意

 **请勿滥用 PaaS 平台的服务，账户封禁风险自负**

## <a id="Overview"></a>概述

本项目用于在 Heroku / Okteto / Railway / Northflank / fly.io 等 PaaS 平台上部署 [mosdns](https://github.com/IrineSistiana/mosdns) DoH 服务。

![未命名绘图 (1)](https://user-images.githubusercontent.com/98247050/179379517-1cb35632-e594-4712-8d62-f0ef1ba5c8d9.jpg)

## <a id="Deployment"></a>部署

- Fork 本项目
- 编辑 /content/config.yaml 以自定义 DNS 设置。默认配置启用广告域名拦截和 ECS。
- 强烈建议自定义 DOH_PATH 变量，以避免部署的服务被他人滥用。

### 部署到 Heroku 
- 需要信用卡认证账户才能 24*7 运行，不然每月限制550小时运行时间。 
   
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

### 部署到 Okteto, Railway, Northflank etc.
- 在 PaaS 平台管理面板中连接你 fork 的 repo
- 设置 DOH_PATH 变量
- 部署

### 部署到 Koyeb
- 在你 forked 的 repo 中新建 release，使用 tag 格式为 "v0.0.1"
- 等待 github action 完成
- 使用 github action 生成的容器镜像部署

### 部署到 fly.io
- 安装 [flyctl](https://fly.io/docs/flyctl/installing/)
- git clone repo，然后切换路径到 repo 文件夹
- 编辑 fly.toml 以设置 DOH_PATH 变量
```
# 登陆
flyctl auth login
# 创建 App
flyctl apps create <app_name>
# 设置部署区域 https://fly.io/docs/reference/regions/
flyctl regions set <region_code> -a <app_name>
# 部署
flyctl deploy --detach -a <app_name> --remote-only --no-cache
```
