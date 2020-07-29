---
title: Java网络编程问题与解决方案
toc: true
date: 2020-07-21 14:05:15
categories:
 - Java
 - Java网络编程
---
<meta name="referrer" content="no-referrer"/>

## 1、User-Agent 解决请求 HTTP 失败
不一定任何请求都能成功，例如我们在浏览器中输入 `IP`  地址详情信息查询的 `API`  ：
```
http://ip.taobao.com/service/getIpInfo.php?ip=117.89.35.58&format=json
```
该 `API` 在浏览器中是可以看到结果的，但是下述 `Java` 程序调用却不行：
```java
  public String getContent(String url) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();
    // 定义一个request
    Request request = new Request.Builder().url(url).build();
    // 返回结果字符串
    String result = null;
    try {
      // 执行请求
      Response response = okHttpClient.newCall(request).execute();
      // 获取响应内容
      result = response.body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }
```
这是因为像 `taobao.com`  这样的大型网站，处于安全等各种因素考虑，会对请求进行比较严格的校验，其中一个重要的校验，是判断请求是否真的来自于一个真实的浏览器。若不是来自浏览器，例如 `Java`  程序请求， `API`  服务器认为不是真实的浏览器访问，就直接拒绝掉了。<br />
<font color=red>**解决方法：**</font><br />
判断请求是否真的来自于一个真实的浏览器，需要从 `HTTP`  消息头（ `Headers` ）中取得 `User-Agent`  信息后，才能判断。 <br />
`User-Agent`  是存放在 `Headers`  中的一种数据信息。作用是，在指定 `URL`  发送请求的时候，告诉服务端当前用户的浏览器类型、版本，甚至操作系统、CPU等非隐私的技术信息。服务器从 `Headers`  中的 `User-Agent`  信息获取到浏览器类型、版本等数据后，就认为是一个浏览器请求的环境了，就会给出响应。<br />
<font color=red>**模拟一个 `win7+chrome` 环境：**</font>
```
Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/14.0.835.163 Safari/535.1
```
## 2、Referer解决“图片防盗链”
`https://ham.youkeda.com/course/j14/3/1/0` 页面中的下述 `img` 元素图片无法正常显示
```html
<img src="https://cdn.nlark.com/yuque/0/2019/
          png/93870/1571386626984-2462f7f9-d397-4e50-91e4-e4b688dd3410.png
          ?_t=41516115" 
     alt="此处应有图片">
```
但拷贝图片网址贴到浏览器地址栏，是可以访问的。<br />因为在`https://ham.youkeda.com/course/j14/3/1/0`页面下，浏览器在请求网页中的图片（或其它任何文件）时，会<font color=red>**自动**</font>在  `HTTP`  消息头 `Headers`  中，加一个 `Referer`  信息，表示<font color=red>**请求的来源**</font>。<br />即浏览器<font color=red>**自动**</font>告诉图片服务器，从当前 `youkeda.com`  请求此图片，这时图片服务器拒绝了访问，因为图片服务器的规则是不允许其它网站（非 `nlark.com` ）访问图片。<br /><font color=red>**解决方法：**</font><br />把 `Referer`  信息设置为图片原始使用的网站即可。

```java
  public String getContent(String url) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();
    // 定义一个request
    Request request = new Request.Builder()
      .url(url)
      .addHeader("User-Agent", "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/14.0.835.163 Safari/535.1")
      .addHeader("Referer", "http://sug.qianqian.com/")
      .addHeader("Host", "sug.qianqian.com")
      .build();
    // 返回结果字符串
    String result = null;
    try {
      // 执行请求
      Response response = okHttpClient.newCall(request).execute();
      // 获取响应内容
      result = response.body().string();
    } catch (IOException e) {
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }

  public static void main(String[] args) {
    String url = "http://sug.qianqian.com/info/suggestion?format=json&version=2&from=0&word=刺心&third_type=0&client_type=0";
    ApiAsker asker = new ApiAsker();
    String content = asker.getContent(url);

    // 解析结果
    Map contentObj = JSON.parseObject(content, Map.class);
    Map data = (Map) contentObj.get("data");
    List list = (List) data.get("song");
    int length = list.size();
    for (int i = 0; i < length; i++) {
      Map song = (Map)list.get(i);
      String songname = song.get("songname").toString();
      String artistname = song.get("artistname").toString();
      System.out.println(songname+ "-"+ artistname);
    }

  }
```