# 1. `Java` là một `ngôn ngữ lập trình   hướng đối tượng` (Object-Oriented Programing Language)

## Phân biệt lập trình hướng thủ tục & hướng đối tượng
- **Hướng thủ tục (procedure program)**: Giải quyết bài toán được chia theo từng thủ tục nhỏ, mỗi thủ tục giải quyết 1 công việc nhỏ và danh sách các thủ tục theo thứ tự sẽ giải quyết được bài toán.

- **Hướng đối tượng (OOP)**: giải quyết bài toán xung quanh các đối tượng, mỗi đối tượng có đặc tính và khả năng riêng biệt đại diện cho 1 tập hợp đối tượng nào đó,
đảm bảo đủ 4 tính chất: đóng gói, kế thừa, đa hình, trừu tượng.

# 2. `Class` và `Object` trong java

- **Class (lớp)** là một khái niệm sinh ra để đại diện cho 1 tập hợp các đối tượng có cùng đặc tính (thuộc tính) và khả năng (phương thức).
Ví dụ: sinh viên A là 1 đối tượng của sinh viên

- Liệt kê thuộc tính trong class:
```java
    // <acccess modifier> <data type> <tên thuộc tính>;

    public String hoTen;

    private int diem;
```

- Tạo ra đối tượng từ 1 class: 
```java
    // <tên class> <tên đối tượng> = new <tên class>();

   Sinhvien sv = new Sinhvien();
```


Việc sử dụng từ khóa `new` khi tạo ra 1 đối tượng từ 1 class đã biết chính là việc gọi tới `constructor` của class đó.

- `Constructor` là 1 phương thức để tạo ra đối tượng, `mỗi class` sẽ có 1 `constructor mặc định` (constructor khởi tạo không tham số). Bình thường nó sẽ bị ẩn đi.
- **Cấu trúc**:
```java
    public <tên class>() {

    }

    public Sinhvien() {

    }
```
- *Lưu ý:*

    - Constructor không có kiểu trả về.

    - Nếu như **không có hàm tạo** => **Không tạo ra được bất kỳ đối tượng nào**

## 3 Toán tử `.` 
- Dùng để truy cập tới những thuộc tính, phương thức nhỏ hơn bên trong class mà đối tượng ấy thuộc về, có thể lấy ra hoặc gán giá trị cho thuộc tính của đối tượng

    => Gán giá trị cho thuộc tính của đối tượng ==> xác định rõ đối tượng có thông tin chi tiết như thế nào.

```java
    Sinhvien sv = new Sinhvien();

    sv.name = "Nguyen A";
    
    sv.age = 20;
```

        -> Gán giá trị cho thuộc tính phải đúng theo kiểu dữ liệu mà thuộc tính được khai báo trong class

- Khi 1 `đối tượng hay biến` `được khai báo nhưng chưa được khởi tạo` thì nó sẽ có giá trị là `NULL`. 
```java
    `int b; -> b = NULL`
```
## 4. Pass of value & pass of reference - Tham trị & tham chiếu
Chia làm 2 loại kiểu dữ liệu trong Java:
- Kiểu dữ liệu nguyên thủy: int, long, float...

    ==> tham trị
- Kiểu dữ liệu đối tượng: String, Person... => vô hạn kiểu tùy thuộc vào cách chúng ta khai báo đặt tên cho class

    ==> tham chiếu. kiểu dữ liệu đối tượng - con trỏ - thì mới thực hiện được tham chiếu

### Phân biệt `tham trị (pass by value)` và `tham chiếu (pass of reference)`

