# HTTP Authentication

Giao thức HTTP bao gồm các cơ chế riêng để xác thực người dùng bằng các sơ đồ xác thực khác nhau, bao gồm:
- **Basic** là một cơ chế xác thực đơn giản gửi thông tin đăng nhập của người dùng dưới dạng chuỗi được mã hóa Base64 trong request header với mỗi thông báo.
- **NTLM** là một cơ chế thử thách-phản hồi và sử dụng một phiên bản của giao thức Windows NTLM.
- **Digest** là một cơ chế thử thách-phản hồi và sử dụng tổng kiểm tra MD5 với thông tin đăng nhập của người dùng.

Tương đối hiếm khi gặp các giao thức xác thực này đang được sử dụng bởi các ứng dụng web được triển khai trên Internet. Chúng được sử dụng phổ biến hơn trong các tổ chức để truy cập các dịch vụ dựa trên mạng nội bộ.