# EKS

**Đề bài:** 
Bajtokomórczak là một đơn vị sống. Đó là một dãy các tế bào được sắp xếp, mỗi tế bào thuộc 1 trong n kiểu (đánh số từ 1 đến n). Đặc điểm nổi bật của đơn vị sống là tốc độ nhân bản cực nhanh.
Trong phút đầu tiên, sinh vật này chỉ có 1 tế bào kiểu 1. Cứ mỗi phút, mỗi tế bào lại tự thực hiện nhân bản thành một chuỗi có ít nhất 2 tế bào. Do đó, sinh vật này có thể có nhiều kiểu tế bào khác nhau. Nhưng tế bào kiểu k luôn tạo ra cùng một trình tự $H(k) = h_{k,1}, h_{k,2},...,h_{k,l_k}$. Nếu ở phút thứ $i$, sinh vật chứa dãy tế bào $c_1, c_2,...,c_p$, thì ở phút $(i + 1)$, nó chứa chuỗi $H(c_1),H(c_2),...,H(c_p)$.
Sinh vật này sẽ trưởng thành nếu dãy tế bào của nó có dãy S cố định là một dãy con liên tục.
Hãy nghiên cứu sinh vật này có thể trưởng thành được không – nếu có, thì khi nào nó trưởng thành.


**Constraints:** 
$1 \leq n \leq 500, 1 \leq m \leq 1000, \sum{l_i} \leq 1000$

**Lời giải:**
*p/s. bài này mình không tìm thấy sol nên đây là sol mình chưa check lại.*
- Giả sử ở $i$ ta muốn tìm thời điểm để chứa string S. 
- $i$ -> $i_1, i_2, ..., i_k$. 
- Nếu string S được tách làm đôi, một phần là suffix $suf$ của S thuộc $i_t$ và một phần là prefix của S thuộc $i_{t+1}$:
	+ $i_t$ -> $u_1, u_2, ..., u_x$
	+ Nếu $u_x$ không chứa $suf$ -> $u_x$ lúc cuối sẽ là một string bằng một suffix nào đó của $suf$. Ta có thể for suffix đó trong $O(m)$, tìm xem mất bao lâu để $u_x$ biến thành suffix đó, rồi check cho các $u_i$ còn lại trong $O(x)$
	+ Làm như thế mất $O(1000^4)$ TLE. Ta cần tìm cách tối ưu độ phức tạp. Một số hướng: 
	1. simplify cấu hình ? -> Ta đang tính thừa những gì ?
	2. tìm một dp khác ? 
	3. Dùng nx mỗi bước size tăng $\geq$ 2 lần ?
	+ Từ *(1), (3)* -> for số bước mất $O(log)$ để check. 
	+ Có số bước = $t$ -> cần biết string của $u$ nào đó sau $t$ bước trông như thế nào rồi check suffix của nó xem có bằng $suf$. Tuy vậy string này có thể trở nên rất to. Tuy vậy để ý process của chúng ta dừng lại nếu $len > 1000$, nên chỉ cần maintain $1000$ char cuối của string -> $O(1000^2 * log)$ thời gian,  $O(n * 1000 * log)$ bộ nhớ, $O(1)$ check suffix bằng hash
	+ Vậy nếu $u_x$ chứa cả $suf$ ? GS $i_{t+1}$ -> $v_1, v_2, ..., v_y$. Nếu $v_1$ không chứa cả prefix thì làm tương tự như trên, chỉ khác là cần tính $1000$ chữ cái đầu của mỗi $i$ sau $x \leq log$ bước. Nếu có thì $state(i_t, i_{t+1}, suf)$ <- $state(u_x, v_1, suf) + 1$. Cái này có thể quản lí bằng [[Dijkstra]] trong $O(1000^2*log)$.
	- Nếu string S có một substring được bao phủ bởi nguyên một $i_k$ nào đó: 
		+ Thuật brute: fix $i_k$ và substring ứng với nó, cũng TLE $O(1000^4)$
		+ Nhưng tương tự ta có thể fix số bước $x \leq log$, for từng $i_k$ với $k$ tăng dần, for từng suffix (Ta coi $i_k$ là cái bắt đầu của string S, nên nó sẽ chứa một suffix của S), check bằng hash + dịch con trỏ -> $O(1000^2 log)$
	- Nếu S nằm hẳn trong $i_k$: $dp(i)$ <- $dp(i_k)+1$. Trường hợp này cũng chỉ là dijkstra 
	
	**Notes**
	- Một số thao tác trong giải trên lặp lại (ý tưởng for x giống nhau ở TH1, 2 và dijkstra 2 lần) -> có thể làm đơn giản lời giải ? 