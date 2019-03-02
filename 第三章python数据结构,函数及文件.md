
## 元组

### 1.创建元组


```python
# 直接用逗号分隔,创建元组
tup=1,2 
tup=(1,2),(3,4) 

# tuple函数能将任意序列,列表迭代器等转化为元组
tup=tuple([1,2,3])
tup=tuple('python') # 字符串实际也类似一个元组,不可修改

gener=(i for i in range(0,5))
tup=tuple(gener)

tup
```




    (0, 1, 2, 3, 4)



### 2.访问元组


```python
# 访问元组元素的方法与list相似
for i in tup:
    print(i)
    
tup[0]
```

    0
    1
    2
    3
    4
    




    0




```python
# 元组内的元素不可修改,但如果元组内的对象是可变的如list,则可以在原位进行修改
tup=('a',[1,2])
tup[1].append(3)
tup
```




    ('a', [1, 2, 3])



### 3.组合元组


```python
# 通过加法运算符,串联多个元组
tup1=(1,2,3)
tup2=(4,5,6)
tup=tup1+tup2
print(tup)

# 通过乘法运算符号,复制串联元组
tup=('a','b','c')*2
tup
```

    (1, 2, 3, 4, 5, 6)
    




    ('a', 'b', 'c', 'a', 'b', 'c')



### 4.拆分元组


```python
# 直接通过逗号按顺序拆分元组
tup=(1,2,3)
a,b,c=tup
print("a={0},b={1},c={2}".format(a,b,c),end='\n\n')

tup=1,2,(3,4)
a,b,(c,d)=tup
print('d=%d'%d,end='\n\n')

# 拆分元组运用到变量的赋值交换上
a,b=1,2
a,b=b,a
print("a={0},b={1}".format(a,b),end='\n\n')

# 拆分元组运用到迭代序列上:
for a,b,c in [(1,2,3),(4,5,6)]:
    print("a={0},b={1},c={2}".format(a,b,c))

'''实际上字典在进行遍历时,items方法也是将字典结构转化为如上元组形式'''
```

    a=1,b=2,c=3
    
    d=4
    
    a=2,b=1
    
    a=1,b=2,c=3
    a=4,b=5,c=6
    




    '实际上字典在进行遍历时,items方法也是将字典结构转化为如上元组形式'




```python
# 高级拆分功能: 只取元组的前几个元素, 剩下元素存储在一个list中

a,b,*rest=(1,2,3,4)
a,b
```




    (1, 2)




```python
rest
```




    [3, 4]




```python
# 习惯的写法
a,b,*_=(1,2,3,4)
```


```python
# 方法count,返回指定元素出现的频率
tup=(2,2,2,3,4)
print(tup.count(2))
```

    3
    

## 列表list

### 1. 增 删 改 查 排序

### 增


