# Assignment #4: T-primes + 贪心

Updated 0337 GMT+8 Oct 15, 2024

2024 fall, Complied by <mark>陈冠宇 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知9月19日导入选课名单后启用。**作业写好后，保留在自己手中，待9月20日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 34B. Sale

greedy, sorting, 900, https://codeforces.com/problemset/problem/34/B



思路：



代码

```python
n,m=map(int,input().split())
winko=list(map(int,input().split()))
xie=[]
for cb in winko:
    if cb<0:
        xie.append(cb)
xie.sort()
cgy=0
if len(xie)>=m:
    for i in range(m):
        cgy=cgy+xie[i]
else:
    for i in range(len(xie)):
        cgy=cgy+xie[i]
print((-1)*cgy)

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241015153158673](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241015153158673.png)



### 160A. Twins

greedy, sortings, 900, https://codeforces.com/problemset/problem/160/A

思路：



代码

```python
n=int(input())
winko=list(map(int,input().split()))
winko.sort()
cgy=0
cb=sum(winko)
ji=0
i=len(winko)-1
while cgy<=cb:
    cgy=cgy+winko[i]
    cb=cb-winko[i]
    i=i-1
    ji=ji+1
print(ji)

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241015154131466](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241015154131466.png)



### 1879B. Chips on the Board

constructive algorithms, greedy, 900, https://codeforces.com/problemset/problem/1879/B

思路：



代码

```python
t=int(input())
for ts in range(t):
    n=int(input())
    lista=list(map(int,input().split()))
    listb=list(map(int,input().split()))
    mina=1000000000
    for a in lista:
        if mina>a:
            mina=a
    hang=mina*n+sum(listb)
    minb=1000000000
    for b in listb:
        if minb>b:
            minb=b
    lie=minb*n+sum(lista)
    print(min(hang,lie))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241015160717333](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241015160717333.png)



### 158B. Taxi

*special problem, greedy, implementation, 1100, https://codeforces.com/problemset/problem/158/B

思路：



代码

```python


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





### *230B. T-primes（选做）

binary search, implementation, math, number theory, 1300, http://codeforces.com/problemset/problem/230/B

思路：一开始尝试质数打表结果代码过长，问了ai才会写欧拉筛



代码

```python
import math
n=int(input())
is_prime=[True]*1000001
primes=[]
for i in range(2,1000001):
    if is_prime[i]==True:
        primes.append(i)
    for prime in primes:
        product=i*prime
        if product>1000000:
            break
        is_prime[product]=False
        if i%prime==0:
            break
is_prime[1]=False
list=list(map(int,input().split()))
'''for i in range(1,1000001):
    if is_prime[i]==True:
        print(i)'''
for i in list:
    if math.sqrt(i)!=int(math.sqrt(i)):
        print("NO")
    else:
        x=int(math.sqrt(i))
        if is_prime[x]==True:
            print("YES")
        else:
            print("NO")

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241015151257813](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241015151257813.png)



### *12559: 最大最小整数 （选做）

greedy, strings, sortings, http://cs101.openjudge.cn/practice/12559

思路：



代码

```python


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

上周二就把作业会写的题目写完了，结果剩下两题拖到现在也没解决...最近状态好像有点差，被其他学科搞得焦头烂额，写计概的时间远远不足QAQ...这周一定要多花时间

哎，好累



