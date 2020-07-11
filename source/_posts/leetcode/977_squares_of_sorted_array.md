---
title: leetcode第977题：有序列表的平方值
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第977题：小写化字符串

给定一个非递减的有序列表，返回他们的平方值的列表，并且这个列表进行(伪)递增排序。

```python

"""
Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.

Example 1:
Input: [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Example 2:
Input: [-7,-3,2,3,11]
Output: [4,9,9,49,121]
 
Note:
1 <= A.length <= 10000
-10000 <= A[i] <= 10000
A is sorted in non-decreasing order.

解题思路：
    已知道列表的大小，先初始化一个列表，大小和输入的列表一样大。
    左右指针：
       左指针从左向右，右指针从右到左
       如果右指针的绝对值小于左指针，那么将左指针的平方放入刚刚创建的列表，位置在r-l, 反之亦然。
       一直迭代到r<=l；
"""

class Solution:
    result = [0] * len(A)
    left = 0
    right = len(A) - 1

    while left <= right:
    	if abs(A[left]) < abs(A[right]):
    	    result[right - left] = A[right] * A[right]
    	    right -= 1
    	else:
            result[right - left] = A[left] * A[left]
            left += 1
    return result
        

```
