---
title: Python中的装包和解包
date: 2020-09-07 16:04:26
tags:
- python
top_img: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/微信图片_20200922105439.png
cover: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/9CZK8.png
copyright_author: 李瑞
copyright_author_href: https://lirui-1997.github.io/
copyright_info: 本博客所有文章除特别声明外，均采用  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0 </a> 许可协议。转载请注明出处！

---

## 拆包（**unpacking**）

**拆包**就是将一个对象拆成多个对象，拆包实际上可以应用到任何可迭代对象上，唯一的硬性要求是，被可迭代对象中的元素数量必须要跟接受这些元素的元组的空档树一致。除非我们用 __*__ 来表示忽略多余的元素。带 __*__ 的变量返回列表。

### 列表拆包

例：
```Python
a, b, c = ['aaa', 'bbb', 'ccc']
print(a, b, c)
# aaa bbb ccc
```
列表中的元素对应赋值给相应的变量。

### 字典拆包

例：
```Python
a, b, c = {'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}
print(a, b, c)
#key1 key2 key3
```
注意对可迭代对象解包时，拆分出的元素是```for```循环结果的元素，所以对字典解包得到的是键！
如果想要得到键值对的形式，可以这样进行解包：
```Python
a, b, c = {'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}.items()
print(a, b, c)
# ('key1', 'value1') ('key2', 'value2') ('key3', 'value3')
```
如果我们想对字典中的值进行解包，可以进行这样的解包：
```Python
a, b, c = {'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}.values()
print(a, b, c)
# value1 value2 value3
```
我们还可以使用 __**__来实现对字典中的值进行解包，例如：
```Python
# A sample program to demonstrate unpacking of 
# dictionary items using ** 
def fun(a, b, c): 
    print(a, b, c) 
  
# A call with unpacking of dictionary 
d = {'a':2, 'b':4, 'c':10} 
fun(**d) 
```
结果：
```Python
2 4 10
```
这里，__**__ 用来解包一个字典，我们传递字典的值给函数，所以```fun(**d)```等于```fun(a=2,b=4,c=10)```。

### 元组拆包

在Python中有一个非常强大的元组赋值特性，它将右侧的值赋到左侧。这种方法也称为将元组的值解包为变量。在装包时，我们将值放入一个新的元组，而在拆包时，我们将这些值提取到一个单一变量中。
例1：
```Python
# Program to understand about  
# packing and unpacking in Python 
  
# this lines PACKS values 
# into tuple a 
a = ("MNNIT Allahabad", 5000, "Engineering")   
  
# this lines UNPACKS values 
# of tuple a 
(college, student, type_ofcollege) = a   
  
# print college name 
print(college) 
  
# print no. of student 
print(student) 
  
# print type of college 
print(type_ofcollege) 
```
结果：
```Python
MNNIT Allahabad
5000
Engineering
```
注意：解包时，左边变量的个数和元组中元素的个数相等。
如果个数不等或参数数量很多时，或者需要传递可选择个数的参数对元组解包时，可以使用（args）语法来实现。所有的值都会被赋值给左边的变量，所有剩下的值都会被赋值给args。为了更加便于理解，请看代码：
```Python
# Python code to study about 
# unpacking python tuple using * 
  
# first and last will be assigned to x and z 
# remaining will be assined to y 
x, *y, z = (10, "Geeks ", " for ", "Geeks ", 50) 
  
# print details 
print(x) 
print(y) 
print(z) 
  
# first and second will be assigned to x and y 
# remaining will be assined to z 
x, y, *z = (10, "Geeks ", " for ", "Geeks ", 50) 
print(x) 
print(y) 
print(z) 
```
结果：
```Python
10
['Geeks ', ' for ', 'Geeks ']
50
10
Geeks 
[' for ', 'Geeks ', 50]
```

### 函数中的传递参数拆包

