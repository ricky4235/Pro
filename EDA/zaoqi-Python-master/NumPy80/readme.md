
## 前言
大家好，NumPy进阶修改80题现在已经全部更新完毕，80道习题涵盖了NumPy中数组**创建、访问、筛选、修改、计算**等常用操作，如果不熟悉NumPy的读者可以刷一遍，因为里面的代码大多拿走就能用，所以如果你已经了解NumPy的基本操作，我更建议将这80题**当成速查手册**使用，随用随查！本文共分为两个部分：

- 完整版NumPy80题
- Notebook版下载方式

## 完整版80题

### 1.导入并查看NumPy版本


```python
import numpy as np
print(np.__version__)
```

    1.15.4


### 2.创建十个全为0的一维数组


```python
np.zeros(10)
```




    array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])



### 3.创建10个全为0的一维数据并修改数据类型为整数


```python
np.zeros(10,dtype = 'int')
```




    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])



### 4.创建20个0-100固定步长的数


```python
np.arange(0,100,5)
```




    array([ 0,  5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80,
           85, 90, 95])



### 5.从list创建数组


```python
List = [1,2,3,4,5,6,7,8,9]
result = np.array(List)
result
```




    array([1, 2, 3, 4, 5, 6, 7, 8, 9])



### 6.创建一个三行三列全是1的矩阵


```python
#方法1
np.ones((3,3))
#方法2
np.array([[ 1., 1., 1.],
       [ 1., 1., 1.],
       [ 1., 1., 1.]])
```




    array([[1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.]])



### 7.创建一个2行2列矩阵并且元素为布尔类型的True


```python
np.full((2,2), True, dtype=bool)
```




    array([[ True,  True],
           [ True,  True]])



### 8.创建等差数列
备注：从5开始，50结束，共10个数据


```python
np.linspace(start=5,stop=50,num=10)
```




    array([ 5., 10., 15., 20., 25., 30., 35., 40., 45., 50.])



### 9.创建等差数列
备注：从5开始，50结束，共10个数据，数据类型为int32
思考：与上一题不同


```python
np.arange(start = 5, stop = 55, step = 5,dtype = 'int32')
```




    array([ 5, 10, 15, 20, 25, 30, 35, 40, 45, 50], dtype=int32)



### 10.创建3x3矩阵
备注：矩阵元素均为0—10之间的随机数


```python
np.random.randint(0,10,(3,3))
```




    array([[9, 8, 2],
           [5, 1, 1],
           [6, 0, 3]])



### 11.创建3x3矩阵
备注：矩阵元素均为服从标准正态分布的随机数


```python
np.random.randn(3, 3)
```




    array([[-1.82084149,  1.57679054, -0.28167398],
           [ 0.78497073,  1.08230743,  0.66150165],
           [-1.32122518, -0.50510931,  0.55786583]])



### 12.将第五题的result修改为3x3矩阵


```python
result = result.reshape(3,3)
```

### 13.对上一题生成的result取转置


```python
result.T
```




    array([[1, 4, 7],
           [2, 5, 8],
           [3, 6, 9]])



### 14.查看result的数据类型


```python
result.dtype
#dtype('int64')
```




    dtype('int64')



### 15.查看result的内存占用


```python
#方法一：直接查看
print(result.nbytes)
#方法2手动计算
print(result.itemsize * 9)
```

    72
    72


### 16.将result的数据类型修改为float


```python
result = result.astype(float)
```

### 17.提取result第三行第三列的元素


```python
result[2,2]
```




    9.0



### 18.将result第三行第三列的元素放大十倍


```python
result[2,2] = result[2,2] * 10
```

### 19.提取result中的所有偶数


```python
result[result % 2 == 0]
```




    array([ 2.,  4.,  6.,  8., 90.])



### 20.将result中所有奇数修改为666


```python
result[result % 2 == 1] = 666
```

## NumPy进阶修炼80题 第二期 ｜基本矩阵操作与运算


```python
import numpy as np
```

### 21.创建主对角线都是5的5x5矩阵


