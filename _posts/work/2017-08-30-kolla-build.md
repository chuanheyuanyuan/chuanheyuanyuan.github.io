---
layout: post
title: 测试日志
description: 第一篇日志.
category: work
music-url: //music.163.com/style/swf/widget.swf?sid=29572804&type=2&auto=1&width=278&height=32
---


## 使用kolla构造openstack镜像
### 从github上拉取kolla
```
git clone https://github.com/openstack/kolla
```

###生成kolla-build.conf
```
pip install tox
tox -e genconfig
```
执行完以上动作，会在./etc/kolla下生成一个kolla-build.conf的文件

###安装kolla-build
```
python setup.py build
```

###执行build
```
python tools/build.py keystone
```



