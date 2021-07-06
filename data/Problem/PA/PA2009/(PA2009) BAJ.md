# Byteantean Towns [B] (baj)
**Đề bài**
Cho $n$ đường thẳng nối 2 điểm $x[i]$ và $y[i]$. Coi từng đường thẳng là biên giới và tính hiệu giữa số điểm ở 2 bên đường thắng. Một điểm được tạo thành khi 2 đường thẳng cắt nhau, và không có 3 đường nào cắt nhau.
**Lời giải**
For each line, first sort the slope in some way so that we know where each line starts, then we see the intersections with the current line and count the number of inversions. Each pair of inversions means that the two lines have intersected before meeting the current line. Chúng ta sẽ sort slope của mỗi đường thẳng và coi đó như một sự mô phỏng cho việc (giả sử y vô tận thì vị trí các đường thẳng là như thế nào), sau đó sort tại điểm cut đường thẳng đang xét, và đếm số cặp nghịch thế (cắt nhau trước khi gặp). Đây là một bài sử dụng một vài công thức [[geometry]], và có thể sẽ phải sử dụng [[binary indexed tree]] để đếm số cặp nghịch thế.
Complexity: $O(n^2logn)$ (($nlogn$) to count inversions)
