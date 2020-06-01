# String in java

# 1.String là gì

Trong hướng dẫn này chúng ta sẽ đi tìm hiểu về string là gì?

- String là 1 kiểu dữ liệu đặc biệt.

- String vừa được coi là kiểu dữ liệu nguyên thủy và nó vừa là object (được khởi tạo bằng từ khóa new )

# 2.Cách khởi tạo String 

C1: Khi nó là kiểu dữ liệu nguyên thủy

String s="Hello";

C2:Khi được khởi tạo bằng từ khóa new

String s = new String("Hello");

# 3.Các hàm hay sử dụng trong java khi sử dụng String

a) Phương thức length () trả về độ dài của chuỗi (tổng số ký tự theo mã unicode).

```java
public class LengthExample {
 public static void main(String args[]) {
  String s1 = "java";
  String s2 = "python";
  System.out.println("string length is: " + s1.length());
  System.out.println("string length is: " + s2.length());
 }
}
```

Output:  string length is: 4

			string length is: 6
			
b)Phương thức charAt() trả về giá trị Char của chuỗi tại vị trí có chỉ số index được chỉ định được chỉ định. Index bắt đầu từ 0.

```java
public class CharAtExample {
 public static void main(String args[]) {
  String name = "hello java";
  char ch = name.charAt(4);
  System.out.println(ch);
 }
}
```
Output: o

c)Phương thức compareTo() so sánh các chuỗi cho trước với chuỗi hiện tại theo thứ tự từ điển. Nó trả về số dương, số âm hoặc 0.

Nếu chuỗi đầu tiên lớn hơn chuỗi thứ hai, nó sẽ trả về số dương (chênh lệch giá trị ký tự). Nếu chuỗi đầu tiên nhỏ hơn chuỗi thứ hai, nó sẽ trả về số âm và nếu chuỗi đầu tiên là bằng chuỗi thứ hai, nó trả về 0.

```java
public class LastIndexOfExample {
 public static void main(String args[]) {
  String s1 = "hello";
  String s2 = "hello";
  String s3 = "meklo";
  String s4 = "hemlo";
  System.out.println(s1.compareTo(s2));
  System.out.println(s1.compareTo(s3));
  System.out.println(s1.compareTo(s4));
 }
}
```

Output:

0

-5

-1

=> Hàm này trả về int và có phân biệt chữ hoa chữ thường

d) Phương thức compareToIgnoreCase(): Về cơ bản là giống hàm compareTo() nhưng hàm này #KHÔNG PHÂN BIỆT CHỮ HOA THƯỜNG

e) Phương thức equals() so sánh hai chuỗi đưa ra dựa trên nội dung của chuỗi. Nếu hai chuỗi khác nhau nó trả về false. Nếu hai chuỗi bằng nhau nó trả về true.

Phương thức equals() của lớp String được ghi đè từ phương thức equals() của lớp Object.

```java
public class EqualsExample {
 public static void main(String args[]) {
  String s1 = "java";
  String s2 = "java";
  String s3 = "JAVA";
  String s4 = "python";
  System.out.println(s1.equals(s2));
  System.out.println(s1.equals(s3));
  System.out.println(s1.equals(s4));
 }
}
```
Output:

true

false

false

f)Phương thức equalsIgnoreCase() so sánh hai chuỗi đưa ra dựa trên nội dung của chuỗi không phân biệt chữ hoa và chữ thường. Nếu hai chuỗi khác nhau nó trả về false. Nếu hai chuỗi bằng nhau nó trả về true.

```java
public class EqualsExample {
 public static void main(String args[]) {
  String s1 = "java";
  String s2 = "java";
  String s3 = "JAVA";
  String s4 = "python";
  System.out.println(s1.equalsIgnoreCase(s2));
  System.out.println(s1.equalsIgnoreCase(s3));
  System.out.println(s1.equalsIgnoreCase(s4));
 }
}
```

Output:

true

true

false

g) Phương thức concat() nối thêm chuỗi được chỉ định vào cuối chuỗi đã cho.

```java 
public class ConcatExample {
 public static void main(String args[]) {
  String s1 = "java string";
  s1.concat("is immutable");
  System.out.println(s1);
  s1 = s1.concat(" is immutable so assign it explicitly");
  System.out.println(s1);
 }
}
```

Output:

java string

java string is immutable so assign it explicitly

h) Phương thức contains() tìm kiếm chuỗi ký tự trong chuỗi này. Nó trả về true nếu chuỗi các giá trị char được tìm thấy trong chuỗi này, nếu không trả về false.

```java

1
2
3
4
5
6
7
8
public class ContainsExample {
 public static void main(String args[]) {
  String name = "what do you know about me";
  System.out.println(name.contains("do you know"));
  System.out.println(name.contains("about"));
  System.out.println(name.contains("hello"));
 }
}
```
Output:

true

true

false

i)Phương thức endsWith() kiểm tra nếu chuỗi này kết thúc với hậu tố nhất định. Nó trả về true nếu chuỗi này kết thúc với hậu tố đã cho, nếu khác thì trả về false.

```java
public class EndsWithExample {
 public static void main(String args[]) {
  String s1 = "hello java";
  System.out.println(s1.endsWith("t"));
  System.out.println(s1.endsWith("java"));
 }
}
```
Output:

false

true

j) Phương thức indexOf() trả về chỉ số của giá trị ký tự đã cho hoặc chuỗi con. Nếu không tìm thấy trả lại giá trị -1. Chỉ số (index) được đếm từ 0.

Phương thức:

int indexOf(int ch) //Trả về vị trị của giá trị Char đã cho.

int indexOf(int ch, int fromIndex) //Trả về vị trị của giá trị Char đã cho tính từ vị trí fromIndex.

int indexOf(String substring) //Trả về vị trị của chuỗi con.

int indexOf(String substring, int fromIndex) //Trả về vị trị của chuỗi con đã cho tính từ vị trí fromIndex.

```java
public class IndexOfExample {
 public static void main(String args[]) {
  String s1 = "this is index of example";
   
  //Truyền vào chuỗi con
  int index1 = s1.indexOf("is");
  int index2 = s1.indexOf("index");
  System.out.println(index1 + "  " + index2);//2 8  
 
  //Truyền vào chuỗi con và chỉ số bắt đầu
  int index3 = s1.indexOf("is", 4);
  System.out.println(index3);//5
 
  //Truyền vào giá trị Char
  int index4 = s1.indexOf('s');
  System.out.println(index4);//3  
 }
}
```

Output:
2  8

5

3

k) Phương thức isEmpty() khi chuỗi trống trả về true, ngược lại trả về false.

```java
public class IsEmptyExample {
 public static void main(String args[]) {
  String s1 = "";
  String s2 = "hello java";
 
  System.out.println(s1.isEmpty());
  System.out.println(s2.isEmpty());
 }
}
```
Output:

true

false

l) Phương thức replace() được sử dụng để thay thế tất cả các ký tự hoặc chuỗi cũ thành ký tự hoặc chuỗi mới.

```java
ublic class ReplaceExample1 {
 public static void main(String args[]) {
  String s1 = "viettuts is a very good website";
  String replaceString = s1.replace('t', 'j');//thay thế tất cả ký tự 't' thành 'j'  
  System.out.println(replaceString);
 }
}
```

Output:

viejjujs is a very good websije

m) Phương thức replaceAll() trả về một chuỗi thay thế tất cả các chuỗi ký tự phù hợp với regex.

```java
public class ReplaceAllExample1 {
 public static void main(String args[]) {
  String s1 = "viettuts is a very good website";
  String replaceString = s1.replaceAll("t", "j"); //thay the "a" thanh "e"  
  System.out.println(replaceString);
 }
}
```

Output:

viejjujs is a very good websije

n) Phương thức split() tách chuỗi này theo biểu thức chính quy(regular expression) và trả về mảng chuỗi.

```java

1
2
3
4
5
6
7
8
9
10
public class SplitExample {
 public static void main(String args[]) {
  String s1 = "java string split method by viettuts";
  String[] words = s1.split("\\s");//tach chuoi dua tren khoang trang
  //su dung vong lap foreach de in cac element cua mang chuoi thu duoc
  for (String w : words) {
   System.out.println(w);
  }
 }
}
```

Output:

java

string

split

method

by

viettuts

o) Phương thức startsWith() được sử dụng để kiểm tra tiền tố của chuỗi có khớp với giá trị tiền tố đã nhập không, nếu đúng trả về true, sai trả về false.

```java
public class StartsWithExample {
 public static void main(String args[]) {
  String s1 = "java string startsWith() method sample";
  System.out.println(s1.startsWith("ja"));
  System.out.println(s1.startsWith("java string"));
 }
}
```

Output:

true
true


p) Phương thức subString() trả về chuỗi con của một chuỗi.

Chúng ta truyền chỉ số bắt đầu và chỉ số kết thúc cho phương thức subString(), với chỉ số bắt đầu tính từ 0 và chỉ số kết thúc tính từ 1.

```java
public class SubstringExample {
 public static void main(String args[]) {
  String s1 = "hellojava";
  System.out.println(s1.substring(3, 7));// "loja"  
  System.out.println(s1.substring(3));// "lojava"  
 }
}
```

Output:

loja
lojava

q) Phương thức toLowerCase() được sử dụng để chuyển chuỗi về dạng chữ thường.

Phương thức toLowerCase() hoạt động giống y chang phương thức toLowerCase(Locale.getDefault()). Nó sử dụng locale mặc định.

w)Phương thức trim() được sử dụng để xóa khoảng trẳng ở đầu và cuối chuỗi. Giá trị unicode của khoảng trắng là '\u0020'. Phương thức trim() kiểm tra giá trị unicode trước và sau chuỗi, nếu tồn tại thì xóa bỏ khoảng trắng đi và trả về chuỗi không có khoảng trắng ở đầu và cuối.

r) Phương thức valueOf() được sử dụng để chuyển đối kiểu dữ liệu khác thành chuỗi. Bằng việc sử dụng phương thức valueOf(), bạn có thể chuyển int thành chuỗi, long thành chuỗi, boolean thành chuỗi, float thành chuỗi, double thành chuỗi, char thành chuỗi, mảng char thành chuỗi, đối tượng thành chuỗi.
  