```python
result = np.diag([5,5,5,5,5])
result
```




    array([[5, 0, 0, 0, 0],
           [0, 5, 0, 0, 0],
           [0, 0, 5, 0, 0],
           [0, 0, 0, 5, 0],
           [0, 0, 0, 0, 5]])



### 22.交换第一列与第二列


```python
a = result[:, [1,0,2,3,4]]
```

### 23.交换第一行与第二行


```python
b = result[[0,1,2,4,3], :]
```

### 24.判断两个矩阵是否有任何元素不同(使用22,23两题得到的矩阵)



```python
print((a == b).all())
```

### 25.计算两个矩阵不同元素的个数(使用22,23两题得到的矩阵)



```python
len(np.argwhere(a != b))
```

### 26.找到两个矩阵不同元素的位置(使用22,23两题得到的矩阵)



```python
np.argwhere(a != b)
```

### 27.矩阵乘法(使用22,23两题得到的矩阵)



```python
np.dot(a,b)
```

### 28.矩阵对应元素相乘(使用22,23两题得到的矩阵)



```python
print(np.multiply(a,b))
print('========方法2========')
print(a * b) #方法2
```

### 29.计算行列式(使用21题生成的矩阵)



```python
np.linalg.det(result)
```

### 30.矩阵求逆(使用21题生成的矩阵)



```python
np.linalg.inv(result)
```

### 31.将22与23题生成的np.array对象修改为np.matrix对象



```python
a = np.matrix(a)
b = np.matrix(b)
```

### 32.计算上一题生成的两个np.matrix格式矩阵的对应元素乘积（对比异同）



```python
np.multiply(a,b)
```

### 33.对31题生成的两个np.matrix格式矩阵做矩阵乘法（对比异同）



```python
a * b
```

### 34.将两个矩阵按照行拼接



```python
np.hstack((a,b))
```

### 35.将两个矩阵按照列拼接



```python
np.vstack((a,b))
```

### 36.思考下面代码运行后new的结果



```python
new = np.pad(result,pad_width = 1,constant_values=1)
```

### 37.找到new中大于1的元素的位置



```python
np.argwhere(new > 1)
```

### 38.将new中大于1的元素修改为9



```python
new[new > 1] = 8
new
```

### 39.对new按列求和



```python
np.sum(new, 0)
```

### 40.对new按行求和



```python
np.sum(new, 1)
```

## NumPy进阶修炼第三期｜41-60


```python
import numpy as np
import pandas as pd
import warnings
warnings.filterwarnings("ignore")
```

### 41 生成指定格式数据
备注：使用numpy生成6行6列的二维数组，值为1-100随机数


```python
data = np.random.randint(1,100, [6,6])
data
```




    array([[28, 77, 35, 79, 44, 93],
           [33, 51, 56, 56, 73, 56],
           [53, 44, 73, 63, 29, 71],
           [25, 90, 87, 51, 44, 30],
           [50, 39,  7, 29, 83, 89],
           [18,  8, 75, 33, 40, 64]])



### 42 找到每列的最大值


```python
np.amax(data, axis=0)
```




    array([53, 90, 87, 79, 83, 93])



### 43 找到每行的最小值


```python
np.amin(data, axis=1)
```




    array([28, 33, 29, 25,  7,  8])



### 44 提取data每个元素的出现次数


```python
np.unique(data,return_counts=True)
```




    (array([ 7,  8, 18, 25, 28, 29, 30, 33, 35, 39, 40, 44, 50, 51, 53, 56, 63,
            64, 71, 73, 75, 77, 79, 83, 87, 89, 90, 93]),
     array([1, 1, 1, 1, 1, 2, 1, 2, 1, 1, 1, 3, 1, 2, 1, 3, 1, 1, 1, 2, 1, 1,
            1, 1, 1, 1, 1, 1]))



### 45 获取data每行元素的大小排名


```python
data.argsort()
```




    array([[0, 2, 4, 1, 3, 5],
           [0, 1, 2, 3, 5, 4],
           [4, 1, 0, 3, 5, 2],
           [0, 5, 4, 3, 2, 1],
           [2, 3, 1, 0, 4, 5],
           [1, 0, 3, 4, 5, 2]])



