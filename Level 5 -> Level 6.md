Ở bài này mình sẽ dùng thêm lệnh grep, là lệnh tìm chuỗi trong file chỉ định, lệnh này tìm kiếm thông tin theo ý người dùng khi người dùng đưa thông tin vào. Lệnh grep có nhiều lựa chọn như thêm -i thì không phân biệt hoa thường, -r để tìm tất cả các file các thư mục con, -v để tìm kiếm ngược, -n để hiện kết quả ở dòng nào, v.v.

Ý tưởng là khi dùng lệnh file thì nó trả về thông tin loại file, sau đó ta dùng grep để tìm và lọc các file chứa thông tin mình muốn ra. Để kết hợp ta dùng thêm " | ". Cú pháp sẽ như thế này <command> | grep <patten>.

Để kiểm tra kích thước của file ta dùng lệnh du. Mặc định, lệnh du sẽ hiển thị dung lượng sử dụng theo đơn vị kilobyte nhưng ta có thể dùng thêm -b để hiện thị dạng byte, ngoài ra ta cần -a để hiện thị toàn bộ file kể cả file ẩn.

Để xác định file có là not executable ta có thể dùng lệnh find kết hợp với -executable (thêm ! nếu muốn tìm file not executable).

Cú pháp lệnh find có dạng find . -(option) filename.

Một số thông tin thú vị cho lệnh find: 
   - 
