Calculate the probability of rolling $n<1e6$ dice with sum $k$ (round down to integer %).
At first sight, seems like a [[combinatorics]] problem as we can use [[Euler distribution problem]] and [[inclusive and exclusive]] to probably solve in O(n), along with Stirling's approximation to calcualte Combinations.
However, it turned out that as $n$ get bigger, the maximum prob get to $0$ and the last number with something more than $1%$ is $<600$. As a result, we do simple [[dynamic programming]], and consider different cases.
[[constraints]] is the important factor that we need to do attention when doing [[approximation]] problems.
Complexity: $O(n*n*6)$ $(n=600)$