### 46 将数组按行重复一次


```python
np.repeat(data, 2, axis=0)
```




    array([[28, 77, 35, 79, 44, 93],
           [28, 77, 35, 79, 44, 93],
           [33, 51, 56, 56, 73, 56],
           [33, 51, 56, 56, 73, 56],
           [53, 44, 73, 63, 29, 71],
           [53, 44, 73, 63, 29, 71],
           [25, 90, 87, 51, 44, 30],
           [25, 90, 87, 51, 44, 30],
           [50, 39,  7, 29, 83, 89],
           [50, 39,  7, 29, 83, 89],
           [18,  8, 75, 33, 40, 64],
           [18,  8, 75, 33, 40, 64]])



### 47 去除数组的重复行


```python
np.unique(data,axis = 0)
```




    array([[18,  8, 75, 33, 40, 64],
           [25, 90, 87, 51, 44, 30],
           [28, 77, 35, 79, 44, 93],
           [33, 51, 56, 56, 73, 56],
           [50, 39,  7, 29, 83, 89],
           [53, 44, 73, 63, 29, 71]])



### 48 不放回抽样
备注：从data的第一行中不放回抽3个元素


```python
np.random.choice(data[0:1][0], 3, replace=False)
```




    array([77, 35, 93])



### 49 提取data第二行中不含第三行的元素的元素


```python
a = data[1:2]
b = data[2:3]
index=np.isin(a,b)
array=a[~index]
array
```




    array([33, 51, 56, 56, 56])



### 50 判断data是否有空行


```python
(~data.any(axis=1)).any()
```




    False



### 51 将每行升序排列


```python
data.sort(axis = 1)
data
```




    array([[28, 35, 44, 77, 79, 93],
           [33, 51, 56, 56, 56, 73],
           [29, 44, 53, 63, 71, 73],
           [25, 30, 44, 51, 87, 90],
           [ 7, 29, 39, 50, 83, 89],
           [ 8, 18, 33, 40, 64, 75]])



### 52 将data的数据格式修改为float


```python
data1 = data.astype(float)
```

### 53 将小于5的元素修改为nan


```python
data1[data1 < 5] = np.nan
data1
```




    array([[nan, 35., 44., 77., 79., 93.],
           [33., 51., 56., 56., 56., 73.],
           [29., 44., 53., 63., 71., 73.],
           [25., 30., 44., 51., 87., 90.],
           [ 7., 29., 39., 50., 83., 89.],
           [ 8., 18., 33., 40., 64., 75.]])



### 54 删除data1含有nan的行


```python
data1 = data1[~np.isnan(data1).any(axis=1), :]
```


```python
data1
```




    array([[33., 51., 56., 56., 56., 73.],
           [29., 44., 53., 63., 71., 73.],
           [25., 30., 44., 51., 87., 90.],
           [ 7., 29., 39., 50., 83., 89.],
           [ 8., 18., 33., 40., 64., 75.]])



### 55 找出data1第一行出现频率最高的值


```python
vals, counts = np.unique(data1[0,:], return_counts=True)
print(vals[np.argmax(counts)])
```

    56.0


### 56 找到data1中与100最接近的数字


```python
a = 100
data1.flat[np.abs(data1 - a).argmin()]
```




    90.0



### 57 data1每一行的元素减去每一行的平均值


```python
data1 - data1.mean(axis=1, keepdims=True)
```




    array([[-21.16666667,  -3.16666667,   1.83333333,   1.83333333,
              1.83333333,  18.83333333],
           [-26.5       , -11.5       ,  -2.5       ,   7.5       ,
             15.5       ,  17.5       ],
           [-29.5       , -24.5       , -10.5       ,  -3.5       ,
             32.5       ,  35.5       ],
           [-42.5       , -20.5       , -10.5       ,   0.5       ,
             33.5       ,  39.5       ],
           [-31.66666667, -21.66666667,  -6.66666667,   0.33333333,
             24.33333333,  35.33333333]])



### 58 将data1归一化至区间[0,1]


