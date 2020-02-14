## Hệ cơ số 

**1. Hệ thập phân(10)** 

Hệ thập phân (hay còn gọi là hệ đếm cơ số 10) dùng 10 ký tự (0,1,2,3,4,5,6,7,8,9) để biểu đạt giá trị số.

**2. Hệ nhị phân(2)** 

Trong hệ nhị phân cơ số là 2 và chỉ có 2 chữ số 0 và 1 . Ví dụ chuỗi số nhị phân 10110 biểu diễn số :
$$
\ 2 * 2^4 + 0*2^3 + 1*2^2 +1*2^1+ 0*2^0 = 22 \,
$$

**3. Hệ thập lục phân (16)**

Các số dưới dạng nhị phân thường dài và khó trình bài , khó nhớ. Việc sử dụng hệ thập lục phân (16) gọi tắt là số hex có ưu điểm là việc chuyển đổi giữa số hex và số nhị phân tương đối dễ dàng. Hệ đếm hex là hệ đếm có cơ số bằng 16 nên các chữ số của nó là : 0 ,1 ,2 ,3 ,4 ,5 ,6 ,7 ,8 ,9 ,10 ,A ,B ,C ,D ,E và F. Vì hết các ký hiệu chữ số nên ta dùng thêm các chữ cái để biểu diễn. Các chữ cái từ A đến F tương ứng biểu diễn  các số từ 10 đến 16. Vì 16 bằng lũy thừa bậc 4 của 2 nên mỗi chữ số hex tương ứng với một số 4 bit. Điều này có nghĩa là nội dung của một byte 8 bit có thể biễu diễn ngắn gọn bằng 2 chữ số hex, chính điều này làm cho số hex trở nên tiện dụng trong máy tính. 

**

## Biểu diễn các số nguyên

-	Số nguyên không dấu (*unsigned integers*) biểu diễn các số nguyên dương. Số nguyên không dấu thích hợp biểu diễn các đại dượng luôn dương chẳng hạn địa chỉ của ô nhớ, bộ đếm hay mã ASCII của ký tự. Số nguyên không dấu lớn nhất có thể chứ trong một byte là `1111` = `FFh` = 256.
-	Số nguyên có dấu (*signed integer*) có thể là số dương hoặc số âm. Bit có trọng số cao nhất msb được dùng để biểu diễn dấu của số . msb = 1 biểu diễn số âm, msb = 0 biểu diễn số dương. Các số âm trong máy tính dưới dạng số bù 2. 
*** Chú ý :**
	-	**msb** (most significant bit) bit có trọng số lớn nhất , đó là bit nằm tận cùng bên trái. Trong một word , bit có trọng số nặng nhất là bit 15, trong 1 byte thì đó là bit 7.
	-	**lsb** (least significant bit ) bit có trọng số nhỏ nhất , nằm ở tận cùng bên phải , bit 0.
	-	**số bù 2** : trước khi xét khái niệm số bù 2, cần hiểu về số bù 1. 	
	- **số bù  1** của một số nguyên nhận được bằng cách lấy phần bù các các bit của nó, nghĩa là đảo bit, thay mỗi bit 0 thành 1 và ngược lại 1 thành 0.
		- Ví dụ : tìm số bù 1 của 5
		5 = `0000 0000 0000 0101`
		=> số bù 1 của 5 là : `1111 1111 1111 1010`.
	- số bù 2 của một số nguyên nhận được bằng cách cộng 1 vào số bù 1.
		- ví dụ : tìm số bù 2 của 5 .
	theo kết quả bên trên 
	số bù 1 của 5  là : `1111 1111 1111 1010` cộng thêm 1. 
	số bù 2 của 5 là :  `1111 1111 1111 1011`.

## Các kiểu dữ liệu

Trong một chương trình Assembly chúng ta có thẻ biểu diễn dữ liệu dưới dạng các số nhị phân, thập phân, số hex và thậm chí cả các ký tự.
 
-	Một số nhị phân được viết như là một chuỗi các bit kết thúc bằng chữ cái `B` hoặc `b`. Ví dụ `1001b`.
-	Một số thập phân là chuỗi các chữ số thập phân kết thúc bằng `D` hoặc `d`.
-	Một số hex được viết kết thúc chữ cái `h` hoặc `0x` ở đầu
các ký tự. 
-	Các ký tự và chuỗi phải được đặt trong dấu nháy đơn `''` hoặc nháy kép `""` .

	*	DB 	- định nghĩa bye
	* DQ - định nghĩa word
	 *	DD - định nghĩa từ kép 
	 *	DQ - định nghĩa 4 word
	 *	DT  - định nghĩa 10 byte 

