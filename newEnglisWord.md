##2上班笔记(2016.8.26)
[How to install mysql on Ubuntu-14](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-14-04)
[Linux操作系统下MySQL数据库的使用方法](http://tech.sina.com.cn/s/s/2008-12-24/09322685698.shtml)

```html
一：mysql:
  1安装：
  sudo apt-get update
  sudo apt-get install mysql-server
  2确认：
  mysql --version
  sudo service mysql start
  service mysql status
  3连接：
    连接到本机上的MYSQL:
      mysql -uroot -p
    连接到远程主机上的MYSQL:
      mysql -h110.110.110.110 -uroot -pabcd123
  4修改密码：
    格式：mysqladmin -u用户名 -p旧密码 password 新密码
  5增加新用户：
    （增加一个用户test1密码为abc，让他可以在任何主机上登录，并对所有数据库有查询、插入、修改、删除的权限。首先用以root用户连入MYSQL，然后键入以下命令：）
    //all ip
    grant select,insert,update,delete on *.* to test1@"%" Identified by "abc";
    //only localhost
    grant select,insert,update,delete on mydb.* to test2@localhost identified by "abc";
    
二：安装mysql client:   
  python3下django连接mysql
  sudo apt-get install libmysqlclient-dev python3-dev
  pip3 install mysqlclient

三：单词： 
parentheses 括号
validation 验证
suffice 满足
introspective 内省
designate 指定
positional  阵地
optional  可选的
straightforward 直截了当
vote tally  票数
publication 出版物
essential 必要
definitive  明确
minimalists 极简主义
shipped 运
migrate 迁移
interactive 互动
backends  后端
appropriate 适当
```


##1上班笔记(2016.8.25)
[Getting Started Django in English](https://docs.djangoproject.com/en/1.10/intro/)

[使用virtualenv在ubuntu上搭建python 3开发环境](http://my.oschina.net/xiaoiaozi/blog/129769)
```html
cruft 克鲁夫特
parenthesis 插入语
retrieves 检索
renders 呈现
strives 努力
inheritance 遗产
dramatically  显着
well-integrated 良好集成
distribution-specific 配送专用
development 发展
prompt  提示
poll  轮询
drop by 顺便拜访
utility 效用
trailing slash  斜杠
encounters  遭遇战
regex 正则表达式
Arbitrary 随意
kwargs
refer to  参考
unambiguously 明白地
```


