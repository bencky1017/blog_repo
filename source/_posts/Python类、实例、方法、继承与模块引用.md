---
title: Python类、实例、方法、继承与模块引用
tags:
  - Python
categories:
  - 教程
keywords: 'Python类,实例,方法,继承,模块'
description: Python类、实例、方法、继承与模块引用
cover: 'https://yuanxiapi.cn/api/img/photo/42246923.jpg'
top_img: 'https://yuanxiapi.cn/api/img/photo/42246923.jpg'
abbrlink: 48562
comments: false
aside: true
date: 2023-02-16 19:08:11
updated: 2023-02-16 19:08:11
---



***

<font size=5 color=#f33b45>**Python类、实例、方法、继承与模块引用**</font>

<font size=4 color=#3399ea>**原创：丶无殇&emsp;&emsp;2023-02-16**</font>

---
Python类
==

包含：属性 attribute、方法 method

一个人的身高、体重和年龄，这些都是属性，而吃饭、说话和洗澡都是方法

`类`和`实例对象`是有区别的，类是抽象，是模板，而`实例`则是根据类创建的对象

比如类：动物，只是一个抽象，并没有动物的详细信息，而猫、狗等，则是具体的动物，是类的对象。

**在class外部定义的可执行函数叫做function，类内部的函数叫做方法method**

格式
--

类名开头大写，无括号，在**Python3**中`Person`、`Person()`、`Person(object)`，效果一样，但在**Python2**中需要写成`Person(object)`

```python
class Person: # Person/Person()/Person(object)
```

换行缩进后定义属性和方法，属性为变量；方法的定义和函数一样（def开头）

```python
class Person:
    # 属性
    name='zhangsan'
    age=29
    height=1.82

    # 方法
    def greet(self):# 打招呼方法
        print(f"你好，我叫{self.name}，我今年{self.age}岁")

# 创建实例
p1=Person()

# 调用方法
p1.greet()
```

输出：

```python
你好，我叫zhangsan，我今年29岁
```

类的定义是一个具体实例（instance）的设计蓝图，在创建实例的时候，只需要调用`类名()`就可以了

`p1.greet()`是方法调用的示范，在实例后面加上`.`可以调用`方法`和`属性`，如`p1.name`



类的编写规范
--

类名使用：大骆驼命名法（UpperCamelCase）

实例和模块名：蛇形命名法（snake_case）



特殊参数self
--

特殊参数`self`会指向实例本身

`self.name`--->当前被创建实例的`name`属性



字符串格式化输出
--

### 方法一：`%s`/`%d`/`%f`

print时候用格式化符号`%s`/`%d`/`%f`占位，字符串后面紧接`%()`，括号中为对应的参数名称

```python
class Person:
    # 属性
    name='zhangsan'
    age=29
    height=1.82

    # 方法
    def greet(self):# 打招呼方法
        print("你好，我叫%s，我今年%d岁,身高是%.2f米"%(self.name,self.age,self.height))

# 创建实例
p1=Person()

# 调用方法
p1.greet()
```

输出：

```python
你好，我叫zhangsan，我今年29岁,身高是1.82米
```

### 方法二：`f'{`表达式`:`格式化`}'`~[Python3.6新增]~

在输出内容的前面加上`f`，内容中需要变量的地方使用`{}`即可

参数为`浮点数`时候可以使用`:.2f`来设置浮点数的格式

```python
class Person:
    # 属性
    name='zhangsan'
    age=29
    height=1.823

    # 方法
    def greet(self):# 打招呼方法
        print(f"你好，我叫{self.name}，我今年{self.age}岁，身高是{self.height:.2f}米")

# 创建实例
p1=Person()

# 调用方法
p1.greet()
```

输出：

```python
你好，我叫zhangsan，我今年29岁,身高是1.82米
```

### 方法三：`.format`语法

使用`{}`占位，字符串后接`.format()`，括号中为对应的参数名称

参数为`浮点数`时候使用`{:.2f}`设置浮点数的格式

```python
class Person:
    # 属性
    name='zhangsan'
    age=29
    height=1.823

    # 方法
    def greet(self):# 打招呼方法
        print("你好，我叫{}，我今年{}岁，身高是{:.2f}米".format(self.name,self.age,self.height))

# 创建实例
p1=Person()

# 调用方法
p1.greet()
```

