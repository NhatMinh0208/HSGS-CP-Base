# SIA

**Đề bài:** Có $n \leq 5*10^5$ loại cỏ. Loại cỏ thứ $i$ mọc thêm $a_i$ cm mỗi ngày. Mỗi 1cm cỏ nặng 1kg. Bác John có một máy cắt cỏ có thể cắt tất cả cỏ ở một độ cao $b$ nào đó - mọi ngọn cỏ cao hơn b cm sẽ bị cắt để cao đúng b cm. 
Bác John sẽ cắt cỏ trong $m \leq 5*10^5$ ngày. Giả định rằng cỏ sẽ bắt đầu mọc vào ngày 0, lúc nửa đêm và luôn bị cắt lúc nửa đêm và thời gian cắt cỏ không đáng kể. Ngày thứ $i$ bác John cắt cỏ là ngày thứ $d_i$ (đảm bảo $d_i < d_{i + 1}$ và $1 \leq d_i \leq 10^{12}$) và cắt ở độ cao $b_i$ cm ($b_i \leq 10^{12}$). Cỏ không bao giờ cao quá $10^{12}$ cm. Hãy tính xem trong ngày thứ $i$ bác John cắt được bao nhiêu kg cỏ. 

**Lời giải** 
- Ở mọi thời điểm, loại cỏ có $a_i$ lớn hơn thì sẽ cao hơn. 
- Xét ngày thứ i. Xét mảng độ cao của cỏ tăng dần vào ngày thứ i. Thao tác ở ngày thứ i trở thành tìm suffix dài nhất mà chỉ chứa các loại cỏ cao hơn $b_i$ và biến chúng thành $b_i$
- Ta [[Quan sát cấu hình]] thấy rằng sau lần cắt đầu tiên, sẽ chia thành 2 nhóm: 1 prefix không bị cắt và một suffix có chiều cao bằng nhau. 
- Có thể biểu diễn các nhóm này thành các tuple $(h, i, l, r)$: bắt đầu mọc từ ngày i, chiều cao khởi đầu là h, gồm các loại cỏ từ l đến r trong mảng a đã được sắp xếp tăng dần. 
- Lúc đầu chỉ có 1 tuple $(0, 1, 1, n)$, sau lần cắt thứ nhất, giả sử suffix dài nhất bị cắt là suffix ở i, khi 
đó ta có 2 tuple $(0, 1, 1, i - 1)$, $(b_1, 1, i, n)$. 
- Khái quát lên, gs ngày i có các tuple $(h_1, i_1, l_1, l_2 - 1)$, $(h_2, i_2, l_2, l_3 - 1)$,... $(h_k, i_k, l_k, n)$. Ta cần tìm ra tuple chứa index của suffix dài nhất bị cắt, xóa các tuple sau nó, và tách tuple đó ra làm 2 tuple mới. 
- Việc tìm kiếm này có thể được tối ưu bằng chặt nhị phân và lưu các tuple trong một mảng. Khi đó bài toán được giải với độ phức tạp $O(n log n)$.

**Notes**
- Số tuple là $O(m)$ -> có thể phát triển thêm bài toán ?