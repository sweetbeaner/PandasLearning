Series和DataFrame是Pandas最常用的数据结构
# Series

一维数组型对象，包含了值Value和数据标签Index

类似一个包含了索引值的字典

## 声明(创建)
### 用列表简单创建
    
    obj = pd.Series(list)
    
索引在左边，值在右边

    pd.Series(['猩猩','鸭鸭','甜豆'])
    
    0    猩猩
    1    鸭鸭
    2    甜豆
    dtype: object

### 传入标签标识参数创建

    pd.Series(['猩猩','鸭鸭','甜豆'], index=['dad','mum','baby'])
    
运行结果

    dad     猩猩
    mum     鸭鸭
    baby    甜豆
    dtype: object
    
### 通过字典生成series
    dict = {'dad':'猩猩','mum':'鸭鸭','baby':'甜豆'}
    pd.series(dict)

### 通过指定index顺序生成series
    indexs = ['baby','mum','dad','friend']
    dict = {'dad':'猩猩','mum':'鸭鸭','baby':'甜豆'}
    ser3 = pd.Series(dict,index = indexs)

缺失值由NaN来来表示，可以用is null和not null来进行判断

    pd.isnull(series)
    
返回一个bool的series
    


## 操作
可以进行bool过滤、计算、或者应用数学函数，索引保持不变
### 计算
    series*n
### bool过滤
    series[series>n]
### 数学函数
    np.exp(series)
### 判断是否存在某个index
类似python字典的操作

    'baby' in series
    
### 修改index
按位置修改index

    ser3.index= ['孩子','妈妈','爸爸','朋友']

## 特性

### 对齐索引特性

对多个series进行操作的时候可以自动对其索引，类似数据库中的join操作

    indexs = ['a','b','c','d']
    ser5=pd.Series([1,2,3,4],index = indexs)
    ser6=pd.Series([4,3,2,1],index = indexs)
    ser5+ser6
    
运行结果
    
    a    5
    b    5
    c    5
    d    5
    dtype: int64
    
### Series对象和index的name属性
每个series对象都可以赋予name属性

    series.name='home'
    series.index.name = 'state'
    
