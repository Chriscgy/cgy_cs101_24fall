# Assignment #B: Dec Mock Exam大雪前一天

Updated 1649 GMT+8 Dec 5, 2024

2024 fall, Complied by <mark>陈冠宇 工学院</mark>



**说明：**

1）⽉考： AC6<mark>（1）</mark> 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### E22548: 机智的股民老张

http://cs101.openjudge.cn/practice/22548/

思路：

维护两个列表，分别代表i位置左侧的最大数和i位置右侧的最小数，然后遍历i取两列表之差的最大值

代码：

```python
nedan_list=list(map(int,input().split()))
n=len(nedan_list)

min_lo=[float('inf')]*n
min_lo[0]=nedan_list[0]
max_lo=[0]*n
max_lo[-1]=nedan_list[-1]

for i in range(1,n):
    min_lo[i]=min(min_lo[i-1],nedan_list[i])
#print(min_lo)

for i in range(n-2,-1,-1):
    max_lo[i]=max(max_lo[i+1],nedan_list[i])
#print(max_lo)

ans=0
for i in range(0,n):
    ans=max(ans,max_lo[i]-min_lo[i])
print(ans)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241210085844441](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241210085844441.png)



### M28701: 炸鸡排

greedy, http://cs101.openjudge.cn/practice/28701/

思路：参考了题解



代码：

```python
n,k=map(int, input().split())
t=list(map(int, input().split()))
t.sort()
s=sum(t)
while True:
    if t[-1]>s/k:
        s-=t.pop()
        k-=1
    else:
        print(f'{s / k:.3f}')
        break
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241210111652650](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241210111652650.png)



### M20744: 土豪购物

dp, http://cs101.openjudge.cn/practice/20744/

思路：不会



代码：

```python

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





### T25561: 2022决战双十一

brute force, dfs, http://cs101.openjudge.cn/practice/25561/

思路：不会



代码：

```python

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





### T20741: 两座孤岛最短距离

dfs, bfs, http://cs101.openjudge.cn/practice/20741/

思路：

考场上基本把这题的代码框架写出来了，但是有两个地方卡着导致没AC：1.visited数组浅拷贝问题一直没发现 2.一时没想起来步数计算的写法

原本我的思路是遍历完第一座岛之后，从岛上每个点出发开始bfs并比较每条路径长度，比较耗时；考完之后看群，发现“将第一座岛上的所有点直接加入栈进行一次bfs”的思路，非常精妙！

代码：

```python
from collections import deque
import copy

def bfs(x,y,n,chizu,legal_number,goal,s,visited,qq):
    qq.append((x,y,0))
    visited[x][y]=True
    while qq:
        x,y,step=qq.popleft()
        dir=[(0,1),(1,0),(0,-1),(-1,0)]
        for dx,dy in dir:
            nx,ny=x+dx,y+dy
            if 0<=nx<n and 0<=ny<n and chizu[nx][ny] == goal and not visited[nx][ny]:
                #print("goal!",nx,ny)
                return step
            if 0<=nx<n and 0<=ny<n and not visited[nx][ny] and chizu[nx][ny]==legal_number :
                #print(nx,ny)
                qq.append((nx,ny,step+1))
                s.append((nx,ny))
                visited[nx][ny]=True


n=int(input())
chizu=[[] for _ in range(n)]
s=[]
for i in range(n):
    k=input()
    for kk in k:
        chizu[i].append(int(kk))
#print(chizu)
visited = [[False for _ in range(n)] for _ in range(n)]

winko=1
for i in range(n):
    for j in range(n):
        if chizu[i][j]==1:
            s=[(i,j)]
            qq=deque([(i,j,0)])
            r=bfs(i,j,n,chizu,1,3,s,visited,qq)
            winko=0
            break
    if winko==0:
        break

#print(s)
qqq=deque()
for x,y in s:
    qqq.append((x,y,0))
print(bfs(x,y,n,chizu,0,1,s,visited,qqq))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241210085639727](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241210085639727.png)



### T28776: 国王游戏

greedy, http://cs101.openjudge.cn/practice/28776

思路：参考了题解



代码：

```python
n=int(input())
aa,bb=map(int,input().split())
numbers=[]
for _ in range(n):
    a,b=map(int,input().split())
    numbers.append((a,b))
numbers.sort(key=lambda x:(x[0]*x[1]))
result=0
for i in range(n):
    result=max(result,aa//numbers[i][1])
    aa*=numbers[i][0]
print(result)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

月考击碎我的计概梦，即使会的题目也要debug好久，不会的题真去研究下一两个小时就过去了，考场上纯等死



