#Tính đóng gói trong java 

Tính đóng gói trong java là kỹ thuật ẩn giấu thông tin không liên quan và hiện thị ra thông liên quan.

Mục đích chính của đóng gói trong java là giảm thiểu mức độ phức tạp phát triển phần mềm.

Đóng gói cũng được sử dụng để bảo vệ trạng thái bên trong của một đối tượng. 

Bởi việc ẩn giấu các biến biểu diễn trạng thái của đối tượng. Việc chỉnh sửa đối tượng được thực hiện,

xác nhận thông qua các phương thức. Hơn nữa, việc ẩn giấu các biến thì các lớp sẽ không chia sẻ thông tin với nhau được. 
 
Điều này làm giảm số lượng khớp nối có thể có trong một ứng dụng.

#Lợi ích của đóng gói trong java

Bạn có thể tạo lớp read-only hoặc write-only bằng việc cài đặt phương thức setter hoặc getter.

Bạn có thể kiểm soát đối với dữ liệu. Giả sử bạn muốn đặt giá trị của 

id chỉ lớn hơn 100 bạn có thể viết logic bên trong lớp setter.

Ví dụ về đóng gói trong java

Hãy xem ví dụ sau về đóng gói trong java với một lớp chỉ có một trường và các phướng thức setter và getter của nó.

File: Student.java

```java
public class Student {
    private String name;
 
    public String getName() {
        return name;
    }
 
    public void setName(String name) {
        this.name = name;
    }
}
```
File: Test.java

```java
class Test {
    public static void main(String[] args) {
        Student s = new Student();
        s.setName("Hai");
        System.out.println(s.getName());
    }
}
```
Kết quả:

Hai
