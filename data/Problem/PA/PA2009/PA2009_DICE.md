Tính tỷ lệ để tung $n<1e6$ quân xúc sắc ra được tổng $k$ (làm tròn về số nguyên % gần nhất). (Ví dụ: 1/6=16%)
Ban đầu, đây là bài toán nhìn khá giống bài [[combinatorics]] vì ta có thể dùng [[Euler distribution problem]] và [[inclusive and exclusive]] để giải trong O(n). Tuy nhiên có 2 vấn đề chính với cách làm này:
1) Chúng ta rất khó để tính toán được 1 C(k,n) với k và n lên đến 1e6
2) Có thể dùng Stirling's approximation nhưng cũng không chắc chắn được về độ chính xác
Tuy nhiên có thể thấy rằng khi $n$ đủ lớn, số khả năng của tổng càng nhiều và có khả năng không một tổng nào quá (1%) ($ans=0$) và số cuối cùng với 1 giá trị có tỷ lệ ít nhất $1%$ là 1 số $<600$. Vì thế, chúng ta có thể [[dynamic programming]] đơn giản.
[[constraints]] là một yếu tố rất quan trọng mà chúng ta cần chú ý khi làm những bài [[approximation]].
Complexity: $O(n*n*6)$ $(n=600)$
