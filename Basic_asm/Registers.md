


## ** THANH GHI (REGISTERS)**

Hoạt động bộ xử lý chủ yếu liên quan đến xử lý dữ liệu. Dữ liệu này có thể được lưu trữ trong bộ nhớ và được truy cập từ đó. Tuy nhiên , việc  lưu trữ dữ liệu hay đọc dữ liệu từ bộ nhớ sẽ làm chậm bộ  xử lý. Các vùng lưu trữ nhỏ được tích hợp sẵn trong bộ xử lý được gọi là các thanh ghi, giúp cải thiện tốc độ của bộ xử lý 

Các thanh ghi được chia thành 3 loại : 
-	Thanh ghi dùng chung 
-	Thanh ghi cờ
-	Thanh ghi đoạn

## I. Thanh ghi chung

 Bao gồm *thanh ghi dữ liệu*, *thanh ghi con trỏ*  và *thanh ghi chỉ số* 

**1.  Thanh ghi dữ liệu**

Có 4  thanh ghi dữ liệu 32 bit được sử dụng cho các phép toán số học, logic ..

![](https://i.imgur.com/cphKrha.png)

**_EAX (thanh ghi chứa – accumulator)_**_: được sử dụng nhiều nhất trong các lệnh số học, logic, và chuyển dữ liệu. Các thao tác nhân, chia sử dụng thanh ghi này._ _Với các hàm API của Windows, kết quả trả về của hàm thường sẽ lưu vào thanh ghi EAX__._

**_EBX (thanh ghi cơ sở – base)_**_: thanh ghi EBX có thể truy cập trực tiếp dữ liệu bộ nhớ và nó cũng là một thanh ghi dùng chung._

**_ECX (thanh ghi đếm – count)_**_: ECX là một thanh ghi dùng chung có thể được sử dụng như là một bộ đếm cho các lệnh khác nhau. Nó cũng có thể chứa địa chỉ lệch của dữ liệu trong bộ nhớ. Các lệnh sử dụng bộ đếm là các lệnh liên quan lặp chuỗi, các lệnh chuyển, xoay và LOOP / LOOPD._

**_EDX (thanh ghi dữ liệu – data)_**_: là một thanh ghi dùng chung dùng để chứa một phần kết quả của phép nhân hoặc một phần của phép chia. Nó cũng có thể truy cập địa chỉ dữ liệu trong bộ nhớ trực tiếp._

![](https://i.imgur.com/CT7FGNe.png)

Ngoài ra 4 thanh ghi còn có thể chia nhỏ thành các thanh ghi 16-bit và 8 bit
Các byte cao và thấp trong thanh ghi có thể truy cập riêng biệt. Byte cao của thanh ghi AX gọi là AH, byte thấp gọi là AL. Tương tự như vậy đối với các byte cao và byte thấp của các thanh ghi BX, CX,DX.

**2. Thanh ghi con trỏ**

Các thanh ghi con trỏ là các thanh ghi EIP, ESP và EBP 32 bit và  16 bit phía bên phải  tương ứng *IP*, *SP* và *BP*. Có ba loại thanh ghi con trỏ -

-   **Con trỏ lệnh (IP)** - Thanh ghi IP 16 bit lưu địa chỉ offset của lệnh tiếp theo sẽ được thực thi. IP kết hợp với thanh ghi CS (dưới dạng CS: IP) cung cấp địa chỉ đầy đủ của lệnh hiện tại trong đoạn mã.
    
-   **Con trỏ ngăn xếp (SP)** - Thanh ghi SP 16 bit cung cấp giá trị offset trong ngăn xếp chương trình. SP kết hợp với thanh ghi SS (SS: SP) là vị trí hiện tại của dữ liệu hoặc địa chỉ trong ngăn xếp chương trình.
    
-   **Con trỏ cơ sở  (BP)** - Thanh ghi BP 16 bit chủ yếu giúp tham chiếu các biến tham số được truyền cho chương trình con. Địa chỉ trong thanh ghi SS được kết hợp với offset trong BP để lấy vị trí của tham số. BP cũng có thể được kết hợp với DI và SI làm thanh ghi cơ sở cho địa chỉ đặc biệt.

  **3. Thanh ghi chỉ số**

Các thanh ghi chỉ số 32 bit, ESI và EDI và các phần 16 bit bên phải tương ứng là  SI và DI.

-   **Chỉ số nguồn (SI - Source Index)** được sử dụng để trỏ tới các ô nhớ trong đoạn dữ liệu được định địa chỉ bởi thanh ghi DS. Bằng cách tăng nội dung của SI, chúng ta có thể truy nhập dễ dàng đến các ô nhớ liên tiếp 
    
-   **Chỉ số đích (DI-Destination Index)** - thực hiện chức năng tương tự như thanh ghi SI. Có một số lệnh gọi là các thao tác chuỗi sử dụng DI để truy cập đến các ô nhớ được định địa chỉ bởi đoạn ES

## II.  Thanh ghi cờ

Mục đích của thanh ghi cờ là chỉ ra các trạng thái của bộ vi xử lý.  Để có thể làm được điều đó nó thiết lập các bit riêng biệt gọi là các cờ (flags). Có hai loại cờ : 
- Cờ trang thái (status flags) 
- Cờ điều khiển (control flags )

![](https://i.imgur.com/eqVewPk.png)

**Cờ trạng thái** phản ánh kết quả của một lệnh mà bộ xử lý thực hiện nó nằm ở các bit 0 (CF), 2 (PF) ,4 (AF) ,6 (ZF) , 7 (SF) và 11(OF) 

**Cờ điều khiển** cho phép hoặc không cho phép một thao tác nào đó của bộ xử lý. Cờ điều khiển nằm ở các bit 8 (TF) , 9 (IF) , 10 (DF). các bit khác *không có ý nghĩa.* 

-   **Cờ nhớ (carry flag - CF) được thiết lập 1 khi có nhớ từ bit msb trong phép cộng hay có vay vào bit msb trong phép trừ . Ngược lại nó bằng 0. Cờ CF bị ảnh hưởng bởi phép dịch và quay.
-   **Cờ chẵn lẻ (PF)** - Cờ CF thiết lập 1 nếu byte thấp của kết quả có số chẵn các bit 1. Nó bằng 0 nếu byte thấp có lẻ bit 1. Ví dụ `FFFFh`, byte thấp có 7 bit 1 nên PF = 0 
-    **Cờ nhớ phụ  (AF)** - Cờ AF được thiết lập nếu có nhớ từ bit 3 trong phép cộng hoặc vay vào bit 3 trong phép trừ. 
- **Cờ zero (ZF)** - được thiết lập 1 khi kết quả bằng 0 và ngược lại
 *Đây là cờ phổ biến nhất sử dụng trong reversing. Chủ yếu được sử dụng tỏng các lệnh rẽ nhánh có điều kiện, làm thay đổi luồng thực thi của chương trình* 
    
-   **Cờ dấu (SF)** - được thiết lập 1 khi bit msb của kết quả bằng 1 có nghĩa là kết quả làm âm nếu làm việc với số có dấu. Ngược lại SF = 0 nếu bit msb của kết quả bằng 0

-   **Cờ tràn (OF)** - được thiết lập 1 khi xảy ra tràn ngược lại nó bằng 0
-  **Hiện tượng tràn**  :  Phạm vi các số được biểu diễn trong máy tính có giới hạn. Ví dụ phạm vi của các số thập phân có dấu có thể biểu diễn bằng word 16 bit là từ `-32678` đến `32767`. Đối với các số không dấu thì phạm vi là từ `0` đến `65535`. Nếu kết quả của một phép tính nằm ngoài phạm vi này thì hiện tượng tràn xảy ra và kết quả nhận được  bị cắt bớt sẽ không phải là kết quả đúng 



