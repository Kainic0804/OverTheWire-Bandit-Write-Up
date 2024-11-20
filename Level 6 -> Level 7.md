Trước khi giải quyết câu hỏi này, mình sẽ nói chút lí thuyết về standard output, standard error và /dev/null.

Đầu tiên, khi ta sử dụng tiện ích dòng lệnh sẽ có hai đầu ra: Đầu ra tiêu chuẩn và Lỗi tiêu chuẩn. Đầu ra tiêu chuẩn được gửi đến stdout. Lỗi tiêu chuẩn được gửi đến stderr.

Theo mặc định, stdout và stderr được liên kết với terminal (hoặc console). Nó có nghĩa là mọi thứ được gửi đến stdout và stderr đều được in ra màn hình. Tuy nhiên ta có thể thay đổi nó. Ví dụ, ta có thể chuyển hướng nó đến file hoặc có thể chuyển hướng nó sang thiết bị vật lí như màn hình LED, LCD,...

Các kiểu chuyển hướng:
- Với 1> ta chuyển hướng thông báo đầu ra tiêu chuẩn.
- Với 2> ta chuyển hướng thông báo lỗi tiêu chuẩn.
- Với &> ta chuyển hướng cả hai.

Tiếp đến /dev/null. Nó là pseudo file (tập tin giả) đặc biệt trong Linux. Nó còn được gọi là black hole (hố đen) vì mọi thứ ghi vào trong nó đều sẽ biến mất, bị loại bỏ.
Để hiểu tại sao mình lại nói đến những thứ trên thì ta sẽ giải quyết vấn đề ngay dưới đây.
![1](https://github.com/user-attachments/assets/11153942-230f-4e45-bb22-66ebf126e1d0)
Câu hỏi yêu cầu ta tìm file được sở hữu bởi người dùng bandit7, sở hữu bởi nhóm bandit6, kích cỡ 33 bytes.

Như thói quen mình sẽ dùng thử các lệnh quen thuộc như ls, du để thăm dò trước. Và như ta đã thấy nó chả có quái gì cả. Lúc này mình nhận ra có lẽ file tìm cần không nằm ở đường dẫn hiện tại. Ta có thể kiểm tra đường dẫn hiện tại bằng pwd.
![2](https://github.com/user-attachments/assets/acab280b-1806-433f-be82-29b86945adff)
Ta sẽ dùng lệnh find kết hợp với các option mình đã nói trong level trước. Nhớ là thêm dấu " / " để tìm kiếm ở toàn bộ đường dẫn vì ta không biết nó nằm ở đâu.
![3](https://github.com/user-attachments/assets/3ae34e5c-af8b-4433-b49c-b8817bb4a186)
Như ta đã thấy, hiện ra 1 mớ file mà người dùng không phải root sẽ không đọc được. Điều này dẫn đến lỗi "Permission denied". Ta cần lọc những file có thông báo lỗi này ra. "Permission denied" là 1 thông báo lỗi tiêu chuẩn. Để lọc những file không đọc được này ta dùng lí thuyết trên bằng cách chuyển hướng thông báo lỗi tiêu chuẩn này sang /dev/null, nơi mà nó sẽ bị xóa đi từ đó còn lại duy nhất 1 file không có thông báo lỗi.
![4](https://github.com/user-attachments/assets/584d0004-dc0c-43e1-8540-51a92920fd7b)

Nếu bạn muốn thì có thể kiểm tra thêm quyền file ta vừa tìm ra bằng lệnh ls -la.

Ta được flag: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj.
