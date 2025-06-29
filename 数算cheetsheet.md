```python
进制转化：
bin() oct() hex()
int('1100101010',2)
except EOFError:
    
import sys# 使用 sys.stdin.read() 读取所有输入
data = sys.stdin.read()  # 读取整个输入流
print(data)

complex(a,b)
a+bj

float(input())
输出：
法一：f"{value:.nf}"  #其中n是希望保留的小数位数
百分数
print(f"Percentage: {percentage:.2%}")  # 输出：85.00%
科学计数法：
print(f"Scientific notation: {large_number:.2e}")  # 输出：1.23e+06

格式化输出：
基本模板：f"字符串 {表达式} 字符串"
 print(f"My name is {name} and I am {age} years old.")
三元运算符：
print(f"Adult status: {'Yes' if age >= 18 else 'No'}")

无空格输出： print(' '.join(map(str, minStep[i]))) #注意这里应该是字符串形式
保护圈： maze.append([-1] + [int(_) for _ in input().split()] + [-1]）
                 
lst.remove(item)
lst.index(item)#返回第一个出现item的下标
lst.pop(0)
del lst[i]
                 
# 创建字典
my_dict = {'name': 'Alice', 'age': 25, 'city': 'New York'}

d=[(1,2),(5,6),(7,'cgy')]
dict(d)
                 
 #通过键来搜索值
法一：print(my_dict['name'])  # 输出：Alice
法二：print(my_dict.get('name'))  # 输出：Alice
 print(my_dict.get('address', 'Not Found'))  # 输出：Not Found
                 
 #通过值来搜索键
找到所有的键：
法一：keys = [key for key, value in my_dict.items() if value == search_value]
法二：keys = list(filter(lambda key: my_dict[key] == search_value, my_dict))
找到第一个符合条件的键：
key = next((key for key, value in my_dict.items() if value == search_value), None)
                        
#删除键值对
法一：del my_dict['city']     
法二：age = my_dict.pop('age')
 print(age)  # 输出：26
                        
 #遍历字典：
    # 遍历键
    for key in my_dict:
    # 遍历值
    for value in my_dict.values():
     print(value)
     # 遍历键值对
    for key, value in my_dict.items():
     print(f"{key}: {value}")
                        
 #字典推导式举例：
numbers = [1, 2, 3, 4, 5]
 squared_dict = {n: n**2 for n in numbers}
 print(squared_dict)
 #字典排序：
sorted_dict = dict(sorted(my_dict.items(), key=lambda x: x[1], reverse=True))

# 创建集合
my_set = {1, 2, 3, 4, 5}
 another_set = set([3, 4, 5, 6, 7])
 #注意：set() 用来创建集合时，它接受一个可迭代对象（如列表、元组、字符串等），因而这里set() 会自动
从列表中提取元素并创建集合，而不能直接set(3, 4, 5, 6, 7)，因为set()括号里只可以有一个参数，而{}
则不同。
# 添加元素
my_set.add(6)  
# 删除元素（不存在元素可抛出错误）
my_set.remove(2)
 # 删除不存在的元素，不会抛出错误
my_set.discard(10) 

lambda的使用：                        
基本模板：lambda arguments: expression  #参数：对参数进行的操作
                        
在字典排序中：
sorted_dict = sorted(my_dict.items(), key=lambda x: x[1])
 #按值升序排序，注意sorted得到的是一个列表!
 #如果想要降序并转化为字典格式如下：
sorted_dict = dict(sorted(my_dict.items(), key=lambda x: x[1], reverse=True))
                        
与map结合：
# 对列表中的每个元素进行平方操作
squared_numbers = list(map(lambda x: x ** 2, numbers))

（1）
sorted() 返回一个新的排序后的列表，原始的可迭代对象不被修改。可以作用于任何可迭代对象，
包括列表、元组、字典等。支持自定义排序规则（通过 
key 参数）。用于需要保持原始数据不变的情况，
或需要排序结果为列表的场景。
如按长度排序：（字典中的用法见上一条）
words = ["banana", "apple", "pear", "cherry"]
 sorted_words = sorted(words, key=len)
对列表中的数组按照数组的第一个数字排序：
sorted_dist=sorted(dist,key=lambda x:x[0])
（2）
.sort() 是 列表对象的方法，只能对 列表 进行排序，原地修改列表，即 排序会直接修改原列表，
返回值为 
None 。适用于不需要保留原列表的情况，或者希望节省内存的场景
                        
alst=[10,20,30]
blst=[3,2,1]
zipped=sorted(list(zip(blst,alst)),key=lambda x:x[0])
blst,alst=zip(*zipped)
print(alst)
print(blst)
t=list(alst)
print(t)
#输出：（30，20，10）（1，2，3）[1,2,3]
                        
从列表中删除元素
法一：my_list = [1, 2, 3, 4, 2, 5]
 my_list.remove(2)  # 删除第一个 2
法二：my_list = [1, 2, 3, 4, 5]
 removed_element = my_list.pop(2)  # 删除索引为 2 的元素 (即 3)
                        
ord()    chr()
                        
enumerate(lst,start=0)
for index,num in enumerate(lst)

3. 迪杰斯特拉算法（最短权值路径）
（1）最短权值路径（现有一个共n个顶点（代表城市）、m条边（代表道路）的无向图（假设顶点编号为从
0到n-1），每条边有各自的边权，代表两个城市之间的距离。求从s号城市出发到达t号城市的最短距
离。）
import heapq
def dijkstra(n, edges, s, t):
    graph = [[] for _ in range(n)]
    for u, v, w in edges:
        graph[u].append((v, w))
        graph[v].append((u, w))
    pq = [(0, s)]  # (distance, node)
    visited = set()
    distances = [float('inf')] * n
    distances[s] = 0
    while pq:
        dist, node = heapq.heappop(pq)
        if node == t:
            return dist
        if node in visited:
            continue
        visited.add(node)
        for neighbor, weight in graph[node]:
            if neighbor not in visited:
                new_dist = dist + weight
                if new_dist < distances[neighbor]:
                    distances[neighbor] = new_dist
                    heapq.heappush(pq, (new_dist, neighbor))
    return -1
 n, m, s, t = map(int, input().split())
 edges = [list(map(int, input().split())) for _ in range(m)]
 result = dijkstra(n, edges, s, t)
 print(result)
                        
双dp：土豪购物
def max_value(s):
    n=len(s)
    dp1=[0 for _ in range(n)]
    dp2=[0 for _ in range(n)]
    dp1[0]=s[0]
    dp2[0]=s[0]
    for i in range(1,n):
        dp1[i]=max(dp1[i-1]+s[i],s[i])#不放回
        dp2[i]=max(dp2[i-1]+s[i],dp1[i-1],s[i])#放回之前某个，放回现在也就是第i个，从现在开始取
    return max(max(dp1),max(dp2))
 s=list(map(int,input().split(',')))
 max_num=max_value(s)
print(max_num)

类似思路：最大摆动子序列
def max_len(n,nums):
 if n==1:
 return 1
 else:
 up=1
 down=1
 for i in range(1,n):
 if nums[i]>nums[i-1]:
 up=down+1
 elif nums[i]<nums[i-1]:
 down=up+1
 return max(up,down)
 n=int(input())
 nums=list(map(int,input().split()))
 print(max_len(n,nums))
                        
小偷背包：01背包
n,b=map(int,input().split())
nedan=list(map(int,input().split()))
weight=list(map(int,input().split()))
dp=[[0 for _ in range(b+1)] for _ in range(n+1)]
for i in range(n+1):
    for j in range(b+1):
        if weight[i-1]<=j:
            dp[i][j]=max(dp[i-1][j],dp[i-1][j-weight[i-1]]+nedan[i-1])
print(dp[n][b])

完全背包：
def complete_knapsack(n, C, weights, values):
    # 初始化 dp 数组，dp[j] 表示容量为 j 时的最大价值
    dp = [0] * (C + 1)
    
    for i in range(n):
        for j in range(weights[i], C + 1):
            dp[j] = max(dp[j], dp[j - weights[i]] + values[i])
    
    return dp[C]

# 示例
n = 3
C = 10
weights = [2, 3, 5]
values = [1, 2, 3]

max_value = complete_knapsack(n, C, weights, values)
print(max_value)  # 输出: 8
                        
欧拉筛
# 返回小于r的素数列表
def oula(r):
    # 全部初始化为0
    prime = [0 for i in range(r+1)]
    # 存放素数
    common = []
    for i in range(2, r+1):
        if prime[i] == 0:
            common.append(i)
        for j in common:
            if i*j > r:
                break
            prime[i*j] = 1
            #将重复筛选剔除
            if i % j == 0:
                break
    return common
 prime = oula(20000)
 print(prime)
                        
def oula(a):
    zhishu=[]
    zhishu1=[True]*(a+1)
    for i in range(2,a+1):
        if zhishu1[i]:
            zhishu.append(i)
        for h in zhishu:
            if h*i<=a:
                zhishu1[h*i]=False
    zhishu=set(zhishu)
    return zhishu
                        
import heapq
heapq.heapify(lst)
heapq.heappush(lst,114)
x=heapq.heappop(lst)
最小元素：lst[0]

双端队列
from collections import deque
pq=deque([(x0,y0)])
                        
3. bisect:用于在已排序的列表中找到插入点，或者对列表进行插入操作，同时保持列表的顺序。常见的应用包
括二分查找（binary search）、在排序列表中插入元素等。
1.bisect_left(arr, x):（bisect_right(arr, x)同理）
返回一个索引，该索引是列表 arr 中插入元素 x 的位置，并且会确保 x 插入后，列表仍然保持升序排列。
如果 x 已经存在于列表中，则返回左边的插入位置（即 x 的第一个位置）。
import bisect
 arr = [1, 3, 4, 10, 12]
 index = bisect.bisect_left(arr, 5)
 print(index)  # 输出 3，因为 5 应该插入在 10 之前，索引 3
 2.insort(arr, x):（insort_left(arr,x) 保持升序，若x已经存在，插入左边，
insort_right(arr,x)同理）
将元素 x 插入到列表 arr 中，并保持列表的顺序。
等效于使用 bisect_right 找到插入位置，然后插入元素。
import bisect
 arr = [1, 3, 4, 10, 12]
 bisect.insort(arr, 5)  # 将 5 插入到正确的位置
print(arr)  # 输出 [1, 3, 4, 5, 10, 12]
二分查找实现：
import bisect
 arr = [1, 3, 4, 10, 12]
 x = 4
 pos = bisect.bisect_left(arr, x)
 if pos < len(arr) and arr[pos] == x:
 print(f"元素 {x} 存在于列表中，位置为 {pos}")
 else:
 print(f"元素 {x} 不在列表中")
区间查找：
import bisect
 intervals = [1, 5, 10, 15, 20]  # 代表的区间为 [1, 5), [5, 10), [10, 15), [15, 20)
 value = 12
 index = bisect.bisect_right(intervals, value)
 print(f"数值 {value} 在区间 {intervals[index-1]} 和 {intervals[index]} 之间")
                        
import itertools
a=[1,2,3]
p=itertools.permutations(a，2)
for pp in p:
    print(pp)
#输出：(1, 2)(1, 3)(2, 1)(2, 3)(3, 1)(3, 2)
```

