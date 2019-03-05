# pandas入门  
  
## P160：5.1 pandas的数据结构介绍  
  
### Series  
  
* Series是一种类似于一维数组的对象  
* Series的字符串表现形式为：索引在左边，值在右边  
* 使用NumPy函数或类似NumPy的运算  
* Series最重要的一个功能是，它会根据运算的索引标签自动对齐数据  
* Series对象本身及其索引都有一个name属性，该属性跟pandas其他的关键功能关系非常密切  
  
### pandas的isnull和notnull函数可用于检测缺失数据  
  
* pd.isnull(obj4)或者obj4.isnull()  
* pd.notnull(obj4)  
  
### DataFrame  
  
* DataFrame是一个表格型的数据结构  
* 建DataFrame的办法有很多，最常用的一种是直接传入一个由等长列表或NumPy数组组成的字典  
* 对于特别大的DataFrame，head方法会选取前五行。例子：frame.head()  
* 通过类似字典标记的方式或属性的方式，可以将DataFrame的列获取为一个Series：frame2['state']或者frame2.state  
* 列可以通过赋值的方式进行修改  
* 为不存在的列赋值会创建出一个新列。关键字del用于删除列:del frame2['eastern']  
* 如果嵌套字典传给DataFrame，pandas就会被解释为：外层字典的键作为列，内层键则作为行索引  
* P174:表5-1.列出了DataFrame构造函数所能接受的各种数据  
  
### 索引对象  
  
* pandas的索引对象负责管理轴标签和其他元数据（比如轴名称等）。构建Series或DataFrame时，所用到的任何数组或其他序列的标签都会被转换成一个Index  
* Index对象是不可变的，因此用户不能对其进行修改  
* 与python的集合不同，pandas的Index可以包含重复的标签  
* P177表5-2：Index的相关函数和属性  
  
## P178：5.2 基本功能  
  
### 重新索引  
  
* pandas对象的一个重要方法是reindex，其作用是创建一个新对象，它的数据符合新的索引。例子：obj2 = obj.reindex(['a', 'b', 'c', 'd', 'e'])  
* method的ffill选项：method='ffill'  
* 借助DataFrame，reindex可以修改（行）索引和列：frame2 = frame.reindex(['a', 'b', 'c', 'd'])  
* 列可以用columns关键字重新索引：frame.reindex(columns=['Texas', 'Utah', 'California'])  
* P181表5-3列出了reindex函数的各参数及说明  
  
### 丢弃指定轴上的项  
  
* drop方法：丢弃某条轴上的一个或多个项很简单，只要有一个索引数组或列表即可：obj.drop(['d', 'c'])  
* 对于DataFrame，可以删除任意轴上的索引值  
    * 用标签序列调用drop会从行标签（axis 0）删除值：data.drop(['Colorado', 'Ohio'])  
    * 通过传递axis=1或axis='columns'可以删除列的值：data.drop('two', axis=1)  
    * 可以就地修改对象，不会返回新的对象：obj.drop('c', inplace=True)  
        * 小心使用inplace，它会销毁所有被删除的数据  
  
### 索引、选取和过滤  
  
* 利用标签的切片运算与普通的Python切片运算不同，其末端是包含的：obj['b':'c']，输出包含标签为'b'和'c'的内容  
* 用切片可以对Series的相应部分进行设置。obj['b':'c'] = 5  
* 用一个值或序列对DataFrame进行索引其实就是获取一个或多个列  
* 用loc和iloc进行选取  
    * 可以使用轴标签（loc）或整数索引（iloc），从  
        DataFrame选择行和列的子集  
  
        * loc例子：data.loc['Colorado', ['two', 'three']]  
        * iloc例子：data.iloc[2, [3, 0, 1]]  
    * P189表5-4pandas中DataFrame选取和重新组合数据的方法  
* 整数索引：易产生bug或者引起歧义，可以用loc和iloc来进行区分  
  
### 算术运算和数据对齐  
  
* 对于DataFrame，对齐操作会同时发生在行和列上  
* 如果DataFrame对象相加，没有共用的列或行标签，结果都会是空  
* 在算术方法中填充值  
    * fill_value参数。例子：df1.add(df2, fill_value=0)  
    * 与此类似，在对Series或DataFrame重新索引时，也可以指定一个填充值：df1.reindex(columns=df2.columns, fill_value=0)  
* P196表5-5列出了Series和DataFrame的算术方法  
    * 它们每个都有一个副本，以字母r开头，它会翻转参数  
  
### DataFrame和Series之间的运算  
  
