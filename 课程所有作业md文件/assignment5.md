# Assignment #5: Greedy穷举Implementation

Updated 1939 GMT+8 Oct 21, 2024

2024 fall, Complied by <mark>陈冠宇 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 04148: 生理周期

brute force, http://cs101.openjudge.cn/practice/04148

思路：



代码：

```python
cc=0
while"迎面走来的你让我如此蠢蠢欲动":
    p,e,i,d=map(int,input().split())
    if p==-1:
        break
    else:
        cc+=1
        zlist=[0]*30000
        while p+23<=29999:
            zlist[p]+=1
            p+=23
        while e+28<=29999:
            zlist[e+28]+=1
            e+=28
        for z in range(i,29999,33):
            if zlist[z]==2:
                ans=z
                break
        x=str(ans-d)
        y=str(cc)
        print("Case "+y+": the next triple peak occurs in "+x+" days.")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241022184014168](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241022184014168.png)



### 18211: 军备竞赛

greedy, two pointers, http://cs101.openjudge.cn/practice/18211

思路：

列表排序后，先从前往后制造直到钱不够用，然后从后往前卖一个，再返回去从刚才的断点继续从前往后制造

每次制造结束后检查多出的武器种类是否有增加

代码：

```python
p=int(input())
wlist=list(map(int,input().split()))
wlist.sort()
#print(wlist)
i=0
j=0
cj=0
cd=0
winko=0
ans=0
while winko==0:
    winko=1
    if i <= (len(wlist) - 1):
        while p>=wlist[i]:
            #print(wlist[i],end=' ')
            p=p-wlist[i]
            cj=cj+1
            i+=1
            winko=0
            ans=max(ans,cj-cd)
            if i>len(wlist)-1:
                break
    if j <= (len(wlist) - i-1):
        if cj>cd:
            #print(wlist[-j-1])
            p=p+wlist[-j-1]
            cd+=1
            j+=1
            winko=0
            if j>len(wlist)-1:
                break
print(ans)
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241022201301502](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241022201301502.png)



### 21554: 排队做实验

greedy, http://cs101.openjudge.cn/practice/21554

思路：

排序了两遍，疑似很低效

代码：

```python
n=int(input())
alist=list(map(int,input().split()))
indices=list(range(len(alist)))
indices.sort(key=lambda x:alist[x])
alist.sort()
zz=n-1
sum=0
for a in range(0,n-1):
    sum=sum+alist[a]*zz
    zz-=1
zong=sum/n
for cb in indices:
    print(cb+1,end=" ")
print()
print("{:.2f}".format(zong))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241028163618986](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241028163618986.png)



### 01008: Maya Calendar

implementation, http://cs101.openjudge.cn/practice/01008/

思路：



代码：

```python
n=int(input())
print(n)
zong=0
dian={"pop":1,"no":2,"zip":3,"zotz":4,"tzec":5,"xul":6,"yoxkin":7,"mol":8,"chen":9,"yax":10,"zac":11,"ceh":12,"mac":13,"kankin":14,"muan":15,"pax":16,"koyab":17,"cumhu":18}
biao=["1 imix","2 ik","3 akbal","4 kan","5 chicchan","6 cimi","7 manik","8 lamat","9 muluk","10 ok","11 chuen","12 eb","13 ben","1 ix","2 mem","3 cib","4 caban","5 eznab","6 canac","7 ahau","8 imix","9 ik","10 akbal","11 kan","12 chicchan","13 cimi","1 manik","2 lamat","3 muluk","4 ok","5 chuen","6 eb","7 ben","8 ix","9 mem","10 cib","11 caban","12 eznab","13 canac","1 ahau","2 imix","3 ik","4 akbal","5 kan","6 chicchan","7 cimi","8 manik","9 lamat","10 muluk","11 ok","12 chuen","13 eb","1 ben","2 ix","3 mem","4 cib","5 caban","6 eznab","7 canac","8 ahau","9 imix","10 ik","11 akbal","12 kan","13 chicchan","1 cimi","2 manik","3 lamat","4 muluk","5 ok","6 chuen","7 eb","8 ben","9 ix","10 mem","11 cib","12 caban","13 eznab","1 canac","2 ahau","3 imix","4 ik","5 akbal","6 kan","7 chicchan","8 cimi","9 manik","10 lamat","11 muluk","12 ok","13 chuen","1 eb","2 ben","3 ix","4 mem","5 cib","6 caban","7 eznab","8 canac","9 ahau","10 imix","11 ik","12 akbal","13 kan","1 chicchan","2 cimi","3 manik","4 lamat","5 muluk","6 ok","7 chuen","8 eb","9 ben","10 ix","11 mem","12 cib","13 caban","1 eznab","2 canac","3 ahau","4 imix","5 ik","6 akbal","7 kan","8 chicchan","9 cimi","10 manik","11 lamat","12 muluk","13 ok","1 chuen","2 eb","3 ben","4 ix","5 mem","6 cib","7 caban","8 eznab","9 canac","10 ahau","11 imix","12 ik","13 akbal","1 kan","2 chicchan","3 cimi","4 manik","5 lamat","6 muluk","7 ok","8 chuen","9 eb","10 ben","11 ix","12 mem","13 cib","1 caban","2 eznab","3 canac","4 ahau","5 imix","6 ik","7 akbal","8 kan","9 chicchan","10 cimi","11 manik","12 lamat","13 muluk","1 ok","2 chuen","3 eb","4 ben","5 ix","6 mem","7 cib","8 caban","9 eznab","10 canac","11 ahau","12 imix","13 ik","1 akbal","2 kan","3 chicchan","4 cimi","5 manik","6 lamat","7 muluk","8 ok","9 chuen","10 eb","11 ben","12 ix","13 mem","1 cib","2 caban","3 eznab","4 canac","5 ahau","6 imix","7 ik","8 akbal","9 kan","10 chicchan","11 cimi","12 manik","13 lamat","1 muluk","2 ok","3 chuen","4 eb","5 ben","6 ix","7 mem","8 cib","9 caban","10 eznab","11 canac","12 ahau","13 imix","1 ik","2 akbal","3 kan","4 chicchan","5 cimi","6 manik","7 lamat","8 muluk","9 ok","10 chuen","11 eb","12 ben","13 ix","1 mem","2 cib","3 caban","4 eznab","5 canac","6 ahau","7 imix","8 ik","9 akbal","10 kan","11 chicchan","12 cimi","13 manik","1 lamat","2 muluk","3 ok","4 chuen","5 eb","6 ben","7 ix","8 mem","9 cib","10 caban","11 eznab","12 canac","13 ahau","1 imix",]
for i in range(n):
    sb=input().split()
    notd=int(sb[0][0:-1])
    if sb[1]=="uayet":
        zong=int(sb[2])*365+361+notd-1
    else:
        zong=int(sb[2])*365+(dian[sb[1]]-1)*20+notd
    onian=zong//260
    onum=zong%260
    print(biao[onum],onian)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241028173546179](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241028173546179.png)



