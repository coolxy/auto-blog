---
layout: post
title:  "python练习园地（二）——string篇"
date:   2020-07-01 21:03:25
author: coolxy
categories: 
  - 教程技巧
  - python
tags: python
---

## python练习题园地（二）——String篇

## [String-1](https://codingbat.com/python/String-1) > hello_name

Given a string name, e.g. "Bob", return a greeting of the form "Hello Bob!". hello_name('Bob') → 'Hello Bob!' hello_name('Alice') → 'Hello Alice!' hello_name('X') → 'Hello X!'

Code:

```python
def hello_name(name):
  return 'Hello '+name+'!'
```

## [String-1](https://codingbat.com/python/String-1) > make_abba

Given two strings, a and b, return the result of putting them together in the order abba, e.g. "Hi" and "Bye" returns "HiByeByeHi". 

make_abba('Hi', 'Bye') → 'HiByeByeHi' 

make_abba('Yo', 'Alice') → 'YoAliceAliceYo' 

make_abba('What', 'Up') → 'WhatUpUpWhat'

```python
def make_abba(a, b):
  return a+b*2+a
```

## [String-1](https://codingbat.com/python/String-1) > make_tags
The web is built with HTML strings like "<i>Yay</i>" which draws Yay as italic text. In this example, the "i" tag makes <i> and </i> which surround the word "Yay". Given tag and word strings, create the HTML string with tags around the word, e.g. "<i>Yay</i>". 

make_tags('i', 'Yay') → '<i>Yay</i>' 

make_tags('i', 'Hello') → '<i>Hello</i>' 

make_tags('cite', 'Yay') → '<cite>Yay</cite>'

Code

```python
def make_tags(tag, word):
  return ('<%s>'+word+'</%s>')%(tag,tag)
```

## [String-1](https://codingbat.com/python/String-1) > make_out_word
Given an "out" string length 4, such as "<<>>", and a word, return a new string where the word is in the middle of the out string, e.g. "<<word>>". 

make_out_word('<<>>', 'Yay') → '<<Yay>>' 

make_out_word('<<>>', 'WooHoo') → '<<WooHoo>>' 

make_out_word('[[]]', 'word') → '[[word]]'

Code

```python
def make_out_word(out, word):
  return out[:2]+word+out[2:]
```

## [String-1](https://codingbat.com/python/String-1) > extra_end
Given a string, return a new string made of 3 copies of the last 2 chars of the original string. The string length will be at least 2. 

extra_end('Hello') → 'lololo' 

extra_end('ab') → 'ababab' 

extra_end('Hi') → 'HiHiHi'

Code:

```python
def extra_end(str):
  str_len=len(str)
  return str[str_len-2:]*3
```

## [String-1](https://codingbat.com/python/String-1) > first_two

Given a string, return the string made of its first two chars, so the String "Hello" yields "He". If the string is shorter than length 2, return whatever there is, so "X" yields "X", and the empty string "" yields the empty string "". 

first_two('Hello') → 'He' 

first_two('abcdefg') → 'ab' 

first_two('ab') → 'ab'

Code:

```python
def first_two(str):
  if len(str)<=2:
    return str
  else:
    return str[:2]
```

## [String-1](https://codingbat.com/python/String-1) > first_half
Given a string of even length, return the first half. So the string "WooHoo" yields "Woo". 

first_half('WooHoo') → 'Woo' 

first_half('HelloThere') → 'Hello' 

first_half('abcdef') → 'abc'

Code:

```python
def first_half(str):
  return str[:int(len(str)/2)]
```

## [String-1](https://codingbat.com/python/String-1) > without_end
Given a string, return a version without the first and last char, so "Hello" yields "ell". The string length will be at least 2. 

without_end('Hello') → 'ell' 

without_end('java') → 'av' 

without_end('coding') → 'odin'

Code:

```python
def without_end(str):
  return str[1:len(str)-1]
```

