---
title: fastjson
toc: true
date: 2020-07-23 15:29:02
categories:
 - Java
 - Java网络编程
---
<meta name="referrer" content="no-referrer"/>

## 1、依赖
```xml
    <!-- JSON 操作库 -->
      <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>fastjson</artifactId>
        <version>1.2.62</version>
      </dependency>
```

## 2、使用
> Fastjson 是一个 Java 库，可以将 Java 对象转换为 JSON 格式，当然它也可以将 JSON 字符串转换为 Java 对象。
### 2.1、序列化对象
```java
public static void main(String[] args) {
    Building b = new Building();
    b.setName("创业大厦");
    b.setAddress("天宁兰陵兰陵路26号 ");

    String content = JSON.toJSONString(b);
    System.out.println(content);
  }
```

### 2.2、反序列化对象
```java
  public static void main(String[] args) {
    Building b = new Building();
    b.setName("创业大厦");
    b.setAddress("天宁兰陵兰陵路26号 ");

    String content = JSON.toJSONString(b);

    // 转换为一个具体的对象
    Building b2 = JSON.parseObject(content, Building.class);
    String name = b2.getName();
    System.out.println(name);

    // 特殊情况下，java系统里没有具体对象的 class ，可以反序列化为 Map
    Building bInfo = JSON.parseObject(content, Building.class);
    String name2 = bInfo.getName();
    System.out.println(name2);
  }
```

### 2.3、解析JSON对象
```json
{
  "code": 0,
  "data": {
    "keyword": "西海情歌",
    "priority": 0,
    "qc": [

    ],
    "semantic": {
      "curnum": 0,
      "curpage": 1,
      "list": [],
      "totalnum": 0
    },
    "song": {
      "curnum": 50,
      "curpage": 1,
      "list": [
        {
          "albumid": 14880,
          "albummid": "0024RXz94OSKCa",
          "albumname": "刀郎Ⅲ",
···
```

```java
 public static void main(String[] args) {
    String url = "https://c.y.qq.com/soso/fcgi-bin/client_search_cp?aggr=1&cr=1&flag_qc=0&p=1&n=30&w=西海情歌&format=json";
    ApiAsker asker = new ApiAsker();
    String content = asker.getContent(url);

    Map contentObj = JSON.parseObject(content, Map.class);
    // 解析嵌套的对象，获取数据
    Map data = (Map) contentObj.get("data");
    Map song = (Map) data.get("song");
    List list = (List) song.get("list");

    String albumname = ((Map)list.get(0)).get("albumname")+"";
    System.out.println("albumname = " + albumname);
  }
```
