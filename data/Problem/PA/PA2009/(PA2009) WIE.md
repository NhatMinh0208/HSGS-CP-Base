# DRILLING (WIE)
**Đề bài:**
    
Byteman là đội trưởng đội tìm kiếm các mỏ dầu thô. Anh khoan 2 lỗ: lỗ A có dầu thô và lỗ B không có dầu thô. Ta biết rằng mỏ dầu nằm trên một đoạn liên tục của đoạn AB với một đầu ở điểm A. Bây giờ, Byteman phải kiểm tra dọc theo đoạn thẳng nối giữa 2 điểm A và B để xem mỏ dầu dài bao nhiêu. Tuy nhiên, điều này không hề đơn giản, vì có một số vị trí mà anh có thể khoan nhanh hơn một vài vị trí khác. Hơn thế nữa, đội của Byteman không đông, nên họ chỉ có thể khoan tối đa 1 vị trí tại một thời điểm. Byteman muốn xác định trước khi nào mình có thể tìm ra biên của mỏ dầu. Byteman cần giúp đỡ. Anh chia đoạn nối giữa hai điểm A và B thành n+1 đoạn có độ dài bằng nhau. Nếu ta giả sử rằng điểm A có tọa độ là 0 và điểm B có tọa độ là n+1, thì có n điểm với các tọa độ 1, 2, …, n giữa 2 điểm này. Trong số các điểm này, chúng ta phải tìm điểm xa A nhất sao cho từ A tới điểm này là một mỏ dầu. Byteman biết thời gian cần để khoan các lỗ thăm dò tại các điểm này – thời gian khoan lần lượt là $t_1, t_2, …, t_n$. Hãy xây dựng một kế hoạch khoan sao cho thời gian cần để xác định biên của mỏ dầu trong trường hợp xấu nhất là ngắn nhất có thể.

**Constraints:** $1 \le n \le 2000, t_i <= 10^6$

**Lời giải:**
Nhìn constraint ta đoán được sol dp: $dp_{l, r}$ là thời gian tối thiểu để xác định ô biên (ô cuối cùng có dầu) biết ô này nằm trong khoảng $[l, r]$. 
	+ Nếu $l = r$: $dp_{l, r} = 0$ 
	+ Nếu $l > r$: giả sử ta khoan ô $m (l + 1 \le m \le r)$. Nếu ô này không có dầu, ta biết rằng ô biên $< m$ và thời gian để xác định ô biên lúc này là $dp_{l, m - 1}$. Nếu ô này có dầu, ta biết ô biên giới $\ge m$, thời gian cần thêm để xác định là $dp_{m, r}$. Trong trường hợp xấu nhất, tổng thời gian để xác định ô biên tính cả thời gian khoan ô m là $max(dp_{l, m - 1}, dp_{m, r}) + t_m$. Như vậy ta tìm được công thức dp: 
	
	$dp_{l, r} = min(\{max(dp_{l, m - 1}, dp_{m, r}) + t_m\})$	với $l + 1 \le m \le r)$
	
Tuy nhiên độ phức tạp của thuật toán này là $O(n ^ 3)$. Ta cần tìm cách tối ưu thuật toán. 
Trước tiên đặt $dp_{i, j} = 0$ nếu $i = j$ và $= MAX$ nếu $i \neq j$. Sau đó ta sort lại các đoạn $l, r$ theo $r - l$ và tính dần lên:
Fix l và m. Ta thực hiện update $dp_{l, r} = min(dp_{l, r}, dp_{l, m - 1} + t_m)$ với  $r$ thỏa mãn $dp_{m, r} \le dp_{l, m - 1}$. Vì $dp_{m, r}$ tăng dần khi r tăng, ta có thể thấy các $r$ thỏa mãn điều kiện trên nằm trong 1 khoảng liên tiếp. Như vậy ta đã có sol $n^2log$ bằng segtree / sparse table. Tuy nhiên cách làm này có thể tối ưu thêm bằng nhận xét rằng các khoảng update tăng dần $(L_i <= L_{i + 1}, R_i <= R_{i + 1})$ nên có thể update bằng stack. 
	
**Độ phức tạp**: $O(n^2)$ 
**Link** [[DP optimization]] [[DP]][[Stack]][[Data structure]]