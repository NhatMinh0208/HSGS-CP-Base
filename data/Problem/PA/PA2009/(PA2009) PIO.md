# Task Pawn [B]
**Đề bài** 
Cho 3 số $n\leq 10000$, $m\leq 1000000$, $p\leq 1000$. Có bảng $n\times n$ và$m$ dòng biểu diễn trên cột $w[i]$ từ $l[i]$ đến $r[i]$ được tô đen . Từ 1 ô, chúng ta có thể đi đến 1 trong 8 ô liền nó và cùng màu. Trả lời $p$ truy vấn xem có thể đi từ $x2,y2$ đến $x1,y1$.
**Lời giải**
Chúng ta có thể dùng set để biết các đoạn trắng đen liên tục trong 1 cột, rồi coi nó là đỉnh của đồ thị và [[dfs]], mỗi query chỉ cần check liệu có đi được từ đỉnh A (chứa $x1,y1$) đến đỉnh B(chứa $x2,y2$).
Complexity: $O(mlogm)$ (worst case).
