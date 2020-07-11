---
title: leetcode第709题：小写化字符串
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第709题：小写化字符串

给定一个字符串，输出字符串的小写。

```python
"""
Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.

 

Example 1:

Input: "Hello"
Output: "hello"

"""

class Solution:
	# 题目太简单就不做解释了
	# 内建字符串方法lower()
	# 或者使用ord, chr的aciss码转换
	# 或者建立dict的映射
    def toLowerCase(self, str: str) -> str:
        return str.lower()
        

```
