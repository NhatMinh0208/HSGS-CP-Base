# ROB
**Đề bài**
Cho một đồ thị có $n \leq 200$ đỉnh. Các đỉnh từ $1$ đến $b \leq n$ là các hầm. Có $m \leq n$ con robot, mỗi con đang ở một đỉnh nào đó. Mỗi bước robot sẽ đi sang một đỉnh bất kỳ. Tìm số k sao cho với mọi cách để mọi robot di chuyển k bước, chúng luôn ở một đỉnh là hầm. 

**Lời giải**
- Khi [[Nhận xét constraints]] $n \leq 200$, trong đồ thị ta thường nghĩ đến floyd, nhân ma trận, gauss -> có thể bắt đầu từ một trong những hướng này. 
- Để ý bài toán <-> Tìm k để *mọi path độ dài k bắt đầu từ một con robot sẽ đến hầm*, từ đó ta thấy đi theo hướng nhân ma trận là hợp lý. 
- Ta xây ma trận $M_i = [u_{i, 1}, u_{i, 2}, ..., u_{i, n}]$ trong đó  $u_{i, j}$ là 1 nếu mọi đường đi độ dài $i$ bắt đầu từ $j$ đều đến hầm. Ma trận được nhân chính là ma trận đồ thị, và thay phép toán $+$ bằng $min()$.
- Vậy với ta có thể tính được đáp án với k từ $1$ đến $X$ trong $O(n^3*X)$. Nhận thấy phép min trong ma trận bit có thể coi như phép $AND$, nên ta có thể tối ưu bằng [[Nhân ma trận bitset]] Từ đó ta tìm cách để giới hạn lại $X$. 
- Có chặt nhị phân được không ? Rõ ràng nếu chặt đáp án thì không. Vậy thì có làm $X \leq n$ được không ? Không, dễ chỉ ra một graph gồm 2 cycle nối với nhau bởi một 2 cạnh chung một đỉnh, một cái length = 3, một cái length = 4 -> ans bé nhất là 11. (idk vẫn chưa nghĩ xong làm tiếp ntn)