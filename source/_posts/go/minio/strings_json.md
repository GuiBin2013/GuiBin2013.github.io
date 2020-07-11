---
title: go 字符串拼接
tags:
	- go
	- 字符串
categories:
	- go
    - go基础
---

## go 字符串拼接

### 常见方式

- 字符串add操作：+
- fmt.Sprintf
- bytes.Buffer
- strings.Builder

### 四种方式性能测试

```go
func BenchmarkStringAdd(b *testing.B)  {
    b.ResetTimer()
    for i:=0;i<b.N;i++{
        var s string
        for j:=0;j<n;j++ {
            s += strconv.Itoa(j)
        }
    }
    b.StopTimer()
}

func BenchmarkStringBuilder(b *testing.B)  {
    b.ResetTimer()
    for i:=0;i<b.N;i++{
        var s strings.Builder
        for j:=0;j<n;j++ {
            s.WriteString(strconv.Itoa(j))
        }
    }
    b.StopTimer()
}

func BenchmarkStringByte(b *testing.B)  {
    b.ResetTimer()
    for i:=0;i<b.N;i++{
        var s bytes.Buffer
        for j:=0;j<n;j++ {
            s.WriteString(strconv.Itoa(j))
        }
    }
    b.StopTimer()
}

func BenchmarkStringFmt(b *testing.B)  {
    b.ResetTimer()
    for i:=0;i<b.N;i++{
        var s string
        for j:=0;j<n;j++ {
            s += fmt.Sprintf("%s%s", s, strconv.Itoa(j))
        }
    }
    b.StopTimer()
}
```

```
 go test -bench=.
// 输出结果
BenchmarkStringAdd-4             5000000               360 ns/op
BenchmarkStringBuilder-4        10000000               141 ns/op
BenchmarkStringByte-4           10000000               162 ns/op
BenchmarkStringFmt-4              500000              2456 ns/op
PASS

```

### 简要分析

由于字符串是一个不可变对象，使用+号以及fmt方式，会造成大量的内存拷贝，尽可能的使用Buffer或者builder的方式去连接字符串。
