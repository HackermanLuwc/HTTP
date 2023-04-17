# HTTP Resquests
Tất cả các thông báo HTTP (yêu cầu và phản hồi) bao gồm một hoặc nhiều tiêu đề, mỗi trên một dòng riêng biệt, theo sau là một dòng trống bắt buộc, tiếp theo là một nội dung thư tùy chọn. Một yêu cầu HTTP điển hình như sau:
```HTTP
GET /auth/488/YourDetails.ashx?uid=129 HTTP/1.1
Accept: application/x-ms-application, image/jpeg, application/xaml+xml,
image/gif, image/pjpeg, application/x-ms-xbap, application/x-shockwaveflash, */*
Referer: https://mdsec.net/auth/488/Home.ashx
Accept-Language: en-GB
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64;
Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR
3.0.30729; .NET4.0C; InfoPath.3; .NET4.0E; FDM; .NET CLR 1.1.4322)
Accept-Encoding: gzip, deflate
Host: mdsec.net
Connection: Keep-Alive
Cookie: SessionId=5B70C71F3FD4968935CDB6682E545476
```

Dòng đầu tiên của mọi yêu cầu HTTP bao gồm ba mục, được phân tách bằng dấu cách:
- Một động từ chỉ phương thức HTTP. Phương pháp được sử dụng phổ biến nhất là `GET` , có chức năng lấy tài nguyên từ máy chủ web. Nếu `GET requests` không có nội dung, thì không có thêm dữ liệu nào theo sau khoảng trống dòng sau tiêu đề thư.
- The requested URL(URL được yêu cầu).URL thường hoạt động như một tên cho tài nguyên được yêu cầu, cùng với một chuỗi truy vấn tùy chọn chứa các tham số mà máy khách đang chuyển đến tài nguyên đó. Chuỗi truy vấn được chỉ định bằng ký tự `?` trong URL. Ví dụ chứa một tham số duy nhất với tên `uid` và giá trị `129`.
- Phiên bản HTTP đang được sử dụng. Các phiên bản HTTP duy nhất được sử dụng phổ biến trên Internet là 1.0 và 1.1, và hầu hết các trình duyệt sử dụng phiên bản 1.1 theo mặc định. Có một số khác biệt giữa các thông số kỹ thuật của hai phiên bản; tuy nhiên, sự khác biệt duy nhất mà bạn có thể gặp phải khi tấn công các ứng dụng web là trong phiên bản 1.1, tiêu đề yêu cầu của `Host`(máy chủ) là bắt buộc.

Dưới đây là một số điểm quan tâm khác trong các yêu cầu:
- Tiêu đề `Referer` được sử dụng để hiển thị địa chỉ URL từ nguồn yêu cầu đó (ví dụ: do người dùng đã nhấp vào liên kết trên trang đó).Lưu ý rằng tiêu đề này đã bị viết sai chính tả trong đặc tả HTTP ban đầu, và phiên bản sai chính tả đã được giữ lại kể từ đó.
- Tiêu đề `User-Agent` được sử dụng để cung cấp thông tin về trình duyệt hoặc phần mềm máy khách khác đã tạo ra yêu cầu. Lưu ý rằng hầu hết các trình duyệt bao gồm tiền tố Mozilla vì lý do lịch sử. Đây là chuỗi `User-Agent` được sử dụng đầu tiên bởi trình duyệt Netscape thống trị và  các trình duyệt khác muốn khẳng định với các trang web rằng chúng tương thích với tiêu chuẩn này. Cũng như nhiều điều kỳ quặc trong lịch sử điện toán, nó đã trở nên như vậy và vẫn tiếp tục được gữ lại, ngay cả trên phiên bản Internet Explorer hiện nay, nó đã đưa ra yêu cầu được hiển thị trong ví dụ.
- Tiêu đề `Host` chỉ định tên máy chủ xuất hiện trong tất cả URL đang được truy cập. Điều này là cần thiết khi nhiều trang web được lưu trữ trên cùng một máy chủ, vì URL được gửi trong dòng đầu tiên của yêu cầu thường không chứa tên máy chủ.
- Tiêu đề Cookie được sử dụng để gửi các tham số bổ sung mà máy chủ đã cấp cho khách hàng.