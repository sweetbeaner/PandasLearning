# DataFrame

DataFrame是Pandas用来表示高阶数据的数据结构

一般用于表示矩阵，既有行索引又有列索引

数据存储一个以上的二维块，而不是字典、列表或其他一维数组

可以采用分层索引表示更高维度的数据

## 声明（创建）
### 用ndarray或Python字典构建
#### 1.python字典

    data = {'姓名':['张三','李四','王五','赵六'],'年龄':[17,28,19,20],'性别':['男','男','女','男']}
    frame = pd.DataFrame(data)
    
可以通过构造函数的参数指定属性顺序

    pd.DataFrame(data,columns=['性别','年龄','姓名'])
    
如果指定的colum没有在data中，则会出现缺失值

    frame = pd.DataFrame(data,columns=['性别','年龄','姓名','身高'])
    
       性别	年龄	姓名	身高
    0	男	17	张三	NaN
    1	男	28	李四	NaN
    2	女	19	王五	NaN
    3	男	20	赵六	NaN
    
#### 2.ndarray

    ndarray = np.random.randn(3,3)
    frame1 = pd.DataFrame(ndarray)

pandas会自动分配索引，并按默认顺序排序

#### 3.字典嵌套字典
外层字典为列，内层字典为行元素

#### 4.利用Series构造Frame
可以取现成的series构造新的Frame
    
## 操作

### 1.取前5行数据

    frame.head()

### 2.取列的名称
    
    frame.columns
    
    Index(['性别', '年龄', '姓名', '身高'], dtype='object')
    
   
### 3.按列检索
    frame['姓名']
    
### 4.按行检索
    frame.loc[index]
    
### 5.给某一列赋值
给列赋值时

列表或ndarray的长度必须与列的长度匹配

用Series给DataFrame赋值时，DataFrame的行会与Series的Index相匹配

    frame['身高'] = np.arange(4.0)
    
返回为Series对象，Series的Name属性为列名

    high = pd.Series([1.7,1.8,1.6],index = [0,1,2])
    frame['身高']=high
    
若此时index未指定，则默认为NaN值

如果被赋值的列不存在，则会自动生成一个新列

    weight = pd.Series([56,80,55,70],index = [0,1,2,3])
    frame['体重']=weight
    
结果
      性别	年龄	姓名	身高	体重
    0	男	17	张三	1.7	56
    1	男	28	李四	1.8	80
    2	女	19	王五	1.6	55
    3	男	20	赵六	NaN	70

### 6.删除某一列

    del frame['是否超重']

### 7.Frame的转置

  frame.T


### 8.Frame的index和列的name

    frame.index.name = '编号'
    frame.columns.name = '属性'

### 9.获取Frame的值
    
    frame.values

## 特性

### 1.对Frame对象的列Series是视图

对选取的Frame对象的列构成的Series的操作是会修改Frame内容的，如果需要拷贝，应该使用copy方法

    ser6 = frame['姓名'].copy()

### 2.
