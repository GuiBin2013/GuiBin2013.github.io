
---
title: leetcode第832题：翻转图片
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第832题：翻转图片

给定一个二维数组，先将这个数组进行垂直翻转，再将每个元素取反

```python

"""
Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].

Example 1:

Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]



解题思路：
    从后向前遍历，每个元素进行与1进行异或，使用嵌套列表生成式。
"""


class Solution:
    def flipAndInvertImage(self, A):
        return [[1 ^ i for i in l[::-1]] for l in A]
```