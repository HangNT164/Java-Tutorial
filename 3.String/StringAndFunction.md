<b>String in java</b>
<br/>
1.Khái niệm và cách tạo string <br/>
- Là 1 kiểu dữ liệu đặc biệt trong java<br/>
- Có 2 cách tạo string <br/>
	String a="Hello";<br/>
	String a=new String();

EX:<br/>
public class StringDemo {
<br/>
   public static void main(String args[]) {<br/>
     char[] helloArray = { 'h', 'e', 'l', 'l', 'o', '.' };<br/>
     String helloString = new String(helloArray);  <br/>
    System.out.println( helloString );<br/>
   }<br/>
}<br/>
// Output:<br/>
hello.<br/>
2.Các phương thức của string trong java<br/>
- Link : https://www.tutorialspoint.com/java/java_strings.htm