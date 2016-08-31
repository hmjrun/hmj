##5笔记(2016.8.31)
[理解Python中的装饰器](http://www.cnblogs.com/rollenholt/archive/2012/05/02/2479833.html)

```python
def test_kwargs(first, *args, **kwargs):
   print 'Required argument: ', first
   for v in args:
      print 'Optional argument (*args): ', v
   for k, v in kwargs.items():
      print 'Optional argument %s (*kwargs): %s' % (k, v)

test_kwargs(1, 2, 3, 4, k1=5, k2=6)
# results:
# Required argument:  1
# Optional argument (*args):  2
# Optional argument (*args):  3
# Optional argument (*args):  4
# Optional argument k2 (*kwargs): 6
# Optional argument k1 (*kwargs): 5

import time
def performance(unit):
    def perf_decorator(f):
        def wrapper(*args, **kw):
            t1 = time.time()
            r = f(*args, **kw)
            t2 = time.time()
            t = (t2 - t1) * 1000 if unit=='ms' else (t2 - t1)
            print 'call %s() in %f %s' % (f.__name__, t, unit)
            return r
        return wrapper
    return perf_decorator

@performance('ms')
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))

print factorial(10)
#result:
#call factorial() in 4.050970 ms
#3628800
```
```html
二：单词
  contrbuting 贡献
  regulary  监管
  feedback  反馈
  widest  最宽
  audience  听众
  conduct 进行
  inclusive 包括的
```

##4笔记(2016.8.30)

```html
一：打包，安装应用
  //在 django/polls 目录里运行
  python setup.py sdist
  
  //安装这个包，得用到pip
  pip install --user django-polls/dist/django-polls-0.1.tar.gz
  
二：单词
  captured 抓获           automated 自动化
  routines  例程          identify  鉴定
  merely as 仅仅作为      negative aspect 消极的一面
  brilliant 辉煌          maintaining 维持
  strategies  策略        conventional  常规
  inadvertently 不经意间  reintroduce 重新引入
  comprehensive 全面      interacts 交互
  disposal  处置          simulate  模拟
  comprised 由            Customize 定制
  impressive  有声有色    intuitive 直观的
  intuitive 直观的        dozens  数十
  element 元件            tuple   元组
  inefficient 低效        slot    插槽
  arbitrary   随意        prerequisites 先决条件
```

##3笔记(2016.8.29)
```html
一：单词
  shortcuts 快捷键          specific 具体
  archive 档案              idiom 成语
  Raising 提高              arbitrary 随意
  partially 部分            hardcoded 硬编码
  tightly-coupled 紧密耦合  reliance  依赖
  explicitly  明确地        altered 改变
  via 通过                  generic 通用
  redundant 冗              Convert 兑换
  code-shuffle  代码洗牌    Amend 修改
```

##2笔记(2016.8.26)
[How to install mysql on Ubuntu-14](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-14-04)

[Linux操作系统下MySQL数据库的使用方法](http://tech.sina.com.cn/s/s/2008-12-24/09322685698.shtml)

```html
一：mysql:
  1，安装：
  sudo apt-get update
  sudo apt-get install mysql-server
  
  2，确认：
  mysql --version
  sudo service mysql start
  service mysql status
  
  3，连接：
    连接到本机上的MYSQL:
      mysql -uroot -p
    连接到远程主机上的MYSQL:
      mysql -h110.110.110.110 -uroot -pabcd123
      
  4，修改密码：
    格式：mysqladmin -u用户名 -p旧密码 password 新密码
    
  5，增加新用户：
    （增加一个用户test1密码为abc，让他可以在任何主机上登录，并对所有数据库有查询、插入、修改、删除的权限。
    首先用以root用户连入MYSQL，然后键入以下命令：）
    //all ip
    grant select,insert,update,delete on *.* to test1@"%" Identified by "abc";
    //only localhost
    grant select,insert,update,delete on mydb.* to test2@localhost identified by "abc";
    
二：安装mysql client:   
  python3下django连接mysql
  sudo apt-get install libmysqlclient-dev python3-dev
  pip3 install mysqlclient
  
三：django命令
   //交互命令，feel free rich API
   python manage.py shell 
   
   //The sqlmigrate command takes migration names and returns their SQL:
   python manage.py sqlmigrate polls 0001 
   
   //run migrate again to create those model tables in your database：
   python manage.py migrate
   
   //开启web服务器
   python manage.py runserver 
   
   //创建管理员
   python manage.py createsuperuser
   
   //创建应用
   python manage.py startapp app_name
   
   //添加应用 /projectName/projectName/settings.py
   INSTALLED_APPS = [
    'polls.apps.PollsConfig',
    'django.contrib.admin',
    ...
]
   
   
四：单词： 
  parentheses 括号          validation 验证
  suffice 满足              introspective 内省
  designate 指定            positional  阵地
  optional  可选的          straightforward 直截了当
  vote tally  票数          publication 出版物
  essential 必要            definitive  明确
  minimalists 极简主义      shipped 运
  migrate 迁移              interactive 互动
  backends  后端            appropriate 适当
```


##1上班笔记(2016.8.25)
[Getting Started Django in English](https://docs.djangoproject.com/en/1.10/intro/)

[Getting Started Django in zh_CN](http://django-intro-zh.readthedocs.io/zh_CN/latest/)

```html
一：Virtualenv
  //首先，安装virtualenv，在默认的python2下的pip就行
  [sudo] pip install virtualenv
  
  //创建虚拟环境:
  virtualenv -p /usr/bin/python3 py3env
  
  //激活虚拟环境：
  source py3env/bin/activate
  
  //退出python3虚拟环境
  deactivate
二：单词
  cruft 克鲁夫特        parenthesis 插入语
  retrieves 检索        renders 呈现
  strives 努力          inheritance 遗产
  dramatically  显着    well-integrated 良好集成
  prompt  提示          distribution-specific 配送专用
  poll  轮询            drop by 顺便拜访
  utility 效用          trailing slash  斜杠
  encounters  遭遇战    regex 正则表达式
  Arbitrary 随意        kwargs
  refer to  参考        unambiguously 明白地
```
