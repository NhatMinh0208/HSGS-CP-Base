    
# Tables (STO)
**Đề bài:**
Thợ mộc Byteman vừa nhận được một đơn hàng đóng s chiếc bàn bằng gỗ thông. Mặc dầu có nhiều tấm gỗ thông trong xưởng, Byteman vẫn chạy ra ngoài tìm đinh vít. Bởi thế anh cần đi bộ đến nhà kho và mang về những hộp đinh. Cần tối thiêu bao nhiêu hộp đinh để đóng đủ bàn?

**Constraints:** $n,s,k,a_i \le 1000$, trong đó $k$ là số đinh cần để đóng mỗi bàn, $n$ là số hộp đinh, $a_i$ là số đinh ở hộp thứ i.

**Lời giải: **
Rất đơn giản, ở bài này chúng ta sử dụng kỹ thuật [[Greedy]]: Chúng ta liên tục lấy hộp đinh có số đinh cao nhất trong các hộp đinh chưa lấy, cho đến khi đủ $s*k$ cái đinh.