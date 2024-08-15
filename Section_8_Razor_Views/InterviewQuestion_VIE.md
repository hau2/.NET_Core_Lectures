
# Phần 8: Các câu hỏi phỏng vấn và câu trả lời

## Mô hình MVC là gì?

**Model-View-Controller (MVC)** là một mẫu kiến trúc tách ứng dụng thành ba thành phần logic chính: model, view và controller. Điều quan trọng là cần lưu ý rằng mẫu này không liên quan đến mô hình phân lớp. Mô hình MVC hoạt động trên phần logic phần mềm, trong khi mô hình phân lớp quyết định cách thức và nơi chúng ta đặt cơ sở dữ liệu và máy chủ ứng dụng.

Trong một ứng dụng tuân theo mô hình MVC, mỗi thành phần có một vai trò cụ thể:
- **Model**: Chứa dữ liệu và logic kinh doanh. Model không xử lý các yêu cầu HTTP.
- **Views**: Chỉ hiển thị thông tin.
- **Controllers**: Xử lý và phản hồi đầu vào của người dùng và quyết định model nào sẽ được truyền cho view nào.

Điều này được gọi là **phân chia trách nhiệm**. Nó giúp ứng dụng dễ phát triển và bảo trì hơn khi tăng độ phức tạp.

Mặc dù MVC là một trong những mẫu phổ biến và lâu đời nhất, các mẫu thay thế như **MVVM** (Model-View-ViewModel), **MVP** (Model-View-Presenter) và **MVA** (Model-View-Adapter) cũng đã xuất hiện.

## Giải thích vai trò của các thành phần khác nhau trong mô hình MVC

- **Model**: Đại diện cho tất cả dữ liệu và logic kinh doanh mà người dùng tương tác trong một ứng dụng web. Trong ASP.NET Core, model được đại diện bởi các lớp C# lưu trữ dữ liệu và logic kinh doanh. Thư mục 'Models' lưu trữ các lớp này. Bạn cũng có thể tạo các lớp **POCO** (Plain Old CLR Object) chỉ để lưu trữ dữ liệu và viết logic kinh doanh trong các lớp model riêng biệt (được gọi là 'Services').

- **View**: Đại diện cho logic giao diện người dùng của ứng dụng, mà trong các ứng dụng web chính là mã HTML được gửi đến trình duyệt của người dùng. Mã HTML trong view có thể được tạo động dựa trên dữ liệu của model.

- **Controller**: Hoạt động như một giao diện giữa Model và View. Nó xử lý logic kinh doanh và các yêu cầu đến, thao tác dữ liệu bằng cách sử dụng Model, và tương tác với Views để tạo ra kết quả cuối cùng. Trong ASP.NET, đây là các lớp C# liên kết model và view với nhau. Controllers có các phương thức hành động phản hồi các yêu cầu HTTP từ trình duyệt, truy xuất dữ liệu từ model và chuyển nó đến view để hiển thị động.

## Giải thích sự khác biệt giữa ViewData và ViewBag

1. **ViewData** là một tập hợp Key-Value dưới dạng Dictionary.
   **ViewBag** là một thuộc tính dynamic, thuộc kiểu "object".

2. **ViewData** là một thuộc tính của lớp `Microsoft.AspNetCore.Mvc.Controller`.
   **ViewBag** là một thuộc tính dynamic của lớp `Microsoft.AspNetCore.Mvc.Controller`.

3. **ViewBag** sử dụng nội bộ **ViewData**, điều này có nghĩa là dữ liệu được đặt trong **ViewData** có thể được truy cập bằng **ViewBag**, vì **ViewBag** giúp truy cập dễ dàng hơn.

4. Phải chuyển đổi kiểu khi đọc giá trị từ **ViewData**, trong khi không cần chuyển đổi kiểu khi đọc từ **ViewBag**.

5. Thời gian tồn tại của cả **ViewData** và **ViewBag** là theo từng yêu cầu. Chúng sẽ tự động bị xóa sau khi xử lý yêu cầu. Một **ViewData** mới sẽ được tạo ra cho mỗi yêu cầu mới.

## Giải thích về Strongly-Typed Views

Strongly-Typed Views là các view gắn chặt với một lớp model. Những view này có thể nhận một đối tượng model (của một lớp model cụ thể) từ controller. Controller có thể cung cấp đối tượng model bằng cách sử dụng phương thức `return View(model)` ở cuối phương thức hành động.

Một số lợi ích của Strongly-Typed Views bao gồm:
- Sử dụng chỉ thị **@model** để chỉ định lớp model ở đầu view.
- Sử dụng các trình trợ giúp thẻ mạnh như **asp-for** trong views.
- Hỗ trợ **IntelliSense** khi truy cập các thuộc tính của model.
- Kiểm tra lỗi tại thời điểm biên dịch để đảm bảo các thuộc tính không tồn tại sẽ gây ra lỗi.
