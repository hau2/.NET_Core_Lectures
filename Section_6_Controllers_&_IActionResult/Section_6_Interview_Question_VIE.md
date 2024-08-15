
# Câu hỏi phỏng vấn Phần 6

## Controller là gì?
**Controller** là một lớp dùng để nhóm các phương thức hành động lại với nhau. Các phương thức hành động sẽ thực hiện các thao tác khi nhận được yêu cầu và trả về `IActionResult` để gửi kết quả phản hồi về trình duyệt.

### Nhiệm vụ chính của Controller:
- Xử lý các yêu cầu (như nhận tham số truy vấn, nội dung yêu cầu, cookie, tiêu đề, v.v.)
- Kiểm tra tính hợp lệ của yêu cầu
- Gọi các mô hình (logic nghiệp vụ)
- Tạo các đối tượng ViewModel hoặc DTO
- Gửi đối tượng DTO tới view (trong trường hợp trả về view)

Lớp controller cần có hậu tố `Controller` (ví dụ: `HomeController`) hoặc áp dụng thuộc tính `[Controller]`.

## Phương thức hành động là gì?
**Phương thức hành động** là một phương thức công khai trong lớp controller, được thực thi khi nhận yêu cầu HTTP với một số hạn chế sau:
- Phải là phương thức công khai
- Không thể bị nạp chồng (trừ khi sử dụng các phương thức HTTP khác nhau)
- Không thể là phương thức tĩnh

## Các loại kết quả hành động trong ASP.NET Core:
- **IActionResult**: Đại diện cho kết quả của một phương thức hành động.
- **ActionResult**: Là triển khai mặc định của `IActionResult`.
- **ContentResult**: Trả về kết quả dạng văn bản.
- **EmptyResult**: Thực thi mà không trả về nội dung.
- **JsonResult**: Định dạng đối tượng dưới dạng JSON.
- **PartialViewResult**: Trả về một phần của view.
- **ViewResult**: Trả về một view đầy đủ.
- **ViewComponentResult**: Hiển thị một thành phần của view.
- **StatusCodeResult**: Gửi mã trạng thái HTTP cụ thể.
- **UnauthorizedResult**: Gửi mã trạng thái HTTP 401.
- **BadRequestResult**: Gửi mã trạng thái HTTP 400.
- **NotFoundResult**: Gửi mã trạng thái HTTP 404.
- **ObjectResult**: Gửi dữ liệu của đối tượng được chỉ định trong nội dung phản hồi.
- **FileResult**: Gửi nội dung của tệp trong phản hồi.
- **RedirectToActionResult**: Chuyển hướng yêu cầu tới một phương thức hành động cụ thể (HTTP 301/302).
- **LocalRedirectResult**: Chuyển hướng yêu cầu tới một URL nội bộ (trong cùng miền).
- **RedirectResult**: Chuyển hướng tới một URL nội bộ hoặc bên ngoài (HTTP 301/302).

## HttpContext là gì?
`HttpContext` là đối tượng bao bọc toàn bộ thông tin liên quan đến yêu cầu HTTP. Bạn có thể truy cập `HttpContext` trong controller bằng thuộc tính `ControllerBase.HttpContext`, và nó có các thuộc tính như `Items`, `Request`, `Response`, `Session`, và `User`.
