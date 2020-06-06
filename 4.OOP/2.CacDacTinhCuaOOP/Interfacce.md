Một Interface trong Java là một bản thiết kế của một lớp. Nó chỉ có các phương thức trừu tượng. Interface là một kỹ thuật để thu được tính trừu tượng hoàn toàn và đa kế thừa trong Java. Interface trong Java cũng biễu diễn mối quan hệ IS-A. Nó không thể được khởi tạo giống như lớp trừu tượng.

Java Compiler thêm từ khóa public và abstract trước phương thức của interface và các từ khóa public, static và final trước các thành viên dữ liệu.

Nói cách khác, các trường của Interface là public, static và final theo mặc định và các phương thức là public và abstract.

Một Interface trong Java là một tập hợp các phương thức trừu tượng (abstract). Một class triển khai một interface, do đó kế thừa các phương thức abstract của interface.

Một interface không phải là một lớp. Viết một interface giống như viết một lớp, nhưng chúng có 2 định nghĩa khác nhau. Một lớp mô tả các thuộc tính và hành vi của một đối tượng. Một interface chứa các hành vi mà một class triển khai.

Trừ khi một lớp triển khai interface là lớp trừu tượng abstract, còn lại tất cả các phương thức của interface cần được định nghĩa trong class.

Một interface tương tự với một class bởi những điểm sau đây:

Một interface được viết trong một file với định dạng .java, với tên của interface giống tên của file.

Bytecode của interface được lưu trong file có định dạng .class.

Khai báo interface trong một package, những file bytecode tương ứng cũng có cấu trúc thư mục có cùng tên package.

Một interface khác với một class ở một số điểm sau đây:

Bạn không thể khởi tạo một interface.

Một interface không chứa bất cứ hàm Contructor nào.

Tất cả các phương thức của interface đều là abstract.

Một interface không thể chứa một trường nào trừ các trường vừa static và final.

Một interface không thể kế thừa từ lớp, nó được triển khai bởi một lớp.

Một interface có thể kế thừa từ nhiều interface khác.

```java
interface printable {  
void print();  
}  
   
class A6 implements printable {  
    public void print() {
        System.out.println("Hello");
    }  
   
    public static void main(String args[]){  
        A6 obj = new A6();  
        obj.print();  
    }
}
```
Khi ghi đè các phương thức được định nghĩa trong interface, có một số qui tắc sau:

Các checked exception không nên được khai báo trong phương thức implements, thay vào đó nó nên được khai báo trong phương thức interface hoặc các lớp phụ được khai báo bởi phương thức interface.

Signature (ký số) của phương thức interface và kiểu trả về nên được duy trì khi ghi đè phương thức (overriding method).

Một lớp triển khai chính nó có thể là abstract và vì thế các phương thức interface không cần được triển khai.

Khi triển khai interface, có vài quy tắc sau:

Một lớp có thể triển khai một hoặc nhiều interface tại một thời điểm.

Một lớp chỉ có thể kế thừa một lớp khác, nhưng được triển khai nhiều interface.

Một interface có thể kế thừa từ một interface khác, tương tự cách một lớp có thể kế thừa lớp khác.

#Sự khác nhau giữa Abstract class và Interface

Abstract class và interface đều được sử dụng để có được sự trừu tượng mà ở đó 

chúng ta có thể khai báo các phương thức trừu tượng. Nhưng có một vài sự khác nhau giữa 

abstract class và interface được liệt kê trong bảng sau:

Abstract class																								Interface
1) Abstract class có phương thức abstract (không có thân hàm) và phương thức non-abstract (có thân hàm).	Interface chỉ có phương thức abstract. Từ java 8, nó có thêm các phương thức default và static.
2) Abstract class không hỗ trợ đa kế thừa.																	Interface có hỗ trợ đa kế thừa
3) Abstract class có các biến final, non-final, static and non-static.										Interface chỉ có các biến static và final.
4) Abstract class có thể cung cấp nội dung cài đặt cho phương thức của interface.							Interface không thể cung cấp nội dung cài đặt cho phương thức của abstract class.
5) Từ khóa abstract được sử dụng để khai báo abstract class.												Từ khóa interface được sử dụng để khai báo interface.

```java																										Ví dụ:
public abstract class Shape {																				public interface Drawable {
public abstract void draw();																				void draw();
}																											}																																																				
```

