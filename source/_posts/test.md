---
title: 这是一个测试
date: 2019-06-08 12:06:06
tags:
---
## 设置次级目录
使用##设置次级目录，插入链接测试[百度首页](https://www.baidu.com/)

### step one
中文乱码解决：
1：在配置中设置语言为中文： zh-CN
2:使用sublime编辑器

### 代码测试
```bash
$ hexo new "new page"
```
建立新的网页
```python
import os
print 'that isvery good！'
```
插入python代码块测试

```c++
#include <iostream>
#include <string>
using namespace std;
class Student{
public:
	string m_name;
	int getscore(){return m_score};
	void setscore(int score){m_score = score;}
private:
	int m_score;
};
int main(){
	Student std1;
	std1.m_name = "大橙子";
	std1.setscore(90);
	cout<<"student "<<st1.m_name()<<" score is "<<std1.getscore()<<endl;
	return 0;
}
```
尝试插入图片：
![](/images/青铜器.JPG)

使用git新建hexo分支，管理博客源文件
这是在git库中修改文件的，然后会使用hexo d -g 提交git库
测试是否可以实现，这样在其他的电脑上，只要clone下来git库就可以维护博客了！
下面进行实际测试，我会在mac电脑上配置git，然后clone下来git库进行修改和推送
问题：
1：mac上是否也需要安装node
