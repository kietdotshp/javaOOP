 # Java IO - Java Input/Output
 - Mục đích: thực hiện những thao tác với tệp và thư mục trong máy tính

 Phân loại tệp file.
 1.  `Văn bản(text)`: hiểu nôm na là những file khi mở bằng notepad mà con người khi nhìn vào có thể đọc và hiểu được.

 2. `Nhị phân(binary)`: là những file khi mở bằng notepad mà nhìn vào không thể hiểu được nội dung.

 Cách đọc ghi của 2 loại `file text` và `file binary`.
 - `Text I/O:` nó sẽ trải qua quá trình encoding/decoding. Nó sẽ chuyển ngôn ngữ mà con người có thể đọc được bằng `encoding` Unicode rồi lưu vào máy tính: `ký tự -> unicode -> binary` lưu vào máy tính. Quá trình `decode`: `binary -> unicode -> ký tự` 
-` Binary`: không có quá trình encoding/decoding, nó lưu luôn vào máy tính

=> Tốc độ đọc/ghi file của file text sẽ mất thời gian hơn so với file binary

## I. Đọc ghi file text
`Java I/O hierarchy tree`
<p align = "center">
<img width = 500 src = "./image/IO_InputOutputReadersWriters.png">
</p>

### `1. Reader file text`

**1.1 InputSreamReader**
- Lớp `InputStreamReader` của gói java.io có thể được sử dụng để chuyển đổi dữ liệu theo byte vào dữ liệu trong ký tự.
- Tạo 1 InputSreamReader
    ```java
        // Creates an InputStream
        FileInputStream file = new FileInputStream(String path);//path đường dẫn đến file cần đọc

        // Creates an InputStreamReader
        InputStreamReader input = new InputStreamReader(file);
        // hoặc có thể viết ngắn gọn lại bằng cách sau:
        InputStreamReader input = new InputStreamReader(new FileInputSream(String path));
    ```
- Các phương thức của InputStreamReader
    - read(): đọc 1 ký tự từ trình đọc, kết quả trả về là ký tự dạng ASCII. Nếu muốn trả về ký tự người dùng thì có thể sử dụng ép kiểu:
    ```java
        data = input.read(); // ví dụ đọc được ký tự 1
        System.out.print(data); // kết quả trả về là 49
        System.out.print((char)data); // kết quả trả về là 1
    ```
    - close(): input.close() - đóng trình đọc file
    - ready(): kiểm tra luồng đã sẵn sàng được đọc chưa

        ....

**1.2 BufferedReader**
- Lớp BufferedReader trong java được sử dụng để đọc văn bản từ một input stream dựa trên các ký tự (character stream). Nó có thể được sử dụng để đọc dữ liệu theo dòng (line by line) bằng phương thức readLine().
- Tạo BufferedReader
```java
    // Creates an InputStream
    FileReader file = new FileReader(String path);//path đường dẫn đến file cần đọc

    // Creates an InputStreamReader
    BufferedReader input = new BufferedReader(file);
    // hoặc có thể viết ngắn gọn lại bằng cách sau:
    BufferedReader bufRead = new BufferedReader(new FileReader(String path));

```

- Phương thức:
    - readline(): bufRead.readline() - đọc theo dòng.
    - close(): bufRead.close() - đóng trình đọc file

**1.3 FileReader**
- Lớp FileReader trong java được sử dụng để đọc dữ liệu từ file.
- Khởi tạo: 
```java
    FileReader fr = new FileReader(String path);
```
- Phương thức chính:
    - read(): được sử dụng để trả về một ký tự 
    - close(): được sử dụng để đóng trình đọc file

**1.4 CharArrayReader**
- Dùng để đọc mảng ký tự
```java
 char[] arr = {'a', 'b', 'c'};
 CharArrayReader reader = new CharArrayReader(arr);

 // đọc ký tự
 reader.read();
```
### `2. Writer file text`
**2.1 OutputStreamWriter**
- Dùng để ghi dữ liệu vào file
- Khởi tạo:
```java
    OutputStreamWriter outWriter = new OutputStreamWriter(new FileOutputStream(String path)) // String path là tên file muốn ghi dữ liệu vào
    // sử dụng write() để ghi dữ liệu
    outWriter.write("nội dung muốn ghi"); 
    
    outWrite.flush(); // đẩy dữ liệu vào file

    outWrite.close(); // đóng file
```
`Lưu ý`: Nếu như dùng câu lệnh khởi tạo như trên, thì mỗi lần dữ liệu được ghi vào file nó sẽ ghi đè lên những dữ liệu cũ( nói cách khác là những dữ liệu trước đó có trong file sẽ bị mất). Vì vậy, nếu muốn ghi thêm dữ liệu vào trong file mà không ghi đè lên dữ liệu cũ thì khi khởi tạo chúng ta làm như sau:
```java
    OutputStreamWriter outWriter = new OutputStreamWriter(new FileOutputStream(String path, true))
    // tham số true là đại diện cho tham số append(được hiểu là ghi thêm dữ liệu)
```
**2.2 BufferedWriter**
```java
    private static void demoBufferefWriter(){
        BufferedWriter buffWriter = null;
        try{
            buffWriter = new BufferedWriter(new FileWriter("demo.txt", true));
            buffWriter.write("Lập trình Java!!!");
            buffWrite.nextLine();
        } catch(IOException e){
            e.printStackTrace();
        } finally{
            try{
                if (buffWriter != null){
                    buffWriter.close();
            } catch(IOException e){
                e.printStackTrace();
            }
            }
        }
    }
```
## II. Đọc ghi file binarry
Cách để ghi nhớ những class dùng để đọc/ghi file text thường có đuôi `er` như BufferedReader/writer. Còn những class dùng để đọc/ghi file nhị phân thì thường có đuôi `stream` như FileInputStream/ FileOutputStream...
<p align = "center">
<img width = 500 src = "./image/IO-file-binary.png">
</p>