## Little endian và Big endian

*Little endian* và *big endian* là hai phương thức khác nhau để lưu trữ dữ liệu. Sự khác biệt của little endian và big endian khi lưu trữ chính là ở việc sắp xếp thứ tự các byte dữ liệu.
-	Trong cơ chế lưu trữ little endian , byte cuối cùng trong biểu diễn nhị phân sẽ được ghi trước. 
	-	Ví dụ `0x000040e7` sẽ được viết thành `\xe7\x40\x00\x00`

Do các byte nhỏ nhất luôn nằm bên trái, điều này cho phép đọc dữ liệu với độ dài tùy ý, thích hợp cho việc ép kiểu , ví dụ từ `int` thành `long int`. Khi ép kiểu bộ nhớ không cần thay đổi, chỉ cần ghi tiếp các byte lớn hơn mà thôi.
- Đối với big endian, các dữ liệu được ghi theo thứ tự bình thường `0x000040e7` sẽ được lưu trữ theo đúng thứ tự  `\x00\x00\x40\xe7` . Đối với big endian, việc đọc dữ liệu các byte lớn nhất trước , sẽ dễ dàng kiểm tra một số âm hay dương, do byte chứa dấu được đọc đầu tiên.

## Các lệnh logic

Chúng ta có thể thay đổi từng bit trong máy tính bằng các lệnh logic. Các giá trị nhị phân 0 và 1 được xem như là các giá trị logic của các toán tử logic TRUE và FALSE một cách tương ứng.

![](https://i.imgur.com/ZNRbPEp.png)


![](https://i.imgur.com/9kIVsLk.png)

- Các lệnh **AND**, **OR**, **XOR** có cú pháp như sau : 
	- `AND đích, nguồn` 

	- `OR    đích, nguồn` 
	
	- `XOR đích, nguồn`
	 
- Kết quả của thao tác được chứa trong toán hạng đich , nó phải là một thanh ghi hay một ô nhớ. Toán hạng nguồn có thể là hằng số, thanh ghi hay ô nhớ. Tuy nhiên thao tác giữa 2 ô nhớ là *không hợp lệ*. 
- Các toán tử này ảnh hưởng tới các cờ sau :
	*-	SF, ZF , PF phản ánh kết quả của lệnh*
	*-	AF không xác định*
	*-	CF, OF = 0*

- Khi sử dụng các lệnh AND , OR và XOR chúng ta có thể thay đổi một cách có chọn lọc các bit của toán hạng địch. Để làm điều đó chúng ta tạo lên một mẫu bit được gọi là mặt nạ (MASK). Các bit của mặt nạ chọn để sao cho các bit tương ứng của toán hạng đích được thay đổi đúng như chúng ta mong muốn.
- Lệnh AND sử dụng để xóa một các bit nhất định của toán hạng đich trong khi giữ nguyên các bit còn lại 
Ví dụ : thanh ghi AL có giá trị `0011 1010`. Cần xóa 4 bit đầu về 0 , sử dụng lệnh AND với `0Fh (0000 1111)` = ` 0000 1010` .Lệnh AND sử dụng trong việc chuyển  chữ thường thành chữ hoa thay cho lệnh SUB.
- Lệnh OR dùng để thiết lập các bit xác định của toán hạng đich trong khi vẫn ngữ nguyên những bit còn lại. 
	- Ví dụ  **BL** có giá trị `0011 1010` 
			`OR BL , 0Fh     ; BL = 0000 1010`
			
- Lệnh OR có thể sử dụng kiểm tra thanh ghi có bằng 0 hay không thay cho lệnh so sánh CMP, vì nó tác động đến cờ ZF và SF . 
- Lệnh XOR dùng để đảo các bit xác định của toán hạng đích trong khi vẫn giữ nguyên những bit còn lại. Lệnh XOR sử dụng nhiều trong việc xóa một thanh ghi. 
	-	Ví dụ :
	   ` MOV AX, 0  				; chuyển 0 và thanh ghi AX`
		`XOR AX,AX`

2 câu lệnh trên là tương đương , tuy nhiên mã máy cho lệnh đầu tiên là 3 byte, lệnh sau là 2 byte, như vậy lệnh sau hiệu quả hơn.
 
- Lệnh NOT lấy số bù của toán hạng đích. Lệnh này không ảnh hưởng tới các cờ .

