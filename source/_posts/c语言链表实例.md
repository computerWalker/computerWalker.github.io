---
title: c语言链表实例
date: 2019-06-08 20:39:23
tags:
---
#### [视频教程](https://www.bilibili.com/video/av54554228?from=search&seid=4343468601199547837) 
使用c语言编写简单的学生档案管理系统  
1. **界面**  
2. **数据操作方法**  
3. **数据**  

main函数中绘制了基本界面、交互反应、主函数  
数据结构是链表，单独的文件写数据结构的操作  
所有的数据操作会直接操作硬盘上的文件，保证信息的同步  
##### 链表
链表是一种数据结构  
每个链表中元素包含了**数据**、**指向下一个数据的指针**  
链表有一个表头
###### 链表的操作
1. 增加，表头插入法，将表头指向新加的元素，新加元素的next指向表头之前指的位置。  
![链表的插入](./链表插入.JPG)  
2. 删除指定位置的数据，把指向这个数据元素的next指向这个数据的next，将这个数据 free 掉。
3. 查找，从链表头指向的元素开始搜索。
4. 修改，替换指定位置的数据，直接替换元素中的数据

---
### 知识点：
c结构体 struct 用来来存放一组不同类型的数据 
```c
struct struct_name{
	variations;
	list;
}; //注意结尾的分号
```
结构体数组  
结构体指针

struct简单实例：
```c
#include <stdlib.h>
#include <stdio.h>

struct student{
    char *name;
    int age;
    int score;
}stu4={(char*)"Mick",12,99};

int main(){
    student stu1 = {(char*)"jack",10,90};
    printf("%s\n",stu1.name);
    printf("%s\n",stu4.name);
    stu4.name = (char*)"NewName";
    printf("%s\n",stu4.name);

    student st2 = {(char*)"Lily",15,95};
    student *sp = &st2;//定义一个指向结构体的指针
    printf("%s\n",sp->name);
    return 0;
}
```  
<font color=#DC143c>需要注意的是，结构体是一种自定义的数据类型，是创建变量的模板，不占用内存空间；结构体变量才包含了实实在在的数据，需要内存空间来存储。</font>
