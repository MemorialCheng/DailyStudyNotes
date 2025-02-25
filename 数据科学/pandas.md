pandas学习笔记
---

## 1.1 常用函数
t.index()

t.columns()

t.values()

t.dtypes()

t.ndim()
<img src="https://github.com/MemorialCheng/EverybodyEveryday/blob/master/数据科学/images/pandas01.png" width = "500">

通过标签获取数据
t.loc(["A":"C"],["name","mobile"])

通过位置获取数据
t.iloc([1:3],[2,4])

## 1.2 pandas之字符串方法

t.dropna(axis=0,how="any",inplace=True)

填充NaN空值为0
t.fillna(0)

替换NaN空值为平均值
t.fillna(t.mean())

替换"age"列为空NaN值为平均值，并保存至t["age"]列
t["age"] = t["age"].fillna(t["age"].mean())


### insert插入函数

data.insert(0, 'One', 1)

参数说明：0，表示在0列位置插入; 'One'表示插入的这一列命为One; 1 表示插入的值。

### 转换为数组
在我们读取一些excel/csv文件的数据后，在训练模型之前经常要对数据进行数组转化。很多时候取得的数据是DataFrame的形式，这个时候要记得转换成数组
```py
eg.1
x = datas.iloc[:,:].as_matrix()
```
当然这个方法已经快要被淘汰了，会出现如下的警告

FutureWarning: Method .as_matrix will be removed in a future version. Use .values instead.

__可以用values__
```py
x = datas.iloc[:,:].values  # 注意values后没有括号
```
__astype() 转换array中元素数据类型__
```py
# 好像也可以转换为数组类型
array = np.array(df).astype(float)
```



# pandas中isin()函数及其逆函数使用
删选过滤掉DataFrame中一些行
https://blog.csdn.net/lzw2016/article/details/80472649

# pandas重置DataFrame或Series的索引index--reset_index()
https://blog.csdn.net/qq_36523839/article/details/80640139

# DataFrame常见操作
https://www.cnblogs.com/lantingg/p/8280143.html
df = df.drop([16,17])

# 正则化
w前面加了反斜杠，是\w,与[a-zA-Z0-9_]等价，

# pandas打乱数据,划分数据集
https://blog.csdn.net/qq_33187136/article/details/105413899

# dataframe
行数:len(df), df.shape[0]
列数:df.shape[1]

## 添加一列/一行
### 添加列
- df["name"] = ["Tom", "Jerry"]

### 添加行
