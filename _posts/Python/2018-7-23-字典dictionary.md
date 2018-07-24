---
layout: post
title: 非数字型_字典
date: 2018-7-23
categories: Python
tag: 字典
---
# 字典的定义
* `dictionary`（字典）是**除列表以外`Python`之中最灵活**的数据类型
* 字典同样可以用来**存储多个数据**
* 通常用于存储 **描述一个`物体`的相关信息**
* 和列表的区别：
1.**列表**是**有序**的对象集合
2.**字典**是**无序**的对象集合
* 字典用`{}`定义
* 字典使用**键值对**存储数据，键值对之间使用`,`分隔
* **键**`key`是索引
* **值**`value`是数据
* **键**和**值**之间使用`:`分隔
* **键必须是唯一的**
* **值**可以取任何数据类型，但**键**只能用**字符串**，**数字**或**元组**

------------------------------------
    xiaoming = {"name":"小明",
                "age":18,
                "gender":True,
                "height":1.75,
                "weight":140}
    # 字典是一个无序的数据集合，使用print函数输出字典时，
    输出的顺序和定义的顺序是不一致的！
    print(xiaoming)   
    

# 字典的增删改
-----------------------
        xiao_dict = {"name":"xiaoming"}

        # 取值
        print(xiao_dict["name"])
        # 在取值的时候，如果指定的key不存在，程序会报错！
        # print(xiao_dict["name123"])

        # 增加、修改
        # 如果key不存在，会新增键值对
        xiao_dict["age"] = 18
        # 如果key存在，会修改已经存在的键值对
        xiao_dict["name"] = "xiaopang"

        # 删除
        xiao_dict.pop("name")
        # 在删除指定的键值对时，如果指定的key不存在，程序会报错

        print(xiao_dict)  


# 字典的常用操作
-------------------------
    xiao_dict = {"name": "xiao",
                  "age": 19}
    # 统计键值对数量
    print(len(xiao_dict))

    # 合并字典
    temp_dict = {"gender": "male"}
    # 注：如果被合并的字典中包含已经存在的键值对时，  
    会覆盖原有的键值对
    xiao_dict.update(temp_dict)

    # 清空字典
    xiao_dict.clear()

    print(xiao_dict)

# 字典的遍历
-------------------------
    xiao_dict = {"name": "xiao",
                  "qq": "111111",
                  "gender": "male"}

    # 迭代遍历字典
    # 变量K是每一次循环中，获取到的键值对的key
    for K in xiao_dict:

        print("%s - %s"% (K,xiao_dict[K]))

# 应用场景
----------------------
* 尽管可以使用`for in`遍历字典
* 但是在开发中，更多的应用场景是：
1.使用**多个键值对**，存储**描述一个`物体`的相关信息**--描述更复杂的数据信息
2,。将**多个字典**放在**一个列表**中，再进行遍历，在循环体内部针对每一个字典进行**相同的处理**

        card_list = [
            {"name": "zhangsan",
            "qq": "123456789",
            "phone": "111000"},
            {"name": "lisi",
            "qq": "987654321",
            "phone": "9732983"},
        ]

        for card_info in card_list:
            print(card_info)
