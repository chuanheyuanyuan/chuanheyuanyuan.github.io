---
layout: post
title: 使用kolla构造openstack镜像
description: 熟悉这个过程，方便DIY
category: work
music-url: //music.163.com/style/swf/widget.swf?sid=29572804&type=2&auto=1&width=278&height=32
---
## 环境准备
### 安装yum源
```
yum install -y epel-release 
```

### 安装pip
```
yum install -y python-pip
```

### 安装依赖包
···
yum install -y python-devel libffi-devel openssl-devel gcc python-setuptools git 
···

## 开始安装
### 从github上拉取kolla
```
git clone https://github.com/openstack/kolla
```

### 生成kolla-build.conf
```
pip install tox
tox -e genconfig
```
注意几点：
- 执行完以上动作，会在./etc/kolla下生成一个kolla-build.conf的文件
- 这个动作是执行了koll/common/config.py文件，如果想改变kolla-build.conf，可以修改这个py文件
- conf文件中配置build的模式有如下几种

```
[glance-base]
type = url
location = http://tarballs.openstack.org/glance/glance-master.tar.gz

[keystone-base]
type = git
location = https://git.openstack.org/openstack/keystone
reference = stable/mitaka

[heat-base]
type = local
location = /home/kolla/src/heat

[ironic-base]
type = local
location = /tmp/ironic.tar.gz
```


### 安装kolla-build
```
python setup.py build
```

### 执行build
```
python tools/build.py keystone
```