### 545C. Woodcutters

dp, greedy, 1500, https://codeforces.com/problemset/problem/545/C

思路：

每棵树先试着往前倒，再试着往后倒，都不行就不倒，然后将“边界”移到被占用的最前一个点。但是我无法证明这种做法一定保证砍倒棵数最多...?

代码：

```python
n=int(input())
winko=[[]for i in range(n)]
for i in range(n):
    winko[i]=list(map(int,input().split()))
si=winko[0][0]
cou=1
#print(winko)
for i in range(1,n-1):
    if i<n-2:
        if winko[i][0]-winko[i][1]>si:
            si=winko[i][0]
            cou=cou+1
        elif winko[i][0]+winko[i][1]<winko[i+1][0]:
            si=winko[i][0]+winko[i][1]
            cou=cou+1
        else:
            si=winko[i][0]
    if i==n-2:
        if winko[i][0]+winko[i][1]<winko[i+1][0] or winko[i][0]-winko[i][1]>si:
            cou=cou+1
if n>=2:
    cou=cou+1
print(cou)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241029102721149](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241029102721149.png)



### 01328: Radar Installation

greedy, http://cs101.openjudge.cn/practice/01328/

思路：



代码：

```python
import math
case=1
while True:
    n,d=map(int,input().split())
    if n==0 and d==0:
        break
    else:
        xlist=[0]*n
        nosylist=[0]*n
        rlist=[]
        left_island=100000000
        winko=1
        for i in range(n):
            xlist[i],nosylist[i]=map(int,input().split())
            if nosylist[i]>d:
                winko=0

        indices=list(range(len(xlist)))
        indices.sort(key=lambda x: (xlist[x]))
        ylist=[nosylist[i] for i in indices]
        xlist.sort()

        left_island=xlist[0]
        ileft=0
        if winko==1:
            rlist.append(math.sqrt(d**2-(ylist[ileft])**2)+xlist[ileft])
        cou=1
        i=1
        #print(left_island)
        #print(xlist)
        #print(ylist)
        while i<n and winko==1:
            if ylist[i]**2+(xlist[i]-rlist[-1])**2>d**2:
                 if xlist[i]>=rlist[-1]:
                     #print("+1")
                    left_island=xlist[i]
                    ileft=i
                    rlist.append(math.sqrt(d ** 2 - (ylist[ileft]) ** 2) + xlist[ileft])
                    cou+=1
                 else:
                     left_island = xlist[i]
                     ileft = i
                     rlist[-1]=math.sqrt(d**2-ylist[ileft]**2) + xlist[ileft]
            i+=1
        if winko!=0:
            print("Case "+str(case)+": "+str(cou))
        else:
            print("Case "+str(case)+": -1")
        case+=1
        input()
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241029152549828](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241029152549828.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

作业题目越来越难，不过基本上可以自己（花很多时间）写出来，或者稍微问一下一些语法的细节。但是很多题目都用的比较低下的算法，没有什么高级东西



