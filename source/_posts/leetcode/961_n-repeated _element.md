---
title: leetcode第961题：找出重复出现n个的元素
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第961题：找出在包含2n的元素的数组中重复出现n个的元素

输入一个列表，这个列表包含2n个元素，其中有n个元素是重复的，其他元素都是只会出现一次，输出这个重复元素的值


```python
"""
In a array A of size 2N, there are N+1 unique elements, and exactly one of these elements is repeated N times.

Return the element repeated N times.

 

Example 1:

Input: [1,2,3,3]
Output: 3
Example 2:

Input: [2,1,2,5,3,2]
Output: 2

Note:

	4 <= A.length <= 10000
	0 <= A[i] < 10000
	A.length is even

基本思路：
	既然是2n个元素并且有n个元素是重复的，那么重复元素的分布有2种情况：
	1. 重复元素至少会连续出现(相邻)一次
	2. 如果1不成立，那么说明重复元素是间隔出现
	
	特殊考虑： 当n=2时，也就是重复元素只出现2次，那么可能存在上述不存在的情况：
	第1个元素和第4个元素重复而已： 2，1，3，2

	遍历整个列表，如果出现相邻(当前元素等于他前面那个元素)或者间隔(当前元素位置i等于i-2位置的元素的值)，那么当前元素就是重复元素
	如果遍历结束没找到，那么说明时特殊情况，即4个元素的情况，返回第一个元素即可

"""

class Solution:
    def repeatedNTimes(self, A: List[int]) -> int:
        for i in range(2, len(A)):
            if A[i] == A[i-2] or A[i-1] == A[i]:
                return A[i]
        
        return A[0]
        

```
