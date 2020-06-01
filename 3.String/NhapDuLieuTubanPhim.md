# 1.Nhập dữ liệu từ bàn phím

Chào các bạn hôm nay mình cùng nhau tìm hiểu về cách nhập dữ liệu từ bàn phím:

Các bạn xem ví dụ sau:

Đề: Nhập vào 3 số nguyên a,b,c

```java
public class Calculation {
    public static void main(String[] args) {
        // Chúng ta khai báo 3 biến a,b,c không có giá trị.
        int a, b, c;
        

        //Khai báo đối tượng Scanner, giúp chúng ta nhận thông tin từ keyboard 
        Scanner sc = new Scanner(System.in);
        System.out.print("Nhập a: "); //print thay vì println, nó sẽ in ra, nhưng không xuống dòng

        a = sc.nextInt(); // sc.nextInt() là cách để lấy giá trị từ bàn phím, nó sẽ chờ tới khi chúng ta nhập một số.
        System.out.print("Nhập b: ");
        b = sc.nextInt();
         System.out.print("Nhập c: ");
        c = sc.nextInt();
        // In các giá trị ra màn hình
        System.out.println("a = " + a + ", b = " + b + ", c = " + c);
        //  Đây là phép cộng String mình đã nói trong Bài #1. 
}
```

Output:

Khi chạy chương trình này, nó sẽ dừng lại sau khi in ra Nhập a như thế này:

Nhập a:

Vì cái dòng lệnh này a = sc.nextInt(). Nó sẽ chờ cho tới khi bạn nhập 1 số nguyên và gõ Enter thì thôi. Giả sử mình nhập 5

Nhập a: 5

Nhập b:

Tương tự với các biến còn lại.

=> Ở đây: Scanner sc = new Scanner(System.in); => Scanner đã làm nhiệm vụ là nhận dữ liệu người dùng nhập từ bàn phím, và gán nó vào biến, bằng câu lệnh nextInt.

# 2.Các phương thức nhập xuất

Tới đây, bạn đã có thể nhập xuất dữ liệu int từ bàn phím rồi, thế còn double hay String thì như thế lào :3

cái này bạn nào thực hành đoạn code trên rồi thì sẽ nhìn thấy ngay là Scanner có một loạt các hàm hỗ trợ như sau:

next(): Nhận vào một String token (nhận vào 1 từ đầu tiên thay cả câu)

nextInt(): Nhận vào một số int

nextLong(): Nhận vào một số long

nextFloat(): Nhận vào một số float

nextDouble(): Nhận vào một số double

sc.nextLine(): Nhận vào một chuỗi String (Cả 1 câu)

nextByte(): Nhận vào một byte

nextBoolean(): Nhận vào một boolean

Các hàm trên bạn hiểu nguyên lý là nó đều sẽ chờ cho tới khi bạn nhập kiểu dữ liệu nó muốn vào.

Có next() và nextLine() khá đặc biệt, mình sẽ ví dụ:

```java
Scanner sc = new Scanner(System.in); //Tạo đối tượng Scanner
System.out.print("Nhập gì đó: ");
String a = sc.nextLine(); // nhận vào 1 string
System.out.println("Bạn vừa nhập: "+a);

System.out.print("Nhập thêm gì đi: ");
String b = sc.next(); // cũng nhận vào 1 String
System.out.println("Bạn vừa nhập: "+b);
```

Output:

Nhập gì đó: abc

Bạn vừa nhập: abc

Nhập thêm gì đi: hdhdhd

Bạn vừa nhập: hdhdhd


=> nextLine thì nhận vào cả 1 chuỗi dài String, cho tới khi bạn nhấn Enter. Còn next dù bạn có nhập dài như nào, nó cũng nhận 1 từ đầu tiên thôi.

# 3: Cách nhập xuất hay dùng để tránh rơi vào vòng lặp vô hạn

```java
  public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choose = Integer.valueOf(scanner.nextLine());
        double doubleChoose = Double.valueOf(scanner.nextLine());
        float floatChoose = Float.valueOf(scanner.nextLine());
        String fileName = scanner.nextLine().trim();
    }
```

#NOTE: NHẬP XUẤT DỮ LIỆU NÀY LÀ CHƯA CÓ VALIDATE CHO DỮ LIỆU ĐẦU VÀO . CÁCH NÀY CHỈ GIÚP BẠN KHÔNG RƠI VÀO VÒNG LẶP VÔ HẠN KHI BẠN NHẬP SỐ RỒI ĐẾN CHỮ 
