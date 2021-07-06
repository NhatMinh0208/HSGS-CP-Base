# KNIGHT(K,N) (KNS)
**Đề bài:**
    
Cờ Bytean là một loại cờ khác thường nhất thế giới. Mỗi ván chơi là một khó khăn lớn vì trò chơi này được chơi trên một bàn cờ vô hạn. Những kỳ thủ trẻ tuổi đam mê cờ Bytean đang học hỏi một kỹ năng cơ bản là xem xét tất cả các vị trí có thể trên bàn cờ sau hàng triệu nước đi. Để làm được điều đó, họ cần biết liệu một quân cờ có thể đi từ một ô vuông này sang một ô vuông khác được không. Quân mạnh nhất trong cờ Bytean là quân mã (K, N). Nước đi của nó tương tự với nước đi của quân mã trong cờ vua truyền thống. Mỗi nước đi của nó bao gồm: có thể đi K ô theo chiều dọc và sau đó đi N ô theo chiều ngang 2 hoặc đi N ô theo chiều dọc và sau đó đi K ô theo chiều ngang. Quân mã trong cờ vua truyền thống do đó có thể được xem như quân mã (2, 1) hoặc quân mã (1, 2). Nhiệm vụ là có hai ô cho trước trên bàn cờ, xác định xem liệu một quân mã (K, N) có thể đi từ ô đầu tiên đến ô thứ hai không (số lượng nước đi không quan trọng).

**Constraints:** $$ T \le 2e4, 0 \le K, N \le 1e9, K + N > 0, -1e9 \le x_1, y_1, x_2, y_2 \le 1e9$$ trong đó T là số test. K và N là những nước đi khả thi của quân mã. Quân mã bắt đầu đi từ ô (x1, y1). Đích tới là ô (x2, y2).

**Lời giải:**
- Trình tự đi các bước không quan trọng, một tập bước chỉ dẫn đến một vị trí duy nhất. 
- Gọi các nước đi $$(n, k), (-n, k), (n, -k), (-n, -k), (k, n), (-k, n), (-n, k), (-n, -k)$$ là nước đi đơn. Xét tập S gồm các nước đi đơn. 
-  $$(n, k) + (-n, k) = (0, 2k)$$ Tương tự ta có thể tạo được các nước đi $$(2n, 0), (-2n, 0), (0, 2n), (0, -2n), (2k, 0), (-2k, 0), (0, 2k), (0, -2k)$$ Gọi các nước đi này là nước đi đôi.
-   $$ (n, k) + (n, k) = (2n, 2k) = (2n, 0) + (0, 2k)$$Chừng nào còn hai nước đi đơn giống nhau trong S ta thay chúng bằng hai nước đi đôi như trên. Sau khi hoàn thành mỗi nước đi đơn chỉ xuất hiện tối đa một lần.
-  Từ các nước đi đôi có thể tạo được các nước đi có dạng $(2an + 2bk, 2cn + 2dk)$ với $a, b, c, d \in Z$.
- Với hai số nguyên $x, y$ thỏa mãn $gcd(x, y) \ne 0$ có 
			$$\{c \in Z | c = ax + by với a, b \in Z\} = \{k * gcd(x, y) với k \in Z\}$$ 
	(xem [[Diophantine equation]] để biết thêm). 
- Như vậy từ các nước đi đôi có thể tạo được các nước đi có dạng $(a * gcd(2n, 2k), b * gcd(2n, 2k))$ với $a, b \in Z$.
- Vì mỗi nước đi đơn xuất hiện tối ta chỉ cần thử tất cả các [[Bitmask]] thể hiện số lần xuất hiện của các nước đi đơn. Nếu sau khi cộng các nước đi đơn vào $(x_1, y_1)$ , $x_2 - x_1$ và $y_2 - y_1$ đều chia hết cho $(2n, 2k)$, ta in ra "YES".
**Độ phức tạp**: $T * (2^8 + log2(1e9))$