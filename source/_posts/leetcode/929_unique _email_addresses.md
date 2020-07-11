---
title: leetcode第929题：唯一邮箱数量
tags:
	- leetcode

categories:
	- leetcode
	- leetcode_easy
---

###### leetcode第929题：唯一邮箱数量

给定一个字符串列表，每个字符串是一个邮箱。
其中@符号前的是本地名，后面的是域名。
在本地名中，忽略所有的"."字符，以及忽略第一个"+"后面的字符
返回唯一的邮箱数量。

```python
"""
IEvery email consists of a local name and a domain name, separated by the @ sign.

For example, in alice@leetcode.com, alice is the local name, and leetcode.com is the domain name.

Besides lowercase letters, these emails may contain '.'s or '+'s.

If you add periods ('.') between some characters in the local name part of an email address, mail sent there will be forwarded to the same address without dots in the local name.  For example, "alice.z@leetcode.com" and "alicez@leetcode.com" forward to the same email address.  (Note that this rule does not apply for domain names.)

If you add a plus ('+') in the local name, everything after the first plus sign will be ignored. This allows certain emails to be filtered, for example m.y+name@email.com will be forwarded to my@email.com.  (Again, this rule does not apply for domain names.)

It is possible to use both of these rules at the same time.

Given a list of emails, we send one email to each address in the list.  How many different addresses actually receive mails? 

Example 1:

Input: ["test.email+alex@leetcode.com","test.e.mail+bob.cathy@leetcode.com","testemail+david@lee.tcode.com"]
Output: 2
Explanation: "testemail@leetcode.com" and "testemail@lee.tcode.com" actually receive mails


基本思路：
  先区分域名和本地名，在对本地名进行"+"符号左右分割，再替换所有的.符号。
"""

class Solution:
    def numUniqueEmails(self, emails: List[str]) -> int:
        addresses = set()
        
        for email in emails:
            local, domain = email.split('@')
            local = local.split('+')[0]
            local = local.replace('.', '')
            addresses.add(local+domain)

        return len(addresses)

                
        
        

```