```python
a = np.max(data1) - np.min(data1)
(data1 - np.min(data1)) / a
```




    array([[0.31325301, 0.53012048, 0.59036145, 0.59036145, 0.59036145,
            0.79518072],
           [0.26506024, 0.44578313, 0.55421687, 0.6746988 , 0.77108434,
            0.79518072],
           [0.21686747, 0.27710843, 0.44578313, 0.53012048, 0.96385542,
            1.        ],
           [0.        , 0.26506024, 0.38554217, 0.51807229, 0.91566265,
            0.98795181],
           [0.01204819, 0.13253012, 0.31325301, 0.39759036, 0.68674699,
            0.81927711]])



### 59  将data1标准化


```python
mu = np.mean(data1, axis=0)
sigma = np.std(data1, axis=0)
(data1 - mu) / sigma
```




    array([[ 1.16268622,  1.41802672,  1.2856926 ,  0.52888589, -1.40282088,
            -0.89773106],
           [ 0.79357948,  0.82006364,  0.93504916,  1.45443618, -0.10391266,
            -0.89773106],
           [ 0.42447275, -0.3758625 , -0.11688115, -0.13222147,  1.28158945,
             1.28247294],
           [-1.23650756, -0.4612858 , -0.70128687, -0.26444294,  0.93521392,
             1.15422565],
           [-1.14423088, -1.40094206, -1.40257375, -1.58665766, -0.71006983,
            -0.64123647]])



### 60 将data1存储至本地


```python
np.savetxt('test.txt',data1)
```

## NumPy进阶修炼第四期｜NumPy最后二十问


```python
import numpy as np
import pandas as pd
import warnings
warnings.filterwarnings("ignore")
```

### 61.如何获得两个数组之间的相同元素
输入:

arr1 = np.random.randint(10,6,6)

arr2 = np.random.randint(10,6,6)


```python
arr1 = np.random.randint(1,10,10)
arr2 = np.random.randint(1,10,10)
```


```python
print("arr1: %s"%arr1)
print("arr2: %s"%arr2)
np.intersect1d(arr1,arr2)
```

    arr1: [9 4 1 4 9 9 8 5 3 1]
    arr2: [1 5 8 7 9 2 6 9 1 2]





    array([1, 5, 8, 9])



### 62.如何从一个数组中删除另一个数组存在的元素
输入:

arr1 = np.random.randint(1,10,10)

arr2 = np.random.randint(1,10,10)


```python
arr1 = np.random.randint(1,10,10)
arr2 = np.random.randint(1,10,10)
print("arr1: %s"%arr1)
print("arr2: %s"%arr2)
np.setdiff1d(arr1,arr2)
```

    arr1: [3 3 2 6 6 1 4 6 2 2]
    arr2: [3 3 2 6 8 8 5 2 4 7]





    array([1])



### 63.如何修改一个数组为只读模式
输入:

arr1 = np.random.randint(1,10,10)


```python
arr1 = np.random.randint(1,10,10)
arr1.flags.writeable = False
```


```python
#尝试修改会报错！
arr1[0] = 6
```


    ---------------------------------------------------------------------------
    
    ValueError                                Traceback (most recent call last)
    
    <ipython-input-31-ddcf305e5efb> in <module>
          1 #尝试修改会报错！
    ----> 2 arr1[0] = 6


    ValueError: assignment destination is read-only


### 64.如何将list转为numpy数组
输入:

a = [1,2,3,4,5]


```python
a = [1,2,3,4,5]
np.array(a)
```




    array([1, 2, 3, 4, 5])



### 65.如何将pd.DataFrame转为numpy数组
输入:

df = pd.DataFrame({'A':[1,2,3],'B':[4,5,6],'C':[7,8,9]})


```python
df = pd.DataFrame({'A':[1,2,3],'B':[4,5,6],'C':[7,8,9]})
print(df)
print(df.values)
```

       A  B  C
    0  1  4  7
    1  2  5  8
    2  3  6  9
    [[1 4 7]
     [2 5 8]
     [3 6 9]]


### 66.如何使用numpy进行描述性统计分析
输入：

arr1 = np.random.randint(1,10,10)

arr2 = np.random.randint(1,10,10)


