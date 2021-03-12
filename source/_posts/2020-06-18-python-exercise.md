---
layout: post
title:  "Python经典习题代码"
date:   2020-06-18 13:03:25
author: coolxy
categories: 
  - 教程技巧
  - python
tags: python
---

## 精心收集的Python经典习题代码

### 1. 用4个数字组成多少个不重复3位数？
```python
    print('用2,4,8,9 `组成不重复的3位数：')
    l=0
    for i in (2,4,8,9):
        for j in (2,4,8,9):
            for k in (2,4,8,9):
                if i!=j and i!=k and j!=k:
                    print(i*100+j*10+k)
                    l+=1
                        print('共有%d个不同的3位数。'%l)
```

### 2.企业资金利润发放问题  

'''
企业发放的奖金根据利润提成。利润(profit)低于或等于10万元时，奖金可提10%；利润高于10万元，低于20万元时，低于10万元的部分按10%提成，高于10万元的部分，可提成7.5%；
20万到40万之间时，高于20万元的部分，可提成5%；40万到60万之间时高于40万元的部分，可提成3%；60万到100万之间时，高于60万元的部分，可提成1.5%，高于100万元时，
超过100万元的部分按1%提成，从键盘输入当月利润profit，求应发放奖金总数？
程序分析：请利用数轴来分界，定位。注意定义时需把奖金定义成长整型
'''

#### 方法1：比较笨的方法，才开始学的时候弄的

```python
bonus=0
profit=int(input('请输入你本月的业绩（总利润  元）：'))
if profit>100000 :
    if profit <=200000:
        bonus = 100000 * 0.1 + (profit - 100000)*0.075
    elif profit <=400000 :
        bonus = 100000 * 0.1 + 100000 * 0.075+ (profit - 200000)*0.05
    elif profit <= 600000 :
        bonus = 100000 * 0.1 +100000*0.075 +200000*0.05+ (profit - 400000)*0.03
    elif profit <= 1000000 :
        bonus = 100000 * 0.1 +100000*0.075 +200000*0.05+ 200000*0.03+(profit - 600000)*0.0015
    elif profit >1000000 :
        bonus = 100000 * 0.1 +100000*0.075 +200000*0.05+ 200000*0.03+400000*0.015+(profit - 1000000)*0.001

else:
    bonus = profit * 0.1
   
print('你本月的业绩利润是：%d 元，共发放奖金：%d 元，继续加油！'%(profit,bonus))
```

#### 方法2：利用函数，自行调用

函数1：

```python
def test_02(profit): 
    rate = [0.1, 0.075, 0.05, 0.03, 0.015, 0.01] 
    amount = [10, 20, 40, 60, 100] 
    sum0 = amount[0] * rate[0] 
    sum1 = sum0 + (amount[1] - amount[0]) * rate[1] 
    sum2 = sum1 + (amount[2] - amount[1]) * rate[2] 
    sum3 = sum2 + (amount[3] - amount[2]) * rate[3] 
    sum4 = sum3 + (amount[4] - amount[3]) * rate[4] 
    if profit <= 10: 
        return profit * rate[0] 
    elif (profit > 10) and (profit <= 20): 
        return sum0 + (profit - amount[0]) * rate[1] 
    elif (profit > 20) and (profit <= 40): 
        return sum1 + (profit - amount[1]) * rate[2] 
    elif (profit > 40) and (profit <= 60): 
        return sum2 + (profit - amount[2]) * rate[3] 
    elif (profit > 60) and (profit <= 100): 
        return sum3 + (profit - amount[3]) * rate[4] 
    elif profit > 100: 
        return sum4 + (profit - amount[4]) * rate[5] 
    else: print("输入金额错误！") 
```

函数2：    

```python
def test_02_1(): 
    i = int(input("净利润:")) 
    arr = [1000000, 600000, 400000, 200000, 100000, 0] 
    rat = [0.01, 0.015, 0.03, 0.05, 0.075, 0.1] 
    r = 0 
    for idx in range(0, 6): 
    	if i > arr[idx]: 
            # print(idx) 
            r += (i - arr[idx]) * rat[idx] 
            # print((i - arr[idx]) * rat[idx]) 
            i = arr[idx] 
            print(r) 
            return r
```

### 3. 判断1000以内的完全平方数

问题：一个整数，它加上100后是一个完全平方数，再加上268又是一个完全平方数，
请问该数是多少？

```python
import math

