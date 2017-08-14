## 通过字典给函数传参

```python
a = {'name':'/etc/passwd','old_file':'./zsh','new_file':'./bash'}
b = ['/etc/passwd','./zsh', './bash']

def func(old_file, new_file, name='./oo'):
    print(old_file)
    print(new_file)
    print(name)

    # 其中字典的键必须与函数形参对应, 键值对与形参对应
func(**a)
	# 列表传值, 元素与形参依次对应, 不推荐
func(*b)
```



## 用类做装饰器

```python
class logit(object):
    def __init__(self, logfile='out.log'):
        self.logfile = logfile

    def __call__(self, func):
        print("123")
        self.notify()
        return func
        
    def notify(self):
        # logit only logs, no more
        pass
# 核心在 __call__ 函数

@logit()
def myfunc1():
    print("456")

myfunc1()
```

与正常的装饰器函数优点:

- 不需要functools.wraps
- 就算没有调用myfunc1这个函数, `__call__()`依然被调用
- 可被继承, 多样化, 操作空间大



## 不要将可变数据类型作为函数参数

```python
def add_to(num, target=[]):
    target.append(num)
    return target

add_to(1)
# Output: [1]

add_to(2)
# Output: [1, 2]

add_to(3)
# Output: [1, 2, 3]

```



## 多使用collections中定义好的数据结构

- defaultdict      字典的扩展
- OrderedDict    
- deque     双端队列, 可作为堆或栈使用
- enum.Enum 

```python
from collections import defaultdict

colours = (
    ('Yasoob', 'Yellow'),
    ('Ali', 'Blue'),
    ('Arham', 'Green'),
    ('Ali', 'Black'),
    ('Yasoob', 'Red'),
    ('Ahmed', 'Silver'),
)

favourite_colours = defaultdict(list)

for name, colour in colours:
    favourite_colours[name].append(colour)

import json
print(json.dumps(favourite_colours))
```

```python
from collections import OrderedDict

d = OrderedDict()
d['a'] = 123
d['v'] = 1
d['f'] = 234

for key, value in d.items():
    print(key+':'+str(value))
```



## 使用Enumerate

```python
my_list = ['apple', 'banana', 'grapes', 'pear']
for c, value in enumerate(my_list, 1):   # 1是可选参数
    print(c, value)
    
counter_list = list(enumerate(my_list, 1))
```



## 上下文管理器

- 基于类的实现

```python
class File(object):
    def __init__(self, file_name, method):
        self.file_obj = open(file_name, method)
    def __enter__(self):
        return self.file_obj
    def __exit__(self, type, value, traceback):
        print("Exception has been handled")
        self.file_obj.close()
        return True
# 主要定义了__enter__ 和 __exit__ 方法
with File('demo.txt', 'w') as opened_file:
    opened_file.undefined_function()
```

- 基于生成器的实现

```python
from contextlib import contextmanager

@contextmanager
def open_file(name):
    f = open(name, 'w')
    yield f
    f.close()
    
# contextmanager函数返回一个以GeneratorContextManager对象封装过的生成器。
# 这个GeneratorContextManager被赋值给open_file函数，我们实际上是在调用GeneratorContextManager对象。
```