```python
arr1 = np.random.randint(1,10,10)
arr2 = np.random.randint(1,10,10)

print("arr1的平均数为:%s" %np.mean(arr1))
print("arr1的中位数为:%s" %np.median(arr1))
print("arr1的方差为:%s" %np.var(arr1))
print("arr1的标准差为:%s" %np.std(arr1))
print("arr1,arr的相关性矩阵为:%s" %np.cov(arr1,arr2))
print("arr1,arr的协方差矩阵为:%s" %np.corrcoef(arr1,arr2))
```

    arr1的平均数为:5.2
    arr1的中位数为:5.0
    arr1的方差为:6.56
    arr1的标准差为:2.5612496949731396
    arr1,arr的相关性矩阵为:[[7.28888889 2.6       ]
     [2.6        7.12222222]]
    arr1,arr的协方差矩阵为:[[1.         0.36085682]
     [0.36085682 1.        ]]


### 67.如何使用numpy进行概率抽样
输入：

arr = np.array([1,2,3,4,5])


```python
arr = np.array([1,2,3,4,5])
np.random.choice(arr,10,p = [0.1,0.1,0.1,0.1,0.6])
```




    array([2, 5, 5, 5, 5, 4, 1, 5, 5, 5])



### 68.如何创建副本
输入：

arr = np.array([1,2,3,4,5])


```python
#对副本数据进行修改，不会影响到原始数据
arr = np.array([1,2,3,4,5])
arr1 = arr.copy()
```

### 69.如何对数组切片
输入:
arr = np.arange(10)

备注：从索引2开始到索引8停止，间隔为2


```python
arr = np.arange(10)
a = slice(2,8,2)
arr[a] #等价于arr[2:8:2]
```




    array([2, 4, 6])



### 70.如何使用NumPy操作字符串
输入:

str1 = ['I love']

str2 = [' Python']


```python
#拼接字符串
str1 = ['I love']
str2 = [' Python']
print(np.char.add(str1,str2))

#大写首字母
str3 = np.char.add(str1,str2)
print(np.char.title(str3))
```

    ['I love Python']
    ['I Love Python']


### 71.如何对数据向上/下取整
输入:

arr = np.random.uniform(0,10,10)


```python
arr = np.random.uniform(0,10,10)
print(arr)
###向上取整
print(np.ceil(arr))
###向下取整
print(np.floor(arr) )
```

    [3.69853424 2.37607144 2.75296734 3.98645188 9.8325098  9.78061437
     1.05052842 6.93954312 3.74869061 0.89292687]
    [ 4.  3.  3.  4. 10. 10.  2.  7.  4.  1.]
    [3. 2. 2. 3. 9. 9. 1. 6. 3. 0.]


### 72.如何取消默认科学计数显示数据


```python
np.set_printoptions(suppress=True)
```

### 73.如何使用NumPy对二维数组逆序
输入：

arr = np.random.randint(1,10,[3,3])


```python
arr = np.random.randint(1,10,[3,3])
print(arr)
print('列逆序')
print(arr[:, -1::-1])
print('行逆序')
print(arr[-1::-1, :])
```

    [[5 6 2]
     [1 6 9]
     [2 7 5]]
    列逆序
    [[2 6 5]
     [9 6 1]
     [5 7 2]]
    行逆序
    [[2 7 5]
     [1 6 9]
     [5 6 2]]


### 74.如何使用NumPy根据位置查找元素
输入：

arr1 = np.random.randint(1,10,5)

arr2 = np.random.randint(1,20,10)

备注：在arr2中根据arr1中元素以位置查找


```python
arr1 = np.random.randint(1,10,5)
arr2 = np.random.randint(1,20,10)
print(arr1)
print(arr2)
print(np.take(arr2,arr1))
```

    [4 9 3 7 9]
    [ 1  3 14  5 13 15 16  6  1  6]
    [13  6  5  6  6]


### 75.如何使用numpy求余数
输入：

a = 10

b = 3


```python
np.mod(a,b)
```




    1



### 76.如何使用NumPy进行矩阵SVD分解
输入：

