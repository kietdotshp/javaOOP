# Abstraction - Tính trừu tượng trong java oop
## `1. Abstract class`: lớp trừu tượng
- Một class được gọi là `abstract class` khi mà nó có `từ khóa abstract` ở phía `trước class`: 
    ```java
    public abstract class SinhVien()
    ```
- Trong `abstract class` có thể `liệt kê` được các `hàm trừu tượng`. Các thành phần còn lại( thuộc tính, phương thức) hoàn toàn giống class bình thường.
- `Hàm trừu tượng( Abstract method)`: chính là hàm được định nghĩa(tên hàm, kiểu trả về, access modifier) nhưng không có phần thân( hay chính là hàm được viết trong `Interface`). Hàm trừu tượng cũng phải có `abstract` phía trước tên hàm.
    - Hàm trừu tượng : định nghĩa ra khả năng `tổng quát` 1 tập hợp các đối tượng có `chung thuộc tính` ==> để cho các lớp con kế thừa nó có thể triển khai cụ thể hàm đó.
    - Khi một `class` thông thường kế thừa 1 `abstract class`, thì nó `bắt buộc` phải `ghi đè Override` các hàm trừu tượng mà `abstract class cha` có

    
        ```java

            public abstract class Person(){
                private int id;
                private String name;

                // hàm trừu tượng
                public abstract void lamViec(){
                    // cách làm việc như nào
                }
            }
        ```
        ```java
            public class GiangVien extends Person(){

                @Override 
                public void lamViec(){
                    // cách làm việc của giảng viên
                }
            }
        ```
    - `Hàm abstract` `chỉ dùng trong abstract class`, class thường không có abstract class
    - Một abtract class kế thừa 1 abstract class nào đó thì nó không cần @Override các hàm trừu tượng của lớp cha.

- **`Lưu ý về abstract class và interface:`**
    - `Không bao giờ khởi tạo` được đối tượng 1 cách `trực tiếp` bằng `constructor` từ các `abstract class và interface`
        ```java
            Person per = new Person(); //không bao giờ được
        ```
    - Nhưng có thể `khởi tạo gián tiếp` bằng cách: 
        - Tạo ra `1 class kế thừa abstract class hoặc interface` tương ứng và khởi tạo ra đối tượng đó
        - Sử dụng anonymous class.
        ```java
            Person per1 = new GiangVien();
        ```
    ### `Phân biệt abstract class và interface`
    - `Abstract class` đại diện cho 1 tập hợp các đối tượng có chung 1 hoặc nhiều thuộc tính và phương thức thông thường, và vẫn còn những khả năng tổng quát khác.
        - `Abstract class`: đại diện cho `sự định danh`(sự nhận diện của 1 tập hợp các đối tượng): id, name, age....
    - `Interface` đại diện cho 1 tập hợp các đối tượng (có thể) không cùng thuộc tính, nhưng cùng khả năng.   
        - `Interface` đại diện cho `khả năng`( vì chỉ chứa các abstract tổng quát)

## 2. `Interface java 8`
## `Default method`
- Các `version java 8 trở xuống` thì định nghĩa `interface không đổi`( chỉ có các abstract method không có thân).
- Từ `java 8 trở đi` thì định nghĩa `interface sẽ thay đổi`, trong interface có thể chứa các phương thức có thân ==> `default method( hàm mặc định)`
    ```java
        default void demo(){
            System.out.println("Hàm có thân trong innterface")
        }
    ```
## `Functional interface`
- Một `interface` được gọi là `functional interface` khi nó `chỉ chứa 1 abstract method`( không tính `default method`).
- có 1 annomation `@FunctionalInterface` ở đầu `interface` để nhận biết.
```java
    @FunctionalInterface
    public interface HocTap(){
        void Hoc();

    }
```

## **=> Sinh ra functional interface để làm gì???**
- Mỗi `interface` chỉ nên `đại diện` cho `1 hàm chức năng` duy nhất, vì khi 1 class kế thừa interface có quá nhiều chức năng thì nó sẽ phải ghi đè hết tất cả những chức năng mà interface đó có trong khi class kia lại chỉ cần 1 hàm chức năng trong số đó thôi.
- Có 1 ưu điểm nữa là `1 class` có thể `kế thừa nhiều interface`, nên nó có thể kế thừa nhiều functional interface và vẫn đảm bảo được những chức năng mà nó mong muốn.

## 3.` Inner Class`: class nội
- Là 1 class được viết bên trong 1 class khác.
- Access modifier của class nội có thể là private, protected, public hoặc default (không bị hạn chế).
    ```java
        public class Teacher(){
            private int id;
            private String name;
            .....


            // inner class: lớp nội tại
            public class Demo{
                private String hometown;
                public void info(){
                    System.out.println("...........")
                }
            }
        }
    ```
- Để khởi tạo đối tượng của 1 inner class thì phải thông qua đối tượng của class bên ngoài của nó.
    ```java
        Teacher t1 = new Teacher();

        Teacher.Demo demo = t1.new Demo();
    ```

==> Trong thực tế ít dùng đến inner class

## 4. `Anonymous class` - lớp vô danh
- Khi khởi tạo 1 đối tượng của abstract class và interface, thì bắt buộc phải tạo ra 1 class kế thừa abstract class và interface đó, và phải ghi đè tất cả các hàm mà nó có. Class con được tạo ra đó không có tên nên được gọi là lớp vô danh - `Anonymous class`.
    ```java
            public abstract class Person(){
                private int id;
                private String name;

                // hàm trừu tượng
                public abstract void lamViec(){
                    // cách làm việc như nào
                }
            }
    ```
    ```java
        public static void main(String[] args){
            Person p1 = new Person(){
                @Override
                public void lamViec(){
                    //.......
                }
            };
        }
    ```
