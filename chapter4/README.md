# NumPy基础：数组和矢量计算  
  
## NumPy的ndarray：一种多维数组对象  
  
### 该对象是一个快速而灵活的大数据集容器  
  
### ndarray是一个通用的同构数据多维容器，也就是说，其中的所有元素必须是相同类型的  
  
### 使用np.array函数创建数组。例子：arr1 = np.array(data1)  
  
### 可以使用zeros,ones,empty创建数组。例子：np.zeros((3, 6))  
  
### arange是Python内置函数range的数组版：np.arange(5) -->array([ 0, 1, 2, 3, 4])  
  
### 可以用dtype来确认数组类型，用astype来改变数组类型  
  
## NumPy数组的运算  
  
### 大小相等的数组之间的任何算术运算都会将运算  
  
应用到元素级  
  
## 基本的索引和切片  
  
### 跟列表最重要的区别在于，数组切片是原始数组的视图。这意味着数据不会被复制，视图上的任何修改都会直接反映到源数组上  
  
### 如果你想要得到的是ndarray切片的一份副本而非视图，就需要明确地进行复制操作，例如arr[5:8].copy()。  
  
### 索引时轴0作为行，轴1作为列  
  
### 布尔型索引  
  
* a = array([ True, False, False, True, False, False, False],  
    dtype=bool)。data[a]  
  
* Python关键字and和or在布尔型数组中无效。要使用&与|。  
  
### 花式索引  
  
## 数组转置和轴对换  
  
### 转置是重塑的一种特殊形式，它返回的是源数据的视图（不会进行任何复制操作）  
  
### T属性：arr.T  
  
### transpose方法：对于高维数组，transpose需要得到一个由轴编号组成的元组才能对这些轴进行转置。例子：arr.transpose((1, 0, 2))  
  
### swapaxes方法：arr.swapaxes(1, 2)#交换轴  
  
## 通用函数：快速的元素级数组函数  
  
### 通用函数（即ufunc）是一种对ndarray中的数据执行元素级运算的函数  
  
### 一元通用函数。如：np.sqrt(arr)，np.exp(arr)  
  
### 二元通用函数。如add或maximum  
  
### modf函数：它会返回浮点数数组的小数和整数部分：。例子：a,b = np.modf(arr)。a为小数部分，b为整数部分  
  
### 其他相关ufunc。见P138表4-3，4-4  
  
## 利用数组进行数据处理  
  
### np.meshgrid函数接受两个一维数组，并产生两个二维矩阵（对应于两个数组中所有的(x,y)对）：生成相应的采样点  
  
### 将条件逻辑表述为数组运算  
  
* numpy.where函数是三元表达式x if condition else y的矢量化版本：例子：result = np.where(cond, xarr, yarr)  
  
### 数学和统计方法  
  
* arr.mean()或者np.mean(arr)#求均值  
    * mean和sum这类的函数可以接受一个axis选项参数，用于计算该轴向上的统计值，最终结果是一个少一维的数组：arr.mean(axis=1)，arr.sum(axis=0)  
* arr.sum()或者np.sum(arr)#求和  
* 累加cumsum方法：例子：arr.cumsum()-->array([ 0, 1, 3, 6, 10, 15, 21, 28])  
* 累积cumprod方法（与累加相似）  
  
### 用于布尔型数组的方法  
  
* 在上面这些方法中，布尔值会被强制转换为1（True）和0（False）  
* any方法和all方法：any用于测试数组中是  
    否存在一个或多个True，而all则检查数组中所有值是否都是True  
  
### 排序  
  
* arr.sort()多维数组可以在任何一个轴向上进行排序，只需将轴编号传给sort即可：arr.sort(1)  
* 顶级方法np.sort返回的是数组的已排序副本，而就地排序则会修改数组本身  
  
## 唯一化以及其它的集合逻辑  
  
### np.unique函数，用于找出数组中的唯一值并返回已排序的结果。例子：np.unique(names)  
  
### np.inld函数，用于测试一个数组中的值在另一个数组中的成员资格，返回一个布尔型数组。例子：values = np.array([6, 0, 0, 3, 2, 5, 6])，np.in1d(values, [2, 3, 6])-->array([ True, False, False, True, True, False, True],dtype=bool)  
  
### NumPy中的集合函数请参见P146表4-6  
  
## 用于数组的文件输入输出  
  
## 线性代数  
  
### dot函数(点积)：x.dot(y)等价于np.dot(x, y)  
  
### numpy.linalg函数：相关常用函数见P153表4-7  
  
## 伪随机数生成  
  
### numpy.random模块。用于高效生成多种概率分布的样本值的函数  
  
* 生成正态分布：samples = np.random.normal(size=(4, 4))  
* P155表4-8列出了部分numpy.random函数  
  
### 你可以用NumPy的np.random.seed更改随机数生成种子  
  
* 例子：np.random.seed(1234)  
  
## 示例：随机漫步  
  
### argmax返回的是该布尔型数组第一个最大值的索引（True就是最大值）。例子：(np.abs(walk) >= 10).argmax()  
  
### 一次模拟多个随机漫步  
  
