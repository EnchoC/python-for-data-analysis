# Python基础  
  
## day1-环境搭建  
  
### Anaconda 安装  
  
### 通过Conda或者pip安装软件包  
  
### python解释器  
  
* Cpython/Ipython/JupyterNotebook  
  
### Ipython Magic指令  
  
* 一个或者两个百分号开头  
* %pwd  %%writefile  %run test.py  %hist   %load  test.py  
  
### Ipython帮助  
  
* help(sum)   sum?   sum??  
  
### jupyter notebook  
  
* 启动方式：命令行输入命令  
* 两种模式：Markdown和Code  
* 配置环境： jupyter notebook --generate-config  /  c.NotebookApp.notebook_dir=……  
* 安装扩展工具  
    * pip install jupyter_contrib_nbextensions  
    * jupyter contrib nbextension install --user  
  
### 编码规范  
  
* 缩进 4个空格  
    * if  while for  def  
* 换行  
    * 第二行缩进到括号的起始处  
    * 第二行缩进 4 个空格，适用于起始括号就换行的情形  
* 引号  
    * ''  / ""  / ''' ''' / """ """  
* import  
* 括号  
    * （）元组  [] 列表 {} 字典  
    * 不要在返回语句或条件语句中使用括号  
* 注释  
    * 块/行注释  #  
    * 文档注释  """ """/  ''' '''  
  
### 数据类型  
  
* 常用  
    * int/float/string/list/dict/numpy/class  
* 其他  
    * bool/tuple/set/Pandas  
  
### 变量  
  
* 命名  
    * python关键字  help("keywords")  
* 变量赋值  
    * Python 中的变量赋值不需要类型声明  
    * 每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。  
    * a = b = c = 1  
        * 指向同一个Number对象 1  
    * a = 1.2  
        * 创建一个新的对象（Number对象）  
* 变量类型 type()  
* 变量地址  id()  
  
## day2-表达式与控制语句  
  
### 运算符  
  
* 算术运算符  
    * + - *  /  %   **   //  
    * 注意： /  与  //  
* 比较运算符  
    * ==  ！=  <>   >  >=  <  <=  
* 赋值运算符  
    * =  +=  -=   *=  /=   %=   **=   //=  
    * 变量绑定对象  
* 位运算符  
    * &  |    ^   ~   <<    >>  
* 逻辑运算符  
    * and    or    not  
    * 短路逻辑  
* 成员运算符  
    * in   not in  
* 身份运算符  
    * is   in  not    id()  
    *  x  is  y  类似于  id(x) == id(y)  
* 运算符优先级  
  
### python赋值机制  
  
* 简单类型-不可变对象-重新赋值创建新对象  
* 容器类型  
    * 成员赋值，成员改变，容器不变，容器赋值，容器改变  
  
### 程序IPO  
  
* 输入  
    * input()   强制类型转换   eval  
* 处理  
    * 斐波那契数列  
* 输出  
    * print  
        * 字符串格式化符号  
        * 格式化操作符辅助指令  
    * print.format  
  
### 程序控制结构  
  
* 顺序  
* 分支  
    * if  
    * if... else...  
    * if...elif ...else...  
    * 嵌套if  
* 循环  
    * for...in...  
    * for ... in ....   /   else  
    * while...  
    * while... /  else  
* 其他  
    * continue  
    * break  
  
### range()内建函数  
  
* range(stop)  
* range(start, stop[, step])  
  
### random库  
  
### 输出作用变量结果  
  
* 输出所有的变量结果  
    from IPython.core.interactiveshell import InteractiveShell  
    InteractiveShell.ast_node_interactivity = "all"  
  
### 异常处理  
  
* try...except  
* try...except...finally  
  
### 字符串  
  
