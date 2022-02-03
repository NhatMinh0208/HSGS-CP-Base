#  Fibonacci Machine (fib)
** Đề bài **
Các số Fibonaci được định nghĩa như sau: F(0) = 0, F(1) = 1, F(m) = F(m-1) + F(m-2) với m ≥ 2. Bộ máy Fibonaci thao thác trên một dãy thanh ghi số nguyên có n phần tử (i1, i2, …, in) mà khởi đầu chỉ là các số 0. Bộ máy này có 2 thao tác: Thêm 1 vào từng từng thanh ghi trong khoảng [a, b], tức là cộng 1 vào các số $i_a, i_{a+1}, …, i_b$; Tính tổng của các số Fibonaci đó, dãy các số dãy này được lưu trong các thành ghi từ khoảng [a, b], tức là tính $F(i_a) + F(i_{a+1}) + … + F(i_b)$ modulo 1e9 + 7. Viết một chương trình mô phỏng bộ máy Fibonaci.
** Giới hạn **
 n và k (1 ≤ n, k ≤ 100000) 
** Lời giải **
- Xét một đoạn [a, b]. Với $v \in Z$, gọi $S_v(a, b) = F(i_a + v) + F(i_{a+1} + v) + … + F(i_b + v)$. Giả sử ta biết giá trị của $S_{-1} (a, b)$và $S_0(a, b)$, ta tính được giá trị của $S_1(a, b)$:
		$$S_1(a, b) = S_0(a,b) + S_{-1}(a, b)$$ 
	Công thức này khá tương tự công thức tính số fibonacci và có thể biểu diễn dưới dạng nhân ma trận: 
	$$\begin{bmatrix} S_v(a,b) & S_{v + 1}(a,b) \end{bmatrix} = \begin{bmatrix} S_{v-1}(a,b) & S_v(a,b) \end{bmatrix} * \begin{bmatrix} 0 & 1 \\ 1 & 1 \end{bmatrix}$$
	Như vậy, ta có thể tính tổng các phần tử trong đoạn [a, b] sau khi cộng 1 vào $i_a, i_{a + 1}, ..., i_b$: 
	$$\begin{bmatrix} S_{v - 1}(a,b) & S_{v}(a,b) \end{bmatrix} = \begin{bmatrix} S_{-1}(a,b) & S_0(a,b) \end{bmatrix} * \begin{bmatrix} 0 & 1 \\ 1 & 1 \end{bmatrix} ^ v$$
	Nếu tính trước $\begin{bmatrix} 0 & 1 \\ 1 & 1 \end{bmatrix} ^ v$ với $0 \le v \le q$, thao tác trên có thể thực hiện trong O(1).
- Như vậy nếu như tính trước khi + 1 vào một đoạn [a, b], có thể không tính luôn tổng mới của cả đoạn, mà có thể chồng các query + 1 lên nhau để một lúc nào đó tính một lượt.
- Nhận xét này dẫn ta nghĩ theo hướng segment tree có lazy update. Ta với mỗi node (l, r) trong cây chỉ cần duy trì các thông tin $S_0(l, r)$ và $S_{-1}(l, r)$ ở thời điểm hiện tại.
**ĐPT**: O(qlogn)
Link: [[Fibonacci]], [[Matrix multiplication]], [[Data structure]]