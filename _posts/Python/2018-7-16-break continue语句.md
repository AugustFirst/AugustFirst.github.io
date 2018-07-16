---
layout: post
title: Break,Continue
date: 2018-7-16
categories: Python
tag: Break,Continue
---
## Break使用语法
-------------------------
    # basic of Break

    i = 0

    while i <= 10:

        if i == 5:
            print(i)
            break
        i += 1

    print("the last i=%d" %i)

## Continue使用语法
* 在使用continue关键字时，需要确认循环的计数是否修改
否则可能导致死循环！
-----------------------------
    # basic of Continue

    i = 0

    while i <= 10:

        if i == 5:
            i += 1
            continue

        print(i)
        i += 1
    print("the last i=%d" %i)
