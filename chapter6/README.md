# 数据加载、存储与文件格式  
  
## 输入输出的常用分类  
  
### 读取文本文件和其他更高效的磁盘存储格式  
  
### 加载数据库中的数据  
  
### 利用Web API操作网络资源  
  
## P220：6.1读写文本格式的数据  
  
### pandas提供了一些用于将表格型数据读取为DataFrame对象的函数。P220表6-1对它们进行了总结  
  
### 并不是所有文件都有标题行，可以让pandas为其分配默认的列名，也可以自己定义列名：pd.read_csv('examples/ex2.csv', header=None)或者pd.read_csv('examples/ex2.csv', names=['a', 'b', 'c', 'd','message'])  
  
### 假设你希望将message列做成DataFrame的索引。你可以明确表示要将该列放到索引4的位置上，也可以通过index_col参数指定"message"：pd.read_csv('examples/ex2.csv', names=names, index_col='message')  
  
### 如果希望将多个列做成一个层次化索引，只需传入由列编号或列名组成的列表即可：parsed = pd.read_csv('examples/csv_mindex.csv',index_col=['key1','key2'])  
  
### 当需要对数据进行规整时（字段被数量不同的空白字符间隔开），可以传递一个正则表达式作为read_table的分隔符。可以用正则表达式表达为\s+：result = pd.read_table('examples/ex3.txt', sep='\s+')  
  
### 可以用skiprows跳过文件的某几行：pd.read_csv('examples/ex4.csv', skiprows=[0, 2, 3])  
  
### 默认情况下，pandas会用一组经常出现的标记值进行识  
  
别，比如NA及NULL  
  
* 可以用isnull找出哪些值是缺失值pd.isnull(result)  
* na_values可以用一个列表或集合的字符串表示缺失值：result = pd.read_csv('examples/ex5.csv', na_values=[1,2,5])  
  
### P226：表6-2列出了pandas.read_csv和pandas.read_table常用的选项  
  
### 逐块读取文本文件  
  
* 在看大文件之前，我们先设置pandas显示地更紧些：pd.options.display.max_rows = 10  
* 如果只想读取几行（避免读取整个文件），通过nrows进行指定即可  
* P228：要逐块读取文件，可以指定chunksize（行数）chunker = pd.read_csv('examples/ex6.csv', chunksize=1000)  
  
### 将数据写出到文本格式  
  
* 数据也可以被输出为分隔符格式的文本：data.to_csv('examples/out.csv')  
* 可以用其他分隔符：data.to_csv(sys.stdout, sep='|')  
* 缺失值在输出结果中会被表示为空字符串。你可能希望将其表示为别的标记值：data.to_csv(sys.stdout, na_rep='NULL')  
* 如果没有设置其他选项，则会写出行和列的标签。当然，它们也都可以被禁用：data.to_csv(sys.stdout, index=False, header=False)  
  
### 处理分隔符格式  
  
* 对于任何单字符分隔符文件，可以直接使用Python内置的csv模块  
* P232：CSV文件的形式有很多。只需定义csv.Dialect的一个子类即可定义出新格式（如专门的分隔符、字符串引用约定、行结束符等）。各个CSV语支的参数也可以用关键字的形式提供给csv.reader，而无需定义子类：reader = csv.reader(f, delimiter='|')  
* P233可用的选项（csv.Dialect的属性）及其功能如表6-3所示  
* 对于那些使用复杂分隔符或多字符分隔符的文件，csv模块就无能为力了。这种情况下，你就只能使用字符串的split方法或正则表达式方法re.split进行行拆分和其他整理工作了  
  
### JSON数据  
  
* JSON（JavaScript Object Notation的简称）已经成为通过HTTP请求在Web浏览器和其他应用程序之间发送数据的标准格式之一。它是一种比表格型文本格式（如CSV）灵活得多的数据格式  
* 通过json.loads即可将JSON字符串转换成  
    Python形式：result = json.loads(obj)  
  
* json.dumps则将Python对象转换成JSON格式：asjson = json.dumps(result)  
* pandas.read_json可以自动将特别格式的JSON数据集转换为Series或DataFrame：data = pd.read_json('examples/example.json')  
* 如果你需要将数据从pandas输出到JSON，可以使用to_json方法：print(data.to_json())  
  
### XML和HTML：Web信息收集  
  
* pandas有一个内置的功能，read_html，它可以使用lxml和Beautiful Soup自动将HTML文件中的表格解析为DataFrame对象tables = pd.read_html('examples/fdic_failed_bank_list.html')  
* 利用lxml.objectify解析XML  
  
## 6.2 二进制数据格式  
  
### 实现数据的高效二进制格式存储最简单的办法之一是使用Python内置的pickle序列化。pandas对象都有一个用于将数据以pickle格式保存到磁盘上的to_pickle方法  
  
* frame.to_pickle('examples/frame_pickle')  
* pd.read_pickle('examples/frame_pickle')  
* 注意：pickle仅建议用于短期存储格式。其原因是很难保证该格式永远是稳定的  
  
### bcolz：一种可压缩的列存储二进制格式，基于Blosc压缩库。  
  
### 使用HDF5格式  
  
* HDF5是一种存储大规模科学数组数据的非常好的文件格式  
* HDF5支持多种压缩器的即时压缩，还能更高效地存储重复模式数据  
* HDFStore支持两种存储模式，'fixed'和'table'。后者通常会更慢，但是支持使用特殊语法进行查询操作  
* 注意：HDF5不是数据库。它最适合用作“一次写多次读”的数据集。  
  
### 读取Microsoft Excel文件  
  
## 6.3 Web APIs交互  
  
### 许多网站都有一些通过JSON或其他格式提供数据的公共API  
  
## 6.4 数据库交互  
  
