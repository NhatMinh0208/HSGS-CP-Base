# KIE

**Đề bài:** Cho một mảng $a$ độ dài $n \leq 10^6$ ($1 \leq a_i \leq 10^3$). Tìm một dãy con có tổng lớn nhất và tổng đó chẵn. 

**Lời giải:**
- Nếu tổng tất cả các số chẵn, in tổng tất cả các số
- Nếu tổng tất cả các số lẻ thì in (tổng tất cả các số - số lẻ nhỏ nhất), trừ trường hợp mảng chỉ có duy nhất một số thì in "NO"
- Độ phức tạp: $O(n)$