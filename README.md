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
  - Sử dụng câu lệnh:
```sql
SELECT* 
FROM SV
WHERE hodem = 'Hầu Nhật';
```
![Screenshot (57)](https://github.com/user-attachments/assets/0b4d22c2-5b39-478c-a06f-4b6cdcedd473)

## 8. Nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em?
  - Sử dụng câu lệnh:
```sql
SELECT masv, hodem, ten, sdt,
       (CASE WHEN SUBSTRING(sdt, 1, 1) = '9' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 2, 1) = '7' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 3, 1) = '4' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 4, 1) = '4' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 5, 1) = '9' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 6, 1) = '3' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 7, 1) = '0' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 8, 1) = '0' THEN 0 ELSE 1 END +
        CASE WHEN SUBSTRING(sdt, 9, 1) = '2' THEN 0 ELSE 1 END)
       AS so_ky_tu_sai
FROM SV
WHERE LEN(sdt) = 9
ORDER BY so_ky_tu_sai;
```
![Screenshot (58)](https://github.com/user-attachments/assets/073a0421-d68a-46ff-bb01-df6fde57703b)

## 9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH?
  - Sử dụng câu lệnh:
```sql
SELECT*,
    -- Thêm cột ngành mới 
    SUBSTRING([lop], 4, 3) AS nganh -- Trích 3 ký tự từ vị trí thứ 4 của cột lop (ví dụ: "K57KMT.01" → "KMT"), đặt tên cột là nganh.
FROM [DanhSachSV_TNUT].[dbo].[SV]
WHERE [lop] LIKE N'%KMT%' -- Chỉ lấy những dòng mà cột lop có chứa chữ "KMT" (lọc ngành KMT)
ORDER BY -- Sắp xếp kết quả theo
    [ten] COLLATE Vietnamese_CI_AS, -- Sắp xếp theo tên sinh viên, dùng bộ mã chuẩn tiếng Việt để phân biệt đúng a, ă, â,...
    [hodem] COLLATE Vietnamese_CI_AS; -- Nếu trùng tên, thì sắp xếp tiếp theo họ đệm, cũng theo tiếng Việt.
```
![Screenshot (59)](https://github.com/user-attachments/assets/bad754a1-1227-4f81-afbf-9bec6e06dcbd)

## 10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VƯỚNG MẮC)? 
  - Sử dụng câu lệnh:
```sql
SELECT *,
    SUBSTRING([lop], 4, 3) AS MaNganh
FROM SV
WHERE lop LIKE '%KMT%'
  AND hodem LIKE N'%Thị%'
  AND (
    ten LIKE N'Anh' OR ten LIKE N'Trang' OR ten LIKE N'Lan' OR
    ten LIKE N'Hoa' OR ten LIKE N'Hương' OR ten LIKE N'Linh' OR
    ten LIKE N'Hạnh' OR ten LIKE N'Thảo' OR ten LIKE N'Hằng' OR
    ten LIKE N'Vân' OR ten LIKE N'My' OR ten LIKE N'Mai' OR
    ten LIKE N'Ngọc' OR ten LIKE N'Yến' OR ten LIKE N'Diệu'
  );
```
   - Ở bài toán này, ta sẽ thêm một điều kiện vào mệnh đề WHERE:
     - ```lop LIKE '%KMT%'```: chỉ sinh viên ngành KMT
     - ```hodem LIKE N'%Thị%'```: chỉ sinh viên có họ đệm chứa "Thị"
     - ```ten LIKE ...```: lọc các tên nữ phổ biến
![Screenshot (60)](https://github.com/user-attachments/assets/4bc88392-0767-4bfd-8f0d-82f5e1f158c4)
   
### => Cách này tuy vẫn có thể truy vấn ra được các sinh viên nữ ngành KMT nhưng chưa tối ưu vì trong bảng không có dữ liệu nào cụ thể để có thể phân biệt rõ các sinh viên nào là nam, sinh viên nào là nữ. 
#### Giải pháp: 
   - Đoán giới tính thông qua họ đệm và tên (*không tối ưu - đã kiểm chứng ở trên*).
   - Thêm cột ```gioitinh``` rồi cập nhật lại dữ liệu.
