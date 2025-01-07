# Assignment #8: 田忌赛马来了

Updated 1021 GMT+8 Nov 12, 2024

2024 fall, Complied by <mark>陈冠宇 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 12558: 岛屿周⻓

matices, http://cs101.openjudge.cn/practice/12558/ 

思路：

![image-20241112160315960](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241112160315960.png)

代码：

```python
n,m=map(int,input().split())
cou=0
chizu=[[0 for _ in range(n+2)]for _ in range(m+2)]
for i in range(1,n+1):
    chizu[i]=[0]+list(map(int,input().split()))+[0]
for i in range(1,n+1):
    for j in range(1,m+1):
        if chizu[i][j]==1:
            cou=cou+4-chizu[i+1][j]-chizu[i-1][j]-chizu[i][j+1]-chizu[i][j-1]
print(cou)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





### LeetCode54.螺旋矩阵

matrice, https://leetcode.cn/problems/spiral-matrix/

与OJ这个题目一样的 18106: 螺旋矩阵，http://cs101.openjudge.cn/practice/18106

思路：



代码：

```python
class Solution(object):
    def spiralOrder(self, matrix):
        m=len(matrix)
        n=len(matrix[0])
        answer=[]
        matrix=[[114]*(n+2)]+matrix+[[114]*(n+2)]
        for i in range(1,m+1):
            matrix[i]=[114]+ matrix[i]+ [114]
        x=1
        y=1
        while True:
            while matrix[x][y]!=114:
                answer.append(matrix[x][y])
                matrix[x][y]=114
                y=y+1
            y=y-1
            x=x+1
            if matrix[x][y]==114:
                break
            while matrix[x][y]!=114:
                answer.append(matrix[x][y])
                matrix[x][y] = 114
                x=x+1
            x=x-1
            y=y-1
            if matrix[x][y]==114:
                break
            while matrix[x][y]!=114:
                answer.append(matrix[x][y])
                matrix[x][y] = 114
                y=y-1
            y=y+1
            x=x-1
            if matrix[x][y]==114:
                break
            while matrix[x][y]!=114:
                answer.append(matrix[x][y])
                matrix[x][y] = 114
                x=x-1
            x=x+1
            y=y+1
            if matrix[x][y]==114:
                break
        return(answer)
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241112165530319](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241112165530319.png)



### 04133:垃圾炸弹

matrices, http://cs101.openjudge.cn/practice/04133/

思路：

想知道那些四五十毫秒的代码是怎么写的（害怕

代码：

```python
d=int(input())
n=int(input())
mark=0
cou=1
wang=[[0 for _ in range(1025)]for _ in range(1025)]
for lese in range(n):
    x,y,i=map(int,input().split())
    for m in range(x-d,x+d+1):
        for n in range(y-d,y+d+1):
            if 0<=m<=1024 and 0<=n<=1024:
                wang[m][n]=wang[m][n]+i
for i in range(0,1025):
    for j in range(0,1025):
        if wang[i][j]==mark:
            cou=cou+1
        if wang[i][j]>mark:
            mark=wang[i][j]
            cou=1
print(cou,mark)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241113184932120](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241113184932120.png)



### LeetCode376.摆动序列

greedy, dp, https://leetcode.cn/problems/wiggle-subsequence/

与OJ这个题目一样的，26976:摆动序列, http://cs101.openjudge.cn/routine/26976/

思路：

为了处理连续相同数字情况，把代码到处打补丁得很丑。。。

代码：

```python
class Solution(object):
    def wiggleMaxLength(self, nums):
        n=len(nums)
        cou=2
        if n==1:
            return(1)
        else:
            if nums[1]-nums[0]>0:
                cgy=-1
            elif nums[1]==nums[0]:
                cou=1
                winko=0
                for i in range(1,n):
                    if nums[i]-nums[i-1]!=0:
                        cgy=(-1)*(nums[i]-nums[i-1])
                        winko=1
                        cou=2
                        break
                if winko==0:
                    return(1)
            else:
                cgy=1
            for i in range(1,n-1):
                if (nums[i+1]-nums[i])*cgy>0:
                    cou+=1
                    cgy=cgy*(-1)

            return(cou)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241113191719995](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241113191719995.png)



### CF455A: Boredom

dp, 1500, https://codeforces.com/contest/455/problem/A

思路：



代码：

```python
n=int(input())
nums=list(map(int,input().split()))
count=[0]*(max(nums)+1)
dp=[0]*(len(count))
for num in nums:
    count[num]+=1
dp[1]=count[1]*1
for i in range(2,len(count)):
    dp[i]=max(dp[i-1],count[i]*i+dp[i-2])
print(dp[-1])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241114081643592](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241114081643592.png)



### 02287: Tian Ji -- The Horse Racing

greedy, dfs http://cs101.openjudge.cn/practice/02287

思路：贪心策略的选择有点难，一开始直接从最慢的开始比较，于是难以处理速度相等的情况

然后因为手动加了一个max(answer,0)被wa了一个小时。。。仔细看了数据才发现可以输出负数，气死我了

代码：

```python
while True:
    n=int(input())
    if n==0:
        break
    else:
        tianwin=0
        qiwin=0
        pingju=0
        tianlist=list(map(int,input().split()))
        qilist=list(map(int,input().split()))
        tianlist.sort()
        qilist.sort()
        #print(tianlist)
        #print(qilist)
        ts=0
        qs=0
        tf=n-1
        qf=n-1
        while ts<=tf and qs<=qf:
            if tianlist[tf]>qilist[qf]:        #先比较最快的马，田忌赢
                tianwin+=1
                qf-=1
                tf-=1
            elif tianlist[tf]<qilist[qf]:      #最快的马田忌输，则用田忌最慢的马比齐王最快的马
                qiwin+=1
                ts+=1
                qf-=1
            else:                              #最快的平局
                if tianlist[ts]>qilist[qs]:    #比较最慢的马，田忌赢
                    tianwin+=1
                    qs+=1
                    ts+=1
                elif tianlist[ts]<qilist[qs]:  #最慢的马田忌输，则用田忌最慢的马比齐王最快的马
                    qiwin+=1
                    qf-=1
                    ts+=1
                else:                            #最慢的也平局,则比较田忌最慢的与齐王最快的
                    if tianlist[ts]==qilist[qf]: #平局
                        pingju+=1
                    else:                         #输
                        qiwin+=1
                    ts+=1
                    qf-=1

    if False:
        print("田",tianwin)
        print("齐",qiwin)
        print("平",pingju)
    print(200*(tianwin-qiwin))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241114113642561](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241114113642561.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

期中周终于结束了，再不读计概就要完蛋了。。。dp和递归都还一知半解，每日选做也好久没做了，呜呜

决定现在开始恶补一下



