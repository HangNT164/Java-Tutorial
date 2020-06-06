#Tính đa hình trong java

Đa hình trong java (Polymorphism) là một khái niệm mà chúng ta có thể thực hiện một hành động bằng nhiều cách khác nhau. Polymorphism được cấu tạo từ 2 từ Hy Lạp: poly và morphs. Trong đó "poly" có nghĩa là nhiều và "morphs" có nghĩa là hình thể. Vậy polymorphism có nghĩa là nhiều hình thể.

Có hai kiểu của đa hình trong java, đó là đa hình lúc biên dịch (compile) và đa hình lúc thực thi (runtime). Chúng ta có thể thực hiện đa hình trong java bằng cách nạp chồng phương thức và ghi đè phương thức.

Nếu bạn nạp chồng phương thức static trong java, đó là một ví dụ về đa hình lúc biên dịch. Trong bài này, chúng ta tập trung vào đa hình lúc runtime trong java.

#Đa hình lúc runtime trong java

Đa hình lúc runtime là quá trình gọi phương thức đã được ghi đè trong thời gian thực thi chương trình. Trong quá trình này, một phương thức được ghi đè được gọi thông qua biến tham chiếu của một lớp cha.

Trước khi tìm hiểu về đa hình tại runtime, chúng ta cùng tìm hiểu về Upcasting.

#Đa hình lúc runtime trong Java với thành viên dữ liệu

Phương thức bị ghi đè không là thành viên dữ liệu, vì thế đa hình tại runtime không thể có được bởi thành viên dữ liệu. Trong ví dụ sau đây, cả hai lớp có một thành viên dữ liệu là speedlimit, chúng ta truy cập thành viên dữ liệu bởi biến tham chiếu của lớp cha mà tham chiếu tới đối tượng lớp con. Khi chúng ta truy cập thành viên dữ liệu mà không bị ghi đè, thì nó sẽ luôn luôn truy cập thành viên dữ liệu của lớp cha.

#Nạp chồng phương thức trong java

Nạp chồng phương thức (method overloading)

Nạp chồng phương thức trong java xảy ra nếu một lớp có nhiều phương thức có tên giống nhau nhưng khác nhau về kiểu dữ liệu hoặc số lượng các tham số.

Giả sử bạn phải thực hiện tính tổng của các số đã cho với bất kỳ số lượng các đối số, nếu bạn viết phương thức a(int, int) cho 2 tham số, b(int, int, int) cho 3 tham số điều này có thể gây khó hiểu cho các lập trình viên khác về ý nghĩa của các phương thức đó vì chúng có tên khác nhau.

Lợi ích của nạp chồng phương thức

Sử dụng nạp chồng phương thức giúp tăng khả năng đọc hiểu chương trình.


Các cách nạp chồng phương thức

#Có 2 cách nạp chồng phương thức trong java

Thay đổi số lượng các tham số

Thay đổi kiểu dữ liệu của các tham số

#1. Nạp chồng phương thức: thay đổi số lượng các tham số

Trong ví dụ này, chúng ta cần tạo 2 phương thức, phương thức add() đầu tiên thực hiện việc tính tổng của 2 số, phương thức thứ hai thực hiện việc tính tổng của 3 số. Sử dụng phương thức static để gọi hàm thông qua tên class thay vì phải tạo thể hiên của lớp.

```java
class Adder{  
    static int add(int a,int b){return a+b;}  
    static int add(int a,int b,int c){return a+b+c;}  
}  
class TestOverloading1{  
    public static void main(String[] args){  
        System.out.println(Adder.add(11,11));  
        System.out.println(Adder.add(11,11,11));  
    }
}  
```
Kết quả:

22

33

#2. Nạp chồng phương thức: thay đổi kiểu dữ liệu của các tham số

Trong ví dụ này, chúng ta sẽ tạo ra 2 phương thức có kiểu dữ liệu khác nhau. Phương thức add() đầu tiên nhận 2 đổi số có kiểu giá trị là integer, phương thức thứ hai nhận 2 đổi số có kiểu giá trị là double.

```java
class Adder{  
    static int add(int a, int b){return a+b;}  
    static double add(double a, double b){return a+b;}  
}  
class TestOverloading2{  
    public static void main(String[] args){  
        System.out.println(Adder.add(11,11));  
        System.out.println(Adder.add(12.3,12.6));  
    }
}  
```
Kết quả:

22

24.9

#Ghi đè phương thức (method overriding)
Ghi đè phương thức trong java xảy ra nếu lớp con có phương thức giống lớp cha.

Nói cách khác, nếu lớp con cung cấp sự cài đặt cụ thể cho phương thức đã được cung cấp bởi một lớp cha của nó được gọi là ghi đè phương thức (method overriding) trong java.

#Sử dụng ghi đè phương thức trong java

Ghi đè phương thức được sử dụng để cung cấp cài đặt đặc biệt của một phương thức mà đã được định nghĩa ở lớp cha.

Ghi đè phương thức được sử dụng cho đa hình runtime.

#Các nguyên tắc ghi đè phương thức trong java

Phương thức phải có tên giống với lớp cha.

Phương thức phải có tham số giống với lớp cha.

Lớp con và lớp cha có mối quan hệ kế thừa.

Ví dụ ghi đè phương thức trong java

Trong ví dụ này, chúng ta định nghĩa phương thức run() trong lớp con giống như đã được định nghĩa trong lớp cha, nhưng được cài đặt rõ ràng trong lớp con. Tên và tham số của phương thức là giống nhau, 2 lớp cha và con có quan hệ kế thừa.

```java
class Vehicle {
    void run() {
        System.out.println("Vehicle is running");
    }
}
 
public class Bike2 extends Vehicle {
    void run() {
        System.out.println("Bike is running safely");
    }
 
    public static void main(String args[]) {
        Bike2 obj = new Bike2();
        obj.run();
    }
}
```
Kết quả:

Bike is running safely