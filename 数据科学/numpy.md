**numpy学习笔记**
---

## 1.1 生成数组

```py
import numpy as np
import random

# 生成数组，默认numpy.ndarray类型
print('===========t1==============')
t1 = np.array([1,2,3])
print(t1)
print(type(t1))

# np.arange(star,stop,step=1,dtype=None)
print('===========t2==============')
t2 = np.arange(0,10,2,dtype = 'int8')
print(t2)
print(type(t2)) # 数组的类名
print(t2.dtype) # 元素的类型

# 生成小数 np.round([],weishu)四舍五入保留多少位小数; 
print('===========t3==============')
t3 = np.round([random.random() for i in range(10)],2)
print(t3)
print(t3.dtype)
```

## 1.2生成矩阵


## 1.3 改变矩阵形状 reshape()


## 1.4 转置 t.transpose()

## 1.5 numpy的三元表达式
小于10的设为2，否则为5
np.where(t<10, 2, 5) 

## 1.6 clip 裁剪
小于10的替换为10，大于18的替换为18
t.clip(10, 18)

## 1.7 astype()改变数据类型
改为浮点型
t.astype(float)

## 1.8 数组拼接
将t1和t2进行垂直拼接
np.vstack(t1, t2)


将t1和t2进行水平拼接
np.hstack(t1, t2)

## 1.9 全为0、全为1的矩阵，单位方阵
元素全为1的3*4矩阵
np.ones((3,4))
元素全为0的2*4矩阵
np.zeros((2,4))
对角线为1的5*5的方阵
np.eye(5)

## 1.10 获取最大值、最小值的位置
axis=0表示行与行之间比较即列最大值，axis=1表示列与列之间比较即行最大值

np.argmax(t, axis = 0)
np.argmin(t, axis = 1)

## 1.11 矩阵赋值
表示将矩阵t中为1的元素，改为-1
t[t == 1] = -1

## 1.12 复制
a=b 完全不复制，a和b相互影响；
a = b[:],视图的操作，一种切片，会创建新的对象a，但是a的数据完全由b保管，他们两个的数据变化是一致的，相互影响；
a = b.copy(),复制，a和b互不影响


## 1.13 相乘函数
np.multiply(x1, x2) 
表示x1和x2相乘


## 1.14 log值
np.log(x)
表示计算x的log值

## 1.15 np.pad()填充
语法结构：
```py
pad(array, pad_width, mode, **kwargs)

# 返回值：数组
```

卷积网络中常用到padding
```py
np.pad(arr3D, ((0, 0), (1, 1), (2, 2)), 'constant')
```
参考博客 https://blog.csdn.net/zenghaitao0128/article/details/78713663?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase

## 1.16 np.random.permutation()
https://blog.csdn.net/weixin_44188264/article/details/93752505

## 1.17 numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)
在指定的间隔内返回均匀间隔的数字。返回num个均匀分布的样本，在[start, stop]
> 常用参数
 numpy.linspace(start, stop, num=50, dtype=None)

## 1.18 np.sin(a)
- a为ndarray对象: np.sin(a) 对矩阵a中每个元素取正弦
- a是单个数据值: np.sin(a) 对a元素取正弦








# python中axis=0 axis=1的理解
首先请看一下官方帮助的解释：
__轴用来为超过一维的数组定义的属性，二维数据拥有两个轴：第0轴沿着行的垂直往下，第1轴沿着列的方向水平延伸。__
注意看，官方对于0和1的解释是轴，也就是坐标轴。而坐标轴是有方向的，所以千万不要用行和列的思维去想axis，因为行和列是没有方向的，这样想会在遇到不同的例子时感到困惑。

 
根据官方的说法，1表示横轴，方向从左到右；0表示纵轴，方向从上到下。当axis=1时，数组的变化是横向的，而体现出来的是列的增加或者减少。

 
其实axis的重点在于方向，而不是行和列。具体到各种用法而言也是如此。当axis=1时，如果是求平均，那么是从左到右横向求平均；如果是拼接，那么也是左右横向拼接；如果是drop，那么也是横向发生变化，体现为列的减少。

当考虑了方向，即axis=1为横向，axis=0为纵向，而不是行和列，那么所有的例子就都统一了。

博客解释很到位:https://blog.csdn.net/weixin_37821353/article/details/88367211  

data.shape
