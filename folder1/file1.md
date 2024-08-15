
# Ghi Chú Về Controllers và Action Methods

## Giới Thiệu Về Controllers
- Trong mô hình kiến trúc Model-View-Controller (MVC), controllers đóng vai trò như nhạc trưởng của ứng dụng web.
- Controllers xử lý các yêu cầu HTTP đến, tương tác với model (tầng dữ liệu), và chọn view phù hợp để trả về phản hồi cho người dùng.

## Mục Đích
- **Tổ Chức Logic**: Controllers nhóm các hành động cùng làm việc trên một loại dữ liệu hoặc chức năng cụ thể.
- **Xử Lý Yêu Cầu**: Chúng xử lý các yêu cầu, truy xuất dữ liệu cần thiết và chuẩn bị phản hồi.
- **Chọn View**: Controllers thường chọn view phù hợp để render, truyền dữ liệu (model) tới view để trình bày.

## Cú Pháp và Quy Ước
- **Đặt Tên Class**: Tên của các lớp controller nên kết thúc bằng "Controller" (ví dụ: `HomeController`, `ProductsController`).
- **Kế Thừa**: Controllers kế thừa từ lớp cơ sở `Controller` (hoặc `ControllerBase` cho API controllers).
- **Đặt Tên Phương Thức Hành Động**: Các phương thức hành động có thể có bất kỳ tên phương thức hợp lệ nào của C#.
- **Các Kiểu Trả Về**: Phương thức hành động có thể trả về các loại khác nhau bao gồm:
  - `IActionResult`: Một giao diện chung cho phép bạn trả về nhiều loại kết quả khác nhau (views, content, redirects, v.v.).
  - `string`, `int`, v.v.: Với API controllers, bạn có thể trả về dữ liệu thô.

## Attribute Routing
- Attribute routing cho phép bạn định nghĩa các route trực tiếp trên các lớp controller và phương thức hành động bằng cách sử dụng attributes:
  - `[Route]` Attribute: Xác định template route cơ bản cho controller hoặc action.
  - `[HttpGet]`, `[HttpPost]`, v.v.: Chỉ định HTTP method mà action sẽ xử lý.

## Trách Nhiệm Của Controller
- **Xử Lý Yêu Cầu**: Xử lý các yêu cầu đến và trích xuất dữ liệu liên quan (từ tham số route, chuỗi truy vấn hoặc nội dung yêu cầu).
- **Tương Tác Với Model**: Truy xuất dữ liệu từ model (cơ sở dữ liệu, dịch vụ) hoặc cập nhật model dựa trên yêu cầu.
- **Chọn View**: Xác định view nào sẽ được render và cung cấp dữ liệu model cần thiết cho view.
- **Xử Lý Lỗi**: Xử lý lỗi một cách tinh tế và trả về các phản hồi phù hợp.

## Action Results

### ContentResult
- **Linh Hoạt**: Bạn có quyền kiểm soát hoàn toàn nội dung bạn gửi và header `Content-Type`, cho phép bạn tùy chỉnh phản hồi theo yêu cầu cụ thể của client.
- **Nhẹ Nhàng**: `ContentResult` hiệu quả vì nó không liên quan đến quá trình render view phức tạp.
- **Trực Tiếp**: Lý tưởng cho các tình huống bạn muốn trả về các thông báo văn bản đơn giản, phản hồi API, hoặc các định dạng nội dung tùy chỉnh.

### JsonResult
- **Định Dạng Chuẩn Hóa**: JSON là định dạng phổ biến cho việc biểu diễn dữ liệu có cấu trúc.
- **Serialization**: ASP.NET Core tự động serialize các đối tượng của bạn thành JSON.
- **Content Type**: `JsonResult` tự động thiết lập header `Content-Type` thành `application/json`.
- **Thân Thiện Với API**: Hoàn hảo cho việc xây dựng RESTful APIs hoặc trả về dữ liệu cho JavaScript phía client tiêu thụ.

### File Results
- **VirtualFileResult**: Phục vụ tệp từ thư mục gốc web của ứng dụng (`wwwroot` theo mặc định) hoặc từ đường dẫn ảo.
- **PhysicalFileResult**: Phục vụ tệp từ đường dẫn tuyệt đối trên hệ thống tệp của máy chủ.
- **FileContentResult**: Phục vụ tệp từ một mảng byte trong bộ nhớ.

### IActionResult
- Giao diện `IActionResult` là một khái niệm cốt lõi trong ASP.NET Core MVC. Nó đóng vai trò như kiểu trả về cho các phương thức hành động, cung cấp sự linh hoạt và cho phép bạn trả về các loại phản hồi khác nhau tùy thuộc vào ngữ cảnh của yêu cầu.

### Kết Quả Mã Trạng Thái (Status Code Results)
- **OkResult**: Chỉ ra rằng yêu cầu thành công (HTTP 200).
- **BadRequestResult**: Chỉ ra rằng có lỗi từ phía client (HTTP 400).
- **NotFoundResult**: Chỉ ra rằng tài nguyên yêu cầu không tìm thấy (HTTP 404).
- **UnauthorizedResult**: Chỉ ra rằng yêu cầu yêu cầu xác thực (HTTP 401).
- **ForbiddenResult**: Chỉ ra rằng người dùng không được phép truy cập tài nguyên (HTTP 403).
- **StatusCodeResult**: Cho phép bạn trả về bất kỳ mã trạng thái HTTP nào tùy ý.

### Redirect Results
- **RedirectResult**: Chuyển hướng tới một URL được chỉ định (có thể là tuyệt đối hoặc tương đối).
- **RedirectToActionResult**: Chuyển hướng tới một phương thức hành động cụ thể trong controller.
- **LocalRedirectResult**: Chuyển hướng tới một URL nội bộ trong cùng ứng dụng.