### **1. ObjectInputStream**

- Lớp `ObjectInputStream` trong java được sử dụng để đọc các đối tượng và dữ liệu nguyên thủy mà được ghi bằng việc sử dụng lớp `ObjectOutputStream`.

    VD:
    - Tạo lớp Student: 
        ```java
        import java.io.Serializable;
        
        public class Student implements Serializable {   
            private int id;
            private String name;
            private String address;
            private int age;
        
            public void Studet() {}
            
            public Student(int id, String name, String address, int age) {
                super();
                this.id = id;
                this.name = name;
                this.address = address;
                this.age = age;
            }
        
            public int getId() {
                return id;
            }
            public void setId(int id) {
                this.id = id;
            }
            public String getName() {
                return name;
            }
            public void setName(String name) {
                this.name = name;
            }
            public String getAddress() {
                return address;
            }
            public void setAddress(String address) {
                this.address = address;
            }
            public int getAge() {
                return age;
            }
            public void setAge(int age) {
                this.age = age;
            }
            public String toString() {
                return "Student@[id=" + id + " , name=" + name + ", "
                        + "address= " + address + ",age =" + age+ "]";
            }
        }
        ```
    - Tạo class demoObjectInputStream
    ```java
        import java.io.FileInputStream;
        import java.io.IOException;
        import java.io.ObjectInputStream;
        
        public class demoObjectInputStream {
            public static void main(String[] args) {
                demoObjectInputStream();
            }
            private static void demoObjectInputStream(){
                ObjectInputStream ois = null;
        
                try {
                    ois = new ObjectInputStream(new FileInputStream("sinvien.txt"));
                    // read student
                    Student student = (Student) ois.readObject();
                    // show student
                    System.out.println(student.toString());
                } catch (ClassNotFoundException ex) {
                    ex.printStackTrace();
                } catch (IOException ex) {
                    ex.printStackTrace();
                } finally {
                    try{
                        if(ois != null){
                            ois.close();
                        }
                    }catch(IOException ex){
                        ex.printStackTrace();
                    }
                }
            }
        }
    ```

### **2. ObjectOutputStream**

- Lớp `ObjectOutputStream` trong java được sử dụng để ghi các kiểu dữ liệu nguyên thuỷ và các đối tượng Java vào một OutputStream. Chỉ có các đối tượng `implements` giao tiếp `java.io.Serializable` mới có thể được ghi vào stream.
    VD:
    - Tạo class Student(giống phần ObjectInputStream)
    - Tạo class demoObjectOutputStream
        ```java
        import java.io.FileOutputStream;
        import java.io.IOException;
        import java.io.ObjectOutputStream;
        
        public class ObjectOutputStreamExample {
            public static void main(String[] args) throws IOException {
                
            }
            private static void demoObjectOutputStream(){
                ObjectOutputStream oos = null;
                try {
                    oos = new ObjectOutputStream(new FileOutputStream("sinhvien.txt"));
                    // create student
                    Student student = new Student(1, "Nguyễn Văn A", "Ha Noi", 17);
                    // write student
                    oos.writeObject(student);
                    oos.flush();
                    System.out.println("Success...");
                } catch (IOException ex) {
                    ex.printStackTrace();
                } finally {
                    try{
                        if(oos != null){
                            oos.close();
                        }
                    }catch(IOException ex){
                        ex.printStackTrace();
                    }
                }
            }
        }
        ```
## **III. Try with resource**
Vd về `try with resource`
```java
    private static void demoObjectInputStream(){
        try(ObjectInputStream ois = new ObjectInputStream(new FileInputStream("sinvien.txt"))) {
            // read student
            Student student = (Student) ois.readObject();
            // show student
            System.out.println(student.toString());
        } catch (ClassNotFoundException ex) {
            ex.printStackTrace();
        } catch (IOException ex) {
            ex.printStackTrace();
        }
    }
```
- `Điều kiện sử dụng try with resource`: là phải thao tác với 1 resource( tài nguyên), và là 1 tài nguyên phải đáp ứng 2 điều kiện:
    - Class đang sử dụng phải kế thừa class AutoCloseable
    - Tài nguyên đang sử dụng phải là tài nguyên trên hệ thống: vd như file, ram...
- Khi dùng `try with resource` không cần phải sử dụng `finally` để đóng mà resource nó sẽ tự động được đóng khi hoàn thiện các thao tác
### **IV. Đường dẫn**
- Đường dẫn tương đối: vd: ./image/exception.png
- Đường dẫn tuyệt đối: chỉ rõ đường dẫn đến 1 file. vd: E:\ITSOL\Java\java-se-tutorial\image\exception.png