#笨办法1,效率低下：
def check_sqrt1():
    print('用多个循环嵌套来解决')
    num1=1
    num2=False
    while num1<1000:
        for i in range(num2,num1):
            for j in range(num2,num1):
                for k in range(num2,num1):
                    if j**2==i+100 and k**2==i+268:
                        print('这个数是%d'%i)
                        num2=True
        if num2:
            break
        num1+=1
```

​    

```python
def check_sqrt2():
    #用数学函数平方根sqrt()来解决，效率高
    print('用int(sqrt())==sqrt() 来判断')
    num=1
    while num <1000:
        if math.sqrt(num + 100)==int(math.sqrt(num+100)) and math.sqrt(num+268)==int(math.sqrt(num+268)):
            print('这个数是:%d  '%num)
        num+=1

#check_sqrt1()
check_sqrt2()d  '%num)
        num+=1
```
### 4. 判断一年中的第几天的问题

问题描述：输入某年某月某日，判断这一天是这一年的第几天？

思路：要判断这年有多少天，是不是闰年，再算是第几天

闰年：被4整除、不被100整除，整百年被400整除

```python
def day_in_year(date):
    month_days=[31,28,31,30,31,30,31,31,30,31,30,31]
    year=int(date[:4])
    month=int(date[4:6])
    day=int(date[6:])
    print(year,month,day)
    if year % 4==0 and year%100!=0 or year % 400==0:
        month_days[1]=29
    dayth=0
    for i in range(month-1):
        dayth+=month_days[i]
    dayth+=day
    return dayth

date=input('请输入日期，如：20200202：')
dayth=day_in_year(date)
print('%s 在%s 年中是第%d天。'%(date,date[:4],dayth))
```

### 5.输入数字的排序问题

有几个整数，请把这几个数由小到大输出

```python
import math

def paixu(n): #这是经典的冒泡法排序
    tmp=int
    for i in range(len(n)):
        for j in range(i+1,len(n)):
            if n[i]>n[j]:
                n[i],n[j]=n[j],n[i]
    return n

num_list=[4,2,9,65,1]
print('原数字组：',num_list)

print('冒泡法排序：',paixu(num_list))
num_list.sort()
print('函数sort() 排序：',num_list)
```
### 6. 斐波那契数列
```
def fib(n):
    fib1=1
    fib2=2
    for i in range(n):
        print(fib1)
        fib1+=fib2
        fib1,fib2 =fib2,fib1
        time.sleep(0.05)
        #print(fib1)
    
n=int(input('请输入斐波那契个数:'))
fib(n)
```
### 7. 输出 9*9 乘法口诀表
输出 9*9 乘法口诀表  
```
for i in range(1,10): #乘数1-9循环
    for j in range(1,i+1):#乘数1-i
        print('%d*%d=%d  '%(i,j,i*j),end='') #
        if i == j:
            print('\n')
```
### 9. 输出1000内的水仙花数  
打印出所有的“水仙花数”，所谓“水仙花数”是指一个三位数，其各位数字立方和等于该数本身。例如：153是一个“水仙花数”，因为153=1的三次方＋5的三次方＋3的三次方。  
```
for i in range(100,1000):
    bai=int(i/100)
    shi=int(((i-int(i/100)*100))/10)
    ge=int((i-int(i/10)*10))
    if i==bai**3+shi**3+ge**3:
        print('%d = %d + %d + %d '%(i,bai**3,shi**3,ge**3))
