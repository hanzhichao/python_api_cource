[TOC]
# Python接口测试课程
> 卡卡倾心原创整理, 基于Python3

> github: http://github.com/hanzhichao  微信: 18010181267

## 第一天: Python基础
### Python简介、环境搭建及包管理
#### Python简介
1. 特点：Python是一门动态、解释型、强类型语音
    1. 动态：在运行期间才做数据检查（不用提前声明变量）- 静态语音(C/Java)：编译时检查数据类型（编码时需要声明变量类型）
    2. 解释型：在执行程序时，才一条条解释成机器语言给计算机执行（无需编译，速度较慢）- 编译型语言(C/Java)：先要将代码编译成二进制可执行文件，再执行
    3. 强类型：类型安全，变量一旦被指定了数据类型，如果不强制转换，那么永远是这种类型（严谨，避免类型错误，速度较慢）- 弱类型（VBScript/JavaScript）: 类型在运行期间会转化，如 js中的 1+"2"="12", 1会由数字转化为string
2. 编码原则：优雅、明确、简单
3. 优点
    1. 简单易学
    2. 开发效率高
    3. 高级语言
    4. 可移植、可扩展、可嵌入
    5. 庞大的三方库
4. 缺点
    1. 速度慢
    2. 代码不能加密
    3. 多线程不能充分利用多核cpu(GIL全局解释性锁，同一时刻只能运行一个线程)
5. 应用领域
    1. 自动化测试（UI/接口）
    2. 自动化运维
    3. 爬虫
    4. Web开发（Django/Flask/..)
    5. 图形GUI开发
    6. 游戏脚本
    7. 金融、量化交易
    8. 数据分析，大数据
    9. 人工智能、机器学习、NLP、计算机视觉
    10. 云计算

#### 环境搭建
Windows Python3环境搭建
1. 下载Python3.6.5*.exe安装包
2. 双击安装，第一个节目选中Add Python3.6.5 to PATH，点击Install Now(默认安装pip)，一路下一步
3. 验证：打开cmd命令行，输入python，应能进入python shell 并显示为Python 3.6.5版本

#### 包管理
1. pip安装
    1. pip install 包名 - 卸载： pip uninstall 包名
    2. pip install 下载的whl包.whl
    3. pip install -r requiements.txt(安装requirements.txt中的所有依赖包) 
    4. pip list 查看已安装的三方包，pip freeze 已文件格式显示已安装的三方包（用于导出requiremnts.txt文件）
2. 源码安装
    1. 下载源码包，解压，进入解压目录
    2. 打开命令行，执行 ```python setup.py install```
    3. 验证：进入python shell,输入import 包名，不报错表示安装成功
3. 三方包默认安装路径：Python3.6.5/Lib/site-packages/ 下

### Python基本语法
1. 缩进
```
if x > 0:
    print("正数")
elif x = 0:
    print("0")
else:
    print("负数")

def add(x,y):
    return x+y
```
2. 一行多条语句
```x=1; y=2; print(x+y)```
3. 断行
```
print("this line is too long, \ 
so I break it to two lines")
```
4. 注释
```
# 单行注释
a = 1

'''这是一段
多行注释'''

def add(x, y):
    """加法函数：这是docstring(函数说明)"""
    pass
```
5. 变量
    1. 变量类型（局部变量、全局变量、系统变量）
    2. 变量赋值
        - 多重赋值```x=y=z=1```
        - 多元赋值```x,y = y,x```
    3. 变量自增 ```x+=1``` ```x-=1```(不支持```x++```, ```x--```)

> Python3中没有常量

### 基本数据类型(6种)
#### 1. 数字Number
1. 种类
    1. 整型int(Python3中没有长整型，int长度几乎没有限制)
    2. 浮点型float
    3. 布尔型bool
        - False: 0,0.0,'',[],(),{}
        - True: 除False以外，['']或[[],[]]不是False
    4. 复数型complex
2. 操作符: +,-,*,/,//(地板除),**(乘方) - Python3中的/是真实除，1/2=0.5
3. 类型转
    1. str(): 其他类型转为支付串, 如```str(12)```
    2. int(): 字符串数字转为整型(字符串不是纯整数会报错), 如```int("12")```
    3. float(): 字符串转换为浮点数，如```float("1.23")```

#### 2. 字符串String
1. 字符串系统方法
    - len(): 计算字符串长度，如```len("abcdefg")```
    - find()/index(): 查找字符串中某个字符第一次出现的索引(index()方法查找不到会报错), 如```"abcdefg".find("b"); "abcedfgg".index("g")```
    - lower()/upper(): 将字符串转换为全小写/大写,如```"AbcdeF".lower();"abcedF".upper()```
    - isdigit()/isalpha()/isalnum(): 判断字符串是否纯数字/纯字母/纯数字字母组合, 如``` isdigit("123")```,结果为 True
    - count(): 查询字符串中某个元素的数量,如```"aabcabc".count("a")```
    - join(): 将列表元素按字符串连接,如```"".join(["a","b","c"])```会按空字符连接列表元素,得到"abc"
    - replace(): 替换字符串中的某已部分,如```"hello,java".replace("java", "python")```,将java 替换为 python
    - split(): 和join相反,将字符串按分隔符分割成列表, 如```"a,b,c,d".split(",")```得到["a", "b", "c", "d"]
    - strip()/lstrip()/rstrip(): 去掉字符串左右/左边/右边的无意字符(包括空格,换行等非显示字符),如```" this has blanks \n".strip()```得到"this has balnks"
2. 字符串格式化
    - %: 如```"Name: %s, Age: %d" % ("Lily", 12)```或```"Name: %(name)s, Age: %(age)d" % {"name": "Lily", "age": 12}```
    - format: 如```"Name: {}, Age: {}".format("Lily", 12)```或```"Name: {name}, Age: {age}".format(name="Lily",age=12)```
    - substitude(不完全替换会报错)/safe_substitude: 如```"Name: ${name}, Age: ${age}".safe_substitude(name="Lily",age=12)```
3. *案例*: 利用format生成自定义html报告


    tpl='''<html>
    <head><title>{title}</title></head>
    <body>
    <h1>{title}</h1>
    <table border=1px>
        <tr>
            <th>序号</th>
            <th>用例</th>
            <th>结果</th>
        </tr>
        {trs}
    </table>
    </body>
    </html>
    '''
    
    tr='''<tr><td>{sn}</td>
    <td>{case_name}</td>
    <td>{result}</td>
    '''
    
    title="自动化测试报告"
    case_results = [("1", "test_add_normal", "PASS"),("2", "test_add_negative", "PASS"), ("3", "test_add_float", "FAIL")]
    
    trs=''
    for case_result in case_results:
        tr_format = tr.format(sn=case_result[0], case_name=case_result[1], result=case_result[2])
        trs += tr_format
        
    html = tpl.format(title=title, trs=trs)
    
    f = open("report.html", "w")
    f.write(html)
    f.close()
结果预览
<h1>自动化测试报告</h1>

序号 | 用例 | 结果
---|---|---
1  |test_add_normal | PASS
2  |test_add_negative | PASS
3  |test_add_float | FAIL

#### 3. 列表List
> 列表元素支持各种对象的混合,支持嵌套各种对象,如```["a", 1, {"b": 3}, [1,2,3]]```

1. 列表操作
    - 赋值: ```l = [1, "hello", ("a", "b")]```
    - 获取: ```a = l[0] # 通过索引获取```
    - 增: ```l.append("c");l.extend(["d","e"]);l+["f"]```
    - 删: ```l.pop() # 按索引删除,无参数默认删除最后一个;l.remove("c") # 按元素删除```
    - 改:```l[1]="HELLO" # 通过索引修改```
    - 查: 遍历 ```for i in l: print(i)```
