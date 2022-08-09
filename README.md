# Generic trong java
## 1. Generic được hiểu như thế nào
- Về cơ bản , Generic được coi là kiểu đối tượng dùng để tham chiếu bất kỳ kiểu đối tượng nào
như Object , Integer , Double , ... hay còn gọi là Non-primitive . 
- Chúng ta sẽ có vài ví dụ dưới đây từ sử dụng Generic
```Java
public class Generic <T> {
    private T t;

    public Generic() {
    }

    public Generic(T t) {
        this.t = t;
    }

    public T getT() {
        return t;
    }

    public void setT(T t) {
        this.t = t;
    }
    
    @Override
    public String toString() {
        return "Generic{" + "t=" + t + '}';
    }
    
}
```
- T là (type parameters) đại diện cho đối tượng bạn truyền vào để lưu trữ, T là ký tự bất kỳ, bạn có thể thay thế bằng 1 từ khác ví dụ như class Queue<ItemType> {...}
- Từ đây ta có thể thấy tham số <T> được gán từ bên trên class và được khai báo kiểu dữ liệu như bình thường . Vậy , Generic sẽ giúp gì cho phía người lập trình ? 
  - Là kiểu đối tượng an toàn :Chỉ được lưu một kiểu đối lượng duy nhất và không cho phép lưu trữ 2 đối tượng có kiểu khác nhau 
  ```Java
  public static void main(String[] args) {
        Generic<String> generic1 = new Generic<>();
        generic1.setT("Kiểu String");
        Generic<Double> generic2 = new Generic<>();
        generic2.setT(5.5);
        System.out.println(generic1);
        System.out.println(generic2);
    }
  ```
- Ta sẽ lấy luôn class Generic đã tạo và thử tạo đối tượng , Lúc này Generic sẽ trả cho ta kết quả như sau : 
  ```Java
      Generic{t=Kiểu String}
      Generic{t=5.5}
  ```
  - Khi chúng ta sử dụng ArrayList mà không có kiểu cố định , chúng ta cần phải ép kiểu để lấy giá trị . Tuy nhiên sau Generic , chúng ta không cần phải ép kiểu đối tượng .
- Điều đó đã chứng minh được là Generic được coi là kiểu dữ liệu đa đối tượng . Tuy nhiên , có vài điều thú vị mà có thể các bạn chưa biết , sang phần tiếp theo để tìm hiểu nhé . 
## Vài điều thú vị về Generic
- Các bạn nhìn qua có thể nó sẽ lạ lẫm . Tuy nhiên khi bước vào lập trình từ Java 1 , các bạn đã sử dụng nó thường xuyên ! Đó chính là bởi vì ArrayList, LinkedList, HashSet, TreeSet, HashMap, Comparator, vv đều là Generic . 
- Generic có thể giới hạn kiểu dữ liệu 
  - Nếu class Generic <T extends String> thì chỉ các kiểu dữ liệu String được sử dụng , chẳng phải nó sẽ giới hạn kiểu dữ liệu , tối ưu hoá hơn sao ? 