![image-20241225200838270](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241225200838270.png)

![image-20241225201038155](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241225201038155.png)

![image-20241225201110039](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241225201110039.png)

```python
import time

for i in range(101):
    print("\r{:3}%".format(i),end=' ')
    time.sleep(0.05)
    
>>> list=[1,2,3,4]
>>> it = iter(list)    # 创建迭代器对象
>>> print (next(it))   # 输出迭代器的下一个元素
1
>>> print (next(it))
2
>>>

from functools import lru_cache
@lru_cache(maxsize=128)

#### 日期与时间
import calendar, datetime print(calendar.isleap(2020)) # 输出: True 
print(datetime.datetime(2023, 10, 5).weekday()) # 输出: 3 (星期四)
```

```python
背包问题（Knapsack Problem）是组合优化中的经典问题，通常的目的是从若干个物品中选择一些物品装入背包，使得背包中物品的总价值最大，且物品的总重量不超过背包的承重限制。

背包问题的变种主要有以下几种：0-1背包、完全背包、多重背包，及其二进制优化。

1. 0-1背包问题
定义： 在0-1背包问题中，给定n个物品和一个容量为C的背包。每个物品有一个重量和价值。每个物品只能选择放入背包或不放入背包，不能部分放入或重复放入。

状态转移方程： 设dp[i][j]表示前i个物品放入容量为j的背包所能获得的最大价值。状态转移方程为：

dp[i][j] = dp[i-1][j]：不选择第i个物品。
dp[i][j] = max(dp[i][j], dp[i-1][j-w[i]] + v[i])：选择第i个物品。
代码实现：

python
复制代码
def knapsack_01(n, C, weights, values):
    dp = [0] * (C + 1)
    for i in range(n):
        for j in range(C, weights[i] - 1, -1):  # 从后往前遍历，避免重复选择
            dp[j] = max(dp[j], dp[j - weights[i]] + values[i])
    return dp[C]
2. 完全背包问题
定义： 在完全背包问题中，给定n个物品和一个容量为C的背包。每个物品有一个重量和价值，并且每个物品可以选择无限个。

状态转移方程： 设dp[i][j]表示前i个物品放入容量为j的背包所能获得的最大价值。状态转移方程为：

dp[i][j] = dp[i-1][j]：不选择第i个物品。
dp[i][j] = max(dp[i][j], dp[i][j-w[i]] + v[i])：选择第i个物品。
与0-1背包的区别在于，完全背包问题允许物品多次选择，因此状态转移时内层循环应从前向后遍历。

代码实现：
def knapsack_complete(n, C, weights, values):
    dp = [0] * (C + 1)
    for i in range(n):
        for j in range(weights[i], C + 1):  # 完全背包，从前往后遍历
            dp[j] = max(dp[j], dp[j - weights[i]] + values[i])
    return dp[C]
3. 多重背包问题
定义： 多重背包问题是完全背包问题的一种扩展。每种物品有一个数量限制，物品的数量不能超过指定的最大数量。

状态转移方程： 设dp[i][j]表示前i种物品放入容量为j的背包所能获得的最大价值。多重背包问题的转移方式稍有变化，我们需要考虑每种物品的数量限制。

通常，可以使用“二进制分解”方法来简化多重背包问题，将问题转化为多个0-1背包问题的组合。

代码实现（分解法）：
def knapsack_multiple(n, C, weights, values, counts):
    dp = [0] * (C + 1)
    for i in range(n):
        # 物品i最多能使用counts[i]次
        for k in range(1, counts[i] + 1):
            for j in range(C, weights[i] * k - 1, -1):
                dp[j] = max(dp[j], dp[j - weights[i] * k] + values[i] * k)
    return dp[C]
4. 二进制优化（优化多重背包）
定义： 对于多重背包问题，我们可以通过“二进制优化”将其转化为多个0-1背包问题。二进制优化方法的核心思想是将每种物品的数量限制分解为若干个数量为2^k的子问题，这样可以减少状态转移的次数。

二进制优化思想：

将每个物品的数量count[i]分解为若干个2^k个物品。
例如，如果某种物品有3个，我们可以把它分解为1 + 2个物品，并分别处理这些“新物品”。
这种分解方法保证了每次只需要考虑“0个、1个、2个、4个……”物品，而不需要考虑所有物品数量的组合。
def knapsack_binary(n, C, weights, values, counts):
    dp = [0] * (C + 1)
    for i in range(n):
        k = 1
        while k <= counts[i]:  # 二进制分解
            for j in range(C, weights[i] * k - 1, -1):
                dp[j] = max(dp[j], dp[j - weights[i] * k] + values[i] * k)
            counts[i] -= k
            k *= 2
        # 处理剩余部分
        if counts[i] > 0:
            for j in range(C, weights[i] * counts[i] - 1, -1):
                dp[j] = max(dp[j], dp[j - weights[i] * counts[i]] + values[i] * counts[i])
    return dp[C]
总结
0-1背包：每个物品只能选择一次。
完全背包：每个物品可以选择任意次数，物品的选择没有限制。
多重背包：每个物品的选择次数有限制，通常通过“二进制优化”将其转化为多个0-1背包问题。
二进制优化：通过将物品的数量限制分解成二进制数次方的形式，从而优化多重背包问题。
```

