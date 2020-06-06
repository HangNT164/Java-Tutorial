#Tính kế thừa trong java

Kế thừa trong java là sự liên quan giữa hai class với nhau, trong đó có class cha (superclass) và class con (subclass). Khi kế thừa class con được hưởng tất cả các phương thức và thuộc tính của class cha. Tuy nhiên, nó chỉ được truy cập các thành viên public và protected của class cha. Nó không được phép truy cập đến thành viên private của class cha.

Tư tưởng của kế thừa trong java là có thể tạo ra một class mới được xây dựng trên các lớp đang tồn tại. Khi kế thừa từ một lớp đang tồn tại bạn có sử dụng lại các phương thức và thuộc tính của lớp cha, đồng thời có thể khai báo thêm các phương thức và thuộc tính khác.

#Cú pháp của kế thừa trong java

Sử dụng từ khóa extends để kế thừa.

```java
class Subclass-name extends Superclass-name {  
   //methods and fields
} 
```

Ví dụ về kế thừa trong java

```java
class Employee {
    float salary = 1000;
}
 
class Programmer extends Employee {
    int bonus = 150;
}
 
public class InheritanceSample1 {
    public static void main(String args[]) {
        Programmer p = new Programmer();
        System.out.println("Programmer salary is: " + p.salary);
        System.out.println("Bonus of Programmer is: " + p.bonus);
    }
}
```

Kết quả:

Programmer salary is: 1000.0

Bonus of Programmer is: 150

#Các kiểu kế thừa trong java

Có 3 kiểu kế thừa trong java đó là đơn kế thừa, kế thừa nhiều cấp, kế thừa thứ bậc.

Khi một class được kế thừa từ nhiều class đươc gọi là đa kế thừa.

Trong java, đa kế thừa chỉ được support thông qua interface, như đã được nói đến trong bài interface trong java