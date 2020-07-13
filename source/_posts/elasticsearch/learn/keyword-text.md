---
title: elasticsearch keyword && text
tags: 
	- elasticsearch
categories:
	- elasticsearch
---
elasticsearch的字符串类型分为keyword和text。

# text
    1. 先分词再索引
    2. 支持模糊、精确查询
    3. 不能用于排序，很少用于聚合

# keyword
    1. 不进行分词，直接索引
    2. 支持模糊、精确查询(模糊查询？)
    3. 支持排序、聚合。

# 使用场景
看看官网的描述。

    If you need to index structured content such as email addresses, hostnames, status codes, or tags, it is likely that you should rather use a keyword field.

    If you need to index full text content such as email bodies or product descriptions, it is likely that you should rather use a text field.

- keyword适用于一些精确查询的场景，例如邮箱地址、主机名、状态码之类的。
- text适用于一些模糊查询的场景，例如搜索邮箱的内容等。

# 即是keyword又是text
elasticsearch默认生成的mapping，针对字符串，如下：

```json
# GET index/_mapping
# 截取一部分
"artist": {
    "type": "text",
    "fields": {
        "keyword": {
            "type": "keyword",
            "ignore_above": 256
        }
    }
}
```
- 如果想想用分词功能，使用**artist**字段，即text.
- 如果想使用不分词的功能，使用**artist.keyword**字段。


