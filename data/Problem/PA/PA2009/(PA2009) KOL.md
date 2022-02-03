# Colouring (kol)
** Đề bài ** 
Một số từ 1 đến n được ghi trong từng ô của một lưới kích thước 2 x n theo cách như sau: 
mỗi số xuất hiện chính xác 2 lần trong lưới và mỗi cột có 2 số khác nhau. Ví dụ: 
$$\begin{matrix} 1 & 5 & 3 & 1 & 5 \\ 4 & 2 & 2 & 4 & 3 \end{matrix}$$ Ta muốn tô màu từng ô thành màu trắng hoặc xám theo cách sau: các ô trong cùng một cột sẽ có màu khác nhau và các ô có cùng số có màu khác nhau. Một ví dụ về cách tô màu (ô có dấu sao có màu trắng):
$$\begin{matrix} *1 & *5 & 3 & 1 & 5 \\ 4 & 2 & *2 & *4 & *3 \end{matrix}$$ 
 Có bao nhiêu cách tô màu như thế?
 ** Giới hạn** $n \le 100$
 ** Lời giải** 
 Giả sử ta tô ô (1, 1) bằng màu trắng. Như vậy ô (2, 1) cùng cột phải có màu xám. Giả sử ô (1, 4) có cùng số với ô (2, 1), ô này phải có màu trắng => ô (2, 4) phải có màu xám...
 Coi các số ghi trong bảng là đỉnh và nối cạnh giữa hai số ghi trong hai ô cùng cột, ta thu được một đồ thị gồm các cycle (do mỗi số xuất hiện ở hai ô không cùng cột, nên nó kề với hai cạnh). Nếu ta tô ô có chứa số i bằng một màu, ta cũng đã quy định màu cho tất cả các ô có đỉnh tương ứng nằm cùng cycle với i. Như vậy mỗi cycle chỉ có 2 cách tô màu.
 Vậy đáp án là $2 ^ {số cycle}$
**ĐPT**: O(n)
Link: [[Permutation]][[Graph]]