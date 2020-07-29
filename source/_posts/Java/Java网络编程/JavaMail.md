---
title: JavaMail
toc: true
date: 2020-07-23 15:33:03
categories:
 - Java
 - Java网络编程
---
<meta name="referrer" content="no-referrer"/>

## 1、依赖
```xml
<dependency>
 <groupId>javax.mail</groupId>
 <artifactId>mail</artifactId>
 <version>1.4</version>
</dependency>
```

## 2、使用
```java
import java.security.Security;
import java.util.Properties;
import javax.mail.Authenticator;
import javax.mail.Message;
import javax.mail.PasswordAuthentication;
import javax.mail.Session;
import javax.mail.Transport;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import com.sun.net.ssl.internal.ssl.Provider;

public class MailClient {
  public static void main(String[] args) {
    try {
      //设置SSL连接、邮件环境
      Security.addProvider(new Provider());
      final String SSL_FACTORY = "javax.net.ssl.SSLSocketFactory";

      //配置邮箱信息
      Properties props = System.getProperties();
      //邮件服务器
      props.setProperty("mail.smtp.host", "smtp.qq.com");
      props.setProperty("mail.smtp.socketFactory.class", SSL_FACTORY);
      props.setProperty("mail.smtp.socketFactory.fallback", "false");
      //邮件服务器端口
      props.setProperty("mail.smtp.port", "465");
      props.setProperty("mail.smtp.socketFactory.port", "465");
      //鉴权信息
      props.setProperty("mail.smtp.auth", "true");
      //建立邮件会话
      Session session = Session.getDefaultInstance(props, new Authenticator() {
        //身份认证
        protected PasswordAuthentication getPasswordAuthentication() {
          //1.账户 授权码
          return new PasswordAuthentication("987454568@qq.com", "rzuqttyyhwpabead");
        }
      });
      //建立邮件对象
      MimeMessage message = new MimeMessage(session);
      //设置邮件的发件人
      message.setFrom(new InternetAddress("987454568@qq.com"));
      //2.设置邮件的单（多）个收件人
      message.setRecipients(Message.RecipientType.TO, "xxxx@qq.com,xxxx@126.com");
      //设置邮件的主题
      message.setSubject("通过javamail发出！！！");
      //文本部分
      message.setContent("文本邮件测试", "text/html;charset=UTF-8");
      message.saveChanges();
      //发送邮件
      Transport.send(message);
    } catch (Exception e) {
      e.printStackTrace();
    }
  }
}
```