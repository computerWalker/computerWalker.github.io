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