2. 列表系统方法
    - append()/insert()/extend(): 添加/插入/扩展(连接)
    - index(): 获取元素索引
    - count(): 统计元素个数
    - pop()/remove(): 按索引/元素删除
    - sort()/reverse(): 排序/反转
    - *案例*: 字符串反转```s="abcdefg"; r=''.join(reversed(a))```

#### 4. 元组Tuple
1. 不可改变,常用作函数参数(安全性好)
2. 同样支持混合元素以及嵌套
3. 只有一个元素时,必须加","号,如```a=("hello",)``` - 因为Python中()还有分组的含义,不加","会识别为字符串

> 字符串/列表/元组统称为序列, 有相似的结构和操作方法

<h3>序列相关操作方法</h3>
1. 索引
    - 正反索引: ```l[3];l[-1]```
    - 索引溢出(IndexError): 当索引大于序列的最大索引时会报错,如[1,2,3,4]最大索引是3,引用l[4]会报IndexError
2. 切片
    - l[1:3] # 从列表索引1到索引3(不包含索引3)进行截取, 如 l = [1, 2, 3, 4, 5], l[1:3]为[2, 3]
    - l[:5:2] # 第一个表示开始索引(留空0), 第二个表示结束索引(留空为最后一个,即-1), 第三个是步长, 即从开头到第5个(不包含第5个),跳一个取一个
    - *案例*: 字符串反转 ```s="abcdefg";r=s[::-1]```
3. 遍历
    - 按元素遍历: ```for item in l: print(item)```
    - 按索引遍历: ```for index in range(len(l)): print(l[index])```
    - 按枚举遍历: ```for i,v in enumerate(l): print((i,v))```
4. 扩展/连接(添加多个元素): extend()/+  ```"abc"+"123";[1,2,3]+[4,5];[1,2,3].extend([4,5,6,7])``` 
5. 类型互转: str()/list()/tuple()
>list转str一般用join(), str转list一般用split()

6. 系统函数
    - len(): 计算长度
    - max()/min(): 求最大/最小元素
    - sorted()/reversed(): 排序/反转并生成新序列(sort()/reverse()直接操作原序列)```l_new=sorted(l);l_new2=reversed(l)``` 

#### 5. 集合Set
1. 集合可以通过序列生成```a = set([1,2,3])```
2. 集合无序,元素不重复(所有元素为可哈希元素)
3. 集合分为可变集合set和不可变集合frozenset
4. 操作方法: 联合|,交集&,差集-,对称差分^
5. 系统函数: add()/update()/remove()/discard()/pop()/clear()
6. *案例1*: 列表去重: ```l=[1,2,3,1,4,3,2,5,6,2];l=list(set(l))``` (由于集合无序,无法保持原有顺序)
7. *案例2*: 100w条数据,用列表和集合哪个性能更好? - 集合性能要远远优于列表, 集合是基于哈希的, 无论有多少元素,查找元素永远只需要一步操作, 而列表长度多次就可能需要操作多少次(比如元素在列表最后一个位置)

#### 6. 字典Dict
1. 字典是由若干key-value对组成, 字典是无序的, 字典的key不能重复,而且必须是可哈希的,通常是字符串
2. 字典操作
    - 赋值: ```d = {"a":1, "b":2}```
    - 获取: ```a = d['a']```或```a = d.get("a") # d中不存在"a"元素时不会报错```
    - 增: ```d["c"] = 3; d.update({"d":5, "e": 6}```
    - 删: ```d.pop("d");d.clear() # 清空```
    - 查: ```d.has_key("c")```
    - 遍历: 
        - 遍历key: ```for key in d:```或```for key in d.keys():```
        - 遍历value: ```for value in d.values():```
        - 遍历key-value对: ```for item in d.items():```
3. *案例*: 更新接口参数 api = {"url": "/api/user/login": data: {"username": "张三", "password": "123456"}},将username修改为"李四"
``` api['data']['username'] = "李四" ``` 或 ```api['data'].update({"username": "李四"})```
> 哈希与可哈希元素
1. 哈希是通过计算得到元素的存储地址(映射), 这就要求不同长度的元素都能计算出地址,相同元素每次计算出的地址都一样, 不同元素计算的地址必须唯一, 基于哈希的查找永远只需要一步操作, 计算一下得到元素相应的地址, 不需要向序列那样遍历, 所以性能较好
2. 可哈希元素: 为了保证每次计算出的地址相同, 要求元素长度是固定的, 如数字/字符串/只包含数字,字符串的元组, 这些都是可哈希元素

> 6种类型简单的特点总结
1. 数字/字符串/元祖: 长度固定
2. 序列(字符串/列表/元祖): 有序
3. 集合/字典: 无序, 不重复/键值不重复

### 条件/循环
#### 条件判断
1. 示例:
```
if x>0:
    print("正数")
elif x=0:
    print("0")
else: 
    print("负数")
```
2. 三元表达式: ```max = a if a > b else b```
3. *案例*: 判断一个字符串是不ip地址


    ip_str = '192.168.100.3'
    ip_list = ip_str.split(".") # 将字符串按点分割成列表
    is_ip = True # 先假设ip合法
    if len(ip_list) != 4:
        is_ip= False
    else:
        for num in ip_list:
            if not isdigit(num) or not 0 <= int(num) <= 255:
                is_ip = False
    if is_ip:
        print("是ip")
    else:
        print("不是ip")
>使用map函数的实现方法(参考):

    def  check_ipv4(str):
        ip = str.strip().split(".")
        return False if len(ip) != 4 or False in map(lambda x:True if x.isdigit() and 0<= int(x) <= 255 else False, ip) else True
#### 循环
1. for in 循环
2. while 循环
        
### 文件读写(文本文件)
> html/xml/config/csv也可以按文本文件处理

#### 文件操作方法
1. open(): 打开```f =open("test.txt")```或```f =open("test.txt","r", encoding="utf-8")```或```with open("test.txt) as f: # 上下文模式,出结构体自动关闭文件```
2. read()/readline()/readlines(): 读取所有内容/读取一行/读取所有行(返回列表) - 注意: 内容中包含\n换行符,可以通过strip()去掉
3. f.write()/f.save(): 写文件/保存文件
4. f.seek(): 移动文件指针,如f.seek(0), 移动到文件开头
5. f.close(): 关闭文件(打开文件要记得关闭)

#### 文件打开模式
1. r/w/a: 只读/只写/追加模式
2. rb/wb/ab: 二进制只读/只写/追加模式(支持图片等二进制文件)
3. r+/rb+, w+/wb+, a+/ab+: 读写,区别在于, r+/w+会清空文件再写内容, r+文件不存在会报错, a+不清空原文件,进行追加, w+/a+文件不存在时会新建文件
> 文件是可迭代的,可以直接用 for line in f: 遍历

### 函数/类
#### 函数定义和调用
```
def add(x, y): # 定义函数
    return x+y

print(add(1,3)) # 调用函数
```
*案例*: 用户注册/登录函数
```
users = {"张三": "123456"}

def reg(username, password):
    if users.get(username): # 如果用户中存在username这个key
        print("用户已存在")
    else:
        users[username] = password # 向users字典中添加元素
        print("添加成功")

def login(username, password)
    if not users.get(username):
        print("用户不存在")
    elif users['username'] == password:
        print("登录成功")
    else:
        print("密码错误")
```
#### 参数和返回值
1. 函数没有return默认返回None
2. 参数支持各种对象,包含数字,支付串,列表,元组,也可以是函数和类
3. 参数默认值: 有默认值的参数必须放在最后面, 如```def add(x, y=1, z=2): 
4. 不定参数: *args和**kwargs, 如```def func(*args, **kwargs):```可以接受任意长度和格式的参数
5. 参数及返回值类型注释(Python3)
```
def(x:int, y:int) -> int: # x,y为int型,函数返回为int型,只是注释,参数格式非法不会报错
    return x+y