在python中，列表、元组、字典都能用来作为参数传递给函数的变量进行解包。
例：
```PYTHON
# Python code to study about 
# unpacking python tuple using function 
  
# function takes normal arguments 
# and multiply them 
def result(x, y): 
    return x * y 
# function with normal variables 
print (result(10, 100)) 
  
# A tuple is created 
z = (10, 100) 
  
# Tuple is passed 
# function unpacked them 
  
print (result(*z)) 
```
```Python
1000
1000
```
列表传参解包：
```Python
# A Python program to demonstrate need  
# of packing and unpacking 
  
# A sample function that takes 4 arguments 
# and prints them. 
def fun(a, b, c, d): 
    print(a, b, c, d) 
  
# Driver Code 
my_list = [1, 2, 3, 4] 
  
# This doesn't work 
fun(my_list) 
```
```Python
fun() missing 3 required positional arguments: 'b', 'c', and 'd'
```
这样一个列表并不能直接作为参数传递给函数，我们可以使用 __*__ 来解包这个列表中的所有元素，使得所有元素都能被传递给不同的参数。
```Python
# A sample function that takes 4 arguments 
# and prints the, 
def fun(a, b, c, d): 
    print(a, b, c, d) 
  
# Driver Code 
my_list = [1, 2, 3, 4] 
  
# Unpacking list into four arguments 
fun(*my_list) 
```
结果：
```PYTHON
(1, 2, 3, 4)
```

## 装包（**packing**）

我们常常不知道有多少个参数需要被传递，因此我们可以使用装包的方式将所有的参数装进一个元组。
例：
```Python
# A Python program to demonstrate use 
# of packing 
  
# This function uses packing to sum 
# unknown number of arguments 
def mySum(*args): 
    sum = 0
    for i in range(0, len(args)): 
        sum = sum + args[i] 
    return sum 
  
# Driver code 
print(mySum(1, 2, 3, 4, 5)) 
print(mySum(10, 20)) 
```
结果：
```Python
15
30
```
上面的函数```mySum()```将所有的参数装进一个单一的变量中，一旦我们有了这个装包好的变量，我们就可以把它当做一个正常的元组。```args[0]```,```arg[1]```分别对应第一、第二个参数。由于元组是不可变的，我们将args元组转化为列表list，使得它能够被修改、删除和重新排列。
我们来看一个**装包**和**解包**的例子。
```Python
# A Python program to demonstrate both packing and 
# unpacking. 
  
# A sample python function that takes three arguments 
# and prints them 
def fun1(a, b, c): 
    print(a,'\n' ,b,'\n', c,'\n') 
  
# Another sample function. 
# This is an example of PACKING. All arguments passed 
# to fun2 are packed into tuple *args. 
def fun2(*args): 
  
    # Convert args tuple to a list so we can modify it 
    args = list(args) 
  
    # Modifying args 
    args[0] = 'Geeksforgeeks'
    args[1] = 'awesome'
  
    # UNPACKING args and calling fun1() 
    fun1(*args) 
  
# Driver code 
fun2('Hello', 'beautiful', 'world!') 
```
在这个例子红，函数```fun2()```将参数传递给args装包成一个元组，将元组转化为列表，修改列表中第1、2个位置元素的值，再将其拆包赋值给函数```fun1()```。最后打印输出，结果如下：
```Python
Geeksforgeeks 
awesome 
world! 
```

### 字典的装包

```Python
# A Python program to demonstrate packing of 
# dictionary items using ** 
def fun(**kwargs): 

    # kwargs is a dict 
    print(type(kwargs)) 

    # Printing dictionary items 
    for key in kwargs: 
        print("%s = %s" % (key, kwargs[key])) 

# Driver code 
fun(name="geeks", ID="101", language="Python")
```
结果：
```Python
<class 'dict'>
name = geeks
ID = 101
language = Python
```

## 参考资料

- https://www.geeksforgeeks.org/packing-and-unpacking-arguments-in-python/?ref=rp
- https://www.geeksforgeeks.org/unpacking-a-tuple-in-python/#:~:text=Packing%20and%20Unpacking%20a%20Tuple%20%3A%20In%20Python,those%20values%20into%20a%20single%20variable.%20Example%201
- https://blog.csdn.net/qq_42908151/article/details/102778197
- https://blog.csdn.net/water19111213/article/details/107642335