描述

给定一组n种不同面额的硬币，以及要支付的总金额

计算并返回可以凑成总金额所需的 **最少的硬币个数** 。如果没有任何一种硬币组合能组成总金额，返回 -1。

你可以认为每种硬币的数量是无限的。

输入

输入为两行

第一行为两个整数n（1 ≤ n ≤ 100），m（0 ≤ m ≤ 10^6），其中n表示硬币的种类数，m表示要凑的总金额

第二行为n个整数，表示硬币的面值，所有硬币面值均小于m

输出

可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，则输出 -1。

```python
n,m=map(int,input().split())
mianzhilist=list(map(int,input().split()))
dp=[float("inf") for _ in range(m+1)]
dp[0]=0
for i in range(0,m+1):
    for j in range(0,n):
        if i>=mianzhilist[j]:
            dp[i]=min(dp[i],dp[i-mianzhilist[j]]+1)
if dp[m]==float("inf"):
    print(-1)
else:
    print(dp[m])
```

```python
#迪杰斯特拉伪代码
import heapq

def dijkstra(graph, start):
    # 初始化
    n = len(graph)  # 顶点个数
    dist = [float('inf')] * n  # 最短路径数组，初始为无穷大
    dist[start] = 0  # 起点到自身的距离为0
    visited = [False] * n  # 记录顶点是否被访问
    pq = [(0, start)]  # 优先队列，存储(距离, 顶点)
    
    while pq:
        current_dist, u = heapq.heappop(pq)
        
        if visited[u]:
            continue  # 如果当前顶点已被访问，跳过
        
        visited[u] = True  # 标记当前顶点为已访问
        
        # 松弛操作
        for v, weight in graph[u]:
            if not visited[v] and current_dist + weight < dist[v]:
                dist[v] = current_dist + weight
                heapq.heappush(pq, (dist[v], v))
    
    return dist
```

