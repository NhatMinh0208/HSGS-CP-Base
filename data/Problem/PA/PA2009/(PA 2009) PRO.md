# Rectangles (PRO)
**Đề bài:**
    
Byteman có một bộ n hình vuông có cạnh 1. Anh ta có thể xếp được bao nhiêu hình chữ nhật khác nhau bằng cách sử dụng những hình vuông này?

Hai hình chữ nhật được xem là khác nhau nếu không hình nào trong số chúng có thể quay hoặc chuyển dịch để trở thành hình kia. Trong quá trình xếp hình chữ nhật, Byteman không thể làm biến dạng các hình vuông hay hay đặt bất kỳ hình vuông nào chồng lên các hình khác.

**Constraints:** $n \le 10000$

**Lời giải:**
Mỗi hình chữ nhật khác nhau có đều 2 thông số: Chiều rộng $w$ và chiều dài $l$ ($w \le l$).
Ở bài toán này chúng ta sẽ sử dụng kỹ thuật [[Brute force]]: Chúng ta sẽ duyệt qua $w$ từ $1$ đến $n$ và đếm số hình chữ nhật có chiều rộng $w$, Việc này tương đương với việc đếm số chiều dài $l$ thỏa mãn $l \ge w$ và $w*l \le n$, hay $l \le floor(n/w)$. Từ 2 dữ kiện này chúng ta dễ dàng suy ra được số $l$ thỏa mãn với mỗi $w$.

**ĐPT:** $O(n)$