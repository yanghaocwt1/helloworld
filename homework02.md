列表

```python
#list
#新建列表
a = list()
b = []
#列表增删改查
#末尾增加一个元素  append
a = ["bcsner"]
print(a)  #['bcsner']
a.append("yanghao")
print(a)    #['bcsner', 'yanghao']
#增加多个元素extend
a.extend("yanghao")
print(a)  #['bcsner', 'yanghao', 'y', 'a', 'n', 'g', 'h', 'a', 'o']
#insert：插入，嵌入
a.insert(2,"hz")
print(a)    #['bcsner', 'yanghao', 'hz', 'y', 'a', 'n', 'g', 'h', 'a', 'o']
#pop：取出，抛出
a.pop(3)
print(a)   #['bcsner', 'yanghao', 'hz', 'a', 'n', 'g', 'h', 'a', 'o']
#clear：清除，使干净
a.clear()
print(a)   #[]
#del  删除
del a[5:8]
print(a)    #['bcsner', 'yanghao', 'hz', 'a', 'n', 'o']
#remove：删除，移出；
a.remove("hz")
print(a)    #['bcsner', 'yanghao', 'a', 'n', 'o']
#替换
a[0]="hzbcsn"
print(a)    #['hzbcsn', 'yanghao', 'a', 'n', 'o']
```

字典

```python
#字典的相关操作
#新建一个字典
b = {}
x = {"a":1,"b":2,"c":3}
print(x)   #{'a': 1, 'b': 2, 'c': 3}
print(type(x))   #<class 'dict'>
#字典的增删改查功能
#增加
x["d"] = 4
print(x)  #{'a': 1, 'b': 2, 'c': 3, 'd': 4}

#修改
x["d"] = 4.414
print(x)   #{'a': 1, 'b': 2, 'c': 3, 'd': 4.414}

#删除
del x["d"]
print(x)  #{'a': 1, 'b': 2, 'c': 3}

#查找
print(x["a"])  #1
```

