# `String handling` trong Java OOP
## `Immutability` - Tính bất biến
- `String` có tính `bất biến`: tức không thể thay đổi
### `String pool` (thùng chứa chuỗi) - java
- Tất cả những chuỗi string được khởi tạo ra sẽ được lưu trữ trong string pool, bất cứ khi nào khởi tạo 1 chuỗi, nó sẽ kiểm tra xem trong string pool đã có chưa, nếu có rồi nó sẽ trỏ tới ô dữ liệu chuỗi đó, còn khi chưa có nó mới tạo mới.

## `String Builder`
- Tiết kiệm bộ nhớ hơn String, chuỗi có thể thay đổi. Khi có thay đổi gì nó sẽ thay đổi trực tiếp trên ô nhớ đó, chứ không cần tạo ra ô nhớ mới như String.
    ```java
    StringBuilder stb = new StringBuilder("Java ");
    stb.append("OOP"); // thêm chuỗi thành: Java OOP

    ```

## `StringBuffer`

```java
    StringBuffer stbuff = new StringBuffer("Java");
```
- Chuỗi có thể thay đổi được.
## Lưu ý:
Có điểm khác giữa `StringBuilder` và `StringBuffer` là:
- Các hàm của `StringBuffer` được `synchronized( đồng bộ)` mà `StringBuilder` `không có`.
    - VD: Hàm append StringBuilder: 
        ```java
        public StringBuilder append(String str){}
        ```
    - Hàm append StringBuffer:
        ```java
        public synchronized StringBuffer append(String str){}
        ```
- `Các hàm khi có synchronized, thì ở cùng 1 thời điểm chỉ có 1 luồng tài nguyên được sử dụng, những tài nguyên khác sẽ phải chờ `

## `StringTokenizer`
```java
    StringTokenizer stToken  = new StringTokenizer("Java");
```
- Cho phép phân tách một chuỗi thành các phần tử `token` của nó.
## `RegEx = Regular Expression` (Biểu thức chính quy)
- Là một tập hợp các ký tự đặc biệt để đại diện cho một tập các ký tự mong muốn

=> viết được các công thức tổng quát cho nhiều tập chuỗi có quy luật giống nhau.

VD: 
```java
    // Số điện thoại của VN có 10 chữ số, bắt đầu bằng số 0
    String sdt = "0123456789";
    System.out.println(sdt.matches("^0\\d{9}")); // Kết quả trả về là True

    String sdt = "0123456789456";
    System.out.println(sdt.matches("^0\\d{9}")); // Kết quả trả về là False

```
Tham khảo: 
1. [Regular Expression in Java](https://openplanning.net/10175/java-regular-expression)
2. [Java String](https://viettuts.vn/java-string/immutable-string-trong-java)