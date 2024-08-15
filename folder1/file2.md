
# IActionResult trong ASP.NET Core

## Tổng Quan
Trong ASP.NET Core, việc thiết lập kiểu trả về của tất cả các phương thức hành động thành `IActionResult` là một thực hành phổ biến. Điều này cho phép bạn trả về bất kỳ loại kết quả hành động nào, chẳng hạn như `ContentResult`, `JsonResult`, `FileResult`, v.v. Nhưng điều này hoạt động như thế nào? `IActionResult` là giao diện cha của tất cả các kết quả hành động trong ASP.NET Core, có nghĩa là tất cả các loại kết quả này đều triển khai giao diện này.

## Hiểu Về IActionResult
Khi bạn chỉ định `IActionResult` làm kiểu trả về, bạn có thể trả về bất kỳ loại dẫn xuất nào như `ContentResult`, `JsonResult`, `FileResult`, và nhiều loại khác. Điều này tương tự như việc sử dụng lớp cha hoặc giao diện làm kiểu trả về trong C#, nơi bạn có thể trả về bất kỳ đối tượng con nào.

### Ví Dụ:
Giả sử bạn có một phương thức hành động trả về một tệp. Bạn có thể sử dụng `IActionResult` làm kiểu trả về và vẫn trả về một `FileContentResult` hoặc bất kỳ loại kết quả nào khác:

```csharp
public IActionResult DownloadFile()
{
    var fileBytes = System.IO.File.ReadAllBytes(@"C:iles\sample.pdf");
    return new FileContentResult(fileBytes, "application/pdf");
}
```

Ở đây, mặc dù kiểu trả về là `IActionResult`, phương thức vẫn trả về `FileContentResult`.

## Lợi Ích Của Việc Sử Dụng IActionResult
Sử dụng `IActionResult` làm kiểu trả về cung cấp sự linh hoạt. Ví dụ, hãy xem xét một ứng dụng yêu cầu người dùng phải đăng nhập và cung cấp một ID sách hợp lệ:

### Ví Dụ:
```csharp
public IActionResult GetBook(int bookId, bool isLoggedIn)
{
    if (!isLoggedIn)
    {
        return Unauthorized("User must be authenticated");
    }

    if (bookId <= 0 || bookId > 1000)
    {
        return BadRequest("Book ID must be between 1 and 1000");
    }

    var bookFile = System.IO.Path.Combine(_webRootPath, "books", $"{bookId}.pdf");
    if (!System.IO.File.Exists(bookFile))
    {
        return NotFound("Book not found");
    }

    var fileBytes = System.IO.File.ReadAllBytes(bookFile);
    return File(fileBytes, "application/pdf");
}
```

Trong ví dụ này, phương thức có thể trả về các loại kết quả khác nhau như `Unauthorized`, `BadRequest`, `NotFound`, hoặc `File`. Tất cả các kiểu trả về này đều được phép vì chúng triển khai giao diện `IActionResult`.

## Các Kết Quả Hành Động Phổ Biến
- **ContentResult**: Trả về văn bản thuần túy hoặc nội dung HTML.
- **JsonResult**: Trả về dữ liệu JSON.
- **FileResult**: Trả về một tệp, chẳng hạn như PDF, hình ảnh hoặc dữ liệu nhị phân khác.
- **RedirectResult**: Chuyển hướng đến một URL khác.
- **ViewResult**: Trả về một view (thường được sử dụng trong các ứng dụng MVC).

## Tóm Tắt
Giao diện `IActionResult` là một tính năng mạnh mẽ trong ASP.NET Core cho phép bạn trả về nhiều loại phản hồi khác nhau từ các phương thức hành động của mình. Bằng cách sử dụng `IActionResult`, bạn giữ cho mã của mình linh hoạt và dễ bảo trì, cho phép ứng dụng của bạn xử lý các loại kết quả khác nhau một cách liền mạch.

Trong các phần tiếp theo, bạn sẽ khám phá thêm về các loại kết quả hành động khác và các trường hợp sử dụng cụ thể của chúng.
