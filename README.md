# ROLLY – Quản lý chi tiêu cá nhân

Dự án ứng dụng quản lý chi tiêu cá nhân bằng Flutter/Dart của NhatHao-2805, kèm báo cáo đồ án để mọi người tham khảo.

> **Tình trạng bản nguồn:** Khi chuẩn bị kho mã, các file Dart được kiểm tra trong `lib/` (gồm `main.dart`, đăng nhập, dịch vụ AI và cơ sở dữ liệu) chỉ chứa byte NUL. Các file được giữ nguyên như bản gốc, chưa khôi phục hoặc xác nhận chạy được. Cần bổ sung lại mã nguồn hợp lệ từ bản sao lưu trước khi sử dụng các bước chạy bên dưới.

## Báo cáo đồ án

📄 [Tải báo cáo Word – baocaoDACS3.docx](baocaoDACS3.docx)

Báo cáo gốc được đưa kèm dự án theo yêu cầu tác giả. Có thể chọn file rồi bấm **Download raw file** trên GitHub để tải và mở bằng Microsoft Word hoặc phần mềm hỗ trợ DOCX.

## Thành phần dự án

Cấu trúc thư mục có các phần dành cho giao dịch, danh mục, ví, ngân sách, thống kê, đăng nhập, quản trị và chatbot. Đây là mô tả theo tên file; chức năng thực tế chưa thể kiểm chứng do tình trạng mã nguồn nêu trên.

Các thư viện khai báo trong `pubspec.yaml`:

- Flutter/Dart: xây dựng giao diện ứng dụng.
- Provider: quản lý trạng thái.
- sqflite và path: cơ sở dữ liệu SQLite và đường dẫn.
- fl_chart, intl: biểu đồ, định dạng tiền và ngày.
- http, flutter_dotenv: gọi API và đọc cấu hình môi trường; cấu hình dự án có ghi chú tích hợp Gemini.

## Yêu cầu

- Flutter SDK đi kèm Dart tương thích `^3.10.7` theo `pubspec.yaml`.
- Git và Android Studio hoặc VS Code có hỗ trợ Flutter.
- Android SDK và thiết bị Android hoặc máy ảo nếu chạy Android.
- Cần khôi phục mã Dart hợp lệ trước khi chạy. Có sẵn thư mục nhiều nền tảng nhưng chưa xác nhận tương thích từng nền tảng.

## Cài đặt và chạy

Sau khi khôi phục mã nguồn:

```sh
git clone https://github.com/NhatHao-2805/ROLLY-QuanLyChiTieu.git
cd ROLLY-QuanLyChiTieu
flutter doctor
flutter pub get
```

Tạo file `.env` ở thư mục gốc vì `pubspec.yaml` khai báo file này trong assets. Nếu dùng API Gemini, điền cấu hình riêng theo đúng tên biến mà mã nguồn đã khôi phục sử dụng. Bản hiện tại chưa xác định được tên biến nên không cung cấp khóa mẫu giả định.

```sh
flutter devices
flutter run -d <device-id>
```

Kiểm tra và tạo APK Android khi mã nguồn đã hoàn chỉnh:

```sh
flutter analyze
flutter test
flutter build apk --release
```

APK thường được tạo tại `build/app/outputs/flutter-apk/app-release.apk`.

## Cách dùng

Sau khi khôi phục và chạy thành công, tham khảo báo cáo Word để xem quy trình nghiệp vụ và giao diện của đồ án. Các phần giao dịch, danh mục, ngân sách, thống kê và chatbot được tổ chức trong `lib/views/`. Chưa có thông tin đăng nhập hay quy trình thao tác đã được kiểm chứng trong bản nguồn hiện tại.

## Cấu trúc thư mục

```text
lib/
  assets/images/   Hình ảnh
  database/        Thành phần cơ sở dữ liệu
  models/          Mô hình dữ liệu
  services/        Dịch vụ API
  viewmodels/      Quản lý trạng thái và logic
  views/           Các màn hình
  widgets/         Thành phần giao diện
android/, ios/     Dự án nền tảng di động
web/, windows/     Dự án nền tảng web và Windows
linux/, macos/     Dự án nền tảng desktop
test/              Thư mục kiểm thử
pubspec.yaml       Cấu hình và thư viện
baocaoDACS3.docx    Báo cáo đồ án gốc
```

## Chú ý

- Bản tải lên giữ lại dữ liệu nguồn hiện có; không coi đây là bản phát hành đã chạy hoặc kiểm thử thành công.
- `.env`, khóa ký ứng dụng, dữ liệu SQLite cá nhân, thư mục build, cache và cấu hình IDE cục bộ không đưa lên GitHub.
- Không commit API key hoặc mật khẩu. Khóa được đóng gói trong ứng dụng client vẫn có thể bị trích xuất; khi triển khai thực tế nên gọi API qua backend bảo vệ khóa.
- Sao lưu dữ liệu trước khi gỡ ứng dụng hoặc thay đổi cơ sở dữ liệu.
- Khi tham khảo hoặc trích dẫn báo cáo, vui lòng ghi nguồn tác giả. Kho mã chưa có giấy phép sử dụng riêng; liên hệ tác giả nếu muốn tái sử dụng hoặc phân phối.

## Tác giả

[NhatHao-2805](https://github.com/NhatHao-2805)
