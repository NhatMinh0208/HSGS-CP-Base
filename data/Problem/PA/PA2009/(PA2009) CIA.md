# Cakes [A] (cia)
**Đề bài**
Đồ thị n đỉnh m cạnh $(n\leq100000,m\leq250000)$. Mỗi đỉnh có 1 giá trị $p[i]$. Với bộ 3 đỉnh đôi một nối với nhau tạo thành tam giác, ta cộng max $p[i]$ trong 3 đỉnh vào answer. Tìm answer?

**Lời giải**
Bài này chúng ta sẽ dùng [[sqrt decomposition]], một cách làm thường thấy ở những bài cần biết quan hệ giữa 1 số đối tượng trong 1 nhóm (như graph) và rất khó để optimize từ $O(n^2)$ xuống $O(nlogn)$ hay 1 số đpt tương tự. Có thể chia thành 2 nhóm như sau
Nhóm 1: $degree(u)>\sqrt m$ 
Iterate qua tất cả các cạnh xem 2 đỉnh có nối với u không. 
Group 2: $degree(u)<\sqrt m$
Chạy qua tất cả các cặp đỉnh kề, và xem có cạnh nối chúng không.
Complexity: $O(n\sqrt n)$ 
