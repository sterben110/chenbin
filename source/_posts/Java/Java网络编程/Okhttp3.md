---
title: Okhttp3
toc: true
date: 2020-07-23 15:28:16
categories:
 - Java
 - Java网络编程
---
<meta name="referrer" content="no-referrer"/>

<strong>用途</strong>
> 1. PUT，DELETE，POST，GET等请求
> 1. 文件的上传下载
> 1. 加载图片(内部会图片大小自动压缩)
> 1. 支持请求回调，直接返回对象、对象集合
> 1. 支持session的保持

## 1、依赖
```xml
<!-- https://mvnrepository.com/artifact/com.squareup.okhttp3/okhttp -->
<dependency>
 <groupId>com.squareup.okhttp3</groupId>
 <artifactId>okhttp</artifactId>
 <version>4.1.0</version>
</dependency>
```


## 2、使用
### 2.1、get请求
```java
  /**
   * 根据输入的url，读取页面内容并返回
   */
  public String getContent(String url) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();
    // 定义一个request
    Request request = new Request.Builder().url(url).build();
    // 使用client去请求
    Call call = okHttpClient.newCall(request);
    // 返回结果字符串
    String result = null;
    try {
      // 获得返回结果
      result = call.execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }
```

### 2.2、post请求
#### 2.2.1、post 表单数据
```java
public String postContent(String url, Map<String, String> formData) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();

    //post方式提交的数据
    Builder builder = new FormBody.Builder();
    // 放入表单数据
    for(String key : formData.keySet()){
      builder.add(key,formData.get(key));
    }
    // 构建 FormBody 对象
    FormBody formBody = builder.build();
    // 指定 post 方式提交FormBody
    Request request = new Request.Builder().url(url).post(formBody).build();

    // 使用client去请求
    Call call = okHttpClient.newCall(request);
    // 返回结果字符串
    String result = null;
    try {
      // 获得返回结果
      result = call.execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }
```

#### 2.2.2、post JSON数据
```java
  // 定义提交数据的类型
  public static final MediaType JSON_TYPE = MediaType.parse("application/json; charset=utf-8");

  /**
   * 向指定的 url 提交数据，以 json 的方式
   */
  public String postContent(String url, Map<String, String> datas) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();

    // 数据对象转换成 json 格式字符串
    String param = JSON.toJSONString(datas);
    //post方式提交的数据
    RequestBody requestBody = RequestBody.create(JSON_TYPE, param);
    Request request = new Request.Builder().url(url).post(requestBody).build();

    // 使用client去请求
    Call call = okHttpClient.newCall(request);
    // 返回结果字符串
    String result = null;
    try {
      // 获得返回结果
      result = call.execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }
```