* 	'   单引号  
    	"   双引号  
    	''' 三单引号  
    	""" 三双引号  
  
* 加法+/数乘*/长度len  
* 字符串方法  
    * 分割split/连接join/replace/大小写upper&lower/去除空格strip  
* 类型转换  
    * 转换为字符串  
        *  str(ob)强制将ob转化成字符串。   
            repr(ob)也是强制将ob转化成字符串。  
  
        * 格式化字符串 format()/  %  
    * 字符串转换为为其他类型  
        * hex()/oct()/bin()/int()/float()  
* 字符编码  
    * ASCII/Unicode/utf-8  
    * ord() / chr()  
  
### 索引切片  
  
* [] 下标索引  
* 正向索引和负索引  
* 分片  var[lower:upper:step]  
  
## day3-组合数据类型  
  
### 分类  
  
* 序列类型：元素向量  
    * str/tuple/list  
    * [] / in / len  
* 集合类型：元素集合  
* 映射类型：“键-值”数据项组合  
  
### 列表 list  
  
* 定义列表 []  或者 list()  
* 列表操作  
    * 长度len() / 加法+ / 数乘 *  
    * 索引切片  
        * [] 下标索引  
        * 正向索引和负索引  
        * 分片  var[lower:upper:step]  
        * 也看用于赋值  
    * 删除元素  del  
    * 从属关系  in  /  not in  
    * 遍历  
        * for <任意变量名>  in  <列表名>:  
                         语句块  
  
* 列表方法  
    * 不改变列表  
        * 元素出现个数count()  
        * 某个元素的位置 index()  
    * 改变列表  
        * 添加单个元素 append()  
        * 添加序列 extend()  
        * 插入元素 insert()  
        * 移除元素 remove()  
        * 弹出元素 pop()  
* 排序  
    * 不改变原列表 sorted()  
    * 改变列表  sort()  
* 列表反向  
    * 不改变 [::-1]  
    * 改变 reserve()  
* 深浅拷贝  
    * 浅拷贝 list1 = list2.copy() 只拷贝第一层  
    * 深拷贝  import  copy   
                     list1 = copy.deepcopy(list2)  
  
### 可变与不可变类型  
  
* 可变： list/dict/set/numpy/class  
* 不可变： interger/float/longt/complex/string/tuple/frozenset  
  
### 元组 tuple  
  
* 创建元组  
    * 空元组 tup = ()  
    * 单元素元组 tup = (10,)  
    *   tup = (10, 11, 12)  
* 访问元组  
    * 索引/切片  
    * 元组元素不可改变  
* 元组连接组合  +  
* 删除整个元组 del  tup  
* 将列表转换为元组  tuple(listexamp)  
* 元组方法 count() / index()/ cmp() / len()  / max()/min()  
  
### 字典 dict  
  
* 基本操作  
    * 空字典 {}  /  dict()  
    * 插入键值  a["one"] = "this is number 1"  
    * 查看键值 a['one']  
    * 更新键值 a["one"] = "this is number 1, too"  
    * 使用{}初始化字典  
    * 使用 dict 初始化字典  
* 适合做键的类型：整型、字符串和元组  
* 不能充当键的类型 ： 浮点数,列表list,字典dict,集合set  
* 字典方法  
    * get()获得键值，不存在，可返回默认值  
    * pop()删除元素，也可用del  
    * update()更新  
    * in 查询字典是否有该键  
    * 显示键-值：keys()/values()/items()  
* 遍历字典  
    * for ... in....  
    * 可遍历 dict/dict.keys()/dict.values()/dict.items()  
    *  enumerate  
  
### 集合 set  
  
* 集合生成  
    * set() 空集合  
    * 列表初始化集合 set([1,2,3,1])  
    * {1,2,3}大括号创建集合  
    * {} 为空字典，而不是空集合  
* 集合操作  
    * 并集  
        *  `a.union(b)` 或者操作 `a | b` 实现  
    * 交集  
        * a.intersection(b) 或者操作 a & b 实现  
    * 差集  
        * .difference(b) 或者操作 a - b 实现  
    * 对称差  
        * a.symmetric_difference(b) 或者操作 a ^ b 实现（异或操作符）  
    *  包含关系  
        * 用 b.issubset(a) 方法，或者更简单的用操作 b <= a  
* 集合方法  
    * 添加单元素 add()  
    * 添加多元素 update()  
    * 删除单元素 remove() / discard()  
    * 弹出元素 pop() -- 其中任意一个  
    * 从a中去除所有属于b的元素  difference_update()  
* 不可变集合  
    *  frozenset([1, 2, 3, 'a', 1])  
  
### Python推导式  
  
* 列表推导式  
    * values = [10, 21, 4, 7, 12]  
        squares = [x**2 for x in values if x <= 10]  
  
    * [(x,y) for x in range(1, 4) for y in range(1, 4)]  
    * 使用()生成generator  
        * multiples = (i for i in range(30) if i % 3 is 0)  
* 集合推导式  
    * square_set = {x**2 for x in values if x <= 10}  
* 字典推导式  
    * square_dict = {x: x**2 for x in values if x <= 10}  
  
## day4-函数模块和包  
  
### 函数定义  
  
* def functionname( parameters ):  
         "函数_文档字符串"  
         function_suite  
        return [expression]  
  
### 函数调用  
  
* 参数传递  
    * 可更改对象  
        * strings, tuples, 和 numbers  
        * 类似 c++ 的值传递  
        * 如fun（a），传递的只是a的值，没有影响a对象本身  
    * 不可更改对象  
        * list,dict,set  
        * 类似 c++ 的引用传递  
        *  列表，字典。如 fun（la），则是将 la 真正的传过去，修改后fun外部的la也会受影响  
* 函数调用时的传参类型  
    * 必备参数  
    * 关键字参数  
    * 默认参数  
    * 不定长参数  
        * *args 表示参数数目不定，可以看成一个元组  
        * **kwargs 表示参数数目不定，相当于一个字典  
*  返回多个值  
    * Python将返回的多个值变成了元组  
*  嵌套函数  
    * 在函数体内定义新函数  
    * 只可内部调用  
* 递归函数  
    * 如果一个函数在内部调用自身本身，这个函数就是递归函数  
  
### 变量作用域  
  
* 变量的作用域决定了在哪一部分程序你可以访问哪个特定的变量名称。  
* 全局变量  
    * 函数外  
    * 函数调用，声明变量 global  
* 局部变量  
    * 函数内  
    * 只能在其被声明的函数内部访问  
* 闭包 nonlocal  
    * 用来在函数或其他作用域中使用外层(非全局)变量  
    * ，闭包变量能够随着闭包函数的调用而实时更新， 但并不是一个全局变量  
    * 相当于C/C++中的静态变量  
  
### 高级用法  
  
*  lambda函数  
    * 匿名函数  
    * lambda 参数:表达式  
        *  lambda x : x**2  
    * 精简代码，更易理解  
        *  map(lambda x:x**2,[1,5,7,4,8])  
* map()函数  
    * 通过 map 的方式利用函数来生成序列  
    * map(aFun, aSeq)  
        * ，然后返回一个函数aFun处理完所有list元素的列表  
    * 可传递多个序列  
        * list(map(lambda x,y : x+y, a, b))  
    * 结果必须使用循环访问或者list生成列表  
* reduce()函数  
    * reduce()传入的参数f必须接受2个参数，一个函数f，一个序列  
    * reduce把结果继续和序列的下一个元素做累积计算  
    * reduce(lambda x,y : x+y, (1,2,3,4,5))  
* filter()函数  
    * 接收一个函数f和一个序列,作用是对每个元素进行判断，返回true或fals  
    * 根据判断结果自动过滤掉不符合条件的元素，返回由符合条件的元素组成的list  
    * list(filter(lambda x : x % 2 == 1, [1,2,3,4,5]))  
    * 结果必须使用循环访问或者list生成列表  
  
### 生成器 generator  
  
* 基本格式  
    * generator = 函数 + yield  
    *  调用这个generator function返回值是一个generator实例。这跟普通的函数调用有所区别  
    * 遵循迭代器（iterator）协议，迭代器协议需要实现__iter__、next接口  
        能过多次进入、多次返回，能够暂停函数体中代码的执行  
  
    * 参考：推导式  
* 基础应用  
    * 按需生成并“返回”结果  
    * 推导式  
        * 对列表进行迭代 []  
        * 对generator进行迭代 ()  
    * 函数+yield  
        * for 循环  
        * next()  
*  yield返回值&&传参  
    * returnval = send(msg)  有参有返回  
    * returnval = next(a)  无参有返回  
  
### 偏函数  
  
* 通过设定参数的默认值，可以降低函数调用的难度  
    * int('1000000', base=2)  
    * def int2(x, base=2):  
            return int(x, base)  
  
    * int2('1000000')  
* 偏函数定义  
    * 给一个函数的某些参数设置默认值，返回一个新的函数，调用这个新函数更简单  
    * 第一部分：参数一是函数  
    * 第二部分：可变参数 *args  
    * 第三部分：关键字参数  
* 偏函数的使用  
    * 普通函数可变参数顺序执行  
        * print(sum(10,20)+sum(1,2,3,4,5))  
    * 普通函数可变参数加关键字参数组合  
        * (sum(1,2,3,4,5,**D)  
    * 偏函数可变参数顺序填充一步到位  
        * sum_add_10    = partial(sum,10)  
        * sum_add_10_20 = partial(sum,10,20)  
  
### 装饰器  
  
* 定义  
    * 增强函数的功能，比如，在函数调用前后自动打印日志，但又不希望修改原函数的定义，这种在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）  
* 实现步骤  
    * 声明装饰器 def log(func):  
    * 嵌套函数：扩展功能+回调func  
    * 返回该嵌套函数  
    * 对原函数声明扩展  
        * @log  
            def now():  
                print('2018-04-01')  
  
    * 实际效果  
        * now = log(now)  
* 装饰器传参  
    * 3层嵌套的decorator  
        * def log(text):  
                def decorator(func):  
                    def wrapper(*args, **kw):  
                        print('%s %s():' % (text, func.__name__))  
                        return func(*args, **kw)  
                    return wrapper  
                return decorator  
  
    * 用法  
        * @log('execute')  
            def now():  
                print('2018-04-01')  
                  
            now()  
  
    * 实际效果  
        * now = log('execute')(now)  
* 自由主题  
  
### 模块和包  
  
* 模块的概念  
    * 一个包含所有你定义的函数和变量的文件，其后缀名是.py  
* 模块搜索路径  
    * 内存中已经加载的模块->内置模块->sys.path路径（导入模块的环境变量）中包含的模块  
* 导入模块  
    * 将整个模块(somemodule)导入  
        * import somemodule  
    * 从某个模块中导入某个函数  
        * from somemodule import somefunction  
    * 从某个模块中导入多个函数  
        * ：from somemodule import firstfunc, secondfunc, thirdfunc  
    * 将某个模块中的全部函数导入  
        *  from somemodule import *  
    * 引用模块时使用别名  
        * import somemodule as othername  
*  模块 __name__ 属性  
    * 只有当文件被当作脚本执行的时候， __name__的值才会是 '__main__'，否则按照模块方式使用  
    * if __name__ == '__main__':  
            test()  
  
* 包  
    * 目录只有包含一个叫做 init.py 的文件才会被认作是一个包  
    * import执行过程  
        * 创建一个新的，空的module对象（它可能包含多个module）  
        * 把这个module对象插入sys.module中  
        * 装载module的代码（如果需要，首先必须编译）  
            * 找到module程序所在的位置  
            * 如 果需要导入的module的名字是m1，则解释器必须找到m1.py  
            * 首先在当前目录查找  
            * 其次当前目录指定的sys.path  
            * 然后是在环境变量PYTHONPATH中查找  
            * 在Unix下，通常是/usr/local/lib/python  
        * 执行新的module中对应的代码  
    * 子主题 3  
    * 子主题 4  
    * 子主题 5  
* 标准库  
  
### 内置函数  
  
* 数学相关  
* 类型转换相关  
* 其他操作  
  
## day5-面向对象编程  
  
### 类定义  
  
* class ClassName(ParentClass):  
        """class docstring"""  
        def method(self):  
            return  
  
* 查看类说明  
    * import numpy as np  
        np.info(Forest)  
  
* 类对象  
    * forest = Forest()  
* 添加属性和方法  
    * 直接添加属性  
        * forest.trees = 100  
        * 缺点：该属性只属于该对象，新建对象没有  
    * 创建类同时绑定属性，并通过构造函数__init__()初始化  
    *  def __init__(self, name = None, trees = 0):  
                self.name = name  
                self.trees = trees  
  
* 面向对象与函数编程  
    * 面向对象：【创建对象】【通过对象执行方法】  
        函数编程：【执行函数】  
  
### 面向对象三大特性  
  
* 封装性  
    * 属性/方法  
    * 通过对象直接调用  对象名.属性名  
        通过self间接调用   对象名.方法名(方法中self.属性名）  
  
* 继承  
    * class ClassName(ParentClass):  
            """class docstring"""  
            def method(self):  
                return  
  
    * 继承意味着它可以使用所有父类的方法和属性，同时还可以定义自己特殊的方法和属性。  
    * 新式类和经典类  
        *  当前类或者父类继承了object类，那么该类便是新式类，否则便是经典类。python3都是新式类  
    * Python多继承  
        * 其寻找方法的方式有两种，分别是：深度优先和广度优先  
        * 经典类：深度优先  
        * 自由主题：广度优先  
* 多态(鸭子类型)  
    * Pyhon不支持多态并且也用不到多态  
    * 鸭子类型（duck typing）是一种动态类型的风格  
        * 当看到一只鸟走起来像鸭子、游泳起来像鸭子、叫起来也像鸭子，那么这只鸟就可以被称为鸭子。  
    * 在基类与派生类中，同名的函数，通过回调或循环遍历实现不同的形态  
  
### 类的成员  
  
* 属性(字段)和方法  
    * 实例属性(普通字段）属于对象  
    * 类属性（静态字段）属于类  
        * 类内：变量=值  
    * 读访问  
        * 直接访问  
            * 对象名.实例属性  
            * 类名.类属性  
        * getattr()  
            * getattr(对象名，属性名)  
            * getattr(类名，属性名)  
        * hasattr()  
    * 写访问  
        * 类属性  
            * 类名.类属性 = value  
            * 对象名.类方法()在方法内修改类属性--需要用 @classmethod的方法  
            * 对象名.类属性 = value  
                * 产生一个同名的实例属性，屏蔽l类属性  
                * 可以删除该实例属性，再可访问类属性  
        * 实例属性  
            * 对象名.实例属性 = value  
            * 对项目.类方法() 在方法内修改实例属性  
    * 属性与方法的绑定  
        * 静态绑定  
            * 定义类时设定好属性/方法  
        * 动态给实例绑定一个属性  
            * 通过对象名新增实例属性，不会影响其他对象  
            * 对象名.新属性=值  
        * 动态给类绑定一个类属性  
            * 类名.新的类属性 = value  
        * 动态给实例绑定方法  
            * types.MethodType(方法名，对象名)  
            * 只影响本对象  
        * 动态给类绑定方法  
            * types.MethodType(方法名，类名)  
            * 类名.方法 = 函数名  
    * 限制一个类中实例的属性绑定  
        * class Student(object):    
                __slots__ = ('name','sex')  
  
        * 即该类只有这两个属性，不能动态增加了  
        * 只对当前类有效，针对派生类则无效了  
* 方法  
    * 类方法  
        * 要用修饰器@classmethod来标识其为类方法  
        * 第一个参数必须是类对象，一般以cls作为第一个参数  
        * 能够通过实例对象和类对象(类名)去访问  
        * 可对类属性进行修改  
    * 静态方法  
        * 通过修饰器@staticmethod来进行修饰  
        * 静态方法不需要多定义参数  
        * 必须通过类对象调用静态方法  
* 类成员修饰符  
    * 私有属性  
        * 内部属性不被外部访问，可以把属性的名称前加上两个下划线  
        * 必须通过实例变量的方法来操作  
            * get/set方法  
        *     def __init__(self, name, score):  
                    self.__name = name  
                    self.__score = score  
  
    * 特殊属性  
        * ，变量名类似__xxx__的，也就是以双下划线开头，并且以双下划线结尾的  
        * 特殊变量是可以直接访问的，不是private变量  
        * __name__  
    * 类属性公有与私有  
        * 公有类属性：类可以访问；类内部可以访问；派生类中可以访问  
        *  name = "公有类属性"  
        * 私有类属性：仅类内部可以访问  
        *  __name = "私有类属性"  
    *  类的特殊属性成员  
        *  __doc__  表示类的描述信息  
        * __module__    表示当前操作的对象在那个模块  
        *  __class__     表示当前操作的对象的类是什么  
        * __name__ 类名  
    * 特殊方法  
        * 构造方法 __init__()  
        * 析构方法 __del__(）  
        * 表示方法 `__repr__()`  
            * `__repr__()` 返回的是不使用 `print` 方法的结果  
            * 即直接执行对象名 ？  
        * 表示方法 `__str__()`  
            * `__str__()` 是使用 `print` 函数显示的结果：  
            * 即 print(对象名) 输出的结果？  
        * 对象触发执行 __call__  
            * …  
                obj = Foo() # 执行 __init__  
                obj()       # 执行 __call__  
  
        * 迭代器 `__iter__`  
* 特性  
    * 三个知识点  
        * 内置的@property装饰器，就是负责把类方法变成只读属性调用的  
        * 既能检查参数，又可以用类似属性这样简单的方式来访问类的变量  
        * 特性的两种定义方式  
    * 装饰器@property 扩展函数  
        * 这样 mass_oz 就变成属性了(只读）  
                @property  
                def mass_oz(self):  
                    return self.mass_mg * 3.53e-5  
  
        * leaf = Leaf(200)  
            print(leaf.mass_oz)  
            是属性不是方法：  
            leaf.mass_oz()--错误  
  
    * 可读可写属性  
        * 对于 `@property` 生成的只读属性，我们可以使用相应的 `@xxxx.setter` 修饰符来使得这个属性变成可写  
        * 其中 xxxx 代表的是 @porperty 修饰的只读属性的名称  
        * 使用 mass_oz.setter 修饰符  
                @mass_oz.setter  
                def mass_oz(self, m_oz):  
                    self.mass_mg = m_oz / 3.53e-5  
  
        * leaf.mass_mg = 150  
*  特性的两种定义方式  
    * 装饰器方式  
        * @property 方法名  
        * @方法名.setter  
        * @方法名.deleter  
    * 静态字段方式  
        * 创建值为property对象的静态字段  
        * property的构造方法中有个四个参数-获取，修改、删除、描述  
        *  def get_bar(self):  
                    return 'wupeiqi'  
               
              BAR = property(get_bar)  
  
## day6-文件IO  
  
### 文件读写  
  
* 打开 f = open("test.txt")  
    * 'r' / 'w'  
* 读所有内容  f.read()  
* 返回行组成的列表  lines = f.readlines()  
* 关闭文件  f.close()  
    * 异常处理  
* 写文件 f.write("some thing")  
* 文件定位  f.seed(6)  
* 二进制文件  
    * 二进制 "wb" / "rb"  
    * encode('utf-8')  
    * decode('utf-8')  
* with方法  
    * with open('newfile.txt','w') as f:  
  
### StringIO和BytesIO  
  
## day7-常用模块  
  
