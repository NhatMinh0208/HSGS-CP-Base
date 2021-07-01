# MIS

**Đề bài:** Cho một đồ thị $n$ đỉnh $m$ cạnh ($n, \space m \leq 2*10^5$). Tìm tập đỉnh lớn nhất sao cho mỗi đỉnh trong tập nối với ít nhất $d < n$ đỉnh khác trong tập. Nếu tồn tại đáp án, in ra các đỉnh, nếu không tồn tại thì in ra "NO". 

**Lời giải:**
- Thay vì đi tìm các đỉnh của tập, ta sẽ loại bỏ các đỉnh chắc chắn không thuộc tập. Đây là một hướng quen thuộc trong các bài yêu cầu [[Tìm một tập đỉnh]]
- Dưới góc nhìn đó, bài toán trở nên đơn giản. Chừng nào còn một đỉnh của đồ thị có bậc nhỏ hơn $d$, ta xóa nó ra khỏi đồ thị. Thao tác này có thể duy trì bằng một cái set. 
- Độ phức tạp: $O(n log n)$