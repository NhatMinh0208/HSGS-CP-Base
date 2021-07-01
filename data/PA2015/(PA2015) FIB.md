# FIB 

**Đề bài:** Tìm số k sao cho biểu diễn thập phân của số fibonacci thứ k kết thúc bằng một chuỗi chữ số có độ dài $n \leq 18$

**Lời giải:**
- Bài toán tương đương với việc tìm k để $F_k \space mod \space 10^n$
- Liên quan tới số dư của số fibonacci -> [[Chu kỳ Pisano]]
- Chu kỳ Pisano của $10^i$ là $6*10^i$
- Số cần tìm có dạng $6*10^n*a$