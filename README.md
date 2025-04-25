# BaiTap_6 by HẦU NHẬT NINH - K225480106077 - K58KTP.K01
---
# Bài tập 6: Hệ quản trị CSDL
## Chủ đề: Câu lệnh Select
### Yêu cầu bài tập: 
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
6. nhập sql để tìm xem có những sv nào trùng tên với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VƯỚNG MẮC)

### DEADLINE: 23H59:59 NGÀY 25/4/2025

#### Ghi chú: Giải thích tại sao lại có SQL như vậy.
---
# Bài Làm
## 1. Các bước để import được dữ liệu trong ```sv_tnut.sql``` vào sql server của em.
   - Đầu tiên, ta sẽ tạo một _database_ mới với tên tùy chọn hoặc để giống như tên file là ```sv_tnut``` cũng được. Ở đây tôi sẽ đặt là ```DanhSachSV_TNUT```.

![Screenshot (48)](https://github.com/user-attachments/assets/2e420772-9132-489c-9b7e-4b257b6c5efb)

   - Sau đó, mở Query mới ở _database_ vừa tạo.

![Screenshot (49)](https://github.com/user-attachments/assets/41760cd0-3d10-48f6-bf0a-1d1c324e42dc)
     
   - __Copy__ toàn bộ các dòng lệnh trong file ```sv_tnut.sql``` rồi __paste__ vào __query__ của database ```DanhSachSV_TNUT```.

![Screenshot (50)](https://github.com/user-attachments/assets/b434883d-c5fe-470c-992f-474564b0fefe)

   - Do ta đặt tên _database_ là ```DanhSachSV_TNUT```, nên sẽ phải sửa lại lệnh vừa __copy__ trong file ```sv_tnut.sql```. Đó là ở câu lệnh đầu tiên, do ban đầu ta đã tạo _database_ mới không trùng tên với _database_ trong file ```sv_tnut.sql``` nên ta phải thay đổi lệnh từ __USE [*sv_tnut*]__ thành __USE [*DanhSachSV_TNUT*]__ để không bị lỗi.

![Screenshot (51)](https://github.com/user-attachments/assets/d0a24505-8469-46cb-bc75-ce6f65cf5ab9)
     
## 2. Truy vấn dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)    
   - Sử dụng câu lệnh:
```sql
SELECT* 
FROM SV
WHERE ten = 'Ninh' AND sdt = '974493002' AND ns = '2003-12-20'; 
```
![Screenshot (52)](https://github.com/user-attachments/assets/bc0c3ede-8290-4de3-86f9-d94665209e4c)

## 3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
   - Sử dụng câu lệnh: 
```sql
SELECT* 
FROM SV
WHERE ns = '2003-12-20';
```
![Screenshot (53)](https://github.com/user-attachments/assets/a597194d-121d-4161-bbd7-f3bfeba028a8)

## 4. Nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
   - Sử dụng câu lệnh:
```sql
SELECT* 
FROM SV
WHERE DAY(ns) = 20 AND MONTH(ns) = 12;
```
![Screenshot (54)](https://github.com/user-attachments/assets/5381df9e-3b80-44ec-8c9f-7c8b729690d5)

## 5. Nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
   - Sử dụng câu lệnh:
```sql
SELECT* 
FROM SV
WHERE MONTH(ns) = 12 AND YEAR(ns) = 2003;
```
![Screenshot (55)](https://github.com/user-attachments/assets/d58b9a25-c791-448a-84b5-f15bcc6569f7)

## 6. Nhập sql để tìm xem có những sv nào trùng tên với em?
  - Sử dụng câu lệnh:
```sql
SELECT* 
FROM SV
WHERE ten = 'Ninh';
```
![Screenshot (56)](https://github.com/user-attachments/assets/61ad66ba-b37e-4185-838a-64308e3996a4)

## 7. Nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em?