```python
def bellman_ford(graph, start, V):
    # 初始化
    dist = [float('inf')] * V
    dist[start] = 0

    # 松弛所有边 V-1 次
    for i in range(V - 1):
        for u, v, weight in graph:
            if dist[u] != float('inf') and dist[u] + weight < dist[v]:
                dist[v] = dist[u] + weight

    # 检测负权环
    for u, v, weight in graph:
        if dist[u] != float('inf') and dist[u] + weight < dist[v]:
            print("Graph contains a negative-weight cycle")
            return None

    return dist
    
# 图的边表示为 (起点, 终点, 权重)
graph = [
    (0, 1, 1),
    (1, 2, 3),
    (0, 2, 4),
    (2, 3, 2),
    (3, 1, -6)
]
V = 4  # 顶点数量
start = 0  # 源点

distances = bellman_ford(graph, start, V)
if distances:
    print("Vertex Distances from Source:", distances)
    
#输出：Graph contains a negative-weight cycle
```

Floyd-Warshall算法基于**动态规划**的思想：

- 如果顶点 `k` 是路径 `(i → j)` 的中间顶点之一，那么最短路径要么不经过 `k`，要么经过 `k`。
- 使用一个二维数组 `dist[i][j]` 来存储顶点 `i` 到顶点 `j` 的最短路径距离。
- 对每个中间顶点 `k`，更新所有顶点对 `(i, j)` 的最短路径，判断是否经过 `k` 会使路径更短。

**状态转移方程：**

dist[i][j]=min⁡(dist[i][j],dist[i][k]+dist[k][j])dist[i][j] = \min(dist[i][j], dist[i][k] + dist[k][j])dist[i][j]=min(dist[i][j],dist[i][k]+dist[k][j])

- `dist[i][j]`：表示从顶点 `i` 到顶点 `j` 的当前最短路径。
- `dist[i][k] + dist[k][j]`：表示从顶点 `i` 到 `j` 经过 `k` 顶点的路径长度。
- 取两者的较小值，更新最短路径。



**初始化：**

- 如果存在边 `i → j`，设置 `dist[i][j]` 为该边的权重。
- 如果 `i == j`，设置 `dist[i][j] = 0`。
- 如果不存在边 `i → j`，设置 `dist[i][j] = ∞`。

**动态规划：**

- 对每个顶点 `k`，将其作为中间节点，遍历所有的顶点对 `(i, j)`。
- 如果经过 `k` 可以缩短 `i → j` 的路径，则更新 `dist[i][j]`。

**检测负权环：**

- 如果存在 `dist[i][i] < 0`，说明图中存在**负权环**。

**输出结果：**

- 如果没有负权环，输出所有顶点对之间的最短路径。
- 如果有负权环，报告存在负权环。

```python
def floyd_warshall(graph):
    V = len(graph)  # 顶点数量
    dist = [[float('inf')] * V for _ in range(V)]
    
    # 初始化距离矩阵
    for i in range(V):
        for j in range(V):
            if i == j:
                dist[i][j] = 0  # 自己到自己的距离为0
            elif graph[i][j] != 0:
                dist[i][j] = graph[i][j]  # 存在边则设为权重

    # 动态规划核心
    for k in range(V):
        for i in range(V):
            for j in range(V):
                if dist[i][j] > dist[i][k] + dist[k][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
    
    # 检测负权环
    for i in range(V):
        if dist[i][i] < 0:
            print("Graph contains a negative-weight cycle")
            return None

    return dist

graph = [
    [0, 3, float('inf')],
    [float('inf'), 0, 1],
    [-2, float('inf'), 0]
]

distances = floyd_warshall(graph)
if distances:
    for row in distances:
        print(row)

输出：
[0, 3, 4]
[float('inf'), 0, 1]
[-2, 1, 0]
```

Boyer-Moore 投票算法
思路

如果我们把众数记为 +1，把其他数记为 −1，将它们全部加起来，显然和大于 0，从结果本身我们可以看出众数比其他数多。

