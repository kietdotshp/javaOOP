# **Polymorphism** - Tính đa hình trong java oop
Tính đa hình được thể hiện như là cùng 1 phương thức, nhưng với mỗi đối tượng nó lại được thể hiện theo các cách khác nhau.
Tính đa hình được thể hiện theo các hình thức như sau:
- `Overload` - nạp chồng phương thức.
- Đa hình với `Override` - ghi đè phương thức.
- Đa hình thông qua các đối tượng.

Mọi `đối tượng (object)` đều là đối tượng (object), nên có 1 class tên là `Object` sinh ra để `đại diện cho tất cả các đối tượng chung chung`.

==> Tất cả các class đều kế thừa `class Object` mà không cần viết `extends Object`


## `Hàm equals()`
- Nếu so sánh 2 dữ liệu kiểu nguyên thủy (int, boolean, double...) thì sử dụng phép so sánh `==`
- Để so sánh 2 đối tượng bằng nhau (dữ liệu kiểu đối tượng => tham chiếu) thì sử dụng hàm `equals()`. Khi so sánh đối tượng thì phải định nghĩa ra cách so sánh riêng, như nào thì 2 đối tượng đó giống nhau, bằng cách `@Override hàm equals()` của `class Object`
    ```java
        @Override
        public boolean equals(Object obj){

        }
    ```

## `Ép kiểu - Casting`
- Ép kiểu dữ liệu của 1 đối tượng có sẵn sang 1 kiểu dữ liệu khác
 - Cứ pháp: 
    ```java
    // (<tên class cần ép kiểu> <đối tượng cần ép kiểu>)
        ConNguoi conNguoi = (ConNguoi) sinhVien; //Ép kiểu sinhVien sang conNguoi
    ```

    -> **Chỉ có thể ép kiểu lớp con sang lớp cha, chứ không ép cha về lớp con.**
    - Trước khi ép kiểu có thể `kiểm tra` xem `đối tượng sinhVien` `có phải thuộc kiểu của class ConNguoi` không bằng cách dùng `instanceof`. Nếu sinhVien là đối tượng của class ConNguoi thì sẽ trả về `true`, ngược lại trả về `false`.
## `Up-casting`


- Là việc `khai báo` đối tượng thuộc `class cha` nhưng `khởi tạo tham chiếu` đối tượng là `class con`
* **Lưu ý**: `chỉ có up-casting không có down-casting`. Tức là không có khai báo lớp con, khởi tạo lớp cha: Sinhvien sinhvien = new ConNguoi();

- `Khi up-casting:`
    
    ```java
        A obj = new B();  // với A là class cha và B là class con
        ConNguoi cn = new SinhVien();
    ```
    - Đối tượng `cn` `chỉ có thể thấy` các thuộc tính của `class ConNguoi` chứ `không thể thấy` các thuộc tính của `class con SinhVien`, tuy nhiên `object` `cn` có thể `gọi các phương thức mà class con SinhVien @Override từ class cha ConNguoi`
    ```java
    class ConNguoi {
        public void display() {
            System.out.println("Tôi là một con người");
        }
    }

    class SinhVien extends ConNguoi {
        @Override
        public void display() {
            System.out.println("Tôi là một sinh viên");
        }

        public void Hoctap() {
            System.out.println("Tôi đang học");
        }
    }

    public class Main {
        public static void main(String[] args) {
            ConNguoi cn = new SinhVien();
            cn.display(); // kết quả: Tôi là một sinh viên
            cn.Hoctap(); // lỗi vì class ConNguoi khong có hàm Hoctap()
        }
    } 
    ```
