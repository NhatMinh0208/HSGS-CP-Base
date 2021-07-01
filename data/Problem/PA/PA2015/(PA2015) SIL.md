# SIL
**Đề bài**
Một cái gym có $k\leq10^9$ thiết bị, mỗi thiết bị chỉ được tối đa một người dùng trong một thời điểm. Có $n\leq10^6$ yêu cầu dùng thiết bị, yêu cầu thứ $i$ là sử dụng thiết bị thứ $p_i$ trong vòng một tiếng và thời điểm bắt đầu trong khoảng $[a_i, b_i]$ ($1 \leq a_i \leq 10^9$). Hãy sắp xếp các yêu cầu sao cho số giờ có ít nhất một thiết bị được dùng là nhỏ nhất, hoặc in ra "NYA" nếu không có cách sắp nào. 

**Lời giải**
- Cấu hình bài toán là một [[Set các đoạn]] + selection
- Ta nghĩ đến một số hướng chính như [[Greedy]], [[DP]], hoặc chặn đáp án (như kiểu maximal non-intersecting path in DAG -> maximal anti-chain), hoặc last resort là [[Flow & Matching]].
- [[Nhận xét constraints]] là $10^6$ -> Thường ta chú ý đến các nhận xét greedy nhiều hơn. Đồng thời không thể nhìn ra luôn state DP là gì nên ta có thể thử greedy trước. 
- GS ta đi từ trái sang phải, thì đến một lúc nào đó ta sẽ dừng lại, nhặt một số đoạn để cho vào điểm này, rồi tiếp tục chạy sang phải. Ta có một số nhận xét:
 	+ Trong các đoạn yêu cầu cùng một thiết bị, ta chọn đoạn *có r nhỏ nhất*. 
 	+ Khi ta dịch sang phải mà vẫn có thể nhét thêm các đoạn vào thì nên dịch sang phải.
	-> Ta có một thuật tham: Dịch con trỏ sang phải, maintain đoạn r gần nhất mà con trỏ không được vượt quá, chừng nào con trỏ vẫn sang phải được thì thêm các đoạn vào và cập nhật r nhỏ nhất, đến lúc dừng lại thì +1 vào đáp án và tiếp tục giải. 
- Đến lúc này thì nên [[Check lại thuật]] -> Nếu 2 đoạn yêu cầu cùng một thiết bị và có r bằng nhau thì thuật toán này sẽ có thể kết thúc con trỏ ở r khiến cho một trong 2 đoạn không chọn được. Để giải quyết, ta [[Đơn giản hóa]] cấu hình để nó thành r phân biệt, bằng tham: nếu 2 đoạn cùng chọn một thiết bị cùng r, thì thay r -> r - 1 cho đoạn có đầu l nhỏ hơn. 
- Độ phức tạp: $O(n log n)$