```python
'''增'''
a=[7, 6, 5, 2, 3]
b=[1,2,3,4,5]

a.append(0) # 增加在列表后面

a.insert(2,'a') # 根据索引进行插入

a+=b # 合并两个列表,从前一个列表后面开始添加

a.extend(b) # 合并两个列表,与上述相同

print(a) 
```

    [7, 6, 'a', 5, 2, 3, 0, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
    

### 删


```python
'''删'''
a=[7, 6, 5, 2, 3]

a_pop =a.pop(0) # 通过索引删除元素,并返回删除的元素
 
a.remove(6) # 通过元素名来删除元素

print(a)
```

    [5, 2, 3]
    

### 改


```python
'''改'''

a=[7, 6, 5, 2, 3]

a[1]=0 # 直接通过索引更改

print(a)
```

    [7, 0, 5, 2, 3]
    

### 查


```python
'''查'''

a=[7, 6, 5, 2, 3]

print(a[1]) # 通过索引返回元素

print(a.index(6)) # 通过元素返回索引

print(a[0:-1]) # 切片,区间为"[head,tail)"

print(a[::2]) # 指定步长输出
```

    6
    1
    [7, 6, 5, 2]
    [7, 5, 3]
    


```python
# 二分查找
import bisect

arr=[1, 2, 2, 2, 3, 4, 7]
insert_index=bisect.bisect(arr,5) # 用二分法查找,要插入的值在list中的位置,并返回索引
print(insert_index)

arr=[1, 2, 2, 2, 3, 4, 7] # 直接插入值
bisect.insort(arr,5)
print(arr)
```

    6
    [1, 2, 2, 2, 3, 4, 5, 7]
    

### 排序


```python
'''排序'''

a=[7, 6, 5, 2, 3]
words=['asdfa','dfd','sadddd','adfa']

a.sort(reverse=False) # 升序(默认reverse=False)

words.sort(key=len) # 通过key指定规则排序,例如字数

a=sorted(a) # 返回一个升序排序的list

a=list(reversed(a)) # reversed方法返回一个逆序排列的迭代器

a=a[::-1] # 通过步长巧妙的逆序输出

print(words)
print(a)

```

    ['dfd', 'adfa', 'asdfa', 'sadddd']
    [2, 3, 5, 6, 7]
    

## 字典dictonary

### 1.创建 增 删 改 查 分类

### 创建


```python
'''创建'''

dic={0:'a',1:'b',2:'c'} # 直接通过键值对创建

a=[7, 6, 5, 2, 3]
b=[1,2,3,4,5]
dic=dict(zip(a,b)) # zip()函数将两个同长度的list的对应位置元素组成tuple,从而通过函数dict构造字典
```

### 增


```python
'''增'''

dic[5]='a' # 直接通过键来增加元素

dic1={0:'a',1:'b',2:'c'}
dic2={3:'d',4:'e',5:'f'}
dic1.update(dic2) # 方法update用于合并两个字典,但重复的键的值会被覆盖
```

### 删


```python
'''删'''

dic={0:'a',1:'b',2:'c'}

del dic[0] # del方法,通过键来删除元素

dic_pop=dic.pop(1) # 通过键来删除元素, 返回对应值
```

### 改


```python
'''改'''

dic={0:'a',1:'b',2:'c'}

dic[1]='f' # 直接通过键来更改"

print(dic)
```

    {0: 'a', 1: 'f', 2: 'c'}
    

### 查


```python
'''查'''

dic={0:'a',1:'b',2:'c'}

print(dic[0]) # 通过键返回值

print(dic.keys()) # 返回所有键

print(dic.values()) # 返回所有值

for key,value in dic.items():
    print('{}={}'.format(key,value)) # 遍历键值对
    
value=dic.get(1,'none') # get(a,b)字典中有a这个键返回对应值, 否则返回b 
print(value)
```

    a
    dict_keys([0, 1, 2])
    dict_values(['a', 'b', 'c'])
    0=a
    1=b
    2=c
    b
    

### 分类


```python
'''分类'''

words = ['apple', 'bat', 'bar', 'atom', 'book']

'''将列表中的元素按照首字母分类'''

# 法一: 通过判断语句进行分类

by_letters={}
for word in words:
    letter=word[0]
    if letter not in by_letters: 
        by_letters[letter]=[word]
    else:
        by_letters[letter].append(word)
print(by_letters)

# 法二: 通过设置默认值来完成分类

by_letters_2={} 
for word in words:
    letter=word[0]
    # 如果key存在于字典,返回对应value,否则在字典中创建默认键值对,返回对应value
    # 即 dic[default_key]=default_value if key not in dic else return dic[key]
    by_letters_2.setdefault(letter,[]).append(word) 
print(by_letters_2)

# 指定字典默认value为list
from collections import defaultdict
by_letters_3=defaultdict(list)
for word in words:
    by_letters_3[word[0]].append(word)
print(by_letters_3)
```

    {'a': ['apple', 'atom'], 'b': ['bat', 'bar', 'book']}
    {'a': ['apple', 'atom'], 'b': ['bat', 'bar', 'book']}
    defaultdict(<class 'list'>, {'a': ['apple', 'atom'], 'b': ['bat', 'bar', 'book']})
    

### 有效键值类型
#### python中任意对象都可作为value , 而key通常是不可变的标量(整数 , 浮点数 ,字符串)或元组(内部元素不可变)
#### 这被称为可哈希性 , 可以通过哈希函数 hash 来检验对象是否可以用作key


```python
print(hash('string'))
print(hash((1,2,3)))

#print(hash((1,[2,3]))) list不满足会报错

dic={tuple([1,2,3]):'a'} # 如果要用list作为key,需要先用tuple转化为元组
dic
```

    -8286288899946027828
    2528502973977326415
    




    {(1, 2, 3): 'a'}



## 集合
#### 集合类似于只有键的字典,集合内元素不重复

### 创 增 删 运算


```python
'''创'''
a={1,2,3,4} 
b=set([4,5,6]) # set函数将只含有可哈希元素的序列转换为集合类型

'''增'''
a.add(4) 

'''删'''
a.remove(4)
r=a.pop() # 从首部删除元素并返回元素
b.clear() # 清空集合
```

### 运算


```python
a={1,2,3,4,5}
b={1,2,3,4,6}

# 并集
m=a.intersection(b)
n=a&b

# 交集
m=a.union(b)
n=a|b

print(a.issubset(m)) # 判断后一个集合是否是前一个的子集
print(a.issuperset(m)) # 判断后一个集合是否是前一个的父集
 
print(a==b) # 判断两个集合的内容是否相同
```

    True
    False
    False
    

## 列表集合字典推导式
#### 用于快速的进行筛选构造序列对象

### 列表:[expr for val in collection if condition]


```python
strings = ['a', 'as', 'bat', 'car', 'dove', 'python']

[word.upper() for word in strings if len(word)>2]
```




    ['BAT', 'CAR', 'DOVE', 'PYTHON']



### 字典:{key_expr : value_expr for value in collection if condition}


```python
dic={'a':1,'b':2,'c':3,'d':4}

{key.upper():value for key,value in dic.items() if value>1}
```




    {'B': 2, 'C': 3, 'D': 4}



### 集合:{expr for val  in collection if condition}


```python
strings = ['a', 'as', 'bat', 'car', 'dove', 'python']

{len(x) for x in strings}
```




    {1, 2, 3, 4, 6}




```python
set(map(len,strings)) # 可以用map函数进行简化,map函数返回一个迭代器
```




    {1, 2, 3, 4, 6}




```python
# 利用推导式构造一个字符串映射表
loc_mapping={key:value for key,value in enumerate(strings)}
loc_mapping
```




    {0: 'a', 1: 'as', 2: 'bat', 3: 'car', 4: 'dove', 5: 'python'}



## 嵌套列表推导式


```python
'''假设有一个嵌套列表,每个列表中都包含一些名字,我们需要一个列表其中存放所有名字中带有2个e及以上的名字'''
all_data=[['John', 'Emily', 'Michael', 'Mary', 'Steven'],['Maria', 'Juan', 'Javier', 'Natalia','Pilar']]
```


```python
# 法一:循环
names_e_all=[]
for names in all_data:
    names_e=[name for name in names if name.count('e')>=2]
    names_e_all.extend(names_e)
names_e_all
```




    ['Steven']




```python
# 法二:嵌套列表推导式
'''实际上结构为:
[(首:组成最终列表的元素) (外循环:for values in data 内循环:for value in values) (尾:判断条件)]
'''
[name for names in all_data for name in names if name.count('e')>=2]
```




    ['Steven']




```python
'''将如下嵌套列表,扁平化为一个整数列表'''
some_tuples = [(1, 2, 3), (4, 5, 6), (7, 8, 9)]

flattened=[x for tup in some_tuples for x in tup]
flattened
```




    [1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
'''将some_tuples转化为嵌套列表形式'''
some_lists=[[x for x in tup] for tup in some_tuples]
some_lists
```




    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]



## 命名空间, 作用域, 局部函数

#### python中变量的作用域被称为命名空间 , 局部命名空间(local)在函数调用时被创建 ,在函数调用完毕后被销毁


```python
def func():
    a=[]
    for i in range(5):
        a.append(i)
a=[]
func()
a
```




    []



#### 利用global关键字声明 , 可以将局部变量声明到全局变量


```python
def func():
    global a
    a=[]
    for i in range(5):
        a.append(i)
func()
a
```




    [0, 1, 2, 3, 4]



## 返回多个值


```python
def func():
    a=1
    b=2
    c=3
    return a,b,c

a,b,c=func() # python函数可以通过此种方式返回多个值
print(a,b,c)

return_value=func() # 实际是将多个值创建一个元组返回
return_value
```

    1 2 3
    




    (1, 2, 3)




```python
def func():
    a=1
    b=2
    c=3
    return {'a':a,'b':b,'c':c}
return_dic=func() # python函数还可以返回字典
return_dic
```




    {'a': 1, 'b': 2, 'c': 3}



## 函数也是对象

#### 例如我们要将下面的字符串进行处理


```python
states = [' Alabama ', 'Georgia!', 'Georgia', 'georgia','FlOrIda', 'south carolina##', 'West virginia?']
```


```python
def clean_strings(strings):
    import re
    result = []
    for value in strings:
        value = value.strip()
        value = re.sub('[!#?]', '', value)
        value = value.title()
        result.append(value)
    return result
strings=clean_strings(states)
strings
```




    ['Alabama',
     'Georgia',
     'Georgia',
     'Georgia',
     'Florida',
     'South Carolina',
     'West Virginia']




```python
# 我们可以将一组对每个字符串都要进行的所有运算 , 组成一个列表
def remove_punctuation(value):
    import re
    return re.sub('[!#?]','',value)

clean_ops=[str.strip,remove_punctuation,str.title]

def clean_string(strings,ops):
    result=[]
    for value in strings:
        for func in ops:
            value=func(value)
        result.append(value)
    return result

clean_string(states,clean_ops)
```




    ['Alabama',
     'Georgia',
     'Georgia',
     'Georgia',
     'Florida',
     'South Carolina',
     'West Virginia']




```python
# 还可以将函数作为其他函数的参数
for value in map(remove_punctuation,states):
    print(value)
```

     Alabama 
    Georgia
    Georgia
    georgia
    FlOrIda
    south carolina
    West virginia
    

## 匿名函数(lambda)

#### 不用声明直接返回结果的函数形式


```python
strings = ['foo', 'card', 'bar', 'aaaa', 'abab']
strings.sort(key=lambda x:len(set(list(x))))
strings
```




    ['aaaa', 'foo', 'abab', 'bar', 'card']



## 柯里化
#### 通过“部分参数应用”（partial argument application）从现有函数派生出新函数的技术


```python
def add_numbers(x, y):
    return x + y

add_five = lambda y: add_numbers(5, y) # add_five 的第二个参数被称为柯里化的
add_five(5) 
```




    10




```python
from functools import partial

add_five = partial(add_numbers, 5)
add_five(5)
```




    10



## 生成器

#### 能以一种一致的方式对序列进行迭代


```python
'''构造生成器'''

# 利用iter()函数将可迭代对象转化为生成器
a=[1,2,3,4,5]
a=iter(a)
print(a)

# 通过yield将函数变为生成器
def func(arr):
    for i in arr:
        yield i**2
print(func(a))

# 通过表达式构造
gen=(i for i in a)
print(gen)
```

    <list_iterator object at 0x000002665260EA20>
    <generator object func at 0x0000026652690620>
    <generator object <genexpr> at 0x0000026652690620>
    

## itertools模块

#### 标准库itertools模块中有一组用于许多常见数据算法的生成器。例如，groupby可以接受任何序列和一个函数。它根据函数的返回值对序列中的连续元素进行分组。


```python
import itertools

names = ['Alan', 'Adam', 'Wes', 'Will', 'Albert', 'Steven']
first_letter=lambda x:x[0]

for letter,name in itertools.groupby(names,first_letter):
    print(letter,list(name))
```

    A ['Alan', 'Adam']
    W ['Wes', 'Will']
    A ['Albert']
    S ['Steven']
    

## 错误和异常处理


```python
def transform_str_num(string):
    # 未报错执行
    try: 
        return (float(string))
    # 报错执行,可指定多个报错类型
    except (ValueError,TypeError):
        print("Value Error")
    # 未报错执行
    else:
        print("Successful")
    # 无论报错都要执行
    finally:
        print("Finish!")
        
num='123'
transform_str_num(num)
```

    Finish!
    




    123.0


