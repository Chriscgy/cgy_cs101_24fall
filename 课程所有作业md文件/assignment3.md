# Assign #3: Oct Mock Exam暨选做题目满百

Updated 1537 GMT+8 Oct 10, 2024

2024 fall, Complied by Hongfei Yan==（陈冠宇 工学院）==



**说明：**

1）Oct⽉考： AC6==（5）== 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。

2）请把每个题目解题思路（可选），源码Python, 或者C++/C（已经在Codeforces/Openjudge上AC），截图（包含Accepted, 学号），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、作业评论有md或者doc。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### E28674:《黑神话：悟空》之加密

http://cs101.openjudge.cn/practice/28674/



思路：

很简单的题目，但是不小心把字母表记成了24个，于是65+24=89，恰好测试数据中没有出现Y和Z，导致这题卡了我将近40分钟才AC......QAQ

代码

```python
n=int(input())
ylist=input()
list=[]
for word in ylist:
    list.append(ord(word))
for x in list:
    if 65<=x<=91:
        while x-n<65:
            x=x+26
        print(chr(x-n),end='')
    else:
        while x-n<97:
            x=x+26
        print(chr(x-n),end='')

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241014184622680](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241014184622680.png)



### E28691: 字符串中的整数求和

http://cs101.openjudge.cn/practice/28691/



思路：



代码

```python
a=input()
x=int(a[0]+a[1])
y=int(a[4]+a[5])
print(x+y)
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241014184653653](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241014184653653.png)



### M28664: 验证身份证号

http://cs101.openjudge.cn/practice/28664/



思路：



代码

```python
n=int(input())
list=['1','0','X','9','8','7','6','5','4','3','2']
for i in range(0,n):
    j=input()
    shen=int(j[0])*7+int(j[1])*9+int(j[2])*10+int(j[3])*5+int(j[4])*8+int(j[5])*4+int(j[6])*2+int(j[7])*1+int(j[8])*6+int(j[9])*3+int(j[10])*7+int(j[11])*9+int(j[12])*10+int(j[13])*5+int(j[14])*8+int(j[15])*4+int(j[16])*2
    if str(list[shen%11])==j[17]:
        print("YES")
    else:
        print("NO")

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241014184759541](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241014184759541.png)



### M28678: 角谷猜想

http://cs101.openjudge.cn/practice/28678/



思路：



代码

```python
n=int(input())
while n!=1:
    if n%2!=0:
        print(str(n)+"*3+1="+str(n*3+1))
        n=n*3+1
    else:
        print(str(n)+'/2='+str(n//2))
        n=n//2
print("End")
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241014184827167](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241014184827167.png)



### M28700: 罗马数字与整数的转换

http://cs101.openjudge.cn/practice/28700/



思路：第一次尝试使用字典，罗马数字转整数的过程中非常好用！但是整数转罗马数字还是只会笨办法



##### 代码

```python
list=input()
winko=0
while True:
    try:
        z=int(list)
        winko=1
        a=z//1000
        b=(z-1000*a)//100
        c=(z-1000*a-100*b)//10
        d=z-1000*a-100*b-10*c
        print('M'*a,end='')
        if b>=1 and b<4:
            print('C'*b,end='')
        elif b==4:
            print('CD',end='')
        elif b>=5 and b<9:
            print('D'+'C'*(b-5),end='')
        elif b==9:
            print('CM',end='')
        if c>=1 and c<4:
            print('X'*c,end='')
        elif c==4:
            print('XL',end='')
        elif c>=5 and c<9:
            print('L'+'X'*(c-5),end='')
        elif c==9:
            print('XC',end='')
        if d>=1 and d<4:
            print('I'*d,end='')
        elif d==4:
            print('IV',end='')
        elif d>=5 and d<9:
            print('V'+'I'*(d-5),end='')
        elif d==9:
            print('IX',end='')
        break
    except ValueError:
        break
if winko==0:
    x=0
    dian={'I':1,'V':5,'X':10,'L':50,'C':100,'D':500,'M':1000}
    i=0
    while i<=len(list)-2:
        if dian[list[i]]>=dian[list[i+1]]:
            x=x+dian[list[i]]
            i=i+1
        else:
            x=x+(dian[list[i+1]]-dian[list[i]])
            i=i+2
    if i==len(list)-1:
        x=x+dian[list[-1]]
    print(x)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241014184937601](C:\Users\72848\AppData\Roaming\Typora\typora-user-images\image-20241014184937601.png)



### *T25353: 排队 （选做）

http://cs101.openjudge.cn/practice/25353/



思路：



代码

```python


```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

月考看到第六题的题目数据就非常清楚用简单思路不可能写出来的。。。遂放弃

之前自学的老本差不多吃光了，以后算法什么的强度上来对我而言应该是个大挑战

不过计概算是我目前最感兴趣的一节专业课！感觉这些知识很有用，成就感满满！









