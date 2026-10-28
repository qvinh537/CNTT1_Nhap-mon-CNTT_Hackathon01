# BÀI LÀM – HACKATHON 01

- **Mã đề:** 16
- **Họ tên: Phạm Quang Vinh** 
- **Lớp:CNTT1** 
- **Link repository:** 
- **Hệ điều hành: Windows** 

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
Lệnh đường dẫn tuyệt đối là: pwd
Lệnh liệt kê nội dung gồm cả file ẩn là: ls
Lệnh di chuyển file là: mv
Lệnh sao chép logo vào media là: cp
Lệnh xóa file là: rm
Lệnh duy chuyển thư mục là: cd.\
Lệnh quay lại thư mục là: cd..
Lệnh đọc nội dung trong thư mục là: get-content
Lệnh lọc nội dung trong thư mục là: select-string
Lệnh ghi nội dung từ file này sang file khác là: >>
Lệnh lọc 2 dòng đầu tiên là: -head

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
- Đường dẫn tuyệt đối là: 
pwd

Path
----
C:\Users\admin\Desktop\sua-may-tinh-website

- Liệt kê nội dung gồm cả file ẩn là:
 ls

    Directory: C:\Users\admin\Desktop\sua-may-tinh-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        10/28/2026   7:43 AM                backup
d-----        10/28/2026   7:48 AM                data
d-----        10/28/2026   7:42 AM                docs
d-----        10/28/2026   7:48 AM                logs
d-----        10/28/2026   7:43 AM                media
------        10/27/2026   1:32 AM             72 .env
-a----        10/28/2026   7:50 AM           2240 bai_lam.md
-a----        10/27/2026   1:32 AM           6767 logo-sua-may-tinh.png
-a----        10/27/2026   1:32 AM             61 quy-dinh-bao-hanh.txt
------        10/27/2026   1:32 AM             22 temp_241.tmp

- Di chuyển file quy-dinh-bao-hanh.txt vào docs và file logo-sua-may-tinh.png vào media
 mv quy-dinh-bao-hanh.txt docs
 mv logo-sua-may-tinh.png media
- Sao chép logo từ media vào backup
cp logo-sua-may-tinh.png ../backup
- Xóa file.tmp tại thư mục gốc
rm temp_241.tmp
- Dùng đường dẫn tương đối di chuyển vào file logs và liệt kê nội dung sau đó quay lại thư mục gốc
cd .\logs
 ls


    Directory: C:\Users\admin\Desktop\sua-may-tinh-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/27/2026   1:32 AM           1069 repair.log
 cd..
```

## 4.3. Lọc log thủ công

### Lệnh đã chạy

```shell

- Đọc file repair.log
get-content repair.log
2026-06-28 08:21:31 [INFO] Gui tin nhan tra may
2026-06-28 08:25:31 [INFO] Tiep nhan may thanh cong
2026-06-28 08:29:31 [INFO] Thanh toan thanh cong
2026-06-28 08:33:31 [WARNING] Anh chup may dung luong lon
2026-06-28 08:37:31 [WARNING] Thoi gian phan hoi cham
2026-06-28 08:41:31 [INFO] Gui tin nhan tra may
2026-06-28 08:45:31 [WARNING] Linh kien RAM sap het
2026-06-28 08:49:31 [INFO] Khach tra cuu tinh trang may
2026-06-28 08:53:31 [INFO] Thanh toan thanh cong
2026-06-28 08:57:31 [ERROR] Thanh toan bi tu choi
2026-06-28 09:01:31 [ERROR] Thanh toan bi tu choi
2026-06-28 09:05:31 [ERROR] Thanh toan bi tu choi
2026-06-28 09:09:31 [WARNING] Anh chup may dung luong lon
2026-06-28 09:13:31 [INFO] Thanh toan thanh cong
2026-06-28 09:17:31 [ERROR] Khong tim thay trang /tra-cuu (404)
2026-06-28 09:21:31 [INFO] Khach tra cuu tinh trang may
2026-06-28 09:25:31 [INFO] Thanh toan thanh cong
2026-06-28 09:29:31 [INFO] Ky thuat vien bao gia
2026-06-28 09:33:31 [ERROR] Khong tim thay trang /tra-cuu (404)
2026-06-28 09:37:31 [ERROR] Khong tim thay trang /tra-cuu (404)

- Liệt kê file repair.log chứa dòng "ERROR"
select-string "ERROR" repair.log

