# `Collection - Generic`
- `Mục đích`: sinh ra để lưu trữ, thao tác với dữ liệu một cách dễ dàng, tối ưu, nhanh chóng. 
- `Java Collection hierarchy tree`:
<p align="center">
<img width = 500 src="./image/he-thong-cap-bac-colection-trong-java.png">
</p>

## `1. List`
### **`1.1 List`**
- Là một `collection có thứ tự `(đôi khi còn được gọi là một chuỗi). `List` có thể `chứa các phần tử trùng lặp`. Thường có quyền kiểm soát chính xác vị trí các phần tử được chèn vào và có thể truy cập chúng bằng chỉ số (vị trí của chúng).
- Khởi tạo list
```java
    List list1 = new ArrayList();
```
- Không giới hạn số lượng phần tử khi khởi tạo
- có thể thêm bất kỳ kiểu dữ liệu nào vào trong list
- Truy cập vào phần tử trong List
    - Thêm phần tử vào trong list: 
    ```java
    list.add(sv1);
    list.add(2.5);
    ```
    - Lấy phần tử trong list:

    *Cách 1*
    ```java
    for(int i = 0; i< list.size(); i++){
        list.get(i);
    }
    ```
    *Cách 2*
    ```java
    Interator interator = list.Interator();
    while(interator.hasNext()){ // hasNext(): kiểm tra trong list còn phần tử không
        Object obj = interator.next(); // next(): lấy phần tử ra
        System.out.println(obj);
    }
    ```
- Trong trường hợp muốn tạo ra 1 list chỉ chứa 1 kiểu dữ liệu nhất định nào đó, thì khi khởi tạo list ta cần thêm hậu tố kiểu dữ liệu vào sau class List(chính là generics).
vd:
    ```java
        List<String> lst = new ArrayList<>(); // chỉ chứa kiểu dữ liệu String
        List<Integer> lst1 = new ArrayList<>(); // chỉ chứa kiểu dữ liệu số nguyên
    ```
- Một số phương thức của List:
    - `list.add()`: thêm phần tử vào trong list.
    - `list.addAll(index, list)`: thêm phần tử vào vị trí thứ index trong List.
    - `list.contains()`: kiểm tra phần tử có trong list hay không, kiểu trả về true or false
    - `list.containsAll()`: kiểm tra nhiều phần tử.
    - `list.clear()`: xóa các phần tử trong list.
    - `list.subList(from_index, to_index)`: Cắt thành List con phần tử có chỉ mục nằm trong đoạn from_index - to_index.
    - `list.sort()`: sắp xếp phần tử

        ...
### **`1.2. Linked list`**
- Khởi tạo:
```java
    List<String> linkedLst = new LinkedList<>(); // danh sách liên kết đơn
```
- Về phương thức hầu như giống với List: add, addAll...
- Đặc điểm: Mỗi phần tử là 1 con trỏ và nó sẽ trỏ đến phần tử tiếp theo trong list, thuận lợi đối với các bài toán tìm kiếm, sắp xếp
### **`1.3 Stack: ngăn xếp`**
- Cơ chế `FILO(First In Last Out)`: vào trước ra sau
- Khởi tạo
```java
    List<String> stack = new Stack();
    Stack<String> stack1 = new Stack();
```
- Phương thức:
    - `push()`: đẩy phần tử vào stack
    - `pop()`: lấy phần tử trên đỉnh stack ra ngoài
    - `peek()`: trả về phần tử trên đỉnh stack nhưng không lấy ra
    - `Stack` cũng có những phương thức của List, `nhưng khuyến cáo không nên sử dụng vì nó sẽ phá vỡ cơ chế của Stack`
### **`1.4 Vector`**
```java
    List<SinhVien> vector = new Vector<>();
    Vector<SinhVien> vector1 = new Vector<>();
```
- Phương thức của vector chủ yếu cũng giống với List: add, remove, contains...

## `2. Set`
```java
    Set<Stirng> set1 = new HashSet<>();
    Set<Stirng> set2 = new TreeSet<>();
    Set<Stirng> set3 = new LinkedHashSet<>();
```
- Set không lưu giá trị trùng lặp trong danh sách
- `HashSet` sử dụng `thuật toán băm` để tổ chức dữ liệu, còn `TreeSet` sử dụng `thuật toán cây nhị phân` để tổ chức dữ liệu trong set.
## `3. Queue: hàng đợi`
- Là một collection được sử dụng để chứa nhiều phần tử trước khi xử lý. Bên cạnh các thao tác cơ bản của collection, Queue cung cấp các thao tác bổ sung như chèn, lấy ra và kiểm tra
- Cơ chế `FIFO(First In First Out)`: vào trước ra trước

vd về `PriorityQueue`<>: hàng đợi ưu tiên

