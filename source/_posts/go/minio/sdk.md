---
title: MINIO GoLang SDK
tags:
	- go
	- minio
categories:
	- go
	- minio
---

## golang minio sdk 

本篇主要是GoLang SDK基本使用 

##### 安装

    go get -u github.com/minio/minio-go

##### 连接minio

```go

import (
    "github.com/minio/minio-go"
    "log"
)

const (
    minioHost = "127.0.0.1:9000"
    minioAccessKeyID = "admin"
    minioSecretAccessKey = "123456"
)

func MinioGetClient() *minio.Client, err {
        // 初使化 minio client对象。
    minioClient, err := minio.New(
        minioHost, minioAccessKeyID, minioSecretAccessKey, false)
    if err != nil {
        log.Fatalln(err)

    return minioClient, err
}

```
##### 创建bucket
```go

func MinioMakeBucket(bucketName string, readonly bool) (bool, error) {
	// 创建存储桶。
	cli := MinioGetClient() //这个函数来自上面定义

    // 先判断是否桶存在
    exists, err := cli.BucketExists(bucketName)
    
    if err != nil {
        log.Fatalln(err)
        return false, err
    }

    if exists {
        log.Printf("Bucket %s has already created\n", bucketName)
        return true, nil
    }

    err = minioClient.MakeBucket(bucketName, "cn-north-1")
    if err ！= nil {
        log.Printf("Bucket %s created failed\n", bucketName)
        return false, err
    } 
    
    return true, nil
}
```

##### 将bucket设置为全局可读
```go
func MinioMakeBucketAllReadOnly(bucketName string) error {   

    cli := MinioGetClient()

    readOnlyPolicy := `{"Version": "2012-10-17","Statement": [{"Action": ["s3:GetObject"],"Effect": "Allow","Principal": {"AWS": ["*"]},"Resource": ["arn:aws:s3:::`
    readOnlyPolicy += bucketName
    readOnlyPolicy += `/*"],"Sid": ""}]}`

    err := minioClient.SetBucketPolicy(bucketName, readOnlyPolicy)
    if err != nil {
        log.Println(err)
    }
    return err
}
```


##### 上传图片

```go

func MinioPutObject(buckName string, filename string, reader io.Reader) error {
	
    _, err = MinioGetClient().PutObject(buckName, filename, reader, reader.Size(), minio.PutObjectOptions{ContentType: "application/octet-stream"})
    return err
}
```
很多时候我们是直接接受到字节流，然后把字节流传输到minio中，先把数据流转换成io流

```go
import (
    "bytes"
    "io"
)
func byte2Reader(b []byte) io.Reader {
    return bytes.NewReader(b)
}
```