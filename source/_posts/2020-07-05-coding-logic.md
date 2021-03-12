---
layout: post
title:  "python练习园地（三）——Logic篇"
date:   2020-07-05 19:03:25
author: coolxy
categories: 
  - 教程技巧
  - python
tags: [python,codingbat]
---

#### 翻译是用百度翻译的，勉强能看明白。

## [Logic-1](https://codingbat.com/python/Logic-1) > cigar_party


When squirrels get together for a party, they like to have cigars. A squirrel party is successful when the number of cigars is between 40 and 60, inclusive. Unless it is the weekend, in which case there is no upper bound on the number of cigars. Return True if the party with the given values is successful, or False otherwise. 

当松鼠聚在一起参加聚会时，他们喜欢抽雪茄。当雪茄数量在40到60支之间时，松鼠派对就成功了。除非是周末，在这种情况下，雪茄数量没有上限。如果具有给定值的参与方成功，则返回True，否则返回False。

cigar_party(30, False) → False 

cigar_party(50, False) → True 

cigar_party(70, True) → True

### Code:

```python
def cigar_party(cigars, is_weekend):
  if not is_weekend:
    if cigars>=40 and cigars<=60:
      return True
    else:
      return False
  elif cigars>=40 :
    return True
  else:
    return False
```

## [Logic-1](https://codingbat.com/python/Logic-1) > date_fashion

You and your date are trying to get a table at a restaurant. The parameter "you" is the stylishness of your clothes, in the range 0..10, and "date" is the stylishness of your date's clothes. The result getting the table is encoded as an int value with 0=no, 1=maybe, 2=yes. If either of you is very stylish, 8 or more, then the result is 2 (yes). With the exception that if either of you has style of 2 or less, then the result is 0 (no). Otherwise the result is 1 (maybe).

#### Eg:

date_fashion(5, 10) → 2 

date_fashion(5, 2) → 0 

date_fashion(5, 5) → 1

你和你的约会对象想在餐馆找张桌子。参数“you”是你衣服的款式，在0到10的范围内，“date”是约会对象衣服的款式。得到表的结果被编码为一个int值，0=no，1=maybe，2=yes。如果你们中的任何一个非常时尚，8或更多，那么结果是2（是）。例外情况是，如果两人的样式为2或更少，则结果为0（否）。否则结果是1（可能）。

### Code:

```python
def date_fashion(you, date):
  if you <=2 or date<=2:
    return 0
  elif you>=8 or date >=8:
    return 2
  else:
    return 1
```

## [Logic-1](https://codingbat.com/python/Logic-1) > squirrel_play

The squirrels in Palo Alto spend most of the day playing. In particular, they play if the temperature is between 60 and 90 (inclusive). Unless it is summer, then the upper limit is 100 instead of 90. Given an int temperature and a boolean is_summer, return True if the squirrels play and False otherwise. 

帕洛阿尔托的松鼠大部分时间都在玩耍。特别是，如果温度在60到90之间（包括60到90），它们就会演奏。除非是夏天，否则上限是100而不是90。给定一个int temperature和一个boolean是_summer，如果松鼠玩游戏，则返回True，否则返回False。

squirrel_play(70, False) → True 

squirrel_play(95, False) → False 

squirrel_play(95, True) → True

### Code:

```python
def squirrel_play(temp, is_summer):
  if is_summer :
    if 60<=temp<=100:
      return True
    else:
      return False
  else:
    if 60<=temp<=90:
      return True
    else:
      return False
```

## [Logic-1](https://codingbat.com/python/Logic-1) > caught_speeding

You are driving a little too fast, and a police officer stops you. Write code to compute the result, encoded as an int value: 0=no ticket, 1=small ticket, 2=big ticket. If speed is 60 or less, the result is 0. If speed is between 61 and 80 inclusive, the result is 1. If speed is 81 or more, the result is 2. Unless it is your birthday -- on that day, your speed can be 5 higher in all cases. 

你开得太快了，警察拦住了你。编写代码来计算结果，编码为int值：0=无罚单，1=小票，2=大票。如果速度小于等于60，则结果为0。如果速度在61和80之间（包括61和80），则结果为1。如果速度为81或更高，则结果为2。除非是你的生日——在那一天，你的速度在所有情况下都可以高出5。

caught_speeding(60, False) → 0

caught_speeding(65, False) → 1 

caught_speeding(65, True) → 0

### Code:

```python
def caught_speeding(speed, is_birthday):
  if is_birthday:
    flag=speed-5
  else:
    flag=speed
    
  if flag<=60:
    return 0
  elif 61<=flag<=80:
    return 1
  else:
    return 2
```

## [Logic-1](https://codingbat.com/python/Logic-1) > sorta_sum

