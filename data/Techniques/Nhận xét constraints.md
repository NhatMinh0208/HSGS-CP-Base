# Nhận xét constraints
- Trong một số bài toán, ta có thể nhìn vào **giới hạn input** và **time limit** để giúp nhìn ra kỹ thuật cần dùng. 
- Ví dụ (chỉ mang tính tương đối): 
1. TL 10s, $n\leq10^5$, bài query -> có thể thuật chuẩn là chia căn và họ cho thế vì chia căn là thuật chuẩn ? 
2. TL 2s, $n\leq 3*10^5$ -> Cần một thuật $O(nlogn)$ hoặc $O(n)$ -> Giả sử đang ra một thuật $O(nlog^2n)$ thì cần nghĩ tiếp cách tối ưu. 