repair.log:10:2026-06-28 08:57:31 [ERROR] Thanh toan bi tu choi
repair.log:11:2026-06-28 09:01:31 [ERROR] Thanh toan bi tu choi
repair.log:12:2026-06-28 09:05:31 [ERROR] Thanh toan bi tu choi
repair.log:15:2026-06-28 09:17:31 [ERROR] Khong tim thay trang /tra-cuu (404)
repair.log:19:2026-06-28 09:33:31 [ERROR] Khong tim thay trang /tra-cuu (404)
repair.log:20:2026-06-28 09:37:31 [ERROR] Khong tim thay trang /tra-cuu (404)

- Ghi lệnh và dán 2 dòng lỗi đầu tiên
repair.log:10:2026-06-28 08:57:31 [ERROR] Thanh toan bi tu choi
repair.log:11:2026-06-28 09:01:31 [ERROR] Thanh toan bi tu choi

```

### 2 dòng lỗi đầu tiên trong daily_report.txt

```text
- Ghi lệnh và dán 2 dòng lỗi đầu tiên
select-string "ERROR" daily_report.txt -head 2

repair.log:10:2026-06-28 08:57:31 [ERROR] Thanh toan bi tu choi
repair.log:11:2026-06-28 09:01:31 [ERROR] Thanh toan bi tu choi


```

## 4.4. Thao tác với tài liệu Markdown (README.md)

> README.md được chấm trực tiếp trên file `README.md` ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] Heading 1: tên dự án
- [x] Mô tả ngắn có cả **in đậm** và *in nghiêng*
- [x] Bảng `Thư mục | Nội dung`, ít nhất 3 dòng dữ liệu
- [x] Code block chứa lệnh PowerShell/Terminal liệt kê nội dung dự án
- [x] Task list ít nhất 2 công việc, có ít nhất 1 mục đã hoàn thành
- [x] Blockquote nhắc không upload `.env`

## 4.5. Chạy script auto_report (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
 write-output "Tác giả: Phạm Quang Vinh" >> auto-report.txt
 write-output "Ngày giờ: $(get-date)" >> auto-report.txt
 get-content repair.log | select-string "ERROR" >> ..\auto-report.txt
```

### Kết quả hiển thị

```text
Tác giả: Phạm Quang Vinh
Ngày giờ: 10/28/2026 08:53:34

2026-06-28 08:57:31 [ERROR] Thanh toan bi tu choi
2026-06-28 09:01:31 [ERROR] Thanh toan bi tu choi
2026-06-28 09:05:31 [ERROR] Thanh toan bi tu choi
2026-06-28 09:17:31 [ERROR] Khong tim thay trang /tra-cuu (404)
2026-06-28 09:33:31 [ERROR] Khong tim thay trang /tra-cuu (404)
2026-06-28 09:37:31 [ERROR] Khong tim thay trang /tra-cuu (404)

```

## 4.6. Đếm số dòng lỗi

### Lệnh

```shell
Measure-Object "ERROR" repair-log

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
6

```

## 4.7. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
Lệnh đường dẫn tuyệt đối là: pwd
Lệnh liệt kê nội dung gồm cả file ẩn là: ls
Lệnh di chuyển file là: mv
Lệnh sao chép logo vào media là: cp
Lệnh xóa file là: rm
Lệnh duy chuyển thư mục là: cd.\
Lệnh quay lại thư mục là: cd..
Lệnh đọc nội dung trong thư mục là: get-content
Lệnh lọc nội dung trong thư mục là: select-string
Lệnh ghi nội dung từ file này sang file khác là: >>
Lệnh lọc 2 dòng đầu tiên là: -head
get-content repair.log
select-string "ERROR" repair.log

```

### Nội dung file logs/tong_hop.txt

```text
Lệnh đường dẫn tuyệt đối là: pwd
Lệnh liệt kê nội dung gồm cả file ẩn là: ls
Lệnh di chuyển file là: mv
Lệnh sao chép logo vào media là: cp
Lệnh xóa file là: rm
Lệnh duy chuyển thư mục là: cd.\
Lệnh quay lại thư mục là: cd..
Lệnh đọc nội dung trong thư mục là: get-content
Lệnh lọc nội dung trong thư mục là: select-string
Lệnh ghi nội dung từ file này sang file khác là: >>
Lệnh lọc 2 dòng đầu tiên là: -head
get-content repair.log
select-string "ERROR" repair.log
```

## 4.8. Excel

> Phần Excel được chấm trực tiếp trên file `data/phieu_sua_thang_6.xlsx`, không cần ghi vào đây.
