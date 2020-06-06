#Tính Trừu Tượng (Abstraction) Là Gì?

Trừu tượng trong thực tế còn có thể hiểu là cái gì đó không có thực. Vậy tính Trừu tượng trong OOP ý muốn nói đến một lớp nào đó mang một đặc tính trừu tượng, không có thực. Và như vậy bạn có thể hiểu là lớp Trừu tượng sẽ là lớp không tồn tại đúng không nào?

Thực ra thì lớp Trừu tượng vẫn có tồn tại, vẫn là một lớp thôi. Nhưng nó trừu tượng ở chỗ, nó không thể được dùng để tạo ra các đối tượng như những lớp bình thường khác. Lớp Trừu tượng khi này chỉ là cái “xác không hồn”, hay bạn có thể hiểu nó chỉ là một cái sườn, để mà bạn có thể tạo ra các lớp con của nó dựa vào sự ràng buộc từ cái sườn này.

Nghe đến đây đủ thấy trừu tượng rồi ha. Chúng ta cùng xem khai báo một lớp là Trừu tượng là như thế nào, và các đặc điểm của một lớp Trừu tượng sẽ ra sao với mục kế tiếp.

Khai Báo Lớp Trừu Tượng Như Thế Nào?

Sau đây là cú pháp để bạn có thể khai báo một lớp Trừu tượng.

```java
abstract  class  tên_lớp {
	các_thuộc_tính;
	các_phương_thức;
}
```

Bạn có thể thấy, để khai báo một lớp là Trừu tượng, chỉ cần thêm vào trước từ khóa class một từ khóa abstract mà thôi.

Nhưng như vậy thì mục đích của sự Trừu tượng này là gì, chúng ta cùng đi đến mục sau đây.

#Tại Sao Phải Trừu Tượng?

Lý do tiên quyết mà bạn phải biết đến Trừu tượng là vì có trên 90% khả năng bạn đi xin việc, người phỏng vấn sẽ hỏi bạn câu này: “em hãy giúp phân biệt giữa lớp abstract và interface”!!! Mình đùa thôi! Nhưng họ hỏi thật đấy!

Thực ra lý do để khai báo một lớp Trừu tượng là vì trong lớp có ít nhất một phương thức Trừu tượng. Có thể nói ngược lại cho dễ hiểu như sau, nếu mà một lớp có ít nhất một phương thức được định nghĩa là Trừu tượng, thì lớp đó phải khai báo Trừu tượng. Đến đây bạn sẽ có rất nhiều thắc mắc, mình xin giải đáp từ từ.

Phương thức Trừu tượng là gì? Chính là phương thức có định nghĩa từ khóa abstract khi khai báo. Cú pháp khai báo một phương thức Trừu tượng cũng giống như khai báo một lớp Trừu tượng thôi.

[kả_năng_truy_cập]  abstract  kiểu_trả_về  tên_phương_thức  ([ các_tham_số_truyền_vào"]);

Phương thức Trừu tượng có tác dụng gì? Phương thức có khai báo abstract sẽ buộc phải không có thân hàm. Như bạn xem cú pháp ở trên, sẽ không có thông tin về khối lệnh của phương thức dạng này. Bạn có thể so sánh với cú pháp của phương thức bình thường ở đây. Bạn chỉ có thể khai báo tên, các tham số truyền vào (nếu có), kiểu trả về, và rồi kết thúc khai báo bằng (;) cho các phương thức Trừu tượng. Có thể thấy rõ sự ràng buộc của tính Trừu tượng bắt đầu ở ngay đây. Sở dĩ các phương thức Trừu tượng không có thân hàm, vì chúng không cần phải làm vậy. Một khi có một lớp nào đó kế thừa từ lớp Trừu tượng này, thì lớp kế thừa đó buộc phải hiện thực (tiếng Anh gọi là implement) nội dung cho tất cả các phương thức Trừu tượng này, bằng cách override lại chúng.

Đến đây bạn có thể thấy lớp Trừu tượng thực sự không quá cao siêu. Nó chỉ là một lớp không có thể hiện (không thể khởi tạo đối tượng từ nó). Nhưng nó lại ràng buộc các lớp con của nó buộc phải hiện thực nội dung cho các phương thức Trừu tượng bên trong nó. Thế thôi.