A = np.random.randint(1,10,[3,3])


```python
np.linalg.svd(A)
```




    (array([[-0.53080534, -0.05856788, -0.84546762],
            [-0.50084903, -0.7830816 ,  0.36869155],
            [-0.68366361,  0.61915508,  0.38633023]]),
     array([15.54841031,  7.33950585,  1.54226802]),
     array([[-0.54854452, -0.50684335, -0.66498777],
            [-0.83142704,  0.24649305,  0.49796612],
            [-0.08847596,  0.82604539, -0.55661568]]))



### 77.如何使用NumPy多条件筛选数据
输入：

arr = np.random.randint(1,20,10)


```python
arr = np.random.randint(1,20,10)
print(arr[(arr>1)&(arr<7)&(arr%2==0)])
```

    [6 4]


### 78.如何使用NumPy对数组分类
输入：

arr = np.random.randint(1,20,10)

备注：将大于等于7，或小于3的元素标记为1，其余为0


```python
arr = np.random.randint(1,20,10)
print(arr)
print(np.piecewise(arr, [arr < 3, arr >= 7], [-1, 1]))
```

    [ 8 19 16  1  4  7 12  1 16  1]
    [ 1  1  1 -1  0  1  1 -1  1 -1]


### 79如何使用NumPy压缩矩阵
输入：

arr = np.random.randint(1,10,[3,1])

备注：从数组的形状中删除单维度条目，即把shape中为1的维度去掉


```python
arr = np.random.randint(1,10,[3,1])
print(arr)
print(np.squeeze(arr))
```

    [[3]
     [8]
     [5]]
    [3 8 5]


### 80.如何使用numpy求解线性方程组
输入：

A = np.array([[1, 2, 3], [2, -1, 1], [3, 0, -1]])

b = np.array([9, 8, 3])

求解Ax = b


```python
A = np.array([[1, 2, 3], [2, -1, 1], [3, 0, -1]])
b = np.array([9, 8, 3])
x = np.linalg.solve(A, b)
print(x)
```

    [ 2. -1.  3.]

## 下载方式

为了让各位读者更方便的刷题，我已经将NumPy80题整理在Notebook中，共分为两个版本，一份**无答案版**可以用来刷题👇

![img](https://mmbiz.qpic.cn/mmbiz_png/2GcSFhuAFlCqaicMUNJg7UMj6RBerrWiacbhMLMzq6dpjxicwnGbnP4U27BfCClc786gELZjiaMvesN0fWWiaQsdvWA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![img](https://mmbiz.qpic.cn/mmbiz_png/2GcSFhuAFlCqaicMUNJg7UMj6RBerrWiac0NzPALfWMRlasLibF3FsKoDrqVqwhmdWQicB6Q4icvyoM3ecMPTYe51pg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

一份**有答案版本**用来参考学习👇

![img](https://mmbiz.qpic.cn/mmbiz_png/2GcSFhuAFlCqaicMUNJg7UMj6RBerrWiacAzuFfVwniczUgE993HZPQUSgibp63Vo9Tz74DvJPxS9RekFRSbgJzZyQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![img](https://mmbiz.qpic.cn/mmbiz_png/2GcSFhuAFlCqaicMUNJg7UMj6RBerrWiacRzb2AFwg0OEnbqvx9gO3l9XUUwZpPwIkrkfg7bJ427S0us5ho9Rib9w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

大家可以在我的GitHub中下载(https://github.com/liuhuanshuo/zaoqi-Python/tree/master/NumPy80)，因为我每题仅给出一种解法，因此在刷题过程中也应该思考**是否有不一样/更高效的方法**，结合[**Pandas120题**](http://mp.weixin.qq.com/s?__biz=MzI1MTUyMjc1Mg==&mid=2247485328&idx=3&sn=1d9d0556409ad9ef8f1ec6eacb1b6c51&chksm=e9f0fc3fde877529e4b520fab357adbcd0aa6ac0fe765c980bc3a3111c1db5e5b59188cb9be6&scene=21#wechat_redirect)使用更是威力无穷！另外Python数据可视化同款专题正在准备中，敬请期待！