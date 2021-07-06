# Type Two de Bruijn Sequences (deb)
**Đề bài**
Một từ s được tạo thành từ (2n + n -1) các ký tự 0 và 1 được gọi là dãy Bruijn bậc n nếu tất cả các từ n ký tự được tạo ra từ các số 0 và 1 là từ con của nó – tức là một đoạn của các ký tự liên tiếp của s. Một ví dụ về dãy Bruijn bậc 3 đó là 0001011100. Một dãy Bruijn típ 2 bậc n là một từ s có độ dài bất kỳ mà mỗi từ n ký tự được tạo ra bởi các số 0 và 1 là một dãy con – tức là một đoạn, không cần các ký tự phải liên tiếp nhau, của s. Một ví dụ về dãy Bruijn típ 2 bậc 3 là 00101101. Như ta đã biết, Nicolaas Govert de Bruijn đã không phát minh ra những dãy như thế nhưng định nghĩa của chúng lại tương tự với định nghĩa phía trên. Xét một từ s được tạo thành từ các ký tự 0 và 1. Có bao nhiêu con số (0 hoặc 1) phải thêm vào cuối của từ s để từ này trở thành một dãy Bruijn tip 2 bậc n?
**Giới hạn**
1 ≤ m, n ≤ 1.000.000
**Lời giải**
- Một xâu nhị phân s là xâu tip 2 bậc n nếu thỏa mãn điều kiện sau: 
	+ Lấy prefix nhỏ nhất có cả 0 và 1 của s, gọi prefix này là nhóm 1 và bỏ prefix này ra khỏi s. 
	+ Liên tục lặp lại thao tác trên để tạo thành các nhóm 2, 3, 4, ... cho đến khi xâu s rỗng hoặc chỉ còn đúng một ký tự.
	+ xâu s là xâu tip 2 bậc n khi và chỉ khi số nhóm là ít nhất n.
	+ Ví dụ: xét xâu 001010101111000. Các nhóm của xâu này là: 001, 01, 01, 01, 1110 và xâu còn lại sau khi thưc hiện thao tác là 00. Như vậy xâu này là dãy bậc 5.
- Chứng minh: 
	+ Một xâu s có ít nhất n nhóm chứa tất cả các xâu nhị phân độ dài n: Xét một xâu nhị phân độ dài n. Ta có thể lấy bit đầu của xâu này từ nhóm 1, bit thứ 2 từ nhóm 2, ..., bit thứ n từ nhóm n.
	+ Mỗi nhóm được tạo thành đều có bit cuối xuất hiện duy nhất 1 lần.  Ví dụ xâu 001010101111000 ở trên: trong nhóm 001, bit cuối là 1 xuất hiện 1 lần, trong nhóm 1110 bit cuối xuất hiện 1 lần.
	+ Một xâu s có < n nhóm không phải là xâu tip n: Giả sử số nhóm của xâu này là k k < n). Xét xâu t được tạo thành theo cách sau: bit đầu của t là bit cuối của nhóm 1 của s, bit thứ 2 là bit cuối của nhóm 2, ..., bit thứ k của t là bit cuối của nhóm k. Từ bit thứ k + 1 đến bit n của t là bit không xuất hiện trong phần còn lại của xâu s (sau khi thực hiện thao tác chia nhóm). Vì t không phải subsequence của s, s không phải xâu tip 2 bậc n. Ví dụ: với s = 001010101111000 và n = 6, t = 111101 không phải subsequence của s.
- Để biến 1 xâu s bậc k thành xâu bậc n: 
	+ Nếu như phần còn lại của xâu s sau khi thực hiện thao tác không rỗng, ta chỉ cần thêm bit không xuất hiện trong đó để tạo thành nhóm thứ k + 1. Ví dụ xâu 001010101111000 có phần còn lại là 00, ta thêm bit 1 vào cuối xâu để tạo thành nhóm mới. Với các nhóm từ k + 2 đến n ta thêm 01 vào xâu để tạo thành nhóm mới.
	+ Nếu phần còn lại rỗng, với các nhóm từ k + 1 đến n ta thêm 01 vào tạo nhóm mới.
**ĐPT**: O(m)
Link: [[Greedy]][[(ARC 081) C]]