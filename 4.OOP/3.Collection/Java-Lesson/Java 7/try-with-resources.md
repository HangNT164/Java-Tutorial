# try-with-resources [Automatic Resource Management]

`try`-with-resources là một tính năng mới trong Java 7, nó giúp chúng ta tự động dọn dẹp các tài nguyên (`resources` - Tài nguyên là một đối tượng phải được đóng `closed` sau khi chương trình kết thúc công việc với nó) sau khi sử dụng, cắt giảm số dòng code và làm cho code hiệu quả hơn. Bất kỳ đối tượng nào implements `java.lang.AutoCloseable`, bao gồm tất cả các đối tượng implement `java.io.Closeable`, có thể được sử dụng như một tài nguyên (`resources`).

Cụ thể chúng ta sẽ đi vào tìm hiều trong bài viết sau.

## Cách dọn dẹp tài nguyên cũ (Trước java 7)

Xem qua ví dụ sau:
```java
BufferedReader br = null;
try {
    String sCurrentLine;
    br = new BufferedReader(new FileReader("C:/temp/test.txt"));
    while ((sCurrentLine = br.readLine()) != null) {
        System.out.println(sCurrentLine);
    }
}
catch (IOException e) {
    e.printStackTrace();
}
finally {
    try {
        if (br != null)
            br.close();
    }
    catch (IOException ex) {
        ex.printStackTrace();
    }
}
```
Khối `finally` dùng để viết mã dọn dẹp các tài nguyên sau khi khối `try` hoàn thành bình thường hoặc dừng đột ngột (Throw Exception). Đây là cách phổ biến thường dùng, nhưng khối `finally` sẽ trở nên dài và trông xấu hơn khi bạn có nhiều tài nguyên hơn cần dọn dẹp và xử lý. 

#### Java 7 giải quyết vấn đề này với tính năng try-with-resources.
## try-with-resources

Bây giờ hãy xem cách mở và đóng tài nguyên mới trong java 7
```java
try (BufferedReader br = new BufferedReader(new FileReader("C:/temp/test.txt"))) {
    String sCurrentLine;
    while ((sCurrentLine = br.readLine()) != null) {
        System.out.println(sCurrentLine);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```
Bây giờ tài nguyên `BufferedReader` sẽ được khai báo trong dấu ngoặc đơn ngay sau từ khóa `try`. Khối `finally` đã được lược bỏ (không cần thiết nữa). `try`-with-resources đảm bảo rằng mỗi tài nguyên sẽ được đóng ở cuối câu lệnh `try`.

## Cách thức hoạt động

Trong java 7, chúng ta có một super interface `java.lang.AutoCloseable` mới. Interface  này có một phương thức:
```java
void close() throws Exception;
```
Tài liệu Java khuyên bạn nên implements interface này trên bất kỳ tài nguyên nào cần phải `close()` sau khi không cần dùng nữa.

Khi bạn khai báo bất kỳ tài nguyên implements `AutoCloseable` nào trong khối `try`-with-resource, ngay sau khi kết thúc khối `try`, JVM gọi phương thức `close()` này trên tất cả các tài nguyên được khởi tạo trong khối `try()`.

## Những điểm tóm tắt chính

* Trước java 7, chúng ta phải sử dụng các khối `finally` để dọn dẹp các tài nguyên. Từ java 7, chúng ta nên sử dụng `try`-with-resource.
* Với java 7, không cần dọn dẹp tài nguyên rõ ràng. Nó sẽ được thực hiện tự động. Tự động dọn dẹp tài nguyên được thực hiện khi khởi tạo tài nguyên trong khối `try`-with-resources theo cú pháp:
```java
    try(...){...}
```
* Dọn dẹp tài nguyên xảy ra vì interface `AutoCloseable` mới. Phương thức `close()` của nó được gọi bởi JVM ngay khi khối `try` kết thúc.
* Nếu bạn muốn sử dụng `try`-with-resources với custom resources, thì việc implementing `AutoCloseable` interface là bắt buộc. Nếu không chương trình sẽ không biên dịch.
* Bạn không được phép gọi phương thức `close()` khi đã sử dụng `try`-with-resources. Điều này nên được gọi tự động bởi JVM. Gọi nó theo cách thủ công có thể gây ra kết quả không mong muốn.
* Một câu lệnh `try`-with-resources có thể có `catch` và `finally` cũng giống như một câu lệnh `try` thông thường. Trong một câu lệnh `try`-with-resources, bất kỳ khối `catch` hoặc `finally` nào đều được chạy sau khi các tài nguyên được khai báo đã được đóng.

## Ví dụ với JDBC

Sau đây chúng ta sẽ cùng sử dụng `try`-with-resources để làm việc với Connection, PreparedStatement, ResultSet

Đầu tiên chúng ta xem qua các interface

`Connection`
```java
public interface Connection  extends Wrapper, AutoCloseable {}
```

`Statement`
```java
public interface Statement extends Wrapper, AutoCloseable {}
```

`PreparedStatement` kế thừa `Statement`
```java
public interface PreparedStatement extends Statement {}
```

`ResultSet`
```java
public interface ResultSet extends Wrapper, AutoCloseable {}
```

Nhìn qua chúng ta đều thấy Connection, PreparedStatement, ResultSet implements AutoCloseable, có nghĩa là chúng đều sử dụng được với `try`-with-resources.

Đầu tiên chúng ta tạo lớp `MSSQLConnection.java` với phương thức `getConnection()` trả về một `Connection`.

Sau đó sử dụng `try`-with-resources để lấy danh sách Products theo ví dụ sau:
```java
public ArrayList<Product> getAllProducts() {
    ArrayList<Product> list = new ArrayList<>();
    String query = "SELECT * FROM Products";
    try (Connection con = MSSQLConnection.getConnection();
            PreparedStatement ps = con.prepareStatement(query)) {

        ResultSet rs = ps.executeQuery();
        while (rs.next()) {
            Product product = new Product();
            list.add(product);
        }
        return list;
        
    } catch (SQLException e) {
        e.printStackTrace();
    }
    return null;
}
```
`ResultSet` không cần phải khởi tạo trong khối `try` vì: Một đối tượng `ResultSet` được tự động đóng bởi đối tượng `Statement` đã sinh ra nó khi đối tượng `Statement` được đóng lại, được thực thi lại, hoặc được sử dụng để lấy kết quả kế tiếp từ một chuỗi các kết quả.

References: [ResultSet - close()](https://docs.oracle.com/javase/7/docs/api/java/sql/ResultSet.html#close%28%29)

## References
* [The try-with-resources Statement](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html)
* [Interface AutoCloseable](https://docs.oracle.com/javase/7/docs/api/java/lang/AutoCloseable.html)