* 当我们从arr减去arr[0]，每一行都会执行这个操作。这就叫做广播  
* 默认情况下，DataFrame和Series之间的算术运算会将Series的索引匹配到DataFrame的列，然后沿着行一直向下广播  
* 如果某个索引值在DataFrame的列或Series的索引中找不到，则参与运算的两个对象就会被重新索引以形成并集  
* 如果你希望匹配行且在列上广播，则必须使用算术运算方法。frame.sub(series3, axis='index')  
  
### 函数应用和映射  
  
* NumPy的ufuncs（元素级数组方法）也可用于操作pandas对象。np.abs(frame)  
* DataFrame的apply方法可将函数应用到由各列或行所形成的一维数组上。f = lambda x: x.max() - x.min()。frame.apply(f)  
* 元素级的Python函数也是可以用的，使用applymap即可。format = lambda x: '%.2f' % x。frame.applymap(format)  
    * 之所以叫做applymap，是因为Series有一个用于应用元素级函数的map方法：frame['e'].map(format)  
  
### 排序和排名  
  
* 要对行或列索引进行排序（按字典顺序），可使用sort_index方法：obj.sort_index()  
* 对于DataFrame，则可以根据任意一个轴上的索引进行排序：frame.sort_index(axis=1)  
* 数据默认是按升序排序的，但也可以降序排序：frame.sort_index(axis=1, ascending=False)  
* 若要按值对Series进行排序，可使用其sort_values方法：obj.sort_values()  
    * 在排序时，任何缺失值默认都会被放到Series的末尾  
* 当排序一个DataFrame时，你可能希望根据一个或多个列中的值进行排序。将一个或多个列的名字传递给sort_values的by选项即可达到该目的：frame.sort_values(by=['a', 'b'])  
* 排名会从1开始一直到数组中有效数据的数量。默认情况，rank是通过“为各组分配一个平均排名”的方式破坏平级关系的：obj.rank()  
    * 也可以根据值在原数据中出现的顺序给出排名：obj.rank(method='first')  
* P208表5-6列出了所有用于破坏平级关系的method选项  
  
### 带有重复标签的轴索引  
  
* 索引的is_unique属性可以告诉你它的值是否是唯一的:obj.index.is_unique  
  
## P209:5.3 汇总和计算描述统计  
  
### pandas对象拥有一组常用的数学和统计方法，它们大部分都属于约简和汇总统计。如从Series中提取单个值（如sum或mean）或从DataFrame的行或列中提取一个Series  
  
* P210表5-7列出了这些约简方法的常用选项  
    * axis 约简的轴  
    * skipna 排除缺失值，默认值为True  
    * level  
  
### 有些方法（如idxmin和idxmax）返回的是间接统计（比如达到最小值或最大值的索引）：df.idxmax()  
  
* 按columns获取最大值对应的index：idxmin和idxmax：df.idxmax()  
* 累计型：df.cumsum()  
* 汇总统计：df.describe()  
  
### P212表5-8列出了所有与描述统计相关的方法  
  
### 相关系数与协方差  
  
* Series的corr方法用于计算两个Series中重叠的、非NA的、按索引对齐的值的相关系数。与此类似，cov用于计算协方差  
    * 计算相关系数returns['MSFT'].corr(returns['IBM'])或者returns.MSFT.corr(returns.IBM)  
    * 计算协方差returns['MSFT'].cov(returns['IBM'])  
* DataFrame的corr和cov方法将以DataFrame的形式分别返回完整的相关系数或协方差矩阵  
    * returns.corr()  
    * returns.cov()  
* 利用DataFrame的corrwith方法，你可以计算其列或行跟另一个Series或DataFrame之间的相关系数。传入一个Series将会返回一个相关系数值Series（针对各列进行计算）  
    * returns.corrwith(returns.IBM)  
    * 传入一个DataFrame则会计算按列名配对的相关系数。这里，我计算百分比变化与成交量的相关系数。returns.corrwith(volume)  
  
### 唯一值、值计数以及成员资格  
  
* 唯一值：unique函数可以得到Series中的唯一值数组：uniques = obj.unique()  
* 值计数：value_counts用于计算一个Series中各值出现的频率：obj.value_counts()。value_counts还是一个顶级pandas方法，可用于任何数组或序pd.value_counts(obj.values, sort=False)  
* 成员资格：isin用于判断矢量化集合的成员资格，可用于过滤Series中或DataFrame列中数据的子集：mask = obj.isin(['b', 'c'])  
    * P218与isin类似的是Index.get_indexer方法，它可以给你一个索引数组，从可能包含重复值的数组到另一个不同值的数组：pd.Index(unique_vals).get_indexer(to_match)  
* P218表5-9给出了这几个方法的一些参考信息  
