# Assignment #7: Nov Mock Exam立冬

Updated 1646 GMT+8 Nov 7, 2024

2024 fall, Complied by <mark>陈冠宇 工学院</mark>



**说明：**

1）⽉考： AC6<mark>（未参加）</mark> 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### E07618: 病人排队

sorttings, http://cs101.openjudge.cn/practice/07618/

思路：



代码：

```python
n=int(input())
hao=[]
age=[]
olderage=[]
olderhao=[]
x=n
helper=[]
for i in range(0,n):
    m,n=input().split()
    if int(n)>=60:
        olderage.append(int(n))
        olderhao.append(m)
        helper.append(x)
        x-=1
    else:
        age.append(int(n))
        hao.append(m)
combined=zip(olderage,helper,olderhao)
sorted_combined=sorted(combined)
olderage,helper,olderhao=zip(*sorted_combined)
for i in range(1,len(olderhao)+1):
    print(olderhao[-i])
for i in range(0,len(hao)):
    print(hao[i])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241109122801722](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241109122801722.png)



### E23555: 节省存储的矩阵乘法

implementation, matrices, http://cs101.openjudge.cn/practice/23555/

思路：



代码：

```python
n,m1,m2=map(int,input().split())
mx=[[0 for _ in range(n)] for _ in range(n)]
my=[[0 for _ in range(n)] for _ in range(n)]
manswer=[[0 for _ in range(n)] for _ in range(n)]
for i in range(0,m1):
    a,b,c=map(int,input().split())
    mx[a][b]=c
for i in range(0,m2):
    a,b,c=map(int,input().split())
    my[a][b]=c
for i in range(0,n):
    for j in range(0,n):
        for k in range(0,n):
            if mx[i][k]*my[k][j]!=0:
                manswer[i][j]=manswer[i][j]+mx[i][k]*my[k][j]
#print(manswer)
for i in range(0,n):
    for j in range(0,n):
        if manswer[i][j]!=0:
            print(i,j,manswer[i][j])
```



代码运行截图 ==（至少包含有"Accepted"）==





### M18182: 打怪兽 

implementation/sortings/data structures, http://cs101.openjudge.cn/practice/18182/

思路：



代码：

```python

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>





### M28780: 零钱兑换3

dp, http://cs101.openjudge.cn/practice/28780/

思路：



代码：

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



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241110154700537](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241110154700537.png)



### T12757: 阿尔法星人翻译官

implementation, http://cs101.openjudge.cn/practice/12757

思路：



代码：

```python
def english_to_number(s):
    word_to_num = {"zero": 0, "one": 1, "two": 2, "three": 3, "four": 4,"five": 5, "six": 6, "seven": 7, "eight": 8, "nine": 9,"ten": 10, "eleven": 11, "twelve": 12, "thirteen": 13, "fourteen": 14,"fifteen": 15, "sixteen": 16, "seventeen": 17, "eighteen": 18, "nineteen": 19,"twenty": 20, "thirty": 30, "forty": 40, "fifty": 50, "sixty": 60,"seventy": 70, "eighty": 80, "ninety": 90,"hundred": 100, "thousand": 1000, "million": 1000000}
    words = s.split()
    negative = False
    number = 0
    current_number = 0
    scale = 1
    if words[0] == "negative":
        negative = True
        words = words[1:]
    for word in words:
        if word == "hundred":
            current_number *= 100
        elif word == "thousand":
            number += current_number * 1000
            current_number = 0
        elif word == "million":
            number += current_number * 1000000
            current_number = 0
        else:
            current_number += word_to_num[word]
    number += current_number
    if negative:
        number = -number
    return number
input_str = input()
print(english_to_number(input_str))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241110155243742](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241110155243742.png)



### T16528: 充实的寒假生活

greedy/dp, cs10117 Final Exam, http://cs101.openjudge.cn/practice/16528/

思路：

dp还是没有完全掌握，很多时候需要问下ai

代码：

```python
def max_activities_dp(n, activities):
    # 按照活动的结束时间进行排序
    activities.sort(key=lambda x: x[1])
    
    # 初始化 dp 数组
    dp = [1] * n
    
    # 动态规划填表
    for i in range(1, n):
        for j in range(i):
            if activities[j][1] < activities[i][0]:
                dp[i] = max(dp[i], dp[j] + 1)
    
    # 返回结果
    return max(dp)

# 主函数
def main():
    import sys
    input = sys.stdin.read
    data = input().split()
    
    index = 0
    n = int(data[index])
    index += 1
    
    activities = []
    for _ in range(n):
        start = int(data[index])
        end = int(data[index + 1])
        activities.append((start, end))
        index += 2
    
    result = max_activities_dp(n, activities)
    print(result)

if __name__ == "__main__":
    main()
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241110161830364](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241110161830364.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

期中季马上要结束了，这一周对于计概是黑暗的一周。。。被其他科目搞得焦头烂额的我根本没法投入大量时间死啃dp之类的阴间知识点。。。等数学考完一定要每天三四个小时地苦读计概才能补上

不过好歹也能自己写出一部分dp的题目，也算是略有进步（？



