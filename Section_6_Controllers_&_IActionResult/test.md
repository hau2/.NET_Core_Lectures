
# Bảng Gian Lận Phần (PPT)

## Giới Thiệu Về Controllers
- Controller là một class dùng để nhóm các hành động (hoặc action methods).
- Action methods thực hiện các thao tác khi nhận được request và trả về kết quả (response).

### Tạo Controllers
- Tên class nên được đặt hậu tố "Controller" (ví dụ: HomeController).
- Thuộc tính [Controller] được áp dụng cho class hoặc class cơ sở của nó.

### Trách Nhiệm Của Controllers
- Đọc request và trích xuất dữ liệu (query string parameters, request body, cookies, headers, v.v.).
- Gọi các mô hình và phương thức logic nghiệp vụ (thường có dưới dạng services).
- Kiểm tra tính hợp lệ của các chi tiết trong request.
- Chuẩn bị và lựa chọn loại phản hồi nào sẽ gửi lại.

### ContentResult
- Đại diện cho bất kỳ loại phản hồi nào dựa trên MIME type được chỉ định (ví dụ: text/plain, application/json).
- Ví dụ: `return new ContentResult() { Content = "nội dung", ContentType = "loại nội dung" };`

### JsonResult
- Đại diện cho một đối tượng ở định dạng JSON.
- Ví dụ: `return new JsonResult(your_object);`

### Kết Quả Tệp (File Results)
- Gửi nội dung của một tệp dưới dạng response.
- Các loại: `VirtualFileResult`, `PhysicalFileResult`, `FileContentResult`.

### IActionResult
- Giao diện cha cho tất cả các lớp kết quả hành động như `ContentResult`, `JsonResult`, `StatusCodeResult`, v.v.
- Cho phép linh hoạt trong việc trả về các loại kết quả khác nhau.

### Kết Quả Mã Trạng Thái (Status Code Results)
- Gửi phản hồi rỗng với mã trạng thái được chỉ định (ví dụ: 200, 400, 404, 500).
- Ví dụ: `return new StatusCodeResult(status_code);`

### Kết Quả Chuyển Hướng (Redirect Results)
- Chuyển hướng trình duyệt với phản hồi HTTP 302 hoặc 301 đến một action hoặc URL khác.
- Các loại: `RedirectToActionResult`, `LocalRedirectResult`, `RedirectResult`.