算法

Boyer-Moore 算法的本质和方法四中的分治十分类似。我们首先给出 Boyer-Moore 算法的详细步骤：

我们维护一个候选众数 candidate 和它出现的次数 count。初始时 candidate 可以为任意值，count 为 0；

我们遍历数组 nums 中的所有元素，对于每个元素 x，在判断 x 之前，如果 count 的值为 0，我们先将 x 的值赋予 candidate，随后我们判断 x：

如果 x 与 candidate 相等，那么计数器 count 的值增加 1；

如果 x 与 candidate 不等，那么计数器 count 的值减少 1。

在遍历完成后，candidate 即为整个数组的众数。

我们举一个具体的例子，例如下面的这个数组：

[7, 7, 5, 7, 5, 1 | 5, 7 | 5, 5, 7, 7 | 7, 7, 7, 7]
在遍历到数组中的第一个元素以及每个在 | 之后的元素时，candidate 都会因为 count 的值变为 0 而发生改变。最后一次 candidate 的值从 5 变为 7，也就是这个数组中的众数。

Boyer-Moore 算法的正确性较难证明，这里给出一种较为详细的用例子辅助证明的思路，供读者参考：

首先我们根据算法步骤中对 count 的定义，可以发现：在对整个数组进行遍历的过程中，count 的值一定非负。这是因为如果 count 的值为 0，那么在这一轮遍历的开始时刻，我们会将 x 的值赋予 candidate 并在接下来的一步中将 count 的值增加 1。因此 count 的值在遍历的过程中一直保持非负。



排序链表：给出头节点head，返回排序后的链表

```python
class Solution:
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        def sortFunc(head,tail):
            if not head:
                return head
            if head.next==tail:
                head.next=None
                return head
            slow=fast=head
            while fast!=tail:
                slow=slow.next
                fast=fast.next
                if fast != tail:
                    fast = fast.next
            mid=slow
            return mergeTwoLists(sortFunc(head,mid),sortFunc(mid,tail))
        def mergeTwoLists(list1, list2):
            if not list1:
                return list2
            if not list2:
                return list1
            if list1.val<=list2.val:
                list1.next=mergeTwoLists(list1.next,list2)
                return list1
            else:
                list2.next=mergeTwoLists(list1,list2.next)
                return list2
        return sortFunc(head,None)
```

滑动窗口最大值

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        n = len(nums)
        q = collections.deque()
        for i in range(k):
            while q and nums[i] >= nums[q[-1]]:
                q.pop()
            q.append(i)

        ans = [nums[q[0]]]
        for i in range(k, n):
            while q and nums[i] >= nums[q[-1]]:
                q.pop()
            q.append(i)
            while q[0] <= i - k:
                q.popleft()
            ans.append(nums[q[0]])
        return ans
```

Prim算法（普里姆算法） 是一种用于求解 最小生成树（Minimum Spanning Tree, MST） 的经典贪心算法。它适用于 带权无向连通图，目标是找到一棵包含所有顶点的树，使得这棵树的所有边的权重之和最小。

🧠 算法原理
Prim 算法的基本思想是：

从一个起点顶点出发，逐步加入当前生成树与其他顶点之间具有最小权重的边，直到所有的顶点都被包含进生成树中。

核心步骤如下：
初始化：
选择任意一个起始顶点（例如顶点0），将其加入到最小生成树集合中。
维护一个数组 key[]，表示每个顶点连接到生成树所需的最小边权值。
维护一个数组 mst_set[]，记录哪些顶点已经被加入到MST中。
初始化 Key[] 中除了起点为0外，其余都为无穷大（∞）。
循环操作：
在未加入MST的顶点中，选出 Key 值最小的顶点 u。
将 u 加入 MST。
更新与 u 相邻的所有顶点 v 的 Key 值（如果连接它们的边权值小于当前 Key[v]）。
结束条件：
所有顶点都被加入 MST 后，算法结束。
✅ 算法特点
只适用于无向连通图。
可以处理带负权边的情况（因为只关心总权重最小的生成树）。
时间复杂度取决于实现方式：
使用邻接矩阵：O(V²)
使用优先队列 + 邻接表：O(E log V)

```python
import sys

class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0 for column in range(vertices)] 
                      for row in range(vertices)]

    # 找出 Key 数组中最小的 Key 值对应的顶点
    def min_key(self, key, mst_set):
        min_val = sys.maxsize
        min_index = -1
        for v in range(self.V):
            if key[v] < min_val and not mst_set[v]:
                min_val = key[v]
                min_index = v
        return min_index

    # Prim 算法主函数
    def prim_mst(self):
        parent = [None] * self.V  # 用来保存构造的MST的父节点
        key = [sys.maxsize] * self.V  # 每个顶点到MST的最小边权重
        key[0] = 0  # 起始点的 Key 设为0
        mst_set = [False] * self.V  # 是否已加入MST
        parent[0] = -1  # 第一个节点没有父节点

        for _ in range(self.V):
            u = self.min_key(key, mst_set)
            mst_set[u] = True

            # 更新相邻顶点的 Key 值
            for v in range(self.V):
                if self.graph[u][v] > 0 and not mst_set[v] and key[v] > self.graph[u][v]:
                    key[v] = self.graph[u][v]
                    parent[v] = u

        # 打印最终MST
        self.print_mst(parent)

    def print_mst(self, parent):
        print("Edge \tWeight")
        for i in range(1, self.V):
            print(f"{parent[i]} - {i}\t{self.graph[i][parent[i]]}")
