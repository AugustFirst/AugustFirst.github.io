---
layout: post
title: 归并排序
date: 2017-8-18
categories: 学习
tag: MergeSort
---
## 归并排序
再次感谢[归并排序 详解 - 理想空间 - 博客园
](http://www.cnblogs.com/jianboqi/archive/2013/01/15/2860500.html)
归并排序时的时间复杂度为O（nlgn) 其主要思想是分治法(divide and conquer)，分就是要将n个元素的序列划分为两个序列，再将两个序列划分为4个序列，
直到每个序列只有一个元素，最后，再将两个有序序列。

这个算法的理解其实可以借助下面这个图：
![归并排序]({{ '/assets/img/14235319-8c15631895704786979d97954264cc66.png' | prepend: site.baseurl  }})
对于原始的数组2,1,3,8,5,7,6,4,10，
在整个过程执行的是顺序是图中红色编号1-20。虽然我们描述中说的是程序先分解，再归并，但实际过程是一边分解一边归并，前半部分分先排好序，后半部分再排好，最后整个归并为一个完整的序列
，下图展示了每个merge过程对作
用于数组的哪部分（红色）。
![归并排序]({{ '/assets/img/14235630-4c79a4e8332846a8bc9551b8bfc1372c.png' | prepend: site.baseurl  }})
整个过程就像一个动态的树，执行顺序就是对树的先序遍历顺序。

### 版本1
---------------
    #include<stdio.h>
    #include<stdlib.h>
    typedef int RecType;//要排序元素类型
    void Merge(RecType *R,int low,int m,int high)
    {
        //将两个有序的子文件R[low..m)和R[m+1..high]归并成一个有序的子文件R[low..high]
        int i=low,j=m+1,p=0;                //置初始值
        RecType *R1;                        //R1是局部向量
        R1=(RecType *)malloc((high-low+1)*sizeof(RecType));
        if(!R1)
        {
            return;                         //申请空间失败
        }

        while(i<=m&&j<=high)                //两子文件非空时取其小者输出到R1[p]上
        {
            R1[p++]=(R[i]<=R[j])?R[i++]:R[j++];
        }

        while(i<=m)                         //若第1个子文件非空，则复制剩余记录到R1中
        {
            R1[p++]=R[i++];
        }
        while(j<=high)                      //若第2个子文件非空，则复制剩余记录到R1中
        {
            R1[p++]=R[j++];
        }

        for(p=0,i=low;i<=high;p++,i++)
        {
            R[i]=R1[p];                     //归并完成后将结果复制回R[low..high]
        }
    }

    void MergeSort(RecType R[],int low,int high)
    {
        //用分治法对R[low..high]进行二路归并排序
        int mid;
        if(low<high)
        {   //区间长度大于1
            mid=(low+high)/2;               //分解
            MergeSort(R,low,mid);           //递归地对R[low..mid]排序
            MergeSort(R,mid+1,high);        //递归地对R[mid+1..high]排序
            Merge(R,low,mid,high);          //组合，将两个有序区归并为一个有序区
        }
    }
    void main()
    {
        int a[7]={49,38,65,97,76,13,27}; //这里对8个元素进行排序
        int low=0,high=6,i;                   //初始化low和high的值

        printf("Before merge sort:\n ");
        for( i=low;i<=high;i++)
        {
            printf("%d\n ",a[i]);             //输出测试
        }

        MergeSort(a,low,high);

        printf("After merge sort:\n ");
        for( i=low;i<=high;i++)
        {
            printf("%d\n ",a[i]);             //输出测试
        }
    }

----------------
### 版本2
----------------

    #include <stdlib.h>
    #include <stdio.h>

    void Merge(int sourceArr[],int tempArr[], int startIndex, int midIndex, int endIndex)
    {
        int i = startIndex, j=midIndex+1, k = startIndex;
        while(i!=midIndex+1 && j!=endIndex+1)
        {
            if(sourceArr[i] > sourceArr[j])
                tempArr[k++] = sourceArr[j++];
            else
                tempArr[k++] = sourceArr[i++];
        }
        while(i != midIndex+1)
            tempArr[k++] = sourceArr[i++];
        while(j != endIndex+1)
            tempArr[k++] = sourceArr[j++];
        for(i=startIndex; i<=endIndex; i++)
            sourceArr[i] = tempArr[i];
    }
    void MergeSort(int sourceArr[], int tempArr[], int startIndex, int endIndex)
    {
        int midIndex;
        if(startIndex < endIndex)
        {
            midIndex = (startIndex + endIndex) / 2;
            MergeSort(sourceArr, tempArr, startIndex, midIndex);
            MergeSort(sourceArr, tempArr, midIndex+1, endIndex);
            Merge(sourceArr, tempArr, startIndex, midIndex, endIndex);
        }
    }

    int main(int argc, char * argv[])
    {
        int a[8] = {50, 10, 20, 30, 70, 40, 80, 60};
        int i, b[8];
        MergeSort(a, b, 0, 7);
        for(i=0; i<8; i++)
            printf("%d \n", a[i]);
        return 0;
    }

---------------
* 总的来说归并排序就是分而治之，核心是归并的部分。
