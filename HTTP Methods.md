#HTTP Method

Khi bạn đang tấn công các ứng dụng web, bạn hầu như chỉ xử lý các phương thức được sử dụng phổ biến nhất: `GET` và `POST`. Bạn cần lưu ý một số khác biệt quan trọng giữa các phương pháp này vì chúng có thể ảnh hưởng đến tính bảo mật của ứng dụng nếu bị bỏ qua.
Phương thức `GET` được thiết kế để truy xuất tài nguyên. Nó có thể được sử dụng để gửi tham số đến tài nguyên được yêu cầu trong chuỗi truy vấn URL. Điều này cho phép người dùng đánh dấu một URL cho tài nguyên động mà họ có thể sử dụng lại. Hoặc những người dùng khác có thể truy xuất tài nguyên tương đương trong lần tiếp theo (như trong truy vấn tìm kiếm được đánh dấu trang). Các URL được hiển thị trên màn hình và được ghi lại ở nhiều nơi khác nhau, chẳng hạn như lịch sử trình duyệt và nhật ký truy cập của máy chủ web. Chúng cũng được truyền trong tiêu đề  `Referer` đến các trang web khác khi các liên kết bên ngoài được theo dõi. Vì những lý do này, không nên sử dụng chuỗi truy vấn để truyền bất kỳ thông tin nhạy cảm nào.
Phương thức `POST` được thiết kế để thực hiện các hành động. Với phương pháp này, các tham số yêu cầu có thể được gửi cả trong chuỗi truy vấn URL và trong phần nội dung của thư. Mặc dù URL vẫn có thể được đánh dấu trang nhưng bất kỳ tham số nào được gửi trong nội dung thư sẽ bị loại trừ khỏi dấu trang. Các tham số này cũng sẽ bị loại trừ khỏi các vị trí khác nhau nơi duy trì nhật ký URL và khỏi tiêu đề `Referer`. Vì phương thức `POST` được thiết kế để thực hiện các hành động, nếu người dùng nhấp vào nút Quay lại của trình duyệt để quay lại trang được truy cập bằng phương thức này, thì trình duyệt sẽ không tự động đưa ra lại yêu cầu. Thay vào đó, nó cảnh báo người dùng về những gì nó sắp làm, như trong hình dưới đây:
![](2023-04-18-00-59-18.png)

Điều này ngăn người dùng vô tình thực hiện một hành động nhiều lần. Vì lý do này, các yêu cầu `POST` phải luôn được sử dụng khi một hành động đang được thực hiện.

Ngoài các phương thức `GET` và `POST`, giao thức HTTP hỗ trợ nhiều phương thức khác đã được tạo cho các mục đích cụ thể. Dưới đây là những cái khác mà khả năng cao là bạn đang cần:
- `HEAD` : hoạt động theo cách tương tự như yêu cầu `GET`, ngoại trừ việc máy chủ không được trả về nội dung thông báo trong phản hồi của nó. Máy chủ sẽ trả về các tiêu đề giống như nó sẽ trả về yêu cầu `GET` tương ứng. Do đó, phương pháp này có thể được sử dụng để kiểm tra xem tài nguyên có tồn tại hay không trước khi thực hiện yêu cầu `GET` cho nó.
- `TRACE` : được thiết kế cho mục đích chẩn đoán. Máy chủ sẽ trả về nội dung phản hồi chính xác của thông báo yêu cầu mà nó nhận được. Điều này có thể được sử dụng để phát hiện ảnh hưởng của bất kỳ máy chủ proxy nào giữa máy khách và máy chủ có thể thao túng yêu cầu.
- `OPTIONS` : yêu cầu máy chủ báo cáo các phương thức HTTP khả dụng cho một tài nguyên cụ thể. Máy chủ thường trả về một phản hồi chứa tiêu đề `Allow` liệt kê các phương thức khả dụng.
- `PUT` : cố gắng tải tài nguyên đã chỉ định lên máy chủ, sử dụng nội dung có trong đoạn yêu cầu. Nếu phương thức này được bật, bạn có thể tận dụng nó để tấn công ứng dụng, chẳng hạn như bằng cách tải lên một tập lệnh tùy ý và thực thi tập lệnh đó trên máy chủ.
- `DELETE` : được sử dụng để xóa tài nguyên được xác định bởi URL.
- `PATCH` : được sử dụng để sửa đổi, cập nhật một phần tài nguyên được xác định bởi URL.

