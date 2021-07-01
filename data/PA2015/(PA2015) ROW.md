# ROW

**Đề bài:** Cho số nguyên dương $n$, gọi $f(n)$ là tổng bình phương các chữ số của $n$ trong hệ thập phân. Cho ba số nguyên $k, a, b \leq 10^{18}$. Tìm số lượng số $n$ thỏa mãn $a \leq n \leq b$ và $k * f(n) = n$.   

**Lời giải**
- Duyệt qua mọi giá trị của $f(n) \leq 81 * 18$ rồi check xem có thỏa mãn không
- Độ phức tạp: $O(max(f(n))$

**Notes**
- Bài này chẳng có gì ngoài việc [[Để ý những giá trị nhỏ]]