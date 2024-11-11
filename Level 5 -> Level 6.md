Ở bài này mình sẽ dùng thêm lệnh grep, là lệnh tìm chuỗi trong file chỉ định, lệnh này tìm kiếm thông tin theo ý người dùng khi người dùng đưa thông tin vào. Lệnh grep có nhiều lựa chọn như thêm i thì không phân biệt hoa thường, r để tìm tất cả các file các thư mục con, v để tìm kiếm ngược, n để hiện kết quả ở dòng nào, v.v

Ý tưởng là khi dùng lệnh file thì nó trả về thông tin loại file, sau đó ta dùng grep để tìm và lọc các file chứa thông tin mình muốn ra. Để kết hợp ta dùng thêm " | ". Cú pháp sẽ như thế này <command> | grep <patten>