Given 2 ints, a and b, return their sum. However, sums in the range 10..19 inclusive, are forbidden, so in that case just return 20.

给定2个整数，a和b，返回它们的和。但是，10到19范围内的和是禁止的，所以在这种情况下只返回20。

sorta_sum(3, 4) → 7

sorta_sum(9, 4) → 20 

sorta_sum(10, 11) → 21

### Code:

```python
def sorta_sum(a, b):
  if 10<=(a+b)<=20:
    return 20
  else:
    return a+b
```

## [Logic-1](https://codingbat.com/python/Logic-1) > alarm_clock

Given a day of the week encoded as 0=Sun, 1=Mon, 2=Tue, ...6=Sat, and a boolean indicating if we are on vacation, return a string of the form "7:00" indicating when the alarm clock should ring. Weekdays, the alarm should be "7:00" and on the weekend it should be "10:00". Unless we are on vacation -- then on weekdays it should be "10:00" and weekends it should be "off". 

给定一周中编码为0=Sun，1=Mon，2=Tue，…6=Sat，以及一个表示我们是否在度假的布尔值，返回一个“7:00”格式的字符串，表示闹钟应该在什么时候响。工作日，警报应为“7:00”，周末应为“10:00”。除非我们在度假——那么在工作日应该是“10:00”，周末应该是“关闭”。

alarm_clock(1, False) → '7:00' 

alarm_clock(5, False) → '7:00' 

alarm_clock(0, False) → '10:00'

### Code:

```python
def alarm_clock(day, vacation):
  if not vacation:
    if 1<=day<=5:
      return "7:00"
    else:
      return "10:00"
  else:
    if 1<=day<=5:
      return "10:00"
    else:
      return "off"
```

##   [Logic-1](https://codingbat.com/python/Logic-1) > love6

The number 6 is a truly great number. Given two int values, a and b, return True if either one is 6. Or if their sum or difference is 6. Note: the function abs(num) computes the absolute value of a number.

数字6是一个非常好的数字。给定两个整型值a和b，如果其中一个是6，则返回True。如果它们的和或差是6。注意：函数abs（num）计算一个数字的绝对值。

love6(6, 4) → True
love6(4, 5) → False
love6(1, 5) → True

### Code:

```python
def love6(a, b):
  if a==6 or b==6 or a+b==6 or abs(a-b)==6:
    return True
  else:
    return False
```

## [Logic-1](https://codingbat.com/python/Logic-1) > in1to10

Given a number n, return True if n is in the range 1..10, inclusive. Unless outside_mode is True, in which case return True if the number is less or equal to 1, or greater or equal to 10. 



in1to10(5, False) → True 

in1to10(11, False) → False 

in1to10(11, True) → True

### Code:

```python
def in1to10(n, outside_mode):
  if (not outside_mode) and 1<=n<=10:
    return True
  elif outside_mode and (n<=1 or n>=10) :
    return True
  else:
    return False
```

## [Logic-1](https://codingbat.com/python/Logic-1) > near_ten