```
#### 函数作为参数(如: 装饰器)
```
def a():
    print("I'm a")
def deco(func):
    print("call from deco")
    func()

deco(a) # 输出"call from deco"并调用a(),输出"I'm a"
```
#### 函数嵌套(支持闭包)
```
def a():
    a_var = 1
    def b:() # 嵌套函数
        a_var += 1
```
#### 函数递归(自己调用自己,直到满足需求)
*案例*: 求N!
```
def factorial(n):
    return 1 if n == 0 or n == 1 else n * factorial(n-1)
```
### 模块/包
#### 模块
1. 一个py文件为一个模块
2. 模块导入
    - import os # 需要通过os调用相关方法, 如os.mkdir(),
    - form configparser import ConfigParser: 可以直接使用CinfigParser()
    - 支持一次导入多个
#### 包
1. 一个文件夹为一个包(Python3,文件夹中不需要建立__init__.py文件)
#### 常用系统模块
1. os: 与操作系统交互
    - os.name/os.sep/os.linesep: 系统名称/系统路径分隔符/系统换行符
    - os.makedir()/os.makedirs(): 建立目录/建立多级目录
    - os.getenv("PATH"): 获取系统PATH环境变量的设置
    - os.curdir/os.prdir: 获取当前路径/上级路径
    - os.walk(): 遍历文件夹及子文件
    - os.path.basename()/os.path.abspath()/os.path.dirname(): 文件名/文件绝对路径/文件上级文件夹名
    - os.path.join()/os.path.split(): 按当前系统分隔符(os.sep)组装路径/分割路径
    - os.path.exists()/os.path.isfile()/os.path.isdir(): 判断文件(文件夹)是否存在/是否文件/是否文件夹
    - *案例*: 用例发现, 列出文件夹及子文件夹中所有test开头的.py文件,并输出文件路径
```
for root,dirs,files in os.walk("./case/"):
    for file in files:
        if file.startswith("test") and file.endswith(".py"):
            print(os.path.join(root, file)
```
2. sys: 与Python系统交互
    - sys.path: 系统路径(搜索路径)
    - sys.platform: 系统平台,可以用来判断是python2还是3
    - sys.argv: py脚本接受的命令行参数
    - sys.stdin/sys.stdout/sys.stderr: 标准输入/输出/错误

### 常见算法
#### 冒泡排序
```
def buddle_sort(l):
    n = len(l) # 把计算长度写到遍历外,可以避免每次都重新计算
    for i in range(n-1): # 从第一个遍历到倒数第二个
        for j in range(n-i): # 第二层遍历
    
```
#### 快速排序
```
def quick_sort(l):
    if len(l) < 2:
        return l # 如果列表只有一个元素, 返回列表(用于结束迭代)
    else:
        pivot =  l[0] # 取列表第一个元素为基准数
        low = [i for i in l[1:] if i < pivot] # 遍历l, 将小于基准数pivot的全放入low这个列表
        high = [i for i in l[1:] if i >= pivot ]
        return quick_sort(low) + [pivot] + quick_sort(high) # 对左右两部分分别进行迭代
```
#### 二分查找
```
def bin_search(l, n): # l为有序列表
    low, high = 0, len(l) - 1 # low,high分别初始化为第一个/最后一个元素索引(最小/最大数索引)
    while low < high:
        mid = (high-low) // 2 # 地板除,保证索引为整数
        if l[mid] == n:
            return mid
        elif l[mid] > n: # 中间数大于n则查找前半部分, 重置查找的最大数
            high = mid -1 
        else: # 查找后半部分, 重置查找的最小数
            low = mid + 1
    return None  # 循环结束没有return mid 则说明没找到
```
> 作业
1. 查找文件中最长的行
2. 统计文件中字符个数
3. 判断字符串"abacdbdde"中第一个不重复的字符
4. 判断字符串"{{({[()]((()))[({})])}}"是否括号全部闭合

## 第二天: Python接口测试(一)
### 简单接口搭建(表单/REST)
#### 五步教会你写接口
>首先要安装flask包: ```pip install flask```
1. 从flask中导入Flask类和request对象: ```from flask import Flask, request```
2. 从当前模块实例化出一个Flask实例:```app=Flask(__name__)```
3. 编写一个函数来处理请求
    1. 从请求对象中获取数据:```a=request.values.get("a");b=request.values.get("b")```
        - request.params: 字典格式,存储请求中的url参数
        - request.form: 字典格式,存储请求中的表单数据
        - request.values: 字典格式, 包含params和form中的值
        - request.json: 字典格式, 存储json类型的请求数据, 如果请求类型非json, 值为空
    2. 进行业务处理: ```sum = int(a) + int(b)```
    3. 组装并返回响应数据: ```return str(sum) # http一般使用字符串传输数据```
4. 为接口指定接口地址和接受的方法:```@app.route("/add/", methods=["GET"]) # 写到函数上面(装饰器)```
5. 运行接口:
    1. 最后添加:
```
if __name__ == "__main__":
app.run()
```
    2. 保存为```add.py```, 打开命令行,进入add.py所在目录,运行```python add.py```ß
完整代码
```
# 1. 导入包 
from flask import Flask, request
# 2. 实例化一个
app = Flask(__name__)
# 3. 编写一个接口处理方法
@app.route("/add/", methods=["GET","POST"]) # 4. 挂载路由(指定接口的url路径), 声明接口接受的方法
def add():  
    # 3.1 从请求中获取参数
    # request.values  {"a": "1", "b": "2"}
    a = request.values.get("a")
    b = request.values.get("b")
    # 3.2 业务操作
    sum = int(a) + int(b)
    # 3.3 组装响应并返回
    return str(sum)

# 5. 运行接口
if __name__ == '__main__':
    app.run() # 默认5000端口,可以指定端口app.run(port=50001)

```
#### REST类型接口实现
```
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/api/sub/", methods=["POST"])
def sub():
    if not request.json: # 如果请求数据类型非json
        return jsonify({"code": "100001", "msg": "请求类型错误", "data": None})

    if not "a" in request.json or not "b" in request.json: # 如果参数中没有a或者没有b
        return jsonify({"code": "100002", "msg": "参数缺失", "data": None})
    
    a = request.json.get("a")
    b = request.json.get("b")
    result = str(float(a) - float(b)) # 使用float支持浮点数相减
    return jsonify({"code": "100000", "msg": "成功", "data": result}) # 使用jsonify将字典数据转换为json类型的相应数据

if __name__ == '__main__':
    app.run()
```
#### 使用Postman测试接口(Form/Json)
#### 编写接口文档

### 接口测试基础
#### 接口测试概念
接口测试是测试系统组件间接口的一种测试。
接口测试主要用于检测外部系统与系统之 间以及内部各个子系统之间的交互点。测试的重点是要检查数据的交换，传递和控制管理过 程，以及系统间的相互逻辑依赖关系等。 
#### 接口测试目的
- 核心：保证系统的稳定 
- 手段：持续集成 
- 目的：提高测试效率，提升用户体验，降低产品研发成本 

#### 接口测试一般流程
- 列出需求
- 安排资源，编写接口用例 -> 用例评审
- 编写接口测试代码 -> 代码评审codeReview
- 执行接口测试

#### 接口测试关注点
- 功能:功能实现,实现与设计一致, 接口通过性测试
- 健壮性: 边界值,容错性
- 性能: 并发及压测
- 稳定性: 长期运行的稳定性
- 安全性: SQL注入, session依赖, 数字签名, http接口的安全性

#### 常见接口种类
- Http/Https接口: 通过http/https协议传送接口数据(通常按字符串/二进制传输), 如常见的网页表单, https安全性更好
- RESTful Api: REST表述性状态传递. 一种设计风格,基于http/https协议, 把一切接口视为资源, 接口要分版本,在统一的域名下管理, 不同的方法(get/post..)做不同的事,通常请求及响应使用json格式
- Web Service: SOAP简单面向对象协议, 基于http实现的一种RPC方案.接口返回一些对象,可以直接通过操作对象,实现我们需要的业务处理.使用xml格式传输数据
- RPC接口: RPC为远程方法调用, 有不同的实现方案,基于TCP/Http协议的都有. RPC可以想我们本地导入和调用对象一样使用. Dubbo接口也是一种RPC接口.

#### 常见接口数据类型
- 请求数据类型(Content-Type):
    - application/x-www-form-urlencoded: 常规只有文本的网页表单
    - application/json: RESTful Api常用格式, 结构清晰, 含有多层嵌套
    - multipart/form-data: 既有文本,又有上传文件或富文本框的混合数据表单
    - text/xml: xml格式, RPC接口常用格式
- 响应数据类型
    - string/html: 返回字符串或网页源码
    - json: RESTful Api常用响应格式, 结构清晰
    - xml: RPC接口常用格式

#### 常见接口安全验证方式
- Auth_1.0/Auth_2.0: 通用接口授权方式
- Session依赖: 需要登录之后才能进行接口操作
- Token验证: 先要使用自己的appid/appsecret通过获取token接口验证身份获取一个token(令牌,有一定有效期), 然后带着token访问接口
- 数字签名: 将原本的参数按一定规则进行组合,配合时间戳或appsecret, 通过加密算法生成一个签名sign, 携带签名进行接口请求

#### 常见接口请求方法
- GET: 获取资源
- POST: 修改资源
- PUT:
- DELETE: 删除资源
- HEAD:
- PATCH:
- OPTIONS:

#### 常见状态码(RESTful规范)
- 200系: 成功
    - 200 OK - [GET]：获取资源成功
    - 201 CREATED - [POST/PUT/PATCH]：创建/修改成功
    - 202 Accepted - [*]：任务接受
    - 204 NO CONTENT - [DELETE]：删除成功
- 300系: 重定向
    - 301 Moved Permanently: 永久重定向
    - 302 Found: 临时重定向
- 400: 资源错误
    - 400 INVALID REQUEST - [POST/PUT/PATCH]：用户请求错误
    - 401 Unauthorized - [*]：没有权限(鉴权失败, 接口层)
    - 403 Forbidden - [*] 资源禁止访问(服务器层,没有访问权限)
    - 404 NOT FOUND - [*]：资源不存在
    - 405 Method Not Allowd: 访问的方法不允许, 如用POST访问只支持GET请求的接口
    - 406 Not Acceptable - [GET]：用户请求的格式不可得(比如用户请求JSON格式，但是只有XML格式)
    - 410 Gone -[GET]：资源被永久删除
    - 422 Unprocesable entity - [POST/PUT/PATCH] 当创建对象时，发生验证错误
- 500系: 服务器内部错误(接口崩溃或有Bug)
    - 500 INTERNAL SERVER ERROR - [*]：服务器发生错误

#### 接口业务类型
- 返回数据型接口: 只从数据库读取数据
- 业务操作型接口: 需要写数据库(接口测试需要要涉及参数化或环境清理)

### 快速上手接口测试
#### 获取接口文档
- Wiki
- Word文档
- Postman导出
- 抽象接口定义
- 接口管理平台

#### 接口文档分析
- 功能分析: 是否能满足业务(是否缺少某个前端需要的参数), 是否能满足所有业务场景(是否有漏开发接口, 比如只开发了单品接口,没开发套餐接口)
- 设计分析: 是否有不规范字段(如,nickname, passwd);不规范格式(如sex,用男,女而不是1,2);是否有易混淆字段(如amount和total);是否有单词拼错;是否有和数据库字段对应但名称不一样的(易错)
- 接口分析: 协议类型(http要考虑安全);请求方法(是否规范);请求编码格式(表单/Json/xml, 很多接口文档不声明,导致测试调试不通);接口授权方式;接口业务类型(关系到是否需要做参数化或环境清理); 返回值类型及结构(关系到怎么断言)
- 接口依赖: 需要什么环境准备和业务场景, 依赖那些接口, 有那些动态数据, 预备环境怎么保障
- 参数分析: 各个参数的参数类型,组成规则,是否允许不传,是否可以为空, 是否允许多传参
- 业务分析: 如price字段必须和数据库中的商品的price字段一致,才能校验通过
- 非功能性: 接口的技术实现方案是否合理, 能否满足高并发的性能要求, 边界值/极限值的处理是否合适, 是否前后端都有数据格式校验等(如精确度为秒级的订单号生成器,在高并发下会导致生成同一订单号的问题)
- 其他: 如反爬,对headers的一些限制和校验, ip等限制

#### 编写接口用例
>Excel/TestLink/禅道

- 单接口用例: 正常数据/边界数据/异常数据(健壮性)/并发(一致性)/性能/安全性(抓包截取伪造/SQL注入/跨域请求)
- 场景用例: 列出常见的用户场景, 用接口进行覆盖, 业务场景压测(寻找某个环节的性能瓶颈)

TestCase | Url | Method | DataType | a | b | Excepted | Actual | Status |
---|---|---|---|---|---|---|---|---|---|
test_add_normal | /api/add/ | GET | Url | 3 | 5 | 8 |  |  |
test_add_zero | /api/add/ | POST | FORM | 0 | 0 | 0 |  |  |
test_add_negetive | /api/add/ | POST | FORM | -3 | 5 | 2|   |  |
test_add_float | /api/add/ | POST | FORM | 3.2 | 5.2 | 8.4 |  |  |
test_add_null | /api/add/ | POST | FORM  | |  | 0 |  |  |

#### 执行接口测试
- Postman: 功能调试
- Jmeter: 性能

### 接口自动化实践
#### 五步教会你写接口自动化用例
> 需要安装三方包:requests pytest pytest-html```pip install requests pytest pytest-html```

1. 导入requests模块
    import requests
2. 组装请求参数和数据
    ```url = 'http://127.0.0.1:5000/add/'```
    ```params = {"a":3, "b":5} # get请求url参数, 字典格式```
    ```data = {"a":3, "b":5} # post请求请求数据, 字典格式```
3. 发送请求得到response对象
    ```resp = requests.get(url=url, params=params)```
    ```resp = requests.post(url=url,data=data)```
4. 解析response对象
    - resp.text # 获取响应文本
5. 断言结果
    assert resp.text == '8'
完整代码:
```
# 1. 导入包
import requests

base_url = "http://127.0.0.1:5005"

# 2. 组装请求
def test_add_normal():
    # url  字符串格式
    url = base_url + "/add/"
    
    # data {} 字典格式
    data = {"a": "1", "b": "2"}
    # 3. 发送请求,获取响应对象
    response = requests.post(url=url, data=data)
# 4. 解析响应
# 5. 断言结果
    assert response.text == '3'
```
#### REST类接口自动测试方法
>请求格式为json

三处不同:
1. 必须通过headers指定内容类型为application/json: ```headers={"Content-Type":"application/json"}
2. 请求数据要转化为字符串: ```data=json.dumps(data)``` (使用json.dumps需要import json)
3. json格式的响应数据,在接口调试通过和稳定的情况下可以使用response.json()解析为字典格式,进行断言

完整代码:
```
# 1. 导入包
import requests
import json

base_url = "http://127.0.0.1:5005"

def test_sub_normal():
    url = base_url + "/api/sub/"
    headers = {"Content-Type": "application/json"} # 1. 必须通过headers指定请求内容类型为json
    data = {"a": "4", "b": "2"}
    data = json.dumps(data) # 2. 序列化成字符串
    response = requests.post(url=url, headers=headers, data=data)
    # 3. 响应解析 # 响应格式为: {"code":"100000", "msg": "成功", "data": "2"}
    resp_code = response.json().get("code") 
    resp_msg = response.json().get("msg")
    resp_data = response.json().get("data")
    # 断言
    assert response.status_code == 200
    assert resp_code == "100000"
    assert resp_msg == "成功"
    assert resp_data == "2"
```
>补充1: 感受Python黑科技之exec()动态生成用例:

数据文件: test_add_data.xls
TestCase | Url | Method | DataType | a | b | Excepted | Actual | Status |
---|---|---|---|---|---|---|---|---|---|
test_add_normal | /api/add/ | GET | Url | 3 | 5 | 8 |  |  |
test_add_zero | /api/add/ | POST | FORM | 0 | 0 | 0 |  |  |
test_add_negetive | /api/add/ | POST | FORM | -3 | 5 | 2|   |  |
test_add_float | /api/add/ | POST | FORM | 3.2 | 5.2 | 8.4 |  |  |
test_add_null | /api/add/ | POST | FORM  | |  | 0 |  |  |
```
import requests
import xlrd

base_url = 'http://127.0.0.1:5005'

# 1.打开excel
wb = xlrd.open_workbook("test_add_data.xls")
# 2. 获取sheet
sh = wb.sheet_by_index(0)  # wb.sheet_by_name("Sheet1")
# 行数 sh.nrows 列数 sh.ncols
# 获取单元格数据
# print(sh.cell(1,0).value)
# print(sh.nrows)
tpl = '''def {case_name}():
    url = base_url + '/add/'
    data = {{"a": "{a}", "b":"{b}"}}
    response = requests.get(url=url, data=data)
    assert response.text == '{expected}'
'''

for row in range(1, sh.nrows):
    case_name = sh.cell(row,0).value
    a = sh.cell(row, 4).value
    b = sh.cell(row, 5).value
    expected = sh.cell(row, 6).value
    case = tpl.format(case_name=case_name, a=a, b=b, expected=expected)
    exec(case)
```
> 动态生成的用例支持pytest发现和执行

#### 自动化接口用例运行
1. 将自动化测试用例保存为test*.py,一个文件里可以写多个用例, 如上面两个接口保存为test_user.py
2. 在自动化用例脚本所在目录打开命令行, 运行```pytest```(运行所有test开头的.py用例)或```pytest test_user.py```(只运行该脚本中用例)
3. pytest一些参数
    - -q: 安静模式(不显示环境信息) ```pytest -q test_user.py```
    - --html=report.html:执行完生成report.html报告(文件名可以自己指定)```pytest test_user.py --html=test_user_report.html```
    - --resultlog=test.log: 执行完成生成执行结果log文件```pytest test_user.py --resultlog=run.log```

### requests库详解
#### 请求方法 
- requests.get()
- requests.post()
- requests.delete()
- .....
- requests.session() # 用来保持session会话,如登录状态
#### 请求参数
- url: 接口地址, str```url="http://127.0.0.1:5000/add/"```
- headers: 请求头, dict ```headers={"Content-Type": "application/json"}```
- params: url参数, dict ```params={"a":"1":"b":"2"}```
- data: 请求数据, dict ```data={"a":"1":"b":"2"}```
- files: 文件句柄, dict ```files={"file": open("1.jpg")}```
- timeout: 超时时间,单位s, str, 超过时间会报超时错误```requests.get(url=url,params=params,timeout=10)
#### 响应解析
- resp: 响应对象
- resp.status_code: 响应状态码
- resp.text # 响应文本
- resp.json() # 响应转化为json对象(字典)-慎用:如果接口出错或返回格式不是json格式,使用这个方法会报错
- resp.content # 响应内容, 二进制类型

## 第三天: Python接口测试(二)
### 各种类型接口的测试
#### GET请求接口
```requests.get(url=url, params=params)```
#### 表单类型
```requests.post(url=url, data=data)```
#### REST类型
```requests.post(url=url, headers={"Content-Type": "application/json"}, data=json.dumps(data)```
#### 上传文件
```requests.post(url=url, files={"file": open("1.jpg", "rb")})```
#### Session依赖
```session=requests.session(); session.post(...); session.post()``` 
#### 接口依赖
1. 接口依赖之动态中间值
```resp=requests.get(...);token=resp.split("=")[1];resp2=requests.post(....token...)```
#### 验签接口

    import hashlib
    
    def md5(str):
        m = hashlib.md5()
        m.update(str.encode('utf8'))
        return m.hexdigest()  #返回摘要，作为十六进制数据字符串值
    
    def makeSign(params):
        if not isinstance(params, dict):
            print("参数格式不正确，必须为字典格式")
            return None
        if 'sign' in params:
            params.pop('sign')
        sign = ''
        for key in sorted(params.keys()):
            sign = sign + key + '=' + str(params[key]) + '&'
        sign = md5(sign + 'appsecret=' + appsecret)
        params['sign'] = sign
        return params

```data = makeSign(data);resp = requests.post(url=url, headers=headers, data=json.dumps(data))```
2. 接口依赖之Mock Server

> Mock和单元测试的桩(Stub)类似, 是通过建立一个模拟对象来解决依赖问题的一种方法.

应用场景: 
    1. 依赖第三方系统接口, 无法调试 
    2. 所依赖接口尚未具备(前后端分离项目, 前端开发时,后端接口尚未开发完毕) 
    3. 所依赖接口需要修改或不稳定
    4. 依赖接口较多或场景复杂, 所依赖接口不是主要验证目标的

解决方法:
    1. 通过Mock.js/RAP/RAP2来动态生成, 模拟接口返回数据
    2. 自己使用Flask大家简单的Mock接口
    3. 使用Python自带的mock库
```
...
```

#### SOAP接口
> pip install suds

```
from suds.client import Client

ip = '127.0.0.1'
port = '5001'

client = Client("http://%s:%s/?wsdl" % (ip, port))
result = client.service.addUser("张790", "123456")
print(result)
```
#### XML-RPC接口
```
import xmlrpc.client

user = xmlrpc.client.ServerProxy('http://127.0.0.1:5002')
print(user.getAll())
```
### 参数化
> 参数化是用来解决动态参数问题的

#### 数据文件参数化
- csv数据文件
    - 优点：以逗号分隔，轻量级
    - 缺点：参数过多不便于区分

```import csv;csv_data = csv.reader(open('data/reg.csv'))```
- config数据文件
    - 优点：方便支持多组数据，支持备注
```
import configparser
    cf=configparser.ConfigParser()
    cf.read('data/reg.config', encoding='utf-8')
    cf.sections()
    cf.options(section)
    cf.get(section,option)
```
- json数据文件
    - 优点：REST接口常用数据格式，格式清楚，适用于多参数及含有嵌套参数
    - 缺点：不支持备注，多组数据不清晰
```
import json
with open('data/reg.json', encoding='utf-8') as f:
    json_data = json.loads(f)  #json_data为列表或字典
```

```
json的序列化和反序列化
需求：python的字典/列表等数据格式为内存对象，需要做存储（持久化）和进行数据交换

序列化: 从内存对象到可存储数据, 方便存储和交换数据
    json.dumps: 列表/字典/json->字符串 ```str_data = json.dumps(dict_data)```
    json.dump: 列表/字典/json->数据文件 ```json.dump(dict_data, open(data_file, "w"))```
反序列化: 从存储数据到内存对象
    json.loads: 字符串->字典/列表```json.loads('{"a":1,"b":2}') #得到字典{"a":1,"b":2}```
    json.load: json数据文档->列表/字典```dict_data = json.load(open('data.json'))```
```
- excel数据文件
    - 优点：直观，构造数据方便
    - 缺点：嵌套数据不方便格式化
    
>pip install xlrd
```
import xlrd
wb=xlrd.open_workbook("data/reg.xlsx")
sh=wb.sheet_by_index(0)
sh=wb.sheet_by_name('Sheet1")
sh.nrows
sh.ncols
sh.cell(x,y).value
```
- xml数据文件
    - 优点：方便自定义多层结构，SOAP,RPC通用格式
``` 
from xml.dom.minidom import parse
dom=parse('data/reg.xml')
root=dom.documentElement
user_nodes=root.getElementsByTagName("user")
user_node.getAttribute('title')
user_node.hasAttribute('title')
name_node=user_node.getElementsByTagName('name')[0]
name=name_node.childNodes[0].data
```
>案例1: 自动执行excel用例并将结果回写excel

数据文件: test_user.xlsx

TestCase|Url|Method|DataType|Data|Excepted|Resp.text|Status
|---|---|---|---|---|---|---|---
test_user_reg_normal|/api/user/reg/|POST|JSON|{"name":"九小1","passwd": "123456"}|    resp.json()["code"]=="100000"| | |      
test_user_login_normal|/api/user/login/|POST|FORM|{"name":"九小1","passwd": "123456"}|"成功" in resp.text| | |      

```
import xlrd
from xlutils.copy import copy
import json
import requests
import sys

base_url = "http://127.0.0.1:5000"

def run_excel(file_name, save_file="result.xls"):
    wb=xlrd.open_workbook(file_name)
    sh=wb.sheet_by_index(0)

    wb2 = copy(wb)
    sh2 = wb2.get_sheet(0)


    for i in range(1,sh.nrows):
        url = base_url + sh.cell(i,1).value
        data = json.loads(sh.cell(i,4).value)
        headers = {}
        method = sh.cell(i,2).value
        data_type = sh.cell(i,3).value
        excepted = sh.cell(i,5).value
        if data_type.lower() == 'json':
            data = json.dumps(data)
            headers = {"Content-Type":"application/json"}

        if method.lower() == "get":
            resp = requests.get(url=url,headers=headers)
        else:
            resp = requests.post(url=url,headers=headers,data=data)
        if eval(excepted):
            status = "PASS"
        else:
            status = "FAIL"
        sh2.write(i,6, resp.text)
        sh2.write(i,7, status)

    wb2.save(save_file)
    print("保存成功")
        
        
if __name__ == "__main__":
    if len(sys.argv)==2:
        run_excel(sys.argv[1])
    elif len(sys.argv)>2:
        run_excel(sys.argv[1],sys.argv[2])
    else:
        print("调用格式: python run_excel.py 用例文件 输出文件")
```
保存脚本为run_excel.py, (最好和数据文件test_user.xlsx放在同一目录下), 在脚本所在目录打开命令行,运行```python run_excel.py test_user.xlsx```

生成的result.xls预览

TestCase|Url|Method|DataType|Data|Excepted|Resp.text|Status
|---|---|---|---|---|---|---|---
test_user_reg_normal|/api/user/reg/|POST|JSON|{"name":"九小1","passwd": "123456"}|    resp.json()["code"]=="100000"| {"code":"100001","data":{"name":"\u4e5d\u5c0f1","passwod":"e10adc3949ba59abbe56e057f20f883e"},"msg":"\u5931\u8d25\uff0c\u7528\u6237\u5df2\u5b58\u5728"}| FAIL|       
test_user_login_normal|/api/user/login/|POST|FORM|{"name":"九小1","passwd": "123456"}|"成功" in resp.text|```<h1>登录成功</h1>``` | PASS |  


#### 随机数据参数化
>import random
- 随机数
    - random.random(): 随机0，1
    - random.randint(0,100): 随机整数
    - random.randrange(0,100,2): 随机偶数
    - random.uniform(1,100): 随机浮点数
- 随机选择
    - random.choice('abcdefg')
    - random.choice(['赵','钱','孙','李','周'])
```
随机姓名的实现:
#随机汉字: chr(random.randint(0x4e00, 0x9fbf))
name=random.choice(['赵','钱','孙','李','周'])+chr(random.randint(0x4e00, 0x9fbf)
```
- 随机样本
    - random.sample('abcdefg', 2)

随机2个字符拼接: ```''.join(random.sample('abcdefg',2)```
- 洗牌
    - random.shuffle([1, 2, 3, 4, 5, 6]): 随机改版列表数据

### 断言/检查点
> 断言/检查点是用来自动验证接口返回数据/业务操作的结果是否满足预期

#### 响应断言
#### 正则表达式
- 元字符
    - . : 任意字符
    - \d: 任意数字 - \D: 任意非数字
    - \w: 任意字符或数字 - \W: 任意非字符及数字
    - \s: 任意空白字符(包含空格或\n等) - \S: 任意非空白字符
    - ^: 匹配开头
    - $: 匹配结尾
    - []: 匹配其中任何一个字符
    - {n,m}: 匹配n-m个重复
    - * : 匹配重复任意次(包含0次)
    - + : 匹配重复至少一次
    - ? : 匹配0或1次
    - (): 分组,获取需要的部分数据
    - | : 或, 匹配多个pattern
    - \元字符: 取消元字符转义
- 贪婪匹配及非贪婪匹配
- 系统函数
    - re.findall(): re.S,支持跨行
    - re.match()
    - re.search()
    - re.sub()/re.subn()
    - re.complie()
#### 数据库断言
> 从数据库读取数据,验证数据库数据是否符合预期
- MySQL断言
> pip install pymysql
    
1. 导入pymysql: ```import pymysql```
2. 建立数据库连接: 
```
conn = pymysql.connect(host='',port=3306,db='',user='',passwd='',charset='utf8')
```
3. 从连接建立操作游标: ```cur=conn.cursor()```
4. 使用游标执行sql命令: ```cur.execute("select * from user")```
5. 获取执行结果:
    1. cur.fetchall(): 获取所有结果
    2. cur.fetchmany(3): 获取多条结果
    3. cur.fetchone(): 获取一条结果
6. 关闭游标及连接(先关游标再关连接):```cur.close();conn.close()```
- PostgreSQL
> pip install pyscopg2
```
import pyscopg2
conn=pyscopg2.connect(host='',port='',dbname='',user='',password='') # 注意是dbname, password
cur=conn.curser()
cur.execute("...")
cur.fetchall()
```
- Oracle
> pip install cx_Oracle
```
...
```
- Mongodb
> pip install pymongo
```
from pymongo import MongoClient

conn = MongoClient('', 27017)
db = conn.mydb
my_set = db.test_set

for i in my_set.find({"name": "张三"}):
    print(i)

print(my_set.findone({"name": "张三"}))
```
- Redis断言
>pip install redis
```
import redis

r = redis.Redis(host='192.168.100.198', port=6379, password='!QE%^E2sdf23RGF@ml239', db=0)
print(r.dbsize())
print(r.get('package'))
print(r.hget('event_order_advance_008aea6a62115ec4923829ee09f76a9c18243f5d', 'user'))

```
#### 服务器断言
>pip install paramiko
```
import paramiko

client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())  
client.connect('192.168.100.241', 22, username='root', password='1234567', timeout=4)
stdin, stdout, stderr = client.exec_command('cat /proc/meminfo')
print(stdout.read())
client.close()

```
完整用例:
```
import requests
import pytest
import json
import hashlib
import re


def md5(string):
    m = hashlib.md5()
    m.update(string.encode('utf8'))
    return m.hexdigest()

def makeSign(data):
    sign=''
    for key in sorted(data.keys()):
        sign += key + '=' + str(data[key]) + '&'
    sign += 'appsecret=NTA3ZTU2ZWM5ZmVkYTVmMDBkMDM3YTBi'
    data['sign'] = md5(sign)
    return data

class DB():
    def __init__(self):
        # 建立连接
        self.conn = pymysql.connect(host='localhost',port=3307,user='root',passwd='',db='api',charset='utf8')

        # 建立一个游标
        self.cur = self.conn.cursor()
    
    def __del__(self):
        self.cur.close()
        self.conn.close()

    def getUserByName(self, name):
        self.cur.execute("select * from user where name='%s'" % name)
        return self.cur.fetchone()

    def checkUser(self, name, passwd):
        user = self.getUserByName(name)
        if user:
            if user[2] == md5(passwd):
                return True
            else:
                return False
        else:
            return None
            
class TestUser(): # pytest识别不能用__init__方法
    base_url = 'http://127.0.0.1:5000'
    db = DB()

    def test_login(self):
        url = self.base_url + '/api/user/login/'
        data = {"name": "张三", "passwd": "123456"}
        resp = requests.post(url=url, data=data)

        #断言
        assert resp.status_code == 200
        assert '登录成功' in resp.text

    def test_reg(self):
        url = self.base_url + '/api/user/reg/'
        headers = {"Content-Type": "application/json"}
        data = {'name': '张10', 'passwd': '123456'}
        resp = requests.post(url=url, headers=headers, data=json.dumps(data))

        #断言
        assert resp.json()['code'] == '100000'
        assert resp.json()['msg'] == '成功'
        assert self.db.getUserByName('张10')


    def test_uploadImage(self):
        url = self.base_url + '/api/user/uploadImage/'
        files = {'file': open("复习.txt")}
        resp = requests.post(url=url, files=files)

        #断言
        assert resp.status_code == 200
        assert '成功' in resp.text
        # todo 服务器断言

    def test_getUserList(self):
        session = requests.session()
        login_url = self.base_url + '/api/user/login/'
        login_data = {"name": "张三", "passwd": "123456"}
        session.post(url=login_url, data=login_data)

        url = self.base_url + '/api/user/getUserList/'
        resp = session.get(url=url)

        #断言
        assert resp.status_code == 200
        assert '用户列表' in resp.text
        assert re.findall('\w{32}',t2) != []

    def test_updateUser(self):
        session = requests.session()  # 接口依赖的接口需要用session
        get_token_url = self.base_url + '/api/user/getToken/'
        params = {"appid": '136425'}
        token_resp = session.get(url=get_token_url, params=params)
        assert re.findall('token=\w{32}$')
        token = token_resp.text.split('=')[1]

        url = self.base_url + '/api/user/updateUser/?token=' + token
        data = {'name': '张三', 'passwd': '234567'}
        headers = {"Content-Type": "application/json"}
        resp = session.post(url=url, headers=headers, data=json.dumps(data))

        #断言
        assert resp.status_code == 200
        assert resp.json()['code'] == '100000'
        assert resp.json()['msg'] == '成功'
        assert self.db.checkUser('张三', '234567')

    def test_delUser(self):
        url = self.base_url + '/api/user/delUser/'
        headers = {"Content-Type": "application/json"}
        data = {'name': '张10', 'passwd': '123456'}
        data = makeSign(data)
        resp = requests.post(url=url, headers=headers, data=json.dumps(data))

        #断言
        assert resp.status_code == 200
        assert resp.json()['code'] == '100000'
        assert resp.json()['msg'] == '成功' 
        assert not self.db.getUserByName('张10')


if __name__ == '__main__':
    t = TestUser()
    # t.test_updateUser()
    # t.test_updateUser()
    t.test_delUser()
    # pytest.main("-q test_user2.py")
```
## 第四天: Python接口测试框架
### 什么是框架
### 目前主流接口测试方案
#### 工具派
#### Java派
#### Python派
#### 接口平台
### 框架类型
#### 录制回放
#### 数据驱动
#### 行为驱动
### 框架的分层与规划
#### 框架分层
<table>
    <tr><td colspan="2">表示层: (用户界面)</td></tr>
    <tr><td>业务逻辑层: (读取数据,配置并组装发送请求)</td><td>执行控制(pytest)</td></tr>
    <tr><td colspan="2">数据层: (配置读取/数据读取/数据库连接/其他(log/email)</td></tr>
</table>

#### 框架规划
- case: 测试用例目录
    - user: (用户模块)
        - test_user.py: 测试用例
    - case.py: 用例公共方法 
- data: 数据文件目录
    - test_user_data.xlsx: 测试用例数据文件
- conf: 配置文件目录
    - default.conf: 默认配置文件
- report: pytest生成的报告保存路径
- log: log保存路径,按天生成log
- common: 公共方法目录
    - config.py: 配置文件读取
    - data.py: 数据文件读取
    - db.py: 数据库连接
    - log.py: 日志配置
    - send_email.py: 发送邮件配置
### 框架实现
#### conf/default.conf: 表示层-项目配置文件
```
[runtime]
log_level=debug
report_dir=report
log_dir=log
timeout=10

[server]
test = http://127.0.0.1:5000
stage = http://127.0.0.1:6000
prod = http://127.0.0.1:7000

[db_test]
host = localhost
port = 3307
db = api
user = root
passwd = 

[db_stage]

[db_prod]

[email]
server = smtp.sina.com
user = test_results@sina.com
pwd =  ******
subject = Api Test Ressult
receiver = superhin@126.com
```
#### data/test_user_data.xlsx: 表示层-用例数据文件
- reg表(sheet名为reg)

TestCase | Url | Method | DataType | Data | Code | Msg |
---|---|---|---|---|---|---|---|---|---|
test_reg_normal | /api/user/reg/ | POST | JSON | {"name": "{NAME}", "passwd": "123456"} | 100000 | 成功 | 
- login表(sheet名为login)

TestCase | Url | Method | DataType | Data | ResponseText |
---|---|---|---|---|---|---|---|---|---|
test_login_normal | /api/user/login/ | POST | FORM | {"name": "张三", "passwd": "123456"} | 登录成功 |

- SQL表(sheet名为SQL)

checkUser | select * from user where name={NAME}
|---|---
checkUserPasswd | select * from user where name={NAME} and passwd={PASSWD}

#### common/config.py:数据层-config文件读取
```
"""
1. 从配置文件中获取各个段信息
2. 返回一个项目的绝对路径
"""
import os
import configparser

# 相对导入包的问题

pro_path = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))


class Config(object):
    def __init__(self, filename="default.conf"):
        self.cf = configparser.ConfigParser()
        self.cf.read(os.path.join(pro_path,"conf",filename))
        
    def get_runtime(self, option):
        return self.cf.get("runtime", option)

    def get_server(self, option):
        return self.cf.get("server", option)

    def get_db_test(self, option):
        return self.cf.get("db_test", option)

    def get_email(self, option):
        return self.cf.get("email",option)

if __name__ == "__main__":
    c = Config()
    print(c.get_runtime("log_level"))
    print(c.get_server("test"))
```
#### data.py: 数据层-数据文件读取
```
"""
1. 从Excel中读取接口的数据
2. 读取Sql命令
"""
import xlrd
import sys
import os
sys.path.append("..")
from common.config import pro_path

class Data(object):
    def __init__(self, filename):
        data_file_path = os.path.join(pro_path,"data",filename)   
        self.wb = xlrd.open_workbook("../data/test_user_data.xlsx")

    def get_case(self,sheet_name, case_name):
        sh = self.wb.sheet_by_name(sheet_name)
        for i in range(1, sh.nrows):
            if sh.cell(i,0).value == case_name:
                return sh.row_values(i)

        print("用例名未找到")
        return None

    def get_sql(self, sql_name):
        sh = self.wb.sheet_by_name("SQL")
        for i in range(sh.nrows):
            if sh.cell(i,0).value == sql_name:
                return sh.cell(i,1).value
        print("sql未找到")
        return None

if __name__ == "__main__":
    d = Data("test_user_data.xlsx")
    print(d.get_case("reg","test_reg_normal"))
    print(d.get_sql("checkUser"))
```
#### db.py: 数据层-数据库连接
```
"""
1. 从配置文件中读取数据库配置
2. 连接数据库
3. 执行sql并返回所有结果
"""
import sys
import pymysql
sys.path.append("..")
from common.config import Config

class DB(object):
    def __init__(self):
        c = Config()
        self.conn = pymysql.connect(host=c.get_db_test("host"),
                                    port=int(c.get_db_test("port")),
                                    db=c.get_db_test("db"),
                                    user=c.get_db_test("user"),
                                    passwd=c.get_db_test("passwd"),
                                    charset="utf8")

        self.cur = self.conn.cursor()

    def do_sql(self, sql):
        self.cur.execute(sql)
        return self.cur.fetchall()

    def __del__(self):
        self.cur.close()
        self.conn.close()

if __name__ == "__main__":
    db = DB()
    print(db.do_sql("select * from user"))

```
#### log.py: 数据层-log配置
```
"""
1. 配置log输出格式 time - loglevel - file - func - line - msg
2. 支持输出到log文件及屏幕
3. 支持返回一个logger,让其他模块调用
"""
import sys
sys.path.append("..")

from common.config import Config, pro_path
import time
import logging
import os

class Log():
    @classmethod
    def config_log(cls):
        cf = Config()
        log_dir = os.path.join(pro_path, cf.get_runtime("log_dir"))
        today = time.strftime("%Y%m%d", time.localtime(time.time()))
        log_file = os.path.join(log_dir, today+".log")

        # 获取一个标准的logger, 配置loglevel
        cls.logger = logging.getLogger()
        cls.logger.setLevel(eval("logging." + cf.get_runtime("log_level").upper()))

        # 建立不同handler
        fh = logging.FileHandler(log_file, mode="a")
        ch = logging.StreamHandler()

        # 定义输出格式
        ft = logging.Formatter("%(asctime)s - %(filename)s[line:%(lineno)d] - %(levelname)s: %(message)s")
        fh.setFormatter(ft)
        ch.setFormatter(ft)

        # 把定制handler 添加到我们logger
        cls.logger.addHandler(fh)
        cls.logger.addHandler(ch)

    @classmethod
    def get_logger(cls):
        cls.config_log()
        return cls.logger

if __name__ == "__main__":
    l= Log.get_logger()
    l.info("abc")
    l.debug("hello, debug")
```
#### send_email.py: 数据层-邮件服务器连接
```
"""
1. 从配置文件中读取stmp配置
2. 从report文件夹下打开report.html,发送邮件
"""
import smtplib
from email.mime.text import MIMEText
import os
import sys
sys.path.append("..")
from common.config import Config, pro_path
from common.log import Log


def send_email(report_name):
    cf = Config()
    logger = Log.get_logger()
    report_file = os.path.join(pro_path, cf.get_runtime("report_dir"),report_name)

    with open(report_file, "rb") as f:
        body = f.read()

    # 格式化email正文
    msg = MIMEText(body, "html", "utf-8")

    # 配置email头
    msg["Subject"] = cf.get_email("subject")
    msg["From"] = cf.get_email("user")
    msg["To"] = cf.get_email("receiver")

    
    # 连接smtp服务器,发送邮件
    smtp = smtplib.SMTP()
    smtp.connect(cf.get_email("server"))
    smtp.login(cf.get_email("user"),cf.get_email("pwd"))
    smtp.sendmail(cf.get_email("user"), cf.get_email("receiver"), msg.as_string())
    print("邮件发送成功")

if __name__ == "__main__":
    send_email("report.html")
```
#### case/case.py: 业务逻辑层, 为用例执行封装方法
```
"""
1. 加载数据
2. 发送接口
3. 为用例封装一些方法

"""
import sys
sys.path.append("..")
from common.log import Log
from common.config import Config
from common.db import DB
from common.data import Data
import json
import requests


class Case(object):
    def __init__(self):
        self.logger = Log.get_logger()
        self.cf = Config()

    def load_data(self, data_file):
        self.data = Data(data_file)

    def set_env(self, env):
        self.env = env

    def run_case(self, sheet_name, case_name, var={}):
        case_data = self.data.get_case(sheet_name, case_name)

        url = self.cf.get_server(self.env) + case_data[1]
        data = case_data[4].format(**var)
        
        if case_data[3].lower() == "form":
            data = json.loads(data)
            headers = {}
        else:
            headers = {"content-type": "application/json"}

        if case_data[2].lower() == "get":
            resp = requests.get(url=url)
        else:
            resp = requests.post(url=url, headers=headers, data=data)
        return resp.text
        
    def check_response(self):
        pass
    
    def check_db(self, sql_name, vars={}):
        sql = self.data.get_sql(sql_name).format(**vars)
        return self.db.exec_sql(sql)
        

if __name__ == "__main__":
    c = Case()
    c.set_env("test")
    c.load_data("test_user_data.xlsx")
    r = c.run_case("login", "test_login_normal")
    print(r)
```
#### case/user/test_user.py: 表示层: 测试用例脚本

```
import sys
import random
import pytest
sys.path.append("../..")
from case.case import Case

case = Case()

def setup_module(module):
    case.set_env('dev')
    case.load_data('test_user_data.xlsx')

def test_login_normal():
    result case.run("login", "test_login_normal")

if __name__ == '__main__':
    pytest.main(["-q", "test_user.py"])
```

#### run_all.py: 表示层: 执行所有用例入口

```
import os
import time
from util.config import Config
from util.e_mail import send_email
import pytest

def main():
    cf = Config()
    report_dir = cf.get_report_dir()
    now = time.strftime('%Y%m%d%H%M%S', time.localtime(time.time()))
    report_name = os.path.join(report_dir, 'report_' + now + '.html')
    pytest.main(["-q", "case", "--html=" + report_name])
    send_email(report_name)

if __name__ == '__main__':
    main()
```