输出：

```python
你好，我叫zhangsan，我今年29岁,身高是1.82米
```



初始化方法\_\_init\_\_()
--

### \_\_init__(self)方法

`__init__` 是 Python 中的特殊方法（special method），它用于初始化对象，在实例别创建后最先调用的函数，第一参数永远是`self`

```python
class Person:
    # 初始化方法
    def __init__(self):
        self.name = '张三'

    # 自定义方法
    def greet(self):
        print('你好，我是'+self.name)

p1=Person()
p1.greet()
```

输出：

```python 
你好，我是张三
```

### \_\_init__方法添加参数

在初始化方法中的参数，为`必填参数`，创建实例的时候不填写会报错

```python
class Person:
    # 初始化方法
    def __init__(self,init_name):
        self.name = init_name

    # 自定义方法
    def greet(self):
        print('你好，我是'+self.name)

p1=Person('李四')
p1.greet()
```

输出：

```python 
你好，我是李四
```

### \__init__方法添加任意参数

目前的方法只能传递固定个数的参数，如果想要传递任意参数，如：自定义求平均数的`average()`方法，使用时候可以是`average(22,33,45)`，也可以是`average(2,6,8,5,6,9,10)`

详情见：[可变参数](#可变参数)



属性修改
--

### 修改类属性

创建好`Person`类后，设置类属性`count`，每创建一个实例`count+1`

```python
class Person:
    # 类属性
    count=0
    
    # 初始化方法
    def __init__(self):
        Person.count+=1

# 实例化对象
p1=Person()
p2=Person()
p3=Person()
print(Person.count)
```

输出：

```python
3
```

### 修改实例属性

在创建好实例`p1`后，修改它的属性

```python
# 修改实例属性
p1.age=21
print(p1.age)

# 删除实例属性
del Person.height
print(Person.height)

# 删除实例
del p1
print(p1)
```

删除只能通过删除类属性实现，`不能直接删除`实例属性

删除方法除了`del`还可以使用`delattr()`函数

`delattr(ClassName,Attribute) `相等于 `del ClassName.Attribute`

输出：

```python
# 删除属性，报错内容
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Person' object has no attribute 'height'
# 表示已经删除了'Person.height'属性

# 删除实例，报错内容
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'p1' is not defined
#表示已经删除了'p1'实例对象
```



类属性和实例属性的优先级
--

类属性优先级`高于`实例属性，无法通过实例修改类属性，修改的只是对应的实例属性

```python 
class Animal:
    localtion = 'Asia'
    def __init__(self,localtion):
        self.localtion = localtion

dog = Animal('GuangDong')
cat = Animal('Africa')
print(dog.localtion)		# ==> GuangDong
print(cat.localtion)		# ==> Africa

cat.localtion='ChongQing'
print(cat.localtion)		# ==> ChongQing
print(Animal.localtion)		# ==> Asia
```

输出：

```python
GuangDong
Africa
ChongQing
Asia
```



保护属性与私有属性
--

### 保护属性：_xxx

单下划线开头的属性，只有类实例和子类实例可以访问，不能通过`from module import *`导入，保护属性，不建议调用访问，不会被代码提示工具显示，但是可以直接访问

### 私有属性：__xxx

双下划线开头的属性/方法，只有类对象自己能访问，子类对象无法访问

```python
#-*- coding:utf-8 -*-

class A(object):
    def __init__(self):# 系统定义方法
        self.string='A string'			# 公有属性
        self._string='A _string'		# 保护属性
        self.__string='A __string'		# 私有属性

    def fun(self):
        return self.string + ' fun-A'

    def _fun(self):
        return self._string+'  _fun-A'

    def __fun(self):# 私有方法
        return self.__string+' __fun-A'

    def for__fun(self):# 内部调用私有方法
        return self.__fun()

class B(A):# A的子类
    def __init__(self):# 系统定义方法
        self.string = 'B string'

a=A()
print(a.string)
print(a._string)
# print(a.__string)# 不可访问

print(a.fun())
print(a._fun())
# print(a.__fun())# 不可访问
print(a.for__fun())

b=B()
print(b.fun())
print(b.fun().__len__())# 系统定义函数
```

输出：

```python 
A string
A _string
A string fun-A
A _string  _fun-A
A __string __fun-A
B string fun-A
14
```

### 访问操作私有属性

通过`实例方法`调用`私有属性`，可以实现访问和修改等操作

在外部调用实例方法时，是不需要显式传递self参数的

```python
class Animal:
    # 初始化方法
    def __init__(self,name,age):
        self.__name=name
        self.__age=age

    # 获取信息
    def get_info(self):
        return 'name={},age={}'.format(self.__name,self.__age)

    # 修改信息
    def set_info(self,name,age):
        self.__name=name
        self.__age=age
        
# 实例化对象
dog=Animal('wc',2)
print(dog.get_info())

# 调用实例方法修改私有属性
dog.set_info('nidie',3)
print(dog.get_info())
```

输出：

```python
name=wc,age=2
name=nidie,age=3
```

### <span id="强制访问私有属性">强制访问私有属性</span>

通过实例强制访问私有属性：`实例名._类名__属性名`

```python
class Animal:
    # 初始化方法
    def __init__(self,name,age):
        self.__name=name
        self.__age=age
        
# 实例化对象
dog=Animal('wangwang',2)

# 强制访问私有属性
print(dog._Animal__name)
print(dog._Animal__age)
```

输出：

```python
wangwang
2
```



类方法
--

### 类方法和实例方法的区别

操作实例对象的属性可以使用`实例方法`，如果需要操作类的属性，就需要使用`类方法`

类方法需要使用装饰器`@classmethod`

与实例方法不同的是：

> 1. 类方法需要使用@classmethod来标记为类方法，否则定义的还是实例方法
> 2. 类方法的第一个参数将传入类本身，通常将参数名命名为 cls，上面的 cls.\__localtion 实际上相当于Animal.__localtion
> 3. 类方法无法获得任何实例属性，只能获得类的引用

### 实例方法

在类`Animal`中，创建实例`dog,cat`，可以通过该`实例`调用的方法，如`dog.get_info`等

```python
# -*- coding=utf-8 -*-
class Animal:
    # 私有属性
    __count=0
    
    # 初始化方法
    def __init__(self,name,age):
        self.name=name
        self.age=age
        Animal.__count+=1
    
    # 实例方法
    def get_info(self):
        return '我是{}，今年{}岁了。总计数：{}个'.format(self.name,self.age,self.__count)
    
    # 类方法
    @classmethod
    def get_cnt(cls):
        return cls.__count
        
dog=Animal('汪汪',2)
cat=Animal('喵喵',3)
print(dog.get_info())
print(cat.get_info())
```

输出：

```python
我是汪汪，今年2岁了。总计数：2个
我是喵喵，今年3岁了。总计数：2个
```

### 类方法

类方法不能直接操作实例属性，必须通过类实例才能操作。

类方法`推荐`使用`类名直接调用`，当然也可以使用`实例对象调用`（不推荐）。

如`Animal.get_cnt`可以调用，使用`dog.get_cnt`也可以调用，但是不推荐这样使用

```python
dog=Animal('汪汪',2)
cat=Animal('喵喵',3)
print(dog.get_cnt())
print(Animal.get_cnt())
```

输出：

```python
2
2
```



继承类
--

当已经创建了一个类`Person`后，还可以再细分为其他类，这些类和`Person`类相似，比如添加几个属性，修改几个方法

此时，不需要重新新建一个类，可以从原来的类中派生一个新的类，原来的称为`父类`或者`基类/超类`，派生出的称为`子类`，子类继承了父类的所有数据和方法

```python
# 父类
class Animal:
    def __init__(self,name):
        self.name=name
    
    def greet(self):
        print(f'我是{self.name}')

# 子类继承父类
class Dog(Animal):
    def greet(self):
        print(f'汪汪，我是{self.name}')
        
```

Dog 类是从 Animal 类继承而来的，Dog 类自动获得了 Animal 类的所有数据和方法，而且还可以对从父类继承来的方法进行修改，调用的方式是一样的

```python
animal = Animal('animal')
animal.greet()
dog = Dog('dog')
dog.greet()
```

输出：

```python
我是animal
汪汪，我是dog
```

### 子类添加方法

给子类`Dog`添加一个`run`的方法

```python
# 子类
class Dog(Animal):
    def greet(self):
        return (f'汪汪，我是{self.name}')

    # 跑的方法
    def run(self):
    	return ('撒丫子')

dog=Dog('dog')
print(dog.greet()+'，我在'+dog.run())
```

输出：

```python
汪汪，我是dog，我在撒丫子
```

### super()函数

`super()` 函数是用于调用父类的一个方法

是用来解决多重继承问题的，直接用类名调用父类方法在使用单继承的时候没问题，但是如果使用多继承，会涉及到MRO【方法解析顺序(Method Resolution Order)】、重复调用（钻石继承）等种种问题

#### 语法~[Python2]~

```python
super(class[,self]).method(param1...)
super(class[,self]).__init__(param1...)
```

此处的`class`为当前的`子类名`，如`class Person`中，子类`class Student(Person)`，`super`语句为`super(Student,self).__init__(name,age)...`

#### 语法~[Python3]~

```python
super().method(param1...)
super().__init__(param1...)
```

#### 示例

继承父类的属性和方法，使用`spuer`方法，新增的属性单独添加

```python
# 父类
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def greet(self):
        print(f'我是{self.name}，我{self.age}了')

# 子类
class Teacher(Person):
    def __init__(self,name,age,score):
        # 继承父类的属性，使用super继承name,age
        super(Teacher,self).__init__(name,age) # super(Teacher,self).__init__(name,age)
        # 新增的属性单独添加
        self.score=score
    
    def greet(self):
        # 继承父类的方法，输出内容为父类的print内容
        super(Teacher,self).greet() # super(Teacher,self).greet()
        print(f'我是{self.name}，我{self.age}了，综合评分{self.score}')

t=Teacher('张三',29,87.5)
t.greet()
```

输出：

```python
我是张三，我29了
我是张三，我29了，综合评分87.5
```

### 实例

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

class Parent(object):
    def __init__(self):
        self.parent = '我是父类'
        print ('Parent')

    def info(self,message):
        print ("%s 来自父类" % message)

class Child(Parent):
    def __init__(self):
        # super(Child,self)首先找到Child的父类Parent，然后把类Child的对象转换为类Parent的对象
        super(Child,self).__init__()
        print ('子类')

    def info(self,message):
        super(Child, self).info(message)
        print ('子类的 info 方法')
        print (self.parent)

# 主函数
if __name__ == '__main__':
    child = Child()
    child.info('Hello World')
```

输出：

```python
Parent
子类
Hello World 来自父类
子类的 info 方法
我是父类
```



isinstance()函数类型判断
--

通过`isinstance()`函数可以判断一个变量的类型

### 语法

```python
isinstance(type,class)# 判断type是不是class类型
```

### 实例

#### 定义类

现有父类`Person(name,gender)`，子类`Student(name,gender,score)`、`Teacher(name,gender,course)`

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score

class Teacher(Person):
    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course
```

#### 实例化对象

```python
p = Person('Tim', 'Male')
s = Student('Bob', 'Male', 88)
t = Teacher('Alice', 'Female', 'English')
```

#### 判断父类

判断`p,s,t`这几个变量的时候可以使用`isinstance()`判断类型

```python
isinstance(p,Person)	# ==> True
isinstance(p,Student)	# ==> False
isinstance(p,Teacher)	# ==> False
```

这说明在继承链上，一个父类的实例不能是子类类型，因为子类比父类多了一些属性和方法

#### 判断子类

```python
isinstance(s,Person)	# ==> True
isinstance(s,Student)	# ==> True
isinstance(s,Teacher)	# ==> False
```

因为`Student`继承自`Person`，所以`s`也是`Person`类型



多态
--

它是指对不同类型的参数进行相同的操作，根据对象类型不同做出不同的行为，继承拿到父类的数据和方法，子类可以重新父类的方法，可以自己添加新的方法，有了继承才有多态，实现为不同数据提供一个统一的接口

### 实例

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
    def who(self):
        return 'I am a Person, my name is %s' % self.name

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score
    def who(self):
        return 'I am a Student, my name is %s' % self.name

class Teacher(Person):
    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course
    def who(self):
        return 'I am a Teacher, my name is %s' % self.name
    
p = Person('Tim', 'Male')
s = Student('Bob', 'Male', 88)
t = Teacher('Alice', 'Female', 'English')

print(p.who())
print(s.who())
print(t.who())
```

输出：

```python
I am a Person, my name is Tim
I am a Student, my name is Bob
I am a Teacher, my name is Alice
```

这种行为别成为多态，一般调用的时候先从子类自身查找方法，如果自身没有，再按照继承链向上找



多重继承
--

多种继承主要在出现组合情况的时候使用，如果没有多重继承，那么使用组合情况可能需要更多的子类

例如python的网络服务器有：`TCPServer`、`UDPServer`、`UnixStreamServer`、`UnixDatagramServer`

服务器运行模式有：`多线程ThreadingMixin`和`多进程ForkingMixin`

要创建`多线程`的`TCPServer`

```python
class MyServer(TCPServer,ThreadingMixin)
```

要创建`多进程`的`UPDServer`

```python
class MyServer(UPDServer,ForkingMixin)
```

### 实例

已知类Student、Teacher继承Person类，技能类BasketballMixin、FootballMixin继承SkillMixin类，请通过多重继承，分别定义“会打篮球的学生”和“会踢足球的老师”

```python
# -*- coding=utf-8 -*-
# 人员
class Person(object):
    def __init__(self):
        print("Person")
    
class Student(Person):
    def __init__(self):
        super(Student,self).__init__()
        print("Student")

class Teacher(Person):
    def __init__(self):
        super(Teacher,self).__init__()
        print("Teacher")

# 技能
class SkillMixin(object):
    def __init__(self):
        print("SkillMixin")

class BasketballMixin(SkillMixin):
    def __init__(self):
        super(BasketballMixin,self).__init__()
        print("BasketballMixin")

class FootballMixin(SkillMixin):
    def __init__(self):
        super(FootballMixin,self).__init__()
        print("FootballMixin")

# 会打篮球的学生
class BasketballStudent(BasketballMixin,Student):
    def __init__(self):
        super(BasketballStudent,self).__init__()
        print('会打篮球的学生')

# 会踢足球的老师
class FootballTeacher(FootballMixin,Teacher):
    def __init__(self):
        super(FootballTeacher,self).__init__()
        print('会踢足球的老师')

s=BasketballStudent()
t=FootballTeacher()
```

输出：

```python
SkillMixin
BasketballMixin
会打篮球的学生
SkillMixin
FootballMixin
会踢足球的老师
```



获取对象信息
--

前文中，可以通过`isinstance()`方法来判断是否是某个类型，现在需要获取更多的信息

### 获取类型type()

通过`type()`方法可以获取变量的类型

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score

p = Person('Alice', 'Female')
s = Student('Bob', 'Male', 100)
type(p) # ==> <class '__main__.Person'>
type(s) # ==> <class '__main__.Student'>
```

输出：

```python 
<class '__main__.Person'>
<class '__main__.Student'>
```

### 获取属性dir()

通过`dir()`方法可以获取变量的所有属性

```python
dir(p)
```

输出：

```python 
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'gender', 'name']
```

`dir()`返回的属性是`字符串列表`，其中`__xxx__`为特殊属性和方法，可以直接访问

如果其中存在`私有属性`，如：初始化属性中的`gender`改为`self.__gender=gender`，则输出：

```python
['_Person__gender', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', 
'__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'name']
```

### 获取设置对象属性

`dir()`返回的属性是`字符串列表`，如果已知一个属性名称，要获取或者设置对象的属性，就需要用 `getattr() `和` setattr()`函数

如上例中的：

```python
p = Person('Alice', 'Female')
s = Student('Bob', 'Male', 100)
```

获取`p`的`name`属性

```python
getattr(p,'name')				# ==> 'Alice'
```

如果有私有属性，需要强制访问，方式为`_类名__属性名`（详情见：[强制访问私有属性](#强制访问私有属性)）

```python
getattr(p,'_Person__gender')	# ==> 'Female'
```

如果获取的属性不存在，则会报错

```python
getattr(p,'age')	# ==> AttributeError: 'Person' object has no attribute 'age'
```

如果获取的属性不存在，指定默认返回值

```python
getattr(p,'age',20)				# ==> 'Female'
```

设置属性值

```python
setattr(p,'name','Mike')		# 'Alice' ==> 'Mike'
```

### <span id="可变参数">可变参数</span>

可以用`setattr()`方法来设置属性值，可变参数，可以用来添加任意关键字参数，以`键值对`的方式设置值

```python
class Person(object):
    def __init__(self, name, gender, **agrv):
        self.name = name
        self.gender = gender
        for k,v in agrv.items():
            setattr(self,k,v)
            
p = Person('Bob', 'Male', age=18, course='Python')
print(p.age)
print(p.course)
```

输出：

```python
18
Python
```

如果不使用`setattr()`方式来添加参数，可以使用`for循环遍历`，例如设计一个求平均数的函数

```python 
def average(*agrv):
    sum = 0
    if len(agrv) == 0:
        print(sum)
    for i in agrv:
        sum += i
    avg = sum / len(agrv)
    print(avg)

average(1,5,6,24)
```

输出：

```python
9.0
```



类的特殊方法
--

### \_\_str__()方法

通常变量可以通过`str()`函数转换为字符串类型输出，但是自定义的类无法转换成字符串

```python 
class Person:
    # 初始化方法
    def __init__(self):
        self.name = '张三'

    # 自定义方法
    def greet(self):
        print('你好，我是'+self.name)

p1=Person()
p1.greet()
str(p1)
```

输出：

```python
你好，我是张三
'<__main__.Person object at 0x00000257907AD760>'
```

输出发现`str()`返回的是这个实例的地址，这是因为使用的是对象的内建方法`__str__`返回的

如果自定义的类也实现`__str__()`方法，便可以转换为字符串输出

```python
class Person:
    # 初始化方法
    def __init__(self):
        self.name = '张三'

    # 自定义方法
    def greet(self):
        print('你好，我是'+self.name)
        
    def __str__(self):
        return '你好，我是'+self.name	# return str(self.name)

p1=Person()
p1.greet()
str(p1)
```

输出：

```python
你好，我是张三
'你好，我是张三'
```

此时发现，如果只输入`p1`，显示的仍然是地址

```python
<__main__.Person object at 0x00000257907A4E50>
```

### \_\_repr__()方法

上述情况是因为Python定义了`__str__()`和`__repr__()`两种方法，`__str__()`显示给用户，而`__repr__()`显示给开发人员，当使用`str()`时候，实际调用的是`__str__()`方法，而直接输入变量，调用的是`__repr__()`方法，所以需要再实现`__repr__()`方法

```python
class Person:
    # 初始化方法
    def __init__(self):
        self.name = '张三'

    # 自定义方法
    def greet(self):
        print('你好，我是'+self.name)
        
    def __str__(self):
        return '你好，我是'+self.name
    
    def __repr__(self):
        return '你好，我是'+self.name

p1=Person()
p1.greet()
str(p1)
```

输出：

```python
你好，我是张三
'你好，我是张三'
你好，我是张三
```

### \_\_len__()方法

对于列表List和元组Tuple，都可以使用内建方法len()来获取元素个数，如果需要达到这个效果，就需要实现`__len__()`方法

例如有个班级Class类，初始化把学生列表传进去，通过len()函数可以返回学生个数

```python
class Class:
    def __init__(self,students):
        self.students=students
        
    def __len__(self):
        return len(self.students)

stu=['Mike','James','Alice']
cls=Class(stu)
print(f'此班级有 {len(cls)} 名学生')
```

输出：

```python
此班级有 3 名学生
```

#### 实例

实现一个斐波那契数列：0,1,1,2,3,5,8...，创建一个`Fib`类，`Fib(10)`表示数列前十个元素，`print(Fib(10))`可以打印输出，`len(Fib(10))`可以返回数列个数10

```python
class Fib(object):
    def __init__(self,num):
        self.res=[]
        self.num=num
        a,b=0,1
        for i in range(num):
            self.res.append(a)
            a,b=b,a+b
    def __str__(self):
        return str(self.res)
        
    def __len__(self):
        return len(self.res)
        
f=Fib(10)
print(f)
print(str(f))
print(len(f))
```

输出：

```python
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
10
```

### \_\_slots__()方法

用来限制可添加的属性，如此时有一个`Student`类，包含`name,gender,score`这几个属性

```python
class Student:
    def __init__(self,name,gender,score):
        self.name = name
        self.gender = gender
        self.score = score
```

类中的参数都可以动态的添加，如此时再添加一个`age`属性

```python
s=Student('Mike','Male',87)
s.age=25	# 动态添加属性age
```

如果不做限制，会有很多属性，不便于后期管理，所以需要使用`__slots__()`方法来限制添加的属性

```python
class Student:
    __slots__ = ('name', 'gender', 'score','total')
    def __init__(self,name,gender,score):
        self.name = name
        self.gender = gender
        self.score = score
```

此时执行动态添加属性`age`的语句，会报错，如果添加`total`则不会报错

```python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Student' object has no attribute 'age'
```

假设Person类通过`__slots__`定义了`name`和`gender`，请在派生类`Student`中通过`__slots__`继续添加`score`的定义，使`Student`类可以实现`name`、`gender`和`score`3个属性。

```python
class Person(object):
    __slots__=['name','gender']
    def __init__(self,name,gender):
        self.name=name
        self.gender=gender

class Student(Person):
    __slots__=['score']
    def __init__(self,name,gender,score):
        super(Student,self).__init__(name,gender)
        self.score=score

s=Student('Alice','Female',96)
s.name='Bob'
s.score=87
print(s.score)
```

### \_\_call__()方法

Python中，函数是一个对象，可以将一个函数赋值给一个变量，且不改变函数的功能

```python
>>> f=abs
>>> f
<built-in function abs>
>>> f.__name__
'abs'
>>> f(-123)
123
```

此时，`f`被称为`可调用的对象`，其实所有的函数都是`可调用对象`

如果把一个类实例也变成一个可调用对象(函数)，需要实现一个`__call__()`方法

```python
class Person:
    def __init__(self,name,age):
        self.name = name
        self.age = age
    
    def __call__(self,friend):
        print('My name is {}.'.format(self.name))
        print('My friend is {}.'.format(friend))
      
p=Person('Bob',25)
p('Mike')		# ==> 用函数的方式调用Person类的实例p
```

输出：

```python
My name is Bob.
My friend is Mike.
```

#### 实例

对前面的斐波那契数列类`Fib`，加入`__call__`方法

```python
class Fib(object):
    def __init__(self):
        self.res=[]
        
    def __call__(self,num):
        self.num=num
        a,b=0,1
        for i in range(num):
            self.res.append(a)
            a,b=b,a+b
        return self.res
f=Fib()
print(f(10))	# 可以像函数一样调用
```

输出：

```python
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```



模块和包
--

为了便于管理自定义的内容，可以将模块根据特定规则划分到包中

导入格式：`from 包 import 模块`

包必须包含`__init__.py`文件，模块文件没有`__init__.py`文件

### 自定义模块

定义一个叫`tools`的模块，模块名：`tools.py`

```python
# tools.py
def say_hello(name):
    print('你好啊{}'.format(name))

def say_goodbye(name):
    print('拜拜{}'.format(name))
```

### 格式

`import 模块名1 [as 别名1], 模块名2 [as 别名2]，…`

`from 模块名 import 成员名1 [as 别名1]，成员名2 [as 别名2]，…`

### 导入模块

导入官方模块不需要考虑路径问题，导入自定义模块需要考虑路径（详情见：[导入模块的路径](#导入模块的路径))

导入整个模块

```python
import MODULE
```

导入模块的部分属性或函数

```python
from PACKAGE import MODULE
```

导入模块中的所有内容

```python
from PACKAGE import *
```

为了防止导入的函数与本文件的函数冲突，有两种方法解决：

1. 直接导入模块，不指定具体内容
2. 使用`from PACKAGE import MODULE as NAME`把导入的内容进行重命名

如使用两种方法导入`math`模块的`sin(),cos()`函数

```python
# 从模块导入所有类
from math import sin,cos,pi
sin(pi/2)
cos(pi/3)

# 导入整个模块
import math
math.sin(pi/2)
math.cos(pi/3)

# 使用别名
from math import sin as s,pi
s(pi/2)
```

### <span id="导入模块的路径">导入模块的路径</span>

使用`sys`模块中的`path`变量，可以得到一个路径列表，导入模块的时候会搜索这个路径列表，如果想要添加路径，可以给`sys.path`赋值

```python
import sys					# 或from sys import path
sys.path.append('../')		#   path.append('../')
```