Given a non-negative number "num", return True if num is within 2 of a multiple of 10. Note: (a % b) is the remainder of dividing a by b, so (7 % 5) is 2. See also: [Introduction to Mod](https://codingbat.com/doc/practice/mod-introduction.html) 

near_ten(12) → True 

near_ten(17) → False 

near_ten(19) → True

### Code:

```python
def near_ten(num):
  if num%10<=2 or 10-num%10<=2:
    return True
  else:
    return False
```

## [Logic-2](https://codingbat.com/python/Logic-2) > make_bricks

We want to make a row of bricks that is **goal** inches long. We have a number of small bricks (1 inch each) and big bricks (5 inches each). Return True if it is possible to make the goal by choosing from the given bricks. This is a little harder than it looks and can be done without any loops. See also: [Introduction to MakeBricks](https://codingbat.com/doc/practice/makebricks-introduction.html) 

我们要砌一排目标长度的砖墙。我们有一些小砖块（每个1英寸）和大砖块（每个5英寸）。如果可以通过从给定的砖块中砌到目标长度，则返回True。这比看起来要难一点，而且不需要任何循环就可以完成。另请参见：MakeBricks简介

make_bricks(3, 1, 8) → True 

make_bricks(3, 1, 9) → False 

make_bricks(3, 2, 10) → True

### Code（已用上循环）:

```python
def make_bricks(small, big, goal):
  for i in range(big+1):
    if i*5<=goal and goal-i*5<=small:
      return True
  else:
    return False
```

## [Logic-2](https://codingbat.com/python/Logic-2) > lone_sum

Given 3 int values, a b c, return their sum. However, if one of the values is the same as another of the values, it does not count towards the sum. 

给定3个int值，a b c，返回它们的和。但是，如果其中一个值与另一个值相同，则相同的数不计入总和。

lone_sum(1, 2, 3) → 6
lone_sum(3, 2, 3) → 2
lone_sum(3, 3, 3) → 0

### Code:

```python
def lone_sum(a, b, c):
  if a==b==c:
    return 0
  elif a==b:
    return c
  elif a==c:
    return b
  elif b==c:
    return a
  else:
    return a+b+c
```

## [Logic-2](https://codingbat.com/python/Logic-2) > lucky_sum

Given 3 int values, a b c, return their sum. However, if one of the values is 13 then it does not count towards the sum and values to its right do not count. So for example, if b is 13, then both b and c do not count.

给定3个int值，a b c，返回它们的和。但是，如果其中一个值是13，则它不计入总和，其右侧的值也不计入。例如，如果b是13，那么b和c都不算数。

lucky_sum(1, 2, 3) → 6
lucky_sum(1, 2, 13) → 3
lucky_sum(1, 13, 3) → 1

### Code1:

```python
def lucky_sum(a, b, c):
  if a==13:
    return 0
  elif b==13:
    return a
  elif c==13:
    return a+b
  else:
    return a+b+c
```

### Code2:

```python
def lucky_sum(a, b, c):
  sum=0
  sum_list=[a,b,c]
  for each in sum_list:
    if each ==13:
      return sum
    else:
      sum+=each
  return sum
```

## [Logic-2](https://codingbat.com/python/Logic-2) > no_teen_sum

Given 3 int values, a b c, return their sum. However, if any of the values is a teen -- in the range 13..19 inclusive -- then that value counts as 0, except 15 and 16 do not count as a teens. Write a separate helper "def fix_teen(n):"that takes in an int value and returns that value fixed for the teen rule. In this way, you avoid repeating the teen code 3 times (i.e. "decomposition"). Define the helper below and at the same indent level as the main no_teen_sum().

给定3个int值，a b c，返回它们的和。但是，如果其中任何一个值是青少年——范围在13到19之间——那么这个值就计为0，除了15和16不算青少年。编写一个单独的helper“def fix_teen（n）：”，它接受一个int值并返回为teen规则固定的值。这样，你就可以避免重复青少年代码3次（即“分解”）。在下面定义与主no_teen_sum（）相同缩进级别的助手。

no_teen_sum(1, 2, 3) → 6
no_teen_sum(2, 13, 1) → 3
no_teen_sum(2, 1, 14) → 3

### Code:

```python
def fix_teen(n):
  if 13<=n<15 or 16<n<=19:
    return 0
  else:
    return n
    
def no_teen_sum(a, b, c):
  sum=0
  for n in (a,b,c):
    x=fix_teen(n)
    sum+=x
  return sum
```

## [Logic-2](https://codingbat.com/python/Logic-2) > round_sum

For this problem, we'll round an int value up to the next multiple of 10 if its rightmost digit is 5 or more, so 15 rounds up to 20. Alternately, round down to the previous multiple of 10 if its rightmost digit is less than 5, so 12 rounds down to 10. Given 3 ints, a b c, return the sum of their rounded values. To avoid code repetition, write a separate helper "def round10(num):" and call it 3 times. Write the helper entirely below and at the same indent level as round_sum().

对于这个问题，如果一个int值最(个位)是5或更多，我们将它舍入到下一个10的倍数，所以15向上舍入到20。如果前一个数字小于10，则交替向下舍入前10位。给定3个整数，a b c，返回它们的四舍五入值之和。为了避免代码重复，编写一个单独的助手（函数）“def round10（num）：”并调用它3次。将助手写在与round_sum（）完全相同的缩进级别下。

round_sum(16, 17, 18) → 60
round_sum(12, 13, 14) → 30
round_sum(6, 4, 4) → 10

### Code：

```python
def round10(num):
  if num%10>=5:
    return (num//10+1)*10	#// 为商取整
  else:
    return num//10*10
    
def round_sum(a, b, c):
  s=0
  for i in (a,b,c):
    r10=round10(i)
    s+=r10
  return s
```

##  [Logic-2](https://codingbat.com/python/Logic-2) > close_far

Given three ints, a b c, return True if one of b or c is "close" (differing from a by at most 1), while the other is "far", differing from both other values by 2 or more. Note: abs(num) computes the absolute value of a number.

给定三个整数，a b c，如果b或c中的一个是“close”（与a相差最多1），而另一个是“far”，则返回True，与其他两个值相差2或更多则不同（返回False )。注意：abs（num）计算数字的绝对值。

close_far(1, 2, 10) → True
close_far(1, 2, 3) → False
close_far(4, 1, 3) → True

### Code:

