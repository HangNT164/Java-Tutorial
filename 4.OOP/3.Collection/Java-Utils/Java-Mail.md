# Java Mail 1.6.2

API JavaMail cung cấp một giao thức độc lập để xây dựng các ứng dụng làm việc với email. API JavaMail có sẵn dưới dạng gói tùy chọn để sử dụng với nền tảng Java SE và nền tảng Java EE .

#### Latest News [August 29, 2018 - JavaMail 1.6.2 Final Release](https://github.com/javaee/javamail/releases)

### 1. Download JavaMail Release
Bản phát hành mới nhất của JavaMail là 1.6.2.

|Item|Description|
|---|---|
|[javax.mail.jar](https://github.com/javaee/javamail/releases/download/JAVAMAIL-1_6_2/javax.mail.jar)|The JavaMail reference implementation, including the SMTP, IMAP, and POP3 protocol providers|

### 2. Code example

Ví dụ này là một ví dụ dùng **Gmail** để gửi đi một emai đơn giản.

```java

import javax.mail.*;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import java.util.Properties;

/**
 *
 * @author anhdt
 */
public class JavaMailDemo {
    
    private final String MAIL = " ";
    private final String PASSWORD = "******";
    
    public void sentEmail(String toEmail, String subject, String text) {
        
        // Config
        Properties props = new Properties();
        props.put("mail.smtp.auth", "true");
        props.put("mail.smtp.starttls.enable", "true");
        props.put("mail.smtp.host", "smtp.gmail.com");
        
        // Authenticator
        Session session = Session.getInstance(props, new Authenticator() {
            @Override
            protected PasswordAuthentication getPasswordAuthentication() {
                return new PasswordAuthentication(MAIL, PASSWORD);
            }
        });

        // Mail info
        try {
            Message message = new MimeMessage(session);
            message.setFrom(new InternetAddress(MAIL));
            message.setRecipients(Message.RecipientType.TO, InternetAddress.parse(toEmail));
            message.setSubject(subject);
            message.setText(text);

            Transport.send(message);           
            System.out.println("Message sent successfully...");
            
        } catch (MessagingException e) {
            throw new RuntimeException(e);
        }
    }    
}

```

Chạy ví dụ với hàm `main`
```java
/**
 * @param args the command line arguments
 */
public static void main(String[] args) {
    String toEmail = "";
    String subject = "[JavaMail] - Demo sent email";
    String text = "Thank you for using JavaMail";
    new JavaMailDemo().sentEmail(toEmail, subject, text);
}
```

Output
```java
run:
Message sent successfully...
BUILD SUCCESSFUL (total time: 5 seconds)
```

### 3. Exception

Nếu gặp `Exception` ở dưới thì là do email của bạn chưa bật tính năng cho xác thực từ bên thứ 3, tính năng này auto tắt do Gmail.

```java
Exception in thread "main" java.lang.RuntimeException: javax.mail.AuthenticationFailedException: 535-5.7.8 Username and Password not accepted. 
Learn more at 535 5.7.8 https://support.google.com/mail/?p=BadCredentials e26sm2342304pgb.48 - gsmtp
```

Để bật tính năng này lên, hãy đăng nhập tài khoản Google rồi truy cập vào link sau: [https://myaccount.google.com/lesssecureapps](https://myaccount.google.com/lesssecureapps) để bật tính năng này lên.