- Khi ta `truyền vào` hàm 1 kiểu `dữ liệu nguyên thủy`, và trong hàm thực hiện thay đổi giá trị của dữ liệu đó thì ở ngoài hàm, `giá trị truyền vào không bị thay đổi khi kết thúc gọi hàm.`
- Khi ta `truyền vào` hàm 1 kiểu `dữ liệu đối tượng`, và trong hàm thực hiện thay đổi giá trị của dữ liệu đó thì ở ngoài hàm, `giá trị truyền vào bị thay đổi khi kết thúc gọi hàm.`



   ```java
    // tham trị (pass of value)
    public static void tangGiaTri(int x) {
        x += 1;
    }

    // tham chiếu (pass of reference)
    public static void tangGiaTri(Person person) {
        person.age += 1;
    }

    public static void main(String[] args) {
        Person p1 = new Person();
        Person p2 = new Person();

        int a = 5;
        tangGiaTri(a); // truyền vào kiểu nguyên thủy
        System.out.println(a); // kết quả  = 5

        p1.age = 20;
        tangGiaTri(p1); truyền vào kiểu đối tượng
        System.out.println(p1.age); // kết quả = 21
    }
    
    p2 = p1; // p2 trỏ tới ô nhớ của p1, lúc này dữ liệu p1, p2 giống nhau
    ```

## 5. Từ khóa `This`

- Từ khóa `this` sinh ra để truy cập vào các `thuộc tính` và `phương thức` của class đó mà `không gây nhầm lẫn` với các class khác hoặc tham số truyền vào.

    ```java
    public void ganTuoi(int age) {
        this.age = age; // this.age: truy cập vào thuộc tính age, age bên phải là tham số truyền vào
    }

## 6. Từ khóa `Static`

- `Static` là 1 từ khóa trong java, nó xuất hiện ở các ví trí sau:
    
    ### 6.1. Trước 1 hằng số, thuộc tính dùng chung cho tất cả các đối tượng được tạo ra

    
    ```java 
    static int id;
    static String name;
    String level;
    public static final String TIEN_SI = "Tiến Sĩ";
    ```
    Bình thường muốn truy cập vào thuộc tính của 1 class phải thông qua đối tượng. 
    ```java
        Person p1 = new Person();
        p1.name = "Nguyễn Văn A";
    ```
    Nhưng khi có từ khóa static trước thuộc tính thì class cũng được phép truy cập vào thuộc tính đó. 

    ```java 
        Person.name = "ABC"
    ```
    ### 6.2. Trước 1 phương thức (hàm)
    ```java
    static String name;
    String level;
    public static void main(String[] args) {
        int a = nhapSo(); // lỗi gọi hàm thường
        System.out.println(name);
        System.out.println(level); // lỗi thuộc tính thường
    }

    public int nhapSo() {
        int a = new Scanner(System.in).nextInt();
        return a;
    }
    ```

    **Những phương thức có static chỉ có thể gọi đến hàm, thuộc tính static, không thể gọi đến hàm & thuộc tính thường. Ngược lại thì hàm thường vẫn có thể gọi hàm static.**

    ### 6.3. Đoạn code static
    ```java
    static {
        // code như java bình thường trong phần thân này
        int a = 5;
        int b = 6;
        System.out.println("Tổng của 2 số " + a + " và " + b + " là: " + (a+b));
    }
    ```
    - `Đoạn code static chỉ được gọi 1 lần duy nhất khi khởi tạo đối tượng của class lần đầu tiên và nó được gọi trước constructor`
## 7. Từ khóa `final`
- Viết trước kiểu dữ liệu, và cho biết đây là `hằng số` (`giá trị không thể thay đổi`)

    ```java
    final double pi = 3.14
    ```

- Khai báo hằng số của 1 class nào đó:

    `<access modifier> static final <kiểu dữ liệu> <tên hằng số> = <giá trị của hằng số>;`

## 8. Enum

- Là 1 nơi để lưu trữ các hằng số
- Hằng số khai báo trong `class`:

```java
    public static final String TIEN_SI = "Tiến Sĩ";
    public static final String THAC_SI = "Thạc Sĩ";
    public static final String GIAO_SU = "Giáo sư";
```
- Hằng số trong `Enum`:
```java
    public enum TrinhDoHocVan {
        THAC_SI("Thạc sĩ");
        TIEN_SI("Tiến sĩ");
        GIAO_SU("Giáo sư");

        public String giaTri;
        TrinhDoHocVan(String giaTri) {
            this.giaTri = giaTri;
        }
    }
```
- Gọi hằng số: 
```java
    gv.level = TrinhDoHocVan.THAC_SI.giaTri;
```