# laravelAdmin

[![Packagist](https://img.shields.io/packagist/l/encore/laravel-admin.svg?maxAge=2592000)](https://gitee.com/laravel-admin/laraveladmin)  

[![Total Downloads](https://img.shields.io/packagist/dt/zsping1989/laravel-admin.svg?style=flat-square)](https://gitee.com/laravel-admin/laraveladmin)  

[![Awesome Laravel](https://img.shields.io/badge/Awesome-laraveladmin-green)](https://gitee.com/laravel-admin/laraveladmin)

#### 介绍
`laravel-admin`是一个可以快速帮你构建后台管理的工具，它提供的页面组件和表单元素等功能，能帮助你使用很少的代码就实现功能完善的后台管理功能。\(QQ群: 391528810\)
[Demo](http://demo.laraveladmin.cn) \|\| [阅读文档](http://www.laraveladmin.cn/home/index)


## 截图

![laravel-admin](https://www.laraveladmin.cn/storage/uploads/images/2020/12/05/kg3F2blsJISs6GbyFdmItHU7VKGLPx4zUIrPS0H6.jpeg)

#### 软件架构

基于laravel框架实现前后端分离的单页面应用架构

使用相关技术:vue+bootstrap+phpswoole+docker+laravel

### Mac环境,Linux环境安装请查看 [Linux安装](README.md)

#### 安装前准备

1. 提前安装好git

2. Windows安装请先手动安装好docker(电脑需支持Hyper-V),并执行命令docker-compose -v检查docker是否已安装成功

3. Windows注意要进入容器请在命令前加上"winpty "

4. Windows请手动设置下载源为国内镜像源

```json5
{
    "registry-mirrors" : [
        "https://mirror.ccs.tencentyun.com",
        "http://registry.docker-cn.com",
        "http://docker.mirrors.ustc.edu.cn",
        "http://hub-mirror.c.163.com"
    ],
    "insecure-registries" : [
        "registry.docker-cn.com",
        "docker.mirrors.ustc.edu.cn"
    ],
    "debug" : true,
    "experimental" : true
}

```

![docker国内镜像设置](https://www.laraveladmin.cn/storage/uploads/images/2020/12/08/7x7wz5WhsQw9drW7yXFmN7DLjZGWvzubcO4PKzFi.png)

5. Windows的其它设置参照

![Windows Docker设置1](https://www.laraveladmin.cn/storage/uploads/images/2020/12/09/P4zc6g4g8pG7DkZjfuC0w6tGDq6eKfJ9mMrumxIR.png)
![Windows Docker设置2](https://www.laraveladmin.cn/storage/uploads/images/2020/12/09/ZOZaJgLBtWQPmSgHClTixeKinFcFP4Da0CTsA2ia.png)
![Windows Docker设置3](https://www.laraveladmin.cn/storage/uploads/images/2020/12/09/SHCVxkHIf6eaLft4yaT1ztTyMXQ6Z8S4xFkx4g3R.png)

6. 设置预将代码存放目录的上级目录跟"\~"目录必须包含 dokcer的File Sharing列表中的目录中(Windows环境的"\~"目录为"C:/Users/Administrator")

> 我的Windows电脑只有一个C盘,直接选的C盘

![docker共享盘设置](https://www.laraveladmin.cn/storage/uploads/images/2020/12/08/kqeBi3cAq0D6NQD0H1mcLNdY3e6IqPUbUEJZwAZf.png)

7. 上面内容设置到docker设置中后记得点应用

8. Windows环境请进入git bash命令行工具进行执行安装
   
![进入git bash](https://www.laraveladmin.cn/storage/uploads/images/2020/12/09/DCVTN13VC08tcVTBGtpYB0xzCrhMf1Gq9DNKfEPl.png)

#### 安装教程

1. 下载代码

```shell
git clone https://gitee.com/laravel-admin/laraveladmin.git
cd laraveladmin
```

2. 参照.env.example配置.env文件(务必设置好mysql密码,redis密码)

```shell
cp .env.example .env
vi .env
```

3. 初始化安装

```shell
sh ./docker/install.sh
```

5. php容器环境中安装composer相关扩展包及项目代码初始化

> 如果安装"laravel/envoy"过程中失败请切换下全局镜像源,进行尝试

    - 腾讯云composer镜像源:https://mirrors.cloud.tencent.com/composer
    - 阿里云composer镜像源:https://mirrors.aliyun.com/composer
    - 华为云composer镜像源:https://mirrors.huaweicloud.com/repository/php
    - laravel(中国)composer镜像源:https://packagist.laravel-china.org
    - phpcomposer:https://packagist.phpcomposer.com

```shell
docker-compose run --rm php composer config -g repo.packagist composer https://mirrors.cloud.tencent.com/composer #设置镜像源
docker-compose run --rm php composer global require laravel/envoy -vvv #该命令出错了请切换镜像源
docker-compose run --rm php composer global dump-autoload
docker-compose run --rm node cnpm install #前端编译扩展包安装
docker-compose run --rm node npm run prod #编译前端页面js
docker-compose run --rm php chmod u+x docker/php/run.sh #启动命令添加执行权限
docker-compose run --rm php envoy run init --branch=master #项目初始化
docker-compose up -d #启动服务
```

6. [解决扩展包mrgoon/aliyun-sms自动加载问题](/aliyun_sms.md "解决扩展包mrgoon/aliyun-sms自动加载问题")

7. 访问

本地开发环境绑定hosts后就可以进行访问了

```
127.0.0.1 local.laraveladmin.cn
```

8. 开发环境前端实时编译启动

```shell
docker-compose run --rm node npm run watch
```

9. 代码更新升级

```shell
winpty docker-compose exec php envoy run update --branch=master
```



#### 使用说明

1. [官网及相关文档: https://www.laraveladmin.cn](https://www.laraveladmin.cn)

2. [在线示例演示环境: https://demo.laraveladmin.cn](https://demo.laraveladmin.cn)

用户名:demo_admin
    
密码:admin123456

#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request
