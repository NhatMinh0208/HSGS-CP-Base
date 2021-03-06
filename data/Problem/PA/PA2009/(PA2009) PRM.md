# Permutations (prm)
** Đề bài **
Given an array of size $n\leq200000$ elements. Check if it is possible to find a permutation of size $n$ such that for every $i$, $p[i]<a[i]$. There are $m\leq500000$ queries with form $pos val$, that you should change $a[pos]=val$. Check if it's still possible to find such a permutation.
**Lời giải**
Solution: We can see that, if we make an array suffix sum, if there's a number $k$ that the number of numbers $>=k$ in the array is less than in the permutation. However, we always know that number for any number on the permutation, so just build a [[segment tree]] of suffix value with the values in the array. We should also track the number $>n$.
Complexity: $O(mlogn)$