```



```python
class MinHeap:
    def __init__(self):
        # 初始化一个空列表来存储堆元素
        self.heap = []

    def parent(self, index):
        """返回给定索引的父节点索引"""
        return (index - 1) // 2

    def left_child(self, index):
        """返回给定索引的左孩子索引"""
        return 2 * index + 1

    def right_child(self, index):
        """返回给定索引的右孩子索引"""
        return 2 * index + 2

    def insert(self, key):
        """插入一个新的值到堆中"""
        # 将新元素添加到堆末尾
        self.heap.append(key)
        current_index = len(self.heap) - 1
        # 维护堆性质：向上调整
        while current_index != 0 and self.heap[self.parent(current_index)] > self.heap[current_index]:
            # 交换当前节点与它的父节点
            self.heap[self.parent(current_index)], self.heap[current_index] = self.heap[current_index], self.heap[self.parent(current_index)]
            current_index = self.parent(current_index)

    def heapify_down(self, index):
        """从指定位置开始向下调整堆"""
        size = len(self.heap)
        smallest = index
        left = self.left_child(index)
        right = self.right_child(index)

        if left < size and self.heap[left] < self.heap[smallest]:
            smallest = left

        if right < size and self.heap[right] < self.heap[smallest]:
            smallest = right

        if smallest != index:
            # 交换并递归调用
            self.heap[index], self.heap[smallest] = self.heap[smallest], self.heap[index]
            self.heapify_down(smallest)

    def extract_min(self):
        """删除并返回最小元素"""
        if len(self.heap) <= 0:
            return float('inf')
        if len(self.heap) == 1:
            return self.heap.pop()

        # 获取根节点的值（最小值）
        root = self.heap[0]
        # 把最后一个节点移到根节点位置
        self.heap[0] = self.heap.pop()
        # 调整堆以维护堆性质
        self.heapify_down(0)
        return root

    def get_min(self):
        """获取但不移除最小元素"""
        if len(self.heap) <= 0:
            return float('inf')
        return self.heap[0]
```

KMP-字符子串匹配

```python
def build_lps(pattern):
    lps = [0] * len(pattern)
    length = 0
    i = 1
    while i < len(pattern):
        if pattern[i] == pattern[length]:
            length += 1
            lps[i] = length
            i += 1
        else:
            if length != 0:
                length = lps[length - 1]
            else:
                lps[i] = 0
                i += 1
    return lps


def kmp_search(text, pattern):
    n = len(text)
    m = len(pattern)
    lps = build_lps(pattern)
    i = j = 0
    while i < n:
        if pattern[j] == text[i]:
            i += 1
            j += 1
        if j == m:
            print(f"Found pattern at index {str(i-j)}")
            j = lps[j-1]
        elif i < n and pattern[j] != text[i]:
            if j != 0:
                j = lps[j-1]
            else:
                i += 1
text = "ABABDABACDABABCABAB"
pattern = "ABABCABAB"
kmp_search(text, pattern)
```

```python
class UnionFind:
    def __init__(self, size):
        # 初始化, 每个节点的父节点是它自己，rank初始为1
        self.parent = list(range(size))
        self.rank = [1] * size  # rank[i]表示以i为根的树的高度上界

    def find(self, p):
        # 查找p的根节点，并进行路径压缩
        if self.parent[p] != p:
            self.parent[p] = self.find(self.parent[p])
        return self.parent[p]

    def union(self, p, q):
        # 合并p和q所属的集合
        rootP = self.find(p)
        rootQ = self.find(q)
        if rootP != rootQ:
            # 按秩合并
            if self.rank[rootP] > self.rank[rootQ]:
                self.parent[rootQ] = rootP
            elif self.rank[rootP] < self.rank[rootQ]:
                self.parent[rootP] = rootQ
            else:
                self.parent[rootQ] = rootP
                self.rank[rootP] += 1

    def connected(self, p, q):
        # 判断p和q是否属于同一个集合
        return self.find(p) == self.find(q)
```

```python
def rabin_karp(text, pattern, base=256, mod=101):
    """
    Rabin-Karp 算法实现字符串匹配

    :param text: 要搜索的文本 (str)
    :param pattern: 要查找的模式串 (str)
    :param base: 基数，通常为字符集大小（如ASCII为256）
    :param mod: 一个大质数，用于减少哈希冲突
    :return: 所有匹配位置的起始索引列表
    """
    n = len(text)
    m = len(pattern)
    if m == 0 or n < m:
        return []

    # 计算 base^(m-1) % mod
    base_m = pow(base, m - 1, mod)

    # 初始哈希值
    hash_text = 0  # 文本子串的哈希值
    hash_pattern = 0  # 模式串的哈希值

    # 计算初始哈希值
    for i in range(m):
        hash_pattern = (base * hash_pattern + ord(pattern[i])) % mod
        hash_text = (base * hash_text + ord(text[i])) % mod

    result = []

    for i in range(n - m + 1):
        if hash_text == hash_pattern:
            # 哈希值匹配，进一步逐字符验证
            if text[i:i+m] == pattern:
                result.append(i)

        # 使用滚动哈希更新下一个窗口的哈希值
        if i < n - m:
            hash_text = (
                base * (hash_text - ord(text[i]) * base_m) + ord(text[i + m])
            ) % mod

            # 防止负数
            if hash_text < 0:
                hash_text += mod

    return result
