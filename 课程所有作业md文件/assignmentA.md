# Assignment #10: dp & bfs

Updated 2 GMT+8 Nov 25, 2024

2024 fall, Complied by <mark>陈冠宇 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### LuoguP1255 数楼梯

dp, bfs, https://www.luogu.com.cn/problem/P1255

思路：高中数学题



代码：

```python
def mygo(n,feb):
    for i in range(2,n):
        feb.append(feb[i-1]+feb[i-2])
    return feb[-1]
feb=[1,1]
mygo(5050,feb)
n=int(input())
print(feb[n])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241126190519832](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241126190519832.png)



### 27528: 跳台阶

dp, http://cs101.openjudge.cn/practice/27528/

思路：高中数学题



代码：

```python
print(2**(int(input())-1))
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241126184656351](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241126184656351.png)



### 474D. Flowers

dp, https://codeforces.com/problemset/problem/474/D

思路：



代码：

```python
mod=1000000007
def mygo(k):
    dp=[0]*100010
    dp[0]=1
    for i in range(1,100010):
        if i<k:
            dp[i]=1
        else:
            dp[i]=(dp[i-1]+dp[i-k])%mod
    prefix_sum=[0]*100010
    for i in range(0,100005):
        prefix_sum[i]=(prefix_sum[i-1]+dp[i])%mod
    return prefix_sum
t,k=map(int,input().split())
prefix_sum=mygo(k)
for tests in range(t):
    a,b=map(int,input().split())
    print((prefix_sum[b]-prefix_sum[a-1])%mod)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241126202056351](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241126202056351.png)



### LeetCode5.最长回文子串

dp, two pointers, string, https://leetcode.cn/problems/longest-palindromic-substring/

思路：



代码：

```python
from collections import deque
class Solution(object):
    def longestPalindrome(self, s):
        max_length = 0
        answer = s[0]
        for i in range(len(s)):  # 奇数
            j = 1
            k = 1
            length = 1
            mygo = deque()
            mygo.append(s[i])
            while i-j >= 0 and i+k < len(s):
                if s[i-j] == s[i+k]:
                    mygo.appendleft(s[i-j])
                    mygo.append(s[i+k])
                    length += 2
                    j += 1
                    k += 1
                else:
                    break
                #print(mygo)
            if max_length < length:
                answer = ''.join(mygo)
                max_length = length
        for i in range(len(s) - 1):
            if s[i] == s[i + 1]:
                j = 1
                k = 1
                length = 2
                mygo = deque([s[i], s[i + 1]])
                while i - j >= 0 and i + 1 + k < len(s):
                    if s[i - j] == s[i + 1 + k]:
                        mygo.appendleft(s[i - j])
                        mygo.append(s[i + 1 + k])
                        length += 2
                        j += 1
                        k += 1
                    else:
                        break
                if max_length < length:
                    answer = ''.join(mygo)
                    max_length = length
        return answer


        """
        :type s: str
        :rtype: str
        """
        
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241127101342994](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241127101342994.png)





### 12029: 水淹七军

bfs, dfs, http://cs101.openjudge.cn/practice/12029/

思路：dfs和bfs都尝试了一遍（以下代码为dfs）。ai说我写得没问题，听说这题输入数据格式很奇葩，我懒得去调试了。。。这种异常数据输入需要掌握吗？还是说期末考不会遇到这种的

代码：

```python
def flow(x,y,m,n,chizu,mark_chizu):
    directions=[(1,0),(0,1),(-1,0),(0,-1)]
    for dx,dy in directions:
        nx,ny=x+dx,y+dy
        if 0<=nx<m and 0<=ny<n and chizu[nx][ny]<=chizu[x][y]:
            if not mark_chizu[nx][ny]:
                mark_chizu[nx][ny]=True
                flow(nx,ny,m,n,chizu,mark_chizu)

K=int(input())
for KK in range(K):
    m,n=map(int,input().split())
    chizu=[]
    mark_chizu=[[False for _ in range(n)] for _ in range(m)]
    for i in range(m):
        chizu.append(list(map(int,input().split())))
    i,j=map(int,input().split())
    p=int(input())
    water_sources=[]
    for pp in range(p):
        a,b=map(int,input().split())
        water_sources.append([a-1,b-1])

    #找到最高放水点
    highest_water_source=water_sources[0]
    for water_source in water_sources:
        if chizu[water_source[0]][water_source[1]]>chizu[highest_water_source[0]][highest_water_source[1]]:
            highest_water_source=water_source
    #print(highest_water_source)
    mark_chizu[highest_water_source[0]][highest_water_source[1]]=True

    #开淹
    flow(highest_water_source[0],highest_water_source[1],m,n,chizu,mark_chizu)
    for water_source in water_sources:
        if not mark_chizu[water_source[0]][water_source[1]]:
            mark_chizu[water_source[0]][water_source[1]]=True
            flow(water_source[0],water_source[1],m,n,chizu,mark_chizu)

    #检查
    if  mark_chizu[i-1][j-1]:
        print("Yes")
    else:
        print("No")


```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

没有AC，呜呜



### 02802: 小游戏

bfs, http://cs101.openjudge.cn/practice/02802/

思路：bfs部分能自己写出，但是难以处理关于记录线段数的问题，也找不到无法联通情况的鉴定条件。。还是得看题解试图研究



代码：

```python

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

难啊，bfs、dfs、dp算是基本会使用了，但是做题的时候还是心有余而力不足



