---
title: 复用Session
toc: true
date: 2020-07-22 15:51:25
categories:
 - Java
 - Java网络编程
---
<meta name="referrer" content="no-referrer"/>

## 经典案例
### 1、登录复用
我们把 `OkHttpClient`  对象进行重构，不再定义为 `postContent()`  方法的变量。而是改为类变量： `private static final OkHttpClient okHttpClient` ，目的就是在整个类中，使用同一个 okHttpClient 执行 HTTP 请求，提升效率。重构在本节课就派上用场了。<br />分析执行两次请求的过程，实际上过程是类似的，区别是 `Request` 不同，所以，又做了一次重构，把真正执行的过程封装成一个方法： `doExcute`  ，被其它 `postContent()`  和 `getContent()`  方法调用。
```java
package com.youkeda.test.http;

import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import okhttp3.Cookie;
import okhttp3.CookieJar;
import okhttp3.FormBody;
import okhttp3.FormBody.Builder;
import okhttp3.HttpUrl;
import okhttp3.OkHttpClient;
import okhttp3.Request;

public class PageLoginer {

  // 用 CookieJar 实现 cookie 的存储，便于登录后请求其它 URL 可以复用
  // 在登录成功后返回Response对象时，会有拦截器链判断Response的Headers中是否有Cookie，若有则保存
  // 登录后请求其它URL过程中，会有拦截器链调用loadForRequest()方法来获得内存中的Cookie
  private static final OkHttpClient okHttpClient = new OkHttpClient.Builder()
      .cookieJar(new CookieJar() {
        private final HashMap<String, List<Cookie>> cookieStore = new HashMap<>();

        @Override
        public void saveFromResponse(HttpUrl url, List<Cookie> cookies) {
          cookieStore.put("mtime.com", cookies);
          //System.out.println("[saveFromResponse]url.host()=" + url.host());
        }

        @Override
        public List<Cookie> loadForRequest(HttpUrl url) {
          //System.out.println("[loadForRequest]url.host()=" + url.host());
          List<Cookie> cookies = cookieStore.get("mtime.com");
          return cookies != null ? cookies : new ArrayList<>();
        }
      })
      .build();

  /**
   * 向指定的 URL 提交数据，并返回提交后的结果
   */
  public String postContent(String url, Map<String, String> formData) {
    //post方式提交的数据
    Builder builder = new FormBody.Builder();
    // 放入表单数据
    for (String key : formData.keySet()) {
      builder.add(key, formData.get(key));
    }
    // 构建 FormBody 对象
    FormBody formBody = builder.build();
    // 指定 post 方式提交FormBody
    Request request = new Request.Builder()
        .url(url)
        .post(formBody)
        .addHeader("User-Agent",
            "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36")
        .addHeader("Referer",
            "https://passport.mtime.com/member/signin/?redirectUrl=http%3A%2F%2Fwww.mtime.com%2F")
        .addHeader("Host", "passport.mtime.com")
        .build();

    return doExcute(request);
  }

  /**
   * 根据输入的url，读取页面内容并返回
   */
  public String getContent(String url) {
    // 定义一个request
    Request request = new Request.Builder()
        .url(url)
        .addHeader("User-Agent",
            "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36")
        .addHeader("Host", "my.mtime.com")
        .build();

    return doExcute(request);
  }

  private String doExcute(Request request) {
    // 返回结果字符串
    String result = null;
    try {
      result = okHttpClient.newCall(request).execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + request.url() + " error . ");
      e.printStackTrace();
    }

    return result;
  }

  public static void main(String[] args) {
    PageLoginer asker = new PageLoginer();

    // 完成登录
    String url = "https://passport.mtime.com/member/signinLogin";
    // 登录表单数据
    Map<String, String> formData = new HashMap();
    formData.put("loginEmailText", "15195960267");
    formData.put("loginPasswordText", "6b22c167fc289650b968021ba3cdee70");
    formData.put("isvcode", "true");
    formData.put("isAutoSign", "false");
    String content = asker.postContent(url, formData);
    System.out.println("login result:");
    System.out.println(content);

    // 请求我的订单
    String myOrderUrl = "http://my.mtime.com/account/";
    String myOrderContent = asker.getContent(myOrderUrl);
    System.out.println("orderList result:");
    System.out.println(myOrderContent);
    
  }
}

```