```

```python
def boyer_moore(text, pattern):
    # 预处理坏字符表
    def preprocess_bad_char(pattern):
        table = {}
        for i in range(len(pattern)):
            table[pattern[i]] = i  # 最后一次出现的位置
        return table

    # 预处理好后缀表
    def preprocess_good_suffix(pattern):
        m = len(pattern)
        suffix_table = [0] * (m + 1)
        border = [0] * (m + 1)
        i = m
        j = 0
        while i > 0:
            while j < m - i and pattern[i + j] == pattern[j]:
                j += 1
            suffix_table[i] = j
            i -= 1
            j = 0
        for i in range(m):
            j = m - suffix_table[i]
            if j <= m:
                border[j] = i
        return suffix_table, border

    n = len(text)
    m = len(pattern)
    if m == 0 or m > n:
        return []

    bad_char = preprocess_bad_char(pattern)
    _, good_suffix_border = preprocess_good_suffix(pattern)

    i = 0
    occurrences = []
    while i <= n - m:
        j = m - 1
        while j >= 0 and pattern[j] == text[i + j]:
            j -= 1
        if j < 0:
            occurrences.append(i)
            # 使用好后缀规则继续查找下一个
            i += good_suffix_border[1]
        else:
            # 计算坏字符规则和好后缀规则的移动步数，取最大值
            bc_shift = j - bad_char.get(text[i + j], -1)
            gs_shift = 1
            if j < m - 1:
                gs_shift = m - good_suffix_border[j + 1] - 1
            i += max(bc_shift, gs_shift)
    return occurrences
```

```python
def rabin_karp_multi_pattern(text, patterns, base=256, mod=101):
    """
    Rabin-Karp 算法实现多模式匹配

    :param text: 要搜索的文本 (str)
    :param patterns: 要查找的多个模式串组成的列表 (List[str])
    :param base: 基数，通常为字符集大小（如ASCII为256）
    :param mod: 一个大质数，用于减少哈希冲突
    :return: 字典，键为模式串，值为该模式串所有匹配位置的索引列表
    """
    n = len(text)
    result = {pattern: [] for pattern in patterns}
    
    # 移除空模式和长度大于 text 的模式
    valid_patterns = [p for p in patterns if len(p) > 0 and len(p) <= n]
    if not valid_patterns:
        return result

    max_len = max(len(p) for p in valid_patterns)
    min_len = min(len(p) for p in valid_patterns)

    # 存储不同长度的模式
    patterns_by_length = {}
    for p in valid_patterns:
        plen = len(p)
        if plen not in patterns_by_length:
            patterns_by_length[plen] = []
        patterns_by_length[plen].append(p)

    # 对每种长度单独处理
    for m in patterns_by_length:
        curr_patterns = patterns_by_length[m]
        hash_to_patterns = {}
        base_m = pow(base, m - 1, mod)

        # 预处理：将当前长度的所有模式串的哈希值存储起来
        for pattern in curr_patterns:
            h = 0
            for ch in pattern:
                h = (base * h + ord(ch)) % mod
            if h not in hash_to_patterns:
                hash_to_patterns[h] = []
            hash_to_patterns[h].append(pattern)

        # 计算初始窗口的哈希值
        hash_text = 0
        for i in range(m):
            hash_text = (base * hash_text + ord(text[i])) % mod

        # 滑动窗口遍历文本
        for i in range(n - m + 1):
            if hash_text in hash_to_patterns:
                current_substring = text[i:i+m]
                for pattern in hash_to_patterns[hash_text]:
                    if current_substring == pattern:
                        result[pattern].append(i)

            # 更新滚动哈希
            if i < n - m:
                hash_text = (
                    base * (hash_text - ord(text[i]) * base_m) + ord(text[i + m])
                ) % mod
                if hash_text < 0:
                    hash_text += mod

    return result
text = "ABABDABACDABABCABAB"
patterns = ["ABAB", "ABABC", "CAB", "AB"]

matches = rabin_karp_multi_pattern(text, patterns)
for pattern, indices in matches.items():
    print(f"Pattern '{pattern}' found at indices:", indices)
#输出：
Pattern 'ABAB' found at indices: [0, 10]
Pattern 'ABABC' found at indices: [10]
Pattern 'CAB' found at indices: [8, 13]
Pattern 'AB' found at indices: [0, 2, 5, 10, 12, 14, 16]
```

拓扑排序

```python
from collections import defaultdict

# 用于表示图的类
class Graph:
    def __init__(self, vertices):
        # 使用字典存储邻接表
        self.graph = defaultdict(list)
        # 图中顶点的数量
        self.V = vertices  

    # 向图中添加边的方法
    def addEdge(self, u, v):
        self.graph[u].append(v)

    # 拓扑排序使用的递归辅助函数
    def topologicalSortUtil(self, v, visited, stack):

        # 将当前节点标记为已访问
        visited[v] = True

        # 对所有与该节点相邻的节点进行递归调用
        for i in self.graph[v]:
            if not visited[i]:
                self.topologicalSortUtil(i, visited, stack)

        # 将当前节点压入栈中，栈中存储的是拓扑排序的结果
        stack.append(v)

    # 执行拓扑排序的函数。它使用了递归的topologicalSortUtil()
    def topologicalSort(self):
        # 初始化所有顶点为未访问状态
        visited = [False]*self.V
        stack = []

        # 调用递归辅助函数对每个顶点进行拓扑排序
        for i in range(self.V):
            if not visited[i]:
                self.topologicalSortUtil(i, visited, stack)

        # 输出栈中的内容，注意要反向输出（因为最后加入的应该是最前面的）
        print(stack[::-1])  # 返回列表的逆序

# 示例用法：
if __name__ == "__main__":
    g = Graph(6)  # 创建一个包含6个顶点的图
    g.addEdge(5, 2)
    g.addEdge(5, 0)
    g.addEdge(4, 0)
    g.addEdge(4, 1)
    g.addEdge(2, 3)
    g.addEdge(3, 1)

    print("拓扑排序结果：")
    g.topologicalSort()  # 执行拓扑排序并打印结果
