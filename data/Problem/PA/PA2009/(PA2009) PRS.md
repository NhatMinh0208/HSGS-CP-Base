# Rectangles 2 (prs)
**Đề bài**
Similar to RECTANGLES but $n\leq1e9$. 
**Lời giải**
We still do [[brute force]], however we can just count the number of pair (i,j) such that $i\leq j$ and $i*j<=n$. We can do this in $O(\sqrt n)$