# HAZ 

**Đề bài:** n con bò chơi casino lần lượt, mỗi con có một lượng tiền nào đó. Sau lượt chơi của một con bò thì nó về cuối hàng. Mỗi lần chơi một con bò sẽ đánh cược bằng 1 đồng, nếu thắng được 2 đồng, nếu thua không được đồng nào. Tuy vậy bác John đã xác định trước kết quả của trò casino: cứ sau M lần chơi, kết quả lại lặp lại. Tìm thời điểm đầu tiên có một con bò hết tiền ? ($n,m \leq 10^6$)

**Lời giải:** 
- Để ý rằng các kết quả chơi của con bò thứ i: $s[i % m], s[(i + n) % m]$, s[(i + 2 * n) % m],...$ tạo thành một cycle. 
- Ta chỉ cần loop qua từng cycle và tính cho mỗi con bò: 
	+ Nếu trong vòng thứ nhất mà bò có thể hết tiền -> tìm thời điểm nhỏ nhất = RMQ
	+ Nếu không: 
		1. Nếu tổng lượng tiền sau vòng nhứ nhất > 0 -> Con bò không bao giờ hết tiền
		2. Nếu < 0 -> Đi qua một lượng cycle rồi làm RMQ như trường hợp đầu.

**Notes:**
- Có $gcd(n, m)$ cycles -> phát triển thêm ?
- Một bài đơn giản trong lớp các bài về [[Function graph]]