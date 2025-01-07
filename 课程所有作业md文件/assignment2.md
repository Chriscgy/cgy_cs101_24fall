# Assignment #2: 语法练习

Updated 0126 GMT+8 Sep 24, 2024

2024 fall, Complied by ==陈冠宇 工学院==



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知9月19日导入选课名单后启用。**作业写好后，保留在自己手中，待9月20日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 263A. Beautiful Matrix

https://codeforces.com/problemset/problem/263/A



思路：



##### 代码

```python
# 
list=[]
for i in range(0,5):
    list.append(input().split())
m=0
n=0
for i in range(0,5):
    for j in range(0,5):
        if list[i][j]=="1":
            m=i
            n=j
            break
print(abs(m-2)+abs(n-2))

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20240924154144118](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240924154144118.png)



### 1328A. Divisibility Problem

https://codeforces.com/problemset/problem/1328/A



思路：



##### 代码

```python
# 
n=int(input())
list=[]
for i in range(n):
    m,n=map(int,input().split())
    while True:
        m0=m
        n0=n
        if m<n:
            list.append(n-m)
            break
        elif m==n or m>n and m%n==0:
            list.append(0)
            break
        else:
            m=m-(m//n0)*n0
for i in list:
    print(i)
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20240924155519966](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240924155519966.png)



### 427A. Police Recruits

https://codeforces.com/problemset/problem/427/A



思路：



##### 代码

```python
# 
n=int(input())
sum=0
fmax=0
list=input().split()
for i in list:
    x=int(i)
    sum=sum+x
    if sum<fmax:
        fmax=sum
print(-fmax)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240924163020212](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240924163020212.png)



### 02808: 校门外的树

http://cs101.openjudge.cn/practice/02808/



思路：



##### 代码

```python
# 
l,m=map(int,input().split())
load=[1]*(l+1)
sum=0
for i in range(0,m):
    x,y=map(int,input().split())
    for j in range(x,y+1):
        load[j]=0
for i in load:
    if i==1:
        sum+=1
print(sum)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240924163550004](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240924163550004.png)



### sy60: 水仙花数II

https://sunnywhy.com/sfbj/3/1/60



思路：



##### 代码

```python
# 
a,b=map(int,input().split())
list=[]
for i in range(a,b+1):
    x=i//100
    y=(i-100*(i//100))//10
    z=i-10*y-100*x
    if i==x**3+y**3+z**3:
        list.append(i)
if len(list)==0:
    print("NO")
else:
    for i in range(0,len(list)-1):
        print(list[i],end=" ")
    print(list[-1])
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240924165126098](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240924165126098.png)



### 01922: Ride to School

http://cs101.openjudge.cn/practice/01922/



思路：



##### 代码

```python
# 
import math
list=[]
while True:
    n=int(input())
    cgy=[]
    if n==0:
        break
    for i in range(0,n):
        qwe=input().split()
        cgy.append(qwe)
    artime=[]
    for i in range(0,n):
        if int(cgy[i][1])>=0:
            artime.append((4.5/int(cgy[i][0]))*3600+int(cgy[i][1]))
    list.append(math.ceil(min(artime)))
for i in list:
    print(i)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240924172919401](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20240924172919401.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

作业题目难度适中，大多数自己慢慢写（可能要花一定时间）能做对，有不会的的题目询问同学或ai后也可以ac

每日选做，八月底九月初那段时间的题都没怎么写，现在的新题尽量每天都做完（偶尔也有被某题卡住写不出来的情况）

感觉题目难度和分值不是很相关，我做起来800和1000的题好像没太大区别？800也不见得比1000简单到哪去QAQ