```java
    Queue<String> stringQueue = new PriorityQueue<>();

    String peek = stringQueue.peek(); //trả về phần tử đầu của hàng đợi nhưng không lấy ra khỏi hàng đợi

    String element = stringQueue.element(); //trả về phần tử đầu của hàng đợi nhưng không lấy ra khỏi hàng đợi, nhưng nếu hàng đợi trống nó sẽ báo lỗi
```
## `4. Map: ánh xạ`
- Cơ chế từ điển dictionary: 1 cặp` Key - Value`,  `Key có kiểu dữ liệu số`, `Value kiểu dữ liệu String`.
- Là một đối tượng ánh xạ mỗi key tương úng với một giá trị. `Map không thể chứa giá trị trùng lặp`. Mỗi key có thể ánh xạ đến nhiều nhất một giá trị.
- VD 
    - Khởi tạo:
        ```java
            Map<Integer, String> map1 = new HashMap<>();

            map1.put(1, "a");// đẩy dữ liệu vào
            map1.put(3, "b");
            map1.put(4, "c");

            map1.replace(1, "10"); // thay value của key 1 thành 10
            map1.remove(3); // xóa key 3 trong map
        ```
    - `Lưu ý`: Nếu như put() hai phần tử có cùng 1 key, khác value vào trong map, thì map chỉ lưu phần tử có key được put() sau cùng( hay được hiểu là value sau sẽ ghi đè lên value trước).
        ```java
            map1.put(3, "old value");
            map1.put(3, "new value");
            ...
            // in ra
            System.out.println("key: " + key + ", value: " + value);
            // kết quả: Key: 3, value: new value
        ```

    ==> Map không bao giờ có key trùng nhau. Nếu như key là kiểu dữ liệu nguyên thủy(int, float...) thì trùng giá trị. Còn nếu kiểu đối tượng thì cần phải ghi đề hàm equals để so sánh
- `SortedMap`: là một Map chứa các phần tử được sắp xếp theo thứ tự tăng dần của key của chúng. 
## `5. Collection in collection`
```java
    List<List<String>> lst = new ArrayList<>();
```
- Có thể khởi tạo và truyền giá trị cho list
```java
    List<List<String>> lst1 = Arrays.asList(Arrays.asList("a","b","c"), Arrays.asList("1","2","3"));
```
- Có thể lồng nhiều collection với nhau, nhưng không nên sử dụng bởi vì độ xử lý sẽ rất phức tạp
## `6. Sort a collection`
1. VD **List < kiểu String>**
```java
public static void main(String[] args){
    List<String> list = new ArrayList<>();
    list.add("chung");
    list.add("anh");
    list.add("văn");
    list.add("manh");

    // cách sắp xếp 1
    Comparator<String> comparator = new Comparator<String>(){
        @Override
        public int compare(String o1, String o2){
            return o1.compareTo(o2);
        }
    };
    list.sort(comparator);
    outputList(list);

    // cách 2

    Collections.sort(list);
    outputList(list);

    public static void outputList(List list){
        for(int i = 0; i < list.size(); i++){
            System.out.println(list.get(i));
        }
    }
}

    // Kết quả sau khi sắp xếp:
            //  anh
            //  chung
            //  manh
            //  van
```
VD2. **List<Đối tượng>**
```java
    public static void main(String[] args){
    List<Student> list = new ArrayList<>();
    list.add(new Student(1, "b"));
    list.add(new Student(3, "anh"));
    list.add(new Student(5, "manh"));
    list.add(new Student(2, "viêt"));

    // cách sắp xếp 1
    Comparator<Student> comparator = new Comparator<Student>(){
        @Override
        public int compare(String o1, String o2){
            return o1.getName().compareTo(o2.getName());// so sánh theo tên
        }
    };
    list.sort(comparator);
    outputList(list);

    // cách 2

    Collections.sort(list, comparator);
    outputList(list);

    // có thể sử dụng anonymous class(lớp mạo danh cho sort) như sau:
    list.sort(new Comparator<Student>(){
        @Override
        public int compare(String o1, String o2){
            return o1.getName().compareTo(o2.getName());// so sánh theo tên
        }
    });


    public static void outputList(List list){
        for(int i = 0; i < list.size(); i++){
            System.out.println(list.get(i));
        }
    }
}
```
## `7. Generic - Tổng quát`
- Là 1 mảng hỗ trợ cho việc xử lý kiểu dữ liệu 1 cách tổng quát cho các tổng hợp(Collection) Map, Set, Queue, List.
- Các ký hiệu của generic được nằm trong dấu kim cương <>.
- Các kí hiệu của generic có thể là bất kỳ ký tự( dãy ký tự) nào, nhưng có 1 số ký tự được quy ước như sau: 

    - `raw type`: T (Type: String, Integer, Double...) , E (Element) , K (Key), V (Value), U, S, G(tùy người dùng đặt).

    - `wild card`: (?), <... extends ...>, <... super ...>

### `Generic với raw type`
- Tạo class Generic
```java
    public class Dictionary(K , V){
        private K key;
        private V value;

        public Dictionary(K key, V value){
            this.key = key;
            this.value = value;
        }

        public K getKey(){
            return key;
        }

        public void setKey(K key){
            this.key = key;
        }
        ...
    }
```
- Khởi tạo đối tượng
```java
    List list1 = new ArrayList();
    // có thể add bất kỳ kiểu dữ liệu nào trong list
    list1.add(1);
    list1.add("abc");
    list1.add(1.5);
    list1.add(new Student(1, "Nguyen Van A"));


    List<Integer> list2 = new ArrayList();
    // chỉ có thể add kiểu dữ liệu số nguyên vào trong list
    list2.add(10);
    list2.add("abc"); // lỗi vì không add được strinh
```
### `Generics với ký tự đại diện Generic method (wildcard)`
- Trong Generic, dấu chấm hỏi `(?)` được gọi là một đại diện (wildcard), nó là `kiểu không xác định`.

- Tùy vào ví trí của Wildcard mà nó sẽ có những ý nghĩa khác nhau:

    - `Collection<?>`: mô tả một tập hợp chấp nhận tất cả các loại đối số (chứa mọi kiểu đối tượng).

    - `List<? extends Number>`: mô tả một danh sách, nơi mà `các phần tử là kiểu Number hoặc kiểu con của Number.`

    - `Comparator<? super String>`: Mô tả một bộ so sánh (Comparator) mà `thông số phải là String hoặc cha của String.`