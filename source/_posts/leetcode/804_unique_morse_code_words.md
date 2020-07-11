---
title: leetcode第804题：唯一的摩斯电码
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第804题：唯一的摩斯电码

给出小写字母对应的摩斯码，输入一个字符串列表，得到字符串列表对应的摩斯码，输出这个不重复的摩斯码的数量
	1. 其中字符串的列表最多有100个字符串
	2. 每个字符串有1-12个字符
	3. 所有字符都是小写字母


```python
"""
International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows: "a" maps to ".-", "b" maps to "-...", "c" maps to "-.-.", and so on.

For convenience, the full table for the 26 letters of the English alphabet is given below:

[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cba" can be written as "-.-..--...", (which is the concatenation "-.-." + "-..." + ".-"). We'll call such a concatenation, the transformation of a word.

Return the number of different transformations among all words we have.

Example:
Input: words = ["gin", "zen", "gig", "msg"]
Output: 2
Explanation: 
The transformation of each word is:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."

There are 2 different transformations, "--...-." and "--...--.".
Note:

The length of words will be at most 100.
Each words[i] will have length in range [1, 12].
words[i] will only consist of lowercase letters.

"""

class Solution:
	# 题目比较简单，不做解释
    def uniqueMorseRepresentations(self, words: List[str]) -> int:
        table = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
        result = set()
        
        for word in words:
            string = ''
            for char in word:
                string += table[ord(char)-97]
            
            result.add(string)
            
        return len(result)
                
        

```