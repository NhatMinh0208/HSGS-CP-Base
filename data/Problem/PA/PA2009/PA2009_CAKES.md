A graph with n vertices and m edges $(n\leq100000,m\leq250000)$. Each vertex has a value $p[i]$. Find all 3 vertices that pairwise connect with each other, and add the max $p[i]$ among 3 vertices to the answer. Find the answer?

Sol: This problem is one of the example of [[sqrt decomposition]], this can be often found in problem when you are required to find a group of objects, with connections to others (like graphs), and can find a way to optimize from $O(n^2)$, to $O(nlogn)$ or so. You can divide the objects into 2 groups like this problem.
Group 1: $degree(u)>\sqrt m$ 
Iterate through all edges and check if these edges connect with u.
Group 2: $degree(u)<\sqrt m$
Iterate through each pair of all adjacent vertices to see if there exists an edge between them.
Complexity: $O(n\sqrt n logn)$ ($logn$ to store edges in set)
