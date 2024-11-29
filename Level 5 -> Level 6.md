Ở bài này mình sẽ dùng thêm lệnh grep, là lệnh tìm chuỗi trong file chỉ định, lệnh này tìm kiếm thông tin theo ý người dùng khi người dùng đưa thông tin vào. Lệnh grep có nhiều lựa chọn như thêm -i thì không phân biệt hoa thường, -r để tìm tất cả các file các thư mục con, -v để tìm kiếm ngược, -n để hiện kết quả ở dòng nào, v.v.

Lệnh grep có các biến thể khác như là egrep, fgrep, rgrep:
- grep: Tìm kiếm theo mẫu sử dụng biểu thức chính quy cơ bản (BRE).
- egrep: Tìm kiếm theo mẫu sử dụng biểu thức chính quy mở rộng (ERE), lệnh này tương đương với grep -E.
- fgrep: Tìm kiếm theo mẫu không sử dụng bất kì biểu thức chính quy nào, lệnh này tương đương với grep -F.
- rgrep: Tìm kiếm mẫu trong toàn bộ cây thư mục bao gồm cả thư mục con, lệnh này tương đương với grep -r.

Biểu thức chính quy là dùng các dấu như +, -, *, | ,v.v nhằm giúp ta tìm kiếm nhiều kiểu mẫu phức tạp hơn. Có gì thì tự tìm hiểu thêm.

![1](https://github.com/user-attachments/assets/0ffe4cb8-d261-4882-b98f-76bbc74a8482)
Ý tưởng ở đây là khi dùng 1 số lệnh như lệnh file, du thì nó trả về thông tin tương ứng, sau đó ta dùng grep để tìm và lọc các file chứa thông tin mình muốn ra. Để kết hợp ta dùng thêm " | ".

Để kiểm tra kích thước của file ta dùng lệnh du. Mặc định, lệnh du sẽ hiển thị dung lượng sử dụng theo đơn vị kilobyte nhưng ta có thể dùng thêm -b để hiện thị dạng byte, ngoài ra ta cần -a để hiện thị toàn bộ file kể cả file ẩn.

Để xác định file có là not executable ta có thể dùng lệnh find kết hợp với -executable (thêm ! nếu muốn tìm file not executable). 

Cú pháp lệnh find có dạng find . -(option) filename. Lưu ý dấu chấm đằng sau thể hiện tìm kiếm ở thư mục hiện tại, ta có thể tìm kiếm ở thư mục khác hoặc toàn bộ thư mục bằng lệnh " / ".

Một số thông tin cho lệnh find: 
- Nó có 1 flag để xem kích thước tệp theo byte -size <bytes>.
- Tìm kiếm theo loại tệp tin: -tyfe f, d, ...
- Tìm kiếm theo thời gian sửa đổi tệp tin: -mtime.
- Tìm kiếm theo tên người dùng sở hữu tệp tin: -user.
- Tìm kiếm theo tên nhóm sở hữu tệp tin: -group.
- Thực hiện một lệnh trên các tệp tin được tìm thấy: -exec (VD: -exev rm{} .kk ko nên thử nha).
- Nó cũng có -readable flag, nhưng nó biểu hiện bạn có quyền đọc file đó hay không chứ không phải là human-readable.

Bây giờ chúng ta sẽ nhìn tổng quát file này, nhìn vào hình ảnh ta thấy có tận 88 thư mục cần mở, vì thế tự mở từng cái một để tìm flag thì trông không được thông minh lắm.
![2](https://github.com/user-attachments/assets/a37bd38d-a92d-4964-aee2-45c969b95f2b)
Tôi kiểm tra những file có định dạng ASCII, đập vào mắt mình là 1 danh sách dài những file ASCII, rất nhiều file có hiển thị "with very long lines". Tôi nghĩ khả năng cao flag sẽ ở những file không có hiển thị dòng này nên tôi thêm grep -v để lọc những file này ra.
![3](https://github.com/user-attachments/assets/dedee950-cd67-4c10-8d60-600584d4d430)
Tiếp tục tìm kiếm file có kích cỡ 1033 bytes, lúc đó tôi bất ngờ vì chỉ cần 1 câu lệnh này đã ra luôn kết quả. Nói thật lúc đó hơi hụt hẫng chỉ biết cười, và tôi đã sai khi cho rằng flag nằm ở file không có "with very long lines". Và ta có flag: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG. 
![4](https://github.com/user-attachments/assets/9514a989-6323-450b-a99e-3d61676cd2a7)
P/S: Lúc dùng kali tôi thấy khá là lag mà lúc đó tôi cũng đã cài xong ubuntu nên muốn thử sang và nó cũng mượt hơn đôi nhiều so với kali nên từ giờ mình sẽ dùng ubuntu để leo tháp hehe :)).

