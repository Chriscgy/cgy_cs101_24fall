# Assignment #6: Recursion and DP

Updated 2201 GMT+8 Oct 29, 2024

2024 fall, Complied by <mark>陈冠宇 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### sy119: 汉诺塔

recursion, https://sunnywhy.com/sfbj/4/3/119  

思路：

代码：

```python
def haoni(n,source,help,target):
    if n>0:
        haoni(n-1,source,target,help)
        print(source+"->"+target)
        haoni(n-1,help,source,target)

a=int(input())
print(2**a-1)
haoni(a,'A','B',"C")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241102111225947](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241102111225947.png)



### sy132: 全排列I

recursion, https://sunnywhy.com/sfbj/4/3/132

思路：

完全不会，ai写的，我崩溃了

代码：

```python
def permute(nums):
    def backtrack(first=0):
        # 如果已经到达数组的最后一个元素，则添加当前排列到结果列表中
        if first == n:  
            output.append(nums[:])
        for i in range(first, n):
            # 动态交换当前索引的值与之后的值
            nums[first], nums[i] = nums[i], nums[first]
            # 继续递归下一个位置
            backtrack(first + 1)
            # 回溯，恢复原始数组状态
            nums[first], nums[i] = nums[i], nums[first]
    
    n = len(nums)
    output = []
    backtrack()
    return output

def main():
    N = int(input().strip())  # 读取输入的正整数
    nums = list(range(1, N+1))  # 创建从1到N的列表
    permutations = permute(nums)  # 获得所有排列
    # 按照字典序对所有排列进行排序
    permutations.sort()
    # 输出每个排列
    for p in permutations:
        print(' '.join(map(str, p)))

if __name__ == "__main__":
    main()
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241104202220098](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241104202220098.png)



### 02945: 拦截导弹 

dp, http://cs101.openjudge.cn/2024fallroutine/02945

思路：

这题和02533一模一样，直接照搬之前写过的代码，改一个符号就行

代码：

```python
n=int(input())
xlist=list(map(int,input().split()))
tong=[1]*n
cgy=1
for i in range(1,n+1):
    mm=0
    for j in range(1,i):
        if xlist[-i]>=xlist[-j]:
            mm=max(mm,tong[-j])
    tong[-i]=mm+1
    #print(tong)
    cgy=max(cgy,tong[-i])
print(cgy)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241105100702883](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241105100702883.png)



### 23421: 小偷背包 

dp, http://cs101.openjudge.cn/practice/23421

思路：



代码：

```python
n,b=map(int,input().split())
nedan=list(map(int,input().split()))
wei=list(map(int,input().split()))
dp=[[0]*(b+1) for _ in range(n+1)]
for i in range(1,n+1):
    for w in range(1,b+1):
        if wei[i-1]<=w:
            dp[i][w]=max(dp[i-1][w],nedan[i-1]+dp[i-1][w-wei[i-1]])
        else:
            dp[i][w]=dp[i-1][w]
print(dp[n][b])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241105103256651](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241105103256651.png)



### 02754: 八皇后

dfs and similar, http://cs101.openjudge.cn/practice/02754

思路：

用ai做的，对着ai的代码研究了半天才看懂，要自己写出来...不太可能

代码：

```python
def is_not_under_attack(row, col, queens):
    # 检查是否有皇后在同一列或对角线上
    for r, c in enumerate(queens):
        if c == col or abs(r - row) == abs(c - col):
            return False
    return True

def solve_n_queens(n, row=0, queens=[]):
    if row == n:
        yield queens[:]
    else:
        for col in range(n):
            if is_not_under_attack(row, col, queens):
                queens.append(col)
                yield from solve_n_queens(n, row + 1, queens)
                queens.pop()

def get_queen_string(b):
    solutions = list(solve_n_queens(8))
    # 将每个解转换成字符串形式
    queen_strings = [''.join(str(q+1) for q in solution) for solution in solutions]
    # 排序
    queen_strings.sort()
    # 返回第b个解
    return queen_strings[b-1]

# 测试代码
n = int(input())
for _ in range(n):
    b = int(input())
    print(get_queen_string(b))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241105113620007](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241105113620007.png)



### 189A. Cut Ribbon 

brute force, dp 1300 https://codeforces.com/problemset/problem/189/A

思路：



代码：

```python
n,a,b,c=map(int,input().split())
dp=[-1]*(n+1)
dp[0]=0
for i in range(1,n+1):
    if i>=a and dp[i-a]!=-1:
        dp[i]=max(dp[i],dp[i-a]+1)
    if i>=b and dp[i-b]!=-1:
        dp[i]=max(dp[i],dp[i-b]+1)
    if i>=c and dp[i-c]!=-1:
        dp[i]=max(dp[i],dp[i-c]+1)
print(dp[n])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241102112257042](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241102112257042.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

作业好难啊！！！！！

期中好忙啊！！！！！