```
### 10. 将一个正整数分解质因数  
例如：输入90,打印出90=2\*3\*3\*5  
```
def zys(num):
    for i in range(2,num):
        if num%i==0:
            yinshu.append(str(i))
            if num/i >i:
                zys(num//i)
            elif num/i>1:
                yinshu.append(str(num//i))
            break
    else:
        yinshu.append(str(num))

num=int(input('请输入一个数字：'))
if num <=1:
    num = int(input('输入错误，请重新输入：'))
    
yinshu=[]
zys(num)
y='+'.join(yinshu)
print(num,'=',y)
```
### 11. 汉诺塔问题  
```
def hano(num,a,b,c):
    if num ==1:
        print(a,' -> ',c)
        return
    else:
        hano(num-1,a,c,b)
        print(a,' -> ',c)
        hano(num-1,b,a,c)
        return

num=int(input('请输入要移动的汉诺塔层数：'))
a,b,c='A','B','C'

hano(num,a,b,c)
```
### 12. 输出完数  
完数：一个数如果恰好等于它的因子之和，这个数就称为"完数"。例如6=1＋2＋3.编程找出1000以内的所有完数。
```
def wanshu(start,end):
    for i in range(start,end):
        num_list=[1]
        for j in range(2,i):
            if i%j==0:
                num_list.append(j)
                num_list.append(i//j)
        if len(num_list)>2:
            s=0
            num_list=list(set(num_list))
            num_list.sort()
            for k in num_list:
                s+=k
            if s==i:
                print(num_list)
                print(sum(num_list))
    
wanshu(1,10000)
```
### 13. 球体下落问题  
一球从100米高度自由落下，每次落地后反跳回原高度的一半；再落下，求它在第10次落地时，共经过多少米？第10次反弹多高？  
#### 方法1（我自己的）
```
h=100.0
s=0.0
for i in range(1,11):
    s+=h    #每次下降的距离
    h=h/2    #弹起的距离
    print('第%d次弹起%f米，球已行动了%f米。'\
    	%(i,h,s))
    if i <10:
        s+=h    #这h是前九次下落的距离，第十次不下落，总距离不再加
    
print(h,'   ',s)
```
#### 方法2：
```
tour = []
height = []
hei = 100.0  # 起始高度
tim = 10  # 次数
for i in range(1, tim + 1):
     # 从第二次开始，落地时的距离应该是反弹高度乘以2（弹到最高点再落下）
    if i == 1:
        tour.append(hei)
    else:
        tour.append(2 * hei)
    hei /= 2
    height.append(hei)
print('总高度：tour = {0}'.format(sum(tour)))
print('第10次反弹高度：height = {0}'.format(height[-1]))
```
### 14.猴子吃桃问题
题目：猴子吃桃问题：猴子第一天摘下若干个桃子，当即吃了一半，还不过瘾，又多吃了一个，第二天早上又将剩下的桃子吃掉一半，又多吃了一个。以后每天早上都吃了前一天剩下的一半零一个。到第10天早上想再吃时，见只剩下一个桃子了。求第一天共摘了多少。程序分析：采取逆向思维的方法，从后往前推断。
```
bea_sum=1
for i in range(10,0,-1):
    if i ==10:
        bea_sum=1
    else:
        bea_sum=(bea_sum+1)*2
  
print('第1天共摘了%d个桃子'%bea_sum)

for i in range(1,11):
    print('第%d 天吃了%d 个桃子'%(i,bea_sum//2+1))
    bea_sum=bea_sum//2 -1
```
### 15. 求阶乘
#### 15.1 函数递归
```
def jiec(n):
    if n==1:
        return 1
    else:
        return jiec(n-1)*n
    
n=int(input('请输入要求阶乘的数字：'))
jie=jiec(n)
print('递归函数：\n%d 的阶乘是：%d '%(n,jie))
print('%d!=%d \n'%(n,jie))
```
#### 15.2 for循环：
```
jie2=1
for i in range(1,n+1):
    jie2*=i
print('for循环求解：\n%d 的阶乘是：%d \n'%(n,jie2))
```
#### 15.3 while 循环求解
```
jie3=1
while i>=1:
    jie3 *=i
    i-=1
print('while循环求解：\n%d 的阶乘是：%d '%(n,jie3))
```
### 16. 输出101-200（区间数可自定）以内的素数
判断101-200之间有多少个素数，并输出所有素数。
```
count=0
for i in range(101,1001):
    for j in range(2,int(i/2)):
        if i%j==0 : #int(i/j)==i/j:
            print('%d 不是素数:%d=%d x %d'%(i,i,j,i/j))
            break
    else:
        count+=1
        print(i ,' 是素数')
            	
print('101-200之间共有%d个素数'%count)
```
### 17. 

***
## 以下问题摘自<https://codingbat.com/>  
### monkey_trouble
We have two monkeys, a and b, and the parameters a_smile and b_smile indicate if each is smiling. We are in trouble if they are both smiling or if neither of them is smiling. Return True if we are in trouble.

monkey_trouble(True, True) → True
monkey_trouble(False, False) → True
monkey_trouble(True, False) → False
```
def mokey_trouble(a_smile,b_smile):
    if (a_smile and b_smile) or (not a_smile and not b_smile):
        return True
    else:
    return False
```