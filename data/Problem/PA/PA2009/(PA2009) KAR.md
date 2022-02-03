# Cards [B] (kar)
** Đề bài**
Cho $r$ lá bài đỏ, $b$ lá bài đen, số nguyên $k$ và số nguyên tố $p$. Tìm số cách xếp $r + b$ lá bài vào một dãy **không** thỏa mãn điều kiện sau modulo : 
	- Mỗi dãy lá bài đen liên tiếp đứng ngay sau một dãy lá bài đỏ dài gấp $k$ lần nó. 
VD: $r = 4, b =2, k = 1, p = 1e9$. Đáp án là 6 (BBRRRR, BRBRRR, BRRBRR, BRRRBR, BRRRRB, RBBRRR). 
Giới hạn: $r, b \le 1e5, 1 \le k \le 10, 2 \le p \le 1e9$
**Lời giải**
Thay vì đếm trực tiếp, ta đếm số dãy **thỏa mãn** điều kiện của đề bài. 
Xét cách xây dãy bài như sau: 
	- Chọn số $x$ trong khoảng từ 1 đến $b$. 
	- Chia $b$ lá bài đen thành $x$ nhóm gồm ít nhất 1 lá. Các nhóm này ứng với các đoạn đen liên tiếp trong dãy cuối cùng. 
	- Với mỗi nhóm có $len$ lá bài đen ta thêm $k * len$ lá bài đỏ. $k * len$ lá bài này sẽ là các lá đỏ đứng liền trước dãy bài đen. 
	- Lấy $r - b * k$ lá đỏ còn lại chia làm $x + 1$ nhóm (nhóm có thể rỗng), nhóm 1 thêm vào trước các lá có sẵn trong nhóm 1 ở trên, nhóm 2 thêm vào trước nhóm 2 ở trên, ..., nhóm $x + 1$ thêm vào cuối. 
Nối các nhóm này lại ta có dãy bài. 
Ta có thể chứng minh mỗi cách xây ứng với một dãy bài **thỏa mãn điều kiện**. Như vậy đáp án là: $C_{r}^{r + b} - (\sum_{x = 1}^{b}C_{x - 1}^{b - 1}*C_{x}^{r - b*k + x})$	
Độ phức tạp: $O(nlogp)$
Related: [[combinatorics]], [[Euler distribution problem]]
	