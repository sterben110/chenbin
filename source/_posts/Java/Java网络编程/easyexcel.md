---
title: easyexcel
toc: true
date: 2020-07-23 15:31:23
categories:
 - Java
 - Java网络编程
---
<meta name="referrer" content="no-referrer"/>

## 1、依赖
> easyexcel 是一个 JAVA 解析 Excel 工具。
```xml
<!-- excel 操作库 -->
      <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>easyexcel</artifactId>
        <version>2.1.6</version>
      </dependency>
```

## 2、使用
### 2.1、不转化为类
```java
// 读取第一个sheet
List<Map<Integer, String>> sheetDatas = EasyExcel.read("xzq_201907.xlsx").sheet(0).doReadSync();
// List 中每个元素表示一行
for (Map<Integer, String> rowData : sheetDatas) {
  // Map 中用序号指代每一列
  for (Integer index : rowData.keySet()) {
    // 列值
    String columnValue = rowData.get(index);
  }
}
```

### 2.2、自动转化为类
```java
  List<DemoData> sheetDatas = EasyExcel.read("xzq_201907.xlsx").head(DemoData.class).sheet(0).doReadSync();
    for (DemoData rowData : sheetDatas) {
      System.out.println(JSON.toJSONString(rowData));
    }
```

```java
public class DemoData {

  private String code1;
  private String city1;
  private String code2;
  private String city2;
  private String code3;
  private String city3;
```