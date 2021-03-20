---
layout: post
title:  "python练习园地（一）——Warmup篇"
date:   2020-06-21 22:03:25
author: coolxy
categories: 
  - 教程技巧
  - python
tags: python
---
## python练习题园地（一）——Warmup篇
最近找到一个网站：<https://codingbat.com/python>，这里是python和java初学者的园地，在这里你可以充分的发挥你在程序学习上的逻辑推理能力。一关一关的过，做你没做过或是曾做过后练习题，在学习的同时还可以熟悉一下英文，大多数都可以看懂。
## Warmup-1:
### Warmup-1 > sleep_in：
The parameter weekday is True if it is a weekday, and the parameter vacation is True if we are on vacation. We sleep in if it is not a weekday or we're on vacation. Return True if we sleep in.  
sleep_in(False, False) → True  
sleep_in(True, False) → False  
sleep_in(False, True) → True  

```python
def sleep_in(weekday, vacation):
  if not weekday and not vacation:
    return True
  elif weekday and not vacation:
    return False
  elif not weekday and vacation:
    return True
  else:
    return True
```
### Warmup-1 > monkey_trouble
We have two monkeys, a and b, and the parameters a_smile and b_smile indicate if each is smiling. We are in trouble if they are both smiling or if neither of them is smiling. Return True if we are in trouble.  
monkey_trouble(True, True) → True  
monkey_trouble(False, False) → True  
monkey_trouble(True, False) → False  
```python
def monkey_trouble(a_smile, b_smile):
  if a_smile and b_smile:
    return True
  elif not a_smile and not b_smile:
    return True
  else:
    return False
```
### Warmup-1 > sum_double
Given two int values, return their sum. Unless the two values are the same, then return double their sum.  
sum_double(1, 2) → 3  
sum_double(3, 2) → 5  
sum_double(2, 2) → 8  
```python
def sum_double(a, b):
  if a!=b:
    return a+b
  else:
    return (a+b)*2
```
### Warmup-1 > diff21
Given an int n, return the absolute difference between n and 21, except return double the absolute difference if n is over 21.  
diff21(19) → 2  
diff21(10) → 11  
diff21(21) → 0  
```python
def diff21(n):
  if n<=21:
    return 21-n
  else:
    return (n-21)*2
```
### Warmup-1 > parrot_trouble
We have a loud talking parrot. The "hour" parameter is the current hour time in the range 0..23. We are in trouble if the parrot is talking and the hour is before 7 or after 20. Return True if we are in trouble.  
parrot_trouble(True, 6) → True  
parrot_trouble(True, 7) → False  
parrot_trouble(False, 6) → False  
```python
def parrot_trouble(talking, hour):
  if talking and (hour<7 or hour>20):
    return True
  else:
    return False
```
###  Warmup-1 > makes10
Given 2 ints, a and b, return True if one if them is 10 or if their sum is 10.  
makes10(9, 10) → True  
makes10(9, 9) → False  
makes10(1, 9) → True  
```python
def makes10(a, b):
  if a==10 or b==10 or a+b==10:
    return True
  else:
    return False
```
简洁版（官方版），仔细思量：
```python
def makes10(a, b):
  return (a == 10 or b == 10 or a+b == 10)
```
### Warmup-1 > near_hundred
Given an int n, return True if it is within 10 of 100 or 200. Note: abs(num) computes the absolute value of a number.  
near_hundred(93) → True  
near_hundred(90) → True  
near_hundred(89) → False  
```python
def near_hundred(n):
  if abs(100-n)<=10 or abs(200-n)<=10 :
    return True
  else:
    return False
```
官方版：
```python
def near_hundred(n):
  return ((abs(100 - n) <= 10) or (abs(200 - n) <= 10))
```
### Warmup-1 > pos_neg
Given 2 int values, return True if one is negative(负数) and one is positive(正数）. Except if the parameter "negative" is True, then return True only if both are negative.  
pos_neg(1, -1, False) → True  
pos_neg(-1, 1, False) → True   
pos_neg(-4, -5, True) → True
```python
def pos_neg(a, b, negative):
  if  ((a<0 and b>0) or(a>0 and b<0)) and not negative:
    return True
  elif negative and (a<0 and b<0) :
    return True 
  else:
    return False
```
官方版：
```python
def pos_neg(a, b, negative):
  if negative:
    return (a < 0 and b < 0)
  else:
    return ((a < 0 and b > 0) or (a > 0 and b < 0))
```
### Warmup-1 > not_string
Given a string, return a new string where "not " has been added to the front. However, if the string already begins with "not", return the string unchanged.  (给定一个字符串，返回一个新字符串，将“not ”添加到字符串开头。但是，如果字符串已经以“not”开头，则不加更改地返回字符串。)
not_string('candy') → 'not candy'  
not_string('x') → 'not x'  
not_string('not bad') → 'not bad'  
```python
def not_string(str):
  if 'not' in str[0:3]:
    return str
  else:
    return "not "+str
```
官方版：
```python
def not_string(str):
  if len(str) >= 3 and str[:3] == "not":
    return str
  return "not " + str
  # str[:3] goes from the start of the string up to but not
  # including index 3
```
### Warmup-1 > missing_char
Given a non-empty string and an int n, return a new string where the char at index n has been removed. The value of n will be a valid index of a char in the original string (i.e. n will be in the range 0..len(str)-1 inclusive).  
missing_char('kitten', 1) → 'ktten'  
missing_char('kitten', 0) → 'itten'  
missing_char('kitten', 4) → 'kittn'  
```python
def missing_char(str, n):
  return str[:n]+str[n+1:]
```
官方版：
```python
def missing_char(str, n):
  front = str[:n]   # up to but not including n
  back = str[n+1:]  # n+1 through end of string
  return front + back
```
### Warmup-1 > front_back
Given a string, return a new string where the first and last chars have been exchanged.  (返回首尾字符交换的字符串）
front_back('code') → 'eodc'  
front_back('a') → 'a'  
front_back('ab') → 'ba'  
以下代码本机测试通过(考虑字符串只有1，或0时）：
```python
def front_back(str):
  if len(str)<=1:
    return str
  else:
    l=len(str)
    first=str[0]
    last=str[l-1]
    return last+str[1:(l-1)]+first
```
官方版：
```python
def front_back(str):
  if len(str) <= 1:
    return str
    mid = str[1:len(str)-1]  # can be written as str[1:-1]
    # last + mid + first
  return str[len(str)-1] + mid + str[0]
```
### Warmup-1 > front3
Given a string, we'll say that the front is the first 3 chars of the string. If the string length is less than 3, the front is whatever is there. Return a new string which is 3 copies of the front.  
front3('Java') → 'JavJavJav'  
front3('Chocolate') → 'ChoChoCho'  
front3('abc') → 'abcabcabc'  
```python
def front3(str):
  if len(str)<3:
    return str*3
  else:
    return str[:3]*3
```
官方代码：
```python
def front3(str):
  # Figure the end of the front
  front_end = 3
  if len(str) < front_end:
    front_end = len(str)
  front = str[:front_end]
  return front + front + front 
  
  # Could omit the if logic, and write simply front = str[:3]
  # since the slice is silent about out-of-bounds conditions.
```
## Warmup-2
### Warmup-2 > string_times
Given a string and a non-negative int n, return a larger string that is n copies of the original string.  (给一个字符串和非负整数，返回整数倍的字符串）
string_times('Hi', 2) → 'HiHi'  
string_times('Hi', 3) → 'HiHiHi'  
string_times('Hi', 1) → 'Hi'  
```python
def string_times(str, n):
  return str*n
```
官方代码：
```python
def string_times(str, n):
  result = ""
  for i in range(n):  # range(n) is [0, 1, 2, .... n-1]
    result = result + str  # could use += here
  return result
```
### Warmup-2 > front_times
Given a string and a non-negative int n, we'll say that the front of the string is the first 3 chars, or whatever is there if the string is less than length 3. Return n copies of the front;（返回字符串的前3个字符的N个副本，小于3则返回3个）  
front_times('Chocolate', 2) → 'ChoCho'  
front_times('Chocolate', 3) → 'ChoChoCho'  
front_times('Abc', 3) → 'AbcAbcAbc'  
```python
def front_times(str, n):
  if len(str)<3:
    return str*n
  else:
    return str[:3]*n
```
官方代码：
```python
def front_times(str, n):
  front_len = 3
  if front_len > len(str):
    front_len = len(str)
  front = str[:front_len]
  
  result = ""
  for i in range(n):
    result = result + front
  return result
```
### Warmup-2 > string_bits
Given a string, return a new string made of every other char starting with the first, so "Hello" yields "Hlo".  
string_bits('Hello') → 'Hlo'  
string_bits('Hi') → 'H'  
string_bits('Heeololeo') → 'Hello'  
```python
def string_bits(str):
  result=''
  if len(str)<=1: #这两句多于了，有i%2==0足够表达
    result=str
  else:
    for i in range(len(str)):
      if i%2==0:
        result=result+str[i]
  return result
```
官方代码：
```python
def string_bits(str):
  result = ""
  # Many ways to do this. This uses the standard loop of i on every char,
  # and inside the loop skips the odd index values.
  for i in range(len(str)):
    if i % 2 == 0:
      result = result + str[i]
  return result
```
### Warmup-2 > string_splosion
Given a non-empty string like "Code" return a string like "CCoCodCode".  
string_splosion('Code') → 'CCoCodCode'  
string_splosion('abc') → 'aababc'  
string_splosion('ab') → 'aab'  
```python
def string_splosion(str):
  result=''
  for i in range(len(str)):
    if i==0:			#这三句多余了，有str[:i+1]就足以包含，参考官方代码
      result=result+str[i]
    else:
      result=result+str[:i+1]
  return result
```
官方代码：
```python
def string_splosion(str):
  result = ""
  # On each iteration, add the substring of the chars 0..i
  for i in range(len(str)):
    result = result + str[:i+1]
  return result
```
### Warmup-2 > last2
Given a string, return the count of the number of times that a substring length 2 appears in the string and also as the last 2 chars of the string, so "hixxxhi" yields 1 (we won't count the end substring).  (返回字符串最后两个字符出现的次数，不计最后出现这一次）
last2('hixxhi') → 1  
last2('xaxxaxaxx') → 1  
last2('axxxaaxx') → 2  
```pthon
def last2(str):
  count=0
  str_len=len(str)
  last=str[str_len-2:str_len]
  for i in range(str_len):
    if str[i:i+2]==last and i<str_len-2:
      count+=1

  return count
```
官方代码：
```python
def last2(str):
  # Screen out too-short string case.
  if len(str) < 2:
    return 0
  
  # last 2 chars, can be written as str[-2:]
  last2 = str[len(str)-2:]
  count = 0
  
  # Check each substring length 2 starting at i
  for i in range(len(str)-2):
    sub = str[i:i+2]
    if sub == last2:
      count = count + 1

  return count
```
### Warmup-2 > array_count9
Given an array of ints, return the number of 9's in the array.（返回整数数组中9出现的次数）
array_count9([1, 2, 9]) → 1
array_count9([1, 9, 9]) → 2
array_count9([1, 9, 9, 3, 9]) → 3
```python
def array_count9(nums):
  count=0
  for each in nums:
    if each==9:
      count+=1
  return count
```
官方代码一致，唯变量不同：
### Warmup-2 > array_front9
Given an array of ints, return True if one of the first 4 elements in the array is a 9. The array length may be less than 4.  (返回整数数组中前4位数中出现9的布尔值）
array_front9([1, 2, 9, 3, 4]) → True  
array_front9([1, 2, 3, 4, 9]) → False  
array_front9([1, 2, 3, 4, 5]) → False  
```python
def array_front9(nums):
  return (9 in nums[:4])
```
官方代码：
```python
def array_front9(nums):
  # First figure the end for the loop
  end = len(nums)
  if end > 4:
    end = 4
  
  for i in range(end):  # loop over index [0, 1, 2, 3]
    if nums[i] == 9:
      return True
  return False
```
### Warmup-2 > array123
Given an array of ints, return True if the sequence of numbers 1, 2, 3 appears in the array somewhere.  
array123([1, 1, 2, 3, 1]) → True  
array123([1, 1, 2, 4, 1]) → False  
array123([1, 1, 2, 1, 2, 3]) → True  
```python
def array123(nums):
  if len(nums)==0:
    return False
  for i in range(len(nums)):
    if i+2<len(nums):
      if nums[i]==1 and nums[i+1]==2 and nums[i+2]==3:
        return True
    else:
        return False
```
官方代码：
```python
def array123(nums):
  # Note: iterate with length-2, so can use i+1 and i+2 in the loop
  for i in range(len(nums)-2):
    if nums[i]==1 and nums[i+1]==2 and nums[i+2]==3:
      return True
  return False
```
### Warmup-2 > string_match
Given 2 strings, a and b, return the number of the positions where they contain the same length 2 substring. So "xxcaazz" and "xxbaaz" yields 3, since the "xx", "aa", and "az" substrings appear in the same place in both strings.  （返回两个字符串中在相同位置出现相同两个字符的次数）
string_match('xxcaazz', 'xxbaaz') → 3  
string_match('abc', 'abc') → 2  
string_match('abc', 'axc') → 0  
```python
def string_match(a, b):
  if len(a)<=len(b):	#以最短的字串长度为主
    len_s=len(a)
  else:
    len_s=len(b)
  count=0
  for i in range(len_s-1):
    if a[i]+a[i+1] == b[i]+b[i+1]:
      count+=1
  return count
```
官方代码：
```python
def string_match(a, b):
  # Figure which string is shorter.
  shorter = min(len(a), len(b))
  count = 0
  
  # Loop i over every substring starting spot.
  # Use length-1 here, so can use char str[i+1] in the loop
  for i in range(shorter-1):
    a_sub = a[i:i+2]
    b_sub = b[i:i+2]
    if a_sub == b_sub:
      count = count + 1

  return count
```