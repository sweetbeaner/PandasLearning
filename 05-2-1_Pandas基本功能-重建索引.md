# reindex

reindex是pandas的重要方法，用于创建一个符合索引要求的**新对象**
## 方法

    newSer = ser.reindex(list or ndarray)
   
reindex返回一个新的数据数据对象，以参数索引排列

## 插值或填值

对于时间序列等连续的index，需要在重建时提供自动的差值或者填值操作

通过method参数设置ffill或者bffil进行控制

+ ffill:填入前一个的值
+ bfill:填入后一个的值


## DataFrame的列关键字重建索引

reindex函数对于DataFrame的操作可以改变行索引、列索引，也可以同时改变

默认reindex行索引

    df1 = df.reindex(['c','d','b','a'])

    df2 = df.reindex(['c','d','b','a'],columns=['A','B','C','D','E','F'])

## loc索引标签

也可用loc选取更改索引，但是不能自动新增NaN的行列值

    df2.loc[['d','b','a'],['E','F','D']]
