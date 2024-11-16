Ở bài này mình sẽ dùng thêm lệnh grep, là lệnh tìm chuỗi trong file chỉ định, lệnh này tìm kiếm thông tin theo ý người dùng khi người dùng đưa thông tin vào. Lệnh grep có nhiều lựa chọn như thêm -i thì không phân biệt hoa thường, -r để tìm tất cả các file các thư mục con, -v để tìm kiếm ngược, -n để hiện kết quả ở dòng nào, v.v.

Ý tưởng là khi dùng 1 số lệnh như lệnh file, du thì nó trả về thông tin tương ứng, sau đó ta dùng grep để tìm và lọc các file chứa thông tin mình muốn ra. Để kết hợp ta dùng thêm " | ".

Để kiểm tra kích thước của file ta dùng lệnh du. Mặc định, lệnh du sẽ hiển thị dung lượng sử dụng theo đơn vị kilobyte nhưng ta có thể dùng thêm -b để hiện thị dạng byte, ngoài ra ta cần -a để hiện thị toàn bộ file kể cả file ẩn.

Để xác định file có là not executable ta có thể dùng lệnh find kết hợp với -executable (thêm ! nếu muốn tìm file not executable).

Cú pháp lệnh find có dạng find . -(option) filename.

Một số thông tin thú vị cho lệnh find: 
   - Nó có 1 flag để xem kích thước tệp theo byte -size <bytes>.
   - Nó cũng có tùy chọn chỉ xem các tập tin -tyfe f ((no directories/non-executables).
   - Nó cũng có -readable flag, nhưng nó biểu hiện bạn có quyền đọc file đó hay không chứ không phải là human-readable.

Bây giờ chúng ta sẽ nhìn tổng quát file này, nhìn vào hình ảnh ta thấy có tận 88 thư mục cần mở, vì thế tự mở từng cái một để tìm flag thì trông không được thông minh lắm.