```

调度场算法（波兰表达式）

```python
def infix_to_postfix(expression):
    # 定义运算符的优先级
    precedence = {'+':1, '-':1, '*':2, '/':2}
    stack = []  # 用于存储操作符和左括号
    postfix = []  # 存储最终的后缀表达式
    number = ''  # 临时字符串，用于构建多位数字或小数

    for char in expression:
        # 如果字符是数字或小数点，则将其添加到number变量中
        if char.isnumeric() or char == '.':
            number += char
        else:
            # 如果当前不是数字或小数点，并且之前有累积的数字，则处理这些数字
            if number:
                num = float(number)
                # 将数字添加到postfix列表中，如果是整数则转换为int类型
                postfix.append(int(num) if num.is_integer() else num)
                number = ''  # 清空number变量
            
            # 处理运算符
            if char in '+-*/':
                # 当栈顶元素的优先级大于等于当前运算符时，弹出栈顶元素并添加到postfix
                while stack and stack[-1] in '+-*/' and precedence[char] <= precedence[stack[-1]]:
                    postfix.append(stack.pop())
                # 将当前运算符压入栈中
                stack.append(char)
            elif char == '(':
                # 左括号直接入栈
                stack.append(char)
            elif char == ')':
                # 右括号：将栈中的元素弹出直到遇到左括号
                while stack and stack[-1] != '(':
                    postfix.append(stack.pop())
                # 弹出左括号（不加入postfix）
                stack.pop()

    # 如果遍历完表达式后number仍有内容，说明还有未处理的数字
    if number:
        num = float(number)
        postfix.append(int(num) if num.is_integer() else num)

    # 将栈中剩余的操作符全部弹出并添加到postfix
    while stack:
        postfix.append(stack.pop())

    # 返回由postfix列表组成的字符串，各元素间以空格分隔
    return ' '.join(str(x) for x in postfix)

# 主程序：读取输入并调用infix_to_postfix函数
n = int(input())  # 输入测试用例的数量
for _ in range(n):
    expression = input()  # 每次输入一个中缀表达式
    print(infix_to_postfix(expression))  # 输出对应的后缀表达式

def postfix_to_infix(postfix):
    stack = []
    for token in postfix.split():
        if token.isalnum():  # 如果是操作数，直接压入栈
            stack.append(token)
        else:  # 如果是运算符
            # 注意：这里假设所有运算符都是二元的
            operand2 = stack.pop()
            operand1 = stack.pop()
            # 使用括号确保运算顺序正确
            temp_exp = "(" + operand1 + " " + token + " " + operand2 + ")"
            stack.append(temp_exp)
    
    # 栈中唯一的元素就是转换后的中缀表达式
    return stack[0]

# 示例用法
postfix_expression = "3 4 2 * 1 5 - 2 3 ^ ^ / +"
print("中缀表达式:")
print(postfix_to_infix(postfix_expression))
```

Trie

```python
class TrieNode:
    def __init__(self):
        self.children = {}  # 子节点，键为字符，值为TrieNode
        self.is_end_of_word = False  # 标记是否为单词结尾

class Trie:
    def __init__(self):
        self.root = TrieNode()  # 根节点为空

    # 插入单词到Trie
    def insert(self, word: str) -> None:
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()  # 创建新节点
            node = node.children[char]  # 移动到子节点
        node.is_end_of_word = True  # 标记单词结束

    # 搜索是否存在完整单词
    def search(self, word: str) -> bool:
        node = self.root
        for char in word:
            if char not in node.children:
                return False  # 字符不存在
            node = node.children[char]
        return node.is_end_of_word  # 返回是否是完整单词

    # 检查是否存在以prefix开头的单词
    def startsWith(self, prefix: str) -> bool:
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
```

强连通分量：

```python
def tarjan(graph):
    """
    使用Tarjan算法查找所有强连通分量
    :param graph: 图的邻接表表示法
    :return: 所有强连通分量组成的列表
    """
    index_counter = [0]  # 全局变量用于计数访问顺序
    stack = []  # 栈用于存储当前正在探索的节点
    lowlinks = {}  # 存储每个节点的low-link值
    index = {}  # 存储每个节点的访问顺序
    result = []  # 存储所有强连通分量
    
    def strongconnect(node):
        # 设置节点的索引和low-link值为其访问顺序
        index[node] = index_counter[0]
        lowlinks[node] = index_counter[0]
        index_counter[0] += 1
        stack.append(node)
        
        # 考虑每一个邻居
        for successor in graph[node]:
            if successor not in index:
                # 如果后继还没有被访问过，递归调用strongconnect
                strongconnect(successor)
                lowlinks[node] = min(lowlinks[node], lowlinks[successor])
            elif successor in stack:
                # 如果后继还在栈中（即属于当前SCC），更新low-link值
                lowlinks[node] = min(lowlinks[node], index[successor])
        
        # 如果节点是它自己所在的SCC的根
        if lowlinks[node] == index[node]:
            connected_component = []
            while True:
                successor = stack.pop()
                connected_component.append(successor)
                if successor == node:
                    break
            result.append(connected_component)
    
    for node in graph:
        if node not in index:
            strongconnect(node)
    
    return result

# 示例用法
if __name__ == "__main__":
    # 定义一个有向图（邻接表形式）
    graph = {
        0: [1],
        1: [2],
        2: [0, 3],
        3: [4],
        4: []
    }
    
    sccs = tarjan(graph)
    print("强连通分量:")
    for scc in sccs:
        print(scc)
```
