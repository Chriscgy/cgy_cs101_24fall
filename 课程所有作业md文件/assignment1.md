# Assignment #1: 自主学习

Updated 0110 GMT+8 Sep 10, 2024

2024 fall, Complied by ==陈冠宇 工学院==



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知9月19日导入选课名单后启用。**作业写好后，保留在自己手中，待9月20日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 02733: 判断闰年

http://cs101.openjudge.cn/practice/02733/



思路：

耗时约5分钟

##### 代码

```python
# 
a=int(input())
if((a%4==0 and a%100!=0)or a%400==0)and a%3200!=0:
    print("Y")
else:
    print("N")
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20240910153606774](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240910153606774.png)



### 02750: 鸡兔同笼

http://cs101.openjudge.cn/practice/02750/



思路：

耗时约5分钟

##### 代码

```python
# 
a=int(input())
if a%2!=0:
    print("0 0")
else:
    if a%4!=0:
        b=a//2
        c=a//4+1
    else:
        b=a//2
        c=a//4
    print(str(c)+" "+str(b))
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20240910154624618](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240910154624618.png)



### 50A. Domino piling

greedy, math, 800, http://codeforces.com/problemset/problem/50/A



思路：

耗时约10分钟

##### 代码

```python
# 
[m,n]=input().split()
m=int(m)
n=int(n)
if m==1 and n==1:
    print("0")
else:
    if n>=m:
        a=m
        m=n
        n=a
    if m%2==0:
        s=m/2*n
    else:
        s=(m//2)*n+n//2
    s=int(s)
    print(s)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240910162246547](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240910162246547.png)



### 1A. Theatre Square

math, 1000, https://codeforces.com/problemset/problem/1/A



思路：

耗时约10分钟

##### 代码

```python
# 
[m,n,a]=input().split()
m=int(m)
n=int(n)
a=int(a)
if m%a==0:
    x=m//a
else:
    x=m//a+1
if n%a==0:
    y=n//a
else:
    y=n//a+1
print(x*y)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240910162743992](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240910162743992.png)



### 112A. Petya and Strings

implementation, strings, 1000, http://codeforces.com/problemset/problem/112/A



思路：

耗时约10分钟

##### 代码

```python
# 
a=input()
b=input()
a=a.lower()
b=b.lower()
x=int(len(a))
s=0
i=0
while i<=x-1:
    if ord(a[i])>ord(b[i]):
        print("1")
        s=1
        break
    if ord(a[i])<ord(b[i]):
        print("-1")
        s=1
        break
    i=i+1
if s==0:
    print("0")
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240910170952937](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240910170952937.png)



### 231A. Team

bruteforce, greedy, 800, http://codeforces.com/problemset/problem/231/A

耗时约10分钟

思路：



##### 代码

```python
# 
n=int(input())
i=1
x=0
while i<=n:
    [a,b,c]=input().split()
    a=int(a)
    b=int(b)
    c=int(c)
    if a+b+c>=2:
        x=x+1
    i=i+1
print(x)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240910172832240](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240910172832240.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

前几年接触过一点点c++的内容但现在已经基本忘光，python更是零基础。。。每道题90%的时间都花在语法上，反复地调试输入输出，查询各种函数的用法，有点身心俱疲。。。但是（可能是因为现在题目都相对简单）目前理解这些算法倒是没有什么障碍，大多数1000以下的题目可以一眼看出解决方案，就是将方案转化成编程语言的过程太痛苦了

![ba153e3e479729ebc5ec2e8fa999fe2f](C:\Users\72848\Documents\Tencent Files\728486338\nt_qq\nt_data\Emoji\emoji-recv\2024-09\Ori\ba153e3e479729ebc5ec2e8fa999fe2f.png)

