---
title: leetcode第771题：珠宝和石头
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第771题：珠宝和石头
	给定宝石的种类(字母)和你拥有的石头(字母)，判断你拥有的石头中是否有珠宝，返回你拥有的珠宝的数量。
	宝石的种类的是唯一的，并且是大小写敏感的，也就是"A"与"a"不同

```python

"""
You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

Example 1:

Input: J = "aA", S = "aAAbbbb"
Output: 3
Example 2:

Input: J = "z", S = "ZZ"
Output: 0
Note:

S and J will consist of letters and have length at most 50.
The characters in J are distinct.

"""

# 直接使用leetcode代码，没有遵循PEP8
class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
    	# 时间复杂度为O(N+M), 空间复杂度为O(N)
        stones = dict()
        jewels_count = 0
        
        for s in S:
            if s not in stones:
                stones[s] = 0
            stones[s] += 1
            
        for j in J:
            if j in stones:
                jewels_count += stones[j]
        
        return jewels_count


    def numJewelsInStones(self, J: str, S: str) -> int:
    	# 时间复杂度为O(N+M), 空间复杂度为O(N)
    	# 其他人的答案，自认为比较合适简洁
        setJ = set(J) # O(n)操作
        return sum(s in setJ for s in S)

```