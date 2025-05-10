# vmtouch - Công cụ Virtual Memory Toucher

## Công cụ chuẩn đoán và điều khiển bộ nhớ đệm hệ thống tập tin

vmtouch là một công cụ dùng để tìm hiểu và điều khiển bộ nhớ đệm hệ thống tập tin của các hệ thống unix và giống unix. Công cụ được cấp phép BSD nên bạn có thể sử dụng theo nhu cầu.

### Hướng dẫn cài đặt nhanh:

```
$ git clone https://github.com/pnson/vmtouch.git
$ cd vmtouch
$ make
$ sudo make install
```

### Cấu trúc dự án:

- `vmtouch.c`: Mã nguồn chính của chương trình
- `vmtouch.pod`: Tài liệu hướng dẫn sử dụng
- `Makefile`: File cấu hình để biên dịch dự án
- `TUNING.md`: Hướng dẫn tinh chỉnh các tham số hệ thống
- `LICENSE`: Thông tin giấy phép BSD
- `CHANGES`: Lịch sử thay đổi của dự án
- `TODO`: Danh sách các tính năng dự kiến phát triển

### Chức năng chính:

- Kiểm tra tình trạng của bộ nhớ đệm (cache) cho các tập tin
- Tải tập tin vào bộ nhớ đệm (touching)
- Xóa tập tin khỏi bộ nhớ đệm (evicting)
- Khóa tập tin trong bộ nhớ vật lý
- Phân tích dung lượng bộ nhớ đệm theo nhiều tiêu chí

### Cách sử dụng:

```
vmtouch [TÙY CHỌN] ... TẬP TIN HOẶC THƯ MỤC ...
```

Các tùy chọn:
- `-t` Tải các trang vào bộ nhớ
- `-e` Xóa các trang khỏi bộ nhớ
- `-l` Khóa các trang trong bộ nhớ vật lý bằng mlock(2)
- `-L` Khóa các trang trong bộ nhớ vật lý bằng mlockall(2)
- `-d` Chế độ daemon
- `-m <size>` Kích thước tập tin tối đa để xử lý
- `-p <range>` Sử dụng phần được chỉ định thay vì toàn bộ tập tin
- `-f` Theo liên kết tượng trưng
- `-F` Không quét các hệ thống tập tin khác
- `-h` Đếm cả các bản sao hard-linked
- `-i <pattern>` Bỏ qua tập tin và thư mục khớp với mẫu
- `-I <pattern>` Chỉ xử lý tập tin khớp với mẫu
- `-b <list file>` Lấy danh sách tập tin hoặc thư mục từ tập tin
- `-0` Trong chế độ batch (-b) phân tách đường dẫn bằng byte NUL thay vì dòng mới
- `-w` Đợi cho đến khi tất cả các trang được khóa (chỉ hữu ích với -d)
- `-P <pidfile>` Ghi một pidfile (chỉ hữu ích với -l hoặc -L)
- `-o <type>` Đầu ra ở định dạng máy đọc được. 'kv' cho cặp key=value
- `-v` Chi tiết
- `-q` Yên lặng

### Ví dụ sử dụng:

1. Kiểm tra mức độ cache của một tập tin:
   ```
   vmtouch /path/to/file
   ```

2. Tải toàn bộ thư mục vào bộ nhớ đệm:
   ```
   vmtouch -t /path/to/directory
   ```

3. Xóa bộ nhớ đệm cho một tập tin lớn:
   ```
   vmtouch -e /path/to/large/file
   ```

4. Khóa một ứng dụng quan trọng trong bộ nhớ:
   ```
   vmtouch -l /path/to/critical/app
   ```

### Liên hệ hỗ trợ:

Vui lòng liên hệ Phạm Lê Ngọc Sơn để được hỗ trợ hoặc báo cáo lỗi.

### Tác giả:

vmtouch được phát triển bởi Phạm Lê Ngọc Sơn
