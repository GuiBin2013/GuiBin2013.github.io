---
title: leetcode第905题：奇偶排序
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第905题：给数组进行奇偶排序

输入一个数组
输出一个数组，偶数在前，奇数在后


```python
"""
Given an array A of non-negative integers, return an array consisting of all the even elements of A, followed by all the odd elements of A.
You may return any answer array that satisfies this condition.

Example 1:

Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.

解题思路：
1. 直接排序，key使用取2的余数
2. 维持2个指针，p1从前向后，p2从后向前，当p1指向奇数，p2指向偶数，然后交换数值，直到p1 > p2

"""

class Solution(object):
    def sortArrayByParity(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        # 使用内建方法
        # return list(sorted(A, key=lambda x: x%2))

        res = A[:]
        start = 0  
        end = len(res) - 1
        while start < end:
            if res[start] % 2 == 1 and res[end] % 2 == 0:
                res[start], res[end] = res[end], res[start]
                start += 1
                end -= 1
            elif res[start] % 2 == 0:
                start += 1
            else:
                end -= 1
        return res


if __name__ == '__main__':
    s = Solution()
    exs = [([3, 1, 2, 4],), ([1, 1, 1, 1],), ([],), ([1, 2, 3, 4, 5, 6],), ([2, 2, 2, 2, 1, 1],), ([1, 3, 3, 4, 2, 2],)]

    for ex in exs:
        print(s.sortArrayByParity(*ex))

        

```
