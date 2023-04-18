#  HTTP Headers

HTTP hỗ trợ một số lượng lớn tiêu đề, một số tiêu đề được thiết kế cho các mục đích đặc biệt khác thường. Một số tiêu đề có thể được sử dụng cho cả yêu cầu và phản hồi, và một số tiêu đề khác dành riêng cho một trong các loại thông báo này. Các phần sau đây mô tả các tiêu đề mà bạn có thể gặp phải khi tấn công các ứng dụng web.
#### Request Headers
- `Accept` : cho máy chủ biết loại nội dung nào mà máy khách sẵn sàng chấp nhận, chẳng hạn như loại hình ảnh, định dạng tài liệu văn phòng, v.v.
- `Accept-Encoding` : cho máy chủ biết loại nội dung mã hóa nào mà máy khách sẵn sàng chấp nhận.
- `Authorization` : gửi thông tin đăng nhập tới máy chủ cho một trong các loại xác thực HTTP tích hợp.
- `Cookie` : gửi cookie đến máy chủ mà máy chủ đã cấp trước đó.
- `Host` : chỉ định tên máy chủ xuất hiện trong URL đầy đủ được đang được yêu cầu.
- `If-Modified-Since` : chỉ định khi trình duyệt nhận được tài nguyên được yêu cầu lần cuối. Nếu tài nguyên không thay đổi kể từ thời điểm đó, máy chủ có thể hướng dẫn máy khách sử dụng bản sao được lưu trong bộ nhớ cache của nó, sử dụng phản hồi có mã trạng thái 304.
- `If-None-Match` : chỉ định một *thẻ thực thể*, là một mã định danh biểu thị nội dung của nội dung thư. Trình duyệt gửi thẻ thực thể mà máy chủ đã cấp cùng với tài nguyên được yêu cầu khi nó được nhận lần cuối. Máy chủ có thể sử dụng thẻ thực thể để xác định xem trình duyệt có thể sử dụng bản sao tài nguyên được lưu trong bộ nhớ cache của nó hay không.
- `Origin` : được sử dụng trong *cross-domain Ajax requests* để chỉ ra miền mà yêu cầu bắt nguồn từ đó.
- `Referer` : chỉ định URL mà yêu cầu hiện tại bắt nguồn từ URL đó.
- `User-Agent` : cung cấp thông tin về trình duyệt hoặc phần mềm máy khách khác đã tạo yêu cầu.

#### Response Headers

- `Access-Control-Allow-Origin` : cho biết liệu tài nguyên có được truy xuất thông qua *cross-domain Ajax requests* hay không.
- `Cache-control` : truyền chỉ thị bộ đệm cho trình duyệt (VD : `no-cache`)
- `ETag` : máy khách có thể gửi số nhận dạng này trong các yêu cầu trong tương lai cho cùng một tài nguyên trong tiêu đề `If-None-Match` để thông báo cho máy chủ phiên bản tài nguyên nào mà trình duyệt hiện đang lưu trong bộ đệm của nó.
- `Expires` : cho trình duyệt biết nội dung của thông báo hợp lệ trong bao lâu. Trình duyệt có thể sử dụng bản sao được lưu trong bộ nhớ cache của tài nguyên này cho đến thời điểm này.
- `Location` : được sử dụng trong các phản hồi chuyển hướng (những phản hồi có mã trạng thái bắt đầu bằng 3) để chỉ định mục tiêu của chuyển hướng.
- `Pragma` : chuyển các chỉ thị bộ nhớ đệm tới trình duyệt.
- `Server` : cung cấp thông tin về phần mềm máy chủ web đang được sử dụng.
- `Set-cookie`: cấp cho trình duyệt cookie mà nó sẽ gửi lại cho máy chủ trong các yêu cầu tiếp theo.
- `WWW-Authenticate` : được sử dụng trong các phản hồi có mã trạng thái 401 để cung cấp chi tiết về (các) loại xác thực mà máy chủ hỗ trợ.
- `X-Frame-Options` : cho biết vị trí và cách thức phản hồi hiện tại có thể được tải trong khung trình duyệt.