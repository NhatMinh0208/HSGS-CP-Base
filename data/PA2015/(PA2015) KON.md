# KON
 
**Đề bài:**
Cho đồ thị có hướng n đỉnh m cạnh. Tìm xem đồ thị có chu kỳ không, và liệt kê các cạnh mà mọi chu kỳ phải đi qua

**Lời giải:**
*p/s:* Đây là sol mình chưa check lại với sol thật. 
- Hướng đầu tiên nghĩ đến là [[DFS tree]]. Vì mô hình bài toán theo cái cây thì dễ hơn. 
- DFS tree trên đồ thị có hướng được đặc trưng bởi các back-edge và cross-edge. Để làm bài toán đơn giản hơn, ta thử coi như đồ thị không có cross-edge. 
- Ta có thể liên tưởng đến [[Cycle basis]] của một đồ thị vô hướng: Tập tất cả các cycle của một đồ thị có thể được tạo bởi tập các back-edge trên cây dfs bất kỳ của đồ thị đó (hơi giống vector basis). Trong đồ thị này, nhận xét là mọi cạnh của một cycle được tạo bởi việc ghép 2 hay nhiều back-edge với nhau đều thuộc một trong các cycle riêng biệt của từng back-edge. Do đó, đáp án chỉ là giao tập cạnh của các cycle đó. [[Quan sát cấu hình]] đồ thị ta còn thấy các cạnh trong đáp án (nếu có) tạo thành một path, và mọi back-edge đi "qua" cái path đó. 
- Để tìm được các cạnh này, ta có thể dfs và tính cho mỗi cạnh xem mọi back-edge có đi qua nó không trong $O(n)$
- Bây giờ ta nhét thêm các cross-edge -> tạo được thêm các cycle mới bằng cách xét một cross-edge u -> v, đi từ u đến v rồi đến một back-edge nào đó, đi đến lca(u, v) rồi về v. Mỗi cycle như thế loại một đoạn prefix các cạnh của path tạo bởi những cạnh thỏa mãn -> xét mọi cross-edge và thay đổi đáp án. Tìm lca -> $O(log)$ -> tổng độ phức tạp là $O(nlogn)$