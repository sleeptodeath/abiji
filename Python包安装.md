## 软件和包安装

### Anaconda3

#### Win10环境安装

官网地址：https://www.anaconda.com/distribution/#download-section

1. 下载exe（如果官网太慢可以用清华源下载）
2. 安装，安装过程中 选择加入环境变量
3. 配置环境变量，如果未加入环境变量，此`我的电脑右键\属性\高级系统设置\环境变量\系统变量\PATH`; 将Anaconda主目录; Anaconda/Script； Anaconda/Library/bin 加入环境变量
4. 验证是否安装成功, 打开cmd,  输入python，conda -V进行测试 

#### conda 命令使用

升级所有包

```
conda upgrade --all
```

⽤ conda update 命令升级指定包：

```
conda update package_name

# 或用 pip install --upgrade package_name
```

查看所有安装包

```
conda list
```

安装python包

```
conda install package_name

# 或用pip install package_name
```

删除python包

```
conda remove package_name
```



##### conda 环境管理

创建环境

```
conda create -n py37 python=3.7

# -n 环境名称
# python=3.7 指定python版本
```

使用activate切换环境(win下是activate)

```
activate py37
```

查看所有环境

```
conda env list
```

删除环境



#### IPython 命令使用

运行文件

```
%run file_name.py
```

给出语句执行时间

```
%time statement
```

查看历史

```
%hist
```



#### Jupyter notebook使用

输入一行Python代，按shift+Enter执行

```

```



#### Numpy	

导入

```
import numpy as np
```

ndarray

> 与list的区别，速度和内存

创建

```
np.array()
```

ndarray对象的属性

```
.ndim
.shape 几行几列
.size 元素个数
.dtype  元素类型
.itemsize 每个元素的大小
```

random库

```
a = np.random.randn()
```
