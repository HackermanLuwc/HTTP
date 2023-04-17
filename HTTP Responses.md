#HTTP Responses
Một phản hồi HTTP điển hình như sau:
```HTTP
HTTP/1.1 200 OK
Date: Tue, 19 Apr 2011 09:23:32 GMT
Server: Microsoft-IIS/6.0
X-Powered-By: ASP.NET
Set-Cookie: tracking=tI8rk7joMx44S2Uu85nSWc
X-AspNet-Version: 2.0.50727
Cache-Control: no-cache
Pragma: no-cache
Expires: Thu, 01 Jan 1970 00:00:00 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 1067
<!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0 Transitional//EN” “http://
www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd”><html xmlns=”http://
www.w3.org/1999/xhtml” ><head><title>Your details</title>
...
```

- Phiên bản HTTP đang được sử dụng ( `HTTP/1.1` ).
- Mã trạng thái số cho biết kết quả của yêu cầu. `200` là mã trạng thái phổ biến nhất; điều đó có nghĩa là yêu cầu đã thành công và tài nguyên được yêu cầu đang được trả lại.
- Một "cụm từ kết luận" bằng văn bản mô tả thêm trạng thái của phản hồi. Điều này có thể có bất kỳ giá trị nào và không được các trình duyệt hiện tại sử dụng cho bất kỳ mục đích nào.

Dưới đây là một số điểm quan tâm khác trong đoạn phản hồi HTTP:
- Tiêu đề `Server`( máy chủ ) chứa biểu ngữ cho biết phần mềm máy chủ web đang được sử dụng và đôi khi là các chi tiết khác như mô-đun đã cài đặt và hệ điều hành máy chủ. Thông tin chứa có thể đúng hoặc sai.
- Tiêu đề `Set-Cookie` cấp cho trình duyệt một cookie khác; điều này được gửi lại trong tiêu đề `Cookie` của các yêu cầu tiếp theo tới máy chủ này.
- Tiêu đề `Pragma` cho biết trình duyệt không lưu trữ phản hồi trong bộ đệm của nó. Tiêu đề `Expires` chỉ ra rằng nội dung phản hồi đã hết hạn trong quá khứ và do đó không được lưu vào bộ nhớ đệm. Các hướng dẫn này thường được đưa ra khi nội dung động được trả lại để đảm bảo rằng các trình duyệt có được phiên bản mới của nội dung này trong những lần tiếp theo.
- Hầu như tất cả các phản hồi HTTP đều chứa nội dung thư theo dòng trống sau tiêu đề. Tiêu đề `Content-Type` chỉ ra rằng phần nội dung của thư này chứa tài liệu HTML.
- Tiêu đề `Content-Length` cho biết độ dài của nội dung thư tính bằng byte.