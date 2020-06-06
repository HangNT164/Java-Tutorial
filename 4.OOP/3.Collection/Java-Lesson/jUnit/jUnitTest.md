# jUnit Test

## JUnit là gì?

JUnit là một framework đơn giản dùng cho việc tạo các unit testing tự động, và chạy các test có thể lặp đi lặp lại. JUnit là một framework được dùng cho unit test trong Java.

Trong JUnit có các Test Case là các lớp của Java, các lớp này bao gồm một hay nhiều các phương thức cần kiểm tra, và Test Case này lại được nhóm với nhau để tạo thành Test Suite. Mỗi phương thức thử trong JUnit phải được thực thi nhanh chóng.

## Annotation trong JUnit

| Annotation          | Ý nghĩa           |
| ------------------- | ----------------- |
| `@RunWith`          | Xác định **test runner**      |
| `@Suite`            | Thực thi nhiều **test case** cùng một lúc |
| `@Before`           | Method sẻ được thực thi **trước** mỗi method **test**. `public void` |
| `@BeforeClass`      | Method sẻ chỉ **chạy 1 lần** và **trước** tất cả method của class. `public static void` |
| `@After`            | Method sẽ được thực thi **sau** mỗi phương thức test. `public void` |
| `@AfterClass`       | Method sẻ chỉ **chạy 1 lần** và **sau** tất cả method của class. `public static void` |
| `@Test`             | Đánh dấu một method dùng để **test**. |
| `@Test(expected = ArithmeticException.class)` | Bắt ngoại lệ cho method **test**. |
| `@Test(timeout=time)` | Xác định thời gian thực thi cho method **test**. |

## Các phương thức Assert()

Các phương thức assertXXX() được dùng để kiểm tra các điều kiện khác nhau.junit.framework.TestCase, lớp cha cho tất cả các test case, thừa kế từ lớp junit.framework.Assert. Lớp này định nghĩa khá nhiều các phương thức assertXXX(). Các phương thức test hoạt động bằng cách gọi những phương thức này.

Sau đây là mô tả các phương thức assertXXX() khác nhau có trong lớp junit.framework.Assert.

- `assertEquals()`: So sánh 2 giá trị để kiểm tra bằng nhau. Test sẽ được chấp nhận nếu các giá trị bằng nhau.
- `assertFalse()`: Đánh giá biểu thức luận lý. Test sẽ được chấp nhận nếu biểu thức sai.
- `assertNotNull()`: So sánh tham chiếu của một đối tượng với null. Test sẽ được chấp nhận nếu tham chiếu đối tượng khác null.
- `assertNotSame()`: So sánh địa chỉ vùng nhớ của 2 tham chiếu đối tượng bằng cách sử dụng toán tử ==. Test sẽ được chấp nhận nếu cả 2 đều tham chiếu đến các đối tượng khác nhau
- `assertNull()`: So sánh tham chiếu của một đối tượng với giá trị null. Test sẽ được chấp nhận nếu tham chiếu là null.
- `assertSame()`: So sánh địa chỉ vùng nhớ của 2 tham chiếu đối tượng bằng cách sử dụng toán tử ==. Test sẽ được chấp nhận nếu cả 2 đều tham chiếu đến cùng một đối tượng.
- `assertTrue()`: Đánh giá một biểu thức luận lý. Test sẽ được chấp nhận nếu biểu thức đúng fail(): Phương thức này làm cho test hiện hành thất bại, phương thức này thường được sử dụng khi xử lý các biệt lệ.

Mặc dù bạn có thể chỉ cần sử dụng phương thức `assertTrue()` cho gần như hầu hết các test, tuy nhiên thì việc sử dụng một trong các phương thức assertXXX() cụ thể sẽ làm cho các test của bạn dễ hiểu hơn và cung cấp các thông điệp thất bại rõ ràng hơn.

Tất cả các phương thức của bảng trên đều nhận vào một `String` không bắt buộc làm tham số đầu tiên. Khi được xác định, tham số này cung cấp một thông điệp mô tả test thất bại.

Ví dụ:
```java
assertEquals(employeeA, employeeB);  
assertEquals("Employees should be equal after the clone() operation.", employeeA, employeeB).
```
Phiên bản thứ 2 được ưa thích hơn vì nó mô tả tại sao test thất bại, điều này sẽ giúp cho việc sửa lỗi được dễ dàng hơn.

## Set Up và Tear Down

Hai phương thức `setUp()` và `tearDown()` là một phần của lớp junit.framework.TestCase Bằng cách sử dụng các phương thức `setUp` và `tearDown`. Khi sử dụng 2 phương thức `setUp()` và `tearDown()` sẽ giúp chúng ta tránh được việc trùng mã khi nhiều test cùng chia sẻ nhau ở phần khởi tạo và dọn dẹp các biến.

JUnit tuân thủ theo một dãy có thứ tự các sự kiện khi chạy các test. Đầu tiên, nó tạo ra một thể hiện mới của test case ứng với mỗi phương thức test. Từ đó, nếu bạn có 5 phương thức test thì JUnit sẽ tạo ra 5 thể hiện của test case. Vì lý do đó, các biến thể hiện không thể được sử dụng để chia sẻ trạng thái giữa các phương thức test. Sau khi tạo xong tất cả các đối tượng test case, JUnit tuân theo các bước sau cho mỗi phương thức test:

- Gọi phương thức `setUp()` của test case
- Gọi phương thức test
- Gọi phương thức `tearDown()` của test case
- Quá trình này được lặp lại đối với mỗi phương thức test trong test case.

Thông thường bạn có thể bỏ qua phương thức tearDown() vì mỗi unit test riêng không phải là những tiến trình chạy tốn nhiều thời gian, và các đối tượng được thu dọn khi JVM thoát. tearDown() có thể được sử dụng khi test của bạn thực hiện những thao tác như mở kết nối đến cơ sở dữ liệu hay sử dụng các loại tài nguyên khác của hệ thống và bạn cần phải dọn dẹp ngay lập tức. Nếu bạn chạy một bộ bao gồm một số lượng lớn các unit test, thì khi bạn trỏ tham chiếu của các đối tượng đến null bên trong thân phương thức tearDown() sẽ giúp cho bộ dọn rác lấy lại bộ nhớ khi các test khác chạy.
