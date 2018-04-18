---
layout: post
title: 数据溢出
date: 2018-4-17
categories: Learning
tag: data overflow
---

### 数据溢出
``` java

    public class TestDemo
    {
      public static void main (String []args)
      { int maxValue=Integer.MAX_VALUE;
        int minValue=Integer.MIN_VALUE;
    	System.out.println(maxValue);
    	System.out.println(minValue);
    	System.out.println(maxValue+1);
    	System.out.println(minValue-1);
    	System.out.println(minValue-2);
      }
    }

>     2147483647
    -2147483648
    -2147483648
    2147483647
    2147483646

### 数据类型

    public class Test
    {
      public static void main (String[] args)
      { int maxValue=Integer.MAX_VALUE;
        int minValue=Integer.MIN_VALUE;
    	long result=maxValue+1;
    	long result1=(long)maxValue+1;
      // 任何的整数其默认类型都是int，但是如果该数据已经超过了int可以保存的数据范围
      // 那么就需将这个数据明确地表示成long型的常量
    	long result2=2147483648l;
    	long result3=2147483648L;
    	System.out.println(result);
    	System.out.println(result1);
    	System.out.println(result2);
    	System.out.println(result3);
      }
    }

>     -2147483648
    2147483648
    2147483648
    2147483648


###  ps:[Java 中 String[] args 和 String args[] 有什么区别？](https://www.zhihu.com/question/20665174)
