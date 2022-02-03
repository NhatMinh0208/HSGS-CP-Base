# Cakes [A] (cia)
**Đề bài**
Đồ thị n đỉnh m cạnh $(n\leq100000,m\leq250000)$. Mỗi đỉnh có 1 giá trị $p[i]$. Với bộ 3 đỉnh đôi một nối với nhau tạo thành tam giác, ta cộng max $p[i]$ trong 3 đỉnh vào answer. Tìm answer?

**Lời giải**
Ta có cảm giác bài này không thể tối ưu từ $n^2$ xuống $nlog$.
Ta sẽ chia các đỉnh thành 2 nhóm: 
	+ Nhóm 1: $degree(u)>\sqrt m$: Iterate qua tất cả các cạnh xem 2 đỉnh có nối với u không. 
	+ Nhóm 2: $degree(u)<\sqrt m$: Chạy qua tất cả các cặp đỉnh kề, và xem có cạnh nối chúng không.
Độ phức tạp: $O(n\sqrt n)$ 
Link: [[sqrt decomposition]]