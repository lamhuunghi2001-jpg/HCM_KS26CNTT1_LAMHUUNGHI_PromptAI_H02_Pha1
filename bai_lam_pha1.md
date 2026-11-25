# BÀI LÀM PHA 1 

- **Họ tên:** Lâm Hữu Nghị
- **Lớp:** HCM-KS26-CNTT1
- **Link repository Pha1:**

> Pha 1 (70 phút đầu, KHÔNG dùng AI). Viết xong, kéo thả file này vào repository Pha1 trước mốc giờ giám thị công bố.

## 4.1. Bảo vệ dữ liệu và chống ảo giác

### a) Ghi chú đã ẩn danh hoá

**GHI CHU DA AN DANH**

```text
[TEN_KHACH]: họ và tên
[SDT]: ********* sdt
[SO_CCCD]: ************ cccd
[EMAIL]: ********@example.com
[DON_HANG]: 3 vé gói SVT trận bán kết Cúp Sao Vàng (2 người lớn và 1 trẻ em 9 tuổi)
[THOI_GIAN]: YYYY-MM-DD
[THANH_TOAN]: Đã đặt cọc 1.500.000 đồng
[YEU_CAU]: 3 ghế ngồi cạnh nhau gần lối đi

```

### b) Hai câu lệnh chống ảo giác

**CAU LENH**

```text
Bạn đang là một nhân viên viên bán vé và đang giải quyết vấn đề "Khán giả huỷ vé trước sự kiện 4 ngày thì được hoàn bao nhiêu tiền?" đang hướng giải quyết một cách chuyên nghiệp lịch sự.
Bạn chỉ được phép trả lời dựa theo file tôi đã gửi để đánh giá mức độ của chính sách hoàn tiền.
Ghi rõ các điều khoản chính sách trong file liên quan đến vấn đề không lấy từ nội dung bên ngoài.
```

## 4.2. Trích xuất tin nhắn đặt vé ra JSON

**PROMPT**

```text
- C- Context: 
Bạn là nhân viên mới của Ban tổ chức giải bóng đá Cúp Sao Vàng, phụ trách hỗ trợ khán giả mua vé các trận đấu. Trưởng ban giao cho bạn xây dựng bộ prompt để xử lý thông tin khán giả, tin nhắn đặt vé, báo giá và khiếu nại một cách an toàn, chính xác.
- R - Request:
Xử lý thông tin của khán giả, tin nhắn đặt vé, báo giá và khiếu nại một cách an toàn, chính xác.
E - Explanation:
QUY TẮC CHUẨN HOÁ (5 quy tắc)
1. ma_goi lấy theo bảng mã gói.
2. ngay_su_kien dạng YYYY-MM-DD; tin nhắn không ghi năm thì lấy năm 2026; không có ngày cụ thể thì null.
3. Khách không nhắc trẻ em thì tre_em là 0 và mọi khách là người lớn.
4. loai_ve chỉ nhận "thuong", "vip" hoặc null.
5. ghi_chu chỉ ghi yêu cầu đặc biệt về chỗ ngồi, hỗ trợ di chuyển hoặc ăn uống; không có thì null.

A - Action: 
Cần xử lý:
TN1
{"loai_ve": "thuong","ngay_su_kien": "2026-12-20", "nguoi_lon": 2, "tre_em": 1}
TN2
{"nguoi_lon": 3, "ma_goi": "FZ", "ngay_su_kien": "2027-01-05", "ghi_chu": "Một người cần hỗ trợ xe lăn."}
TN3
   {"ghi_chu": "Trận chung kết Cúp Sao Vàng tháng 12 còn vé không ạ?", "nguo_lon": 4, "loai_ve": "VIP", "ghi_chu": "có một người khiếm thị cần hỗ trợ tìm chỗ"}

T - Tone:
Chuyên nghiệp, lịch sự.
E - Extras:
Chỉ về JSON, không chào hỏi, không giải thích.
```

## 4.3. Báo giá vé bằng Chain-of-Thought

### a) Prompt

**PROMPT**

```text
Bạn là một nhân viên bán vé yêu cầu của bạn là tính giá vé chính xác. 
BẢNG GIÁ VÉ (đồng/người lớn)
SVT – Sân Vận Động: 1.200.000
FZ – Fan Zone: 800.000
VIP – Khán đài VIP: 2.500.000
1. Trẻ em từ 5 đến 11 tuổi tính 70% giá người lớn. Trẻ dưới 5 tuổi miễn phí.
2. Nhóm từ 5 người lớn trở lên được giảm 5% trên tiền vé (tiền người lớn + tiền trẻ em).
3. Phụ thu khu ghế ưu tiên: 300.000 đồng/người. Phụ thu không được giảm giá.
4. Tổng tiền = tiền vé sau giảm + phụ thu.
ÊU CẦU BÁO GIÁ
Nhóm cổ động viên đi xem trận bán kết, mua gói SVT, gồm 5 người lớn, 2 trẻ em (8 tuổi và 10 tuổi) và 1 bé 3 tuổi. Có 1 người lớn chọn khu ghế ưu tiên.
Suy luận từng bước theo thứ tự tiền người lớn → tiền trẻ em → tiền vé → giảm giá nhóm → phụ thu → tổng tiền, mỗi bước ghi phép tính; dòng cuối có dạng [RESULT: <tổng tiền> đồng].
```

## 4.4. Dây chuyền xử lý khiếu nại (Prompt Chaining)

### a) Prompt Trạm 1

**PROMPT**

```text

```

### b) Hai điều cần kiểm tra ở JSON đầu ra của Trạm 1

1. (Viết câu trả lời vào đây – xoá dòng này)

2.

### c) Câu lệnh viết tiếp

**CAU LENH**

```text
(Viết câu lệnh vào đây – xoá dòng này)
```

## 4.5. Prompt chấm bài theo Rubric

**PROMPT**

```text
Viê
```

## 4.6. Hoàn thiện System Prompt

> Phần Vai trò và Chuẩn đầu ra đã cho sẵn. Viết tiếp phần Quy tắc ràng buộc và Xử lý ngoại lệ.

```text
[Vai trò]
Bạn là "Trợ lý Cúp Sao Vàng", nhân viên tư vấn vé và dịch vụ trên website của giải bóng đá Cúp Sao Vàng, giúp khán giả chọn và đặt một trong 3 gói: SVT (Sân Vận Động – vé trận đấu), FZ (Fan Zone – khu cổ vũ), VIP (Khán đài VIP).

[Quy tắc ràng buộc]
1. (Viết quy tắc 1 – xoá dòng này)
2.
3.

[Chuẩn đầu ra]
Trả lời bằng tiếng Việt, lịch sự, tối đa 120 từ. Giá vé trình bày dạng gạch đầu dòng. Kết thúc bằng một câu hỏi về nhu cầu tiếp theo của khách.

[Xử lý ngoại lệ]
- Khách hỏi ngoài phạm vi: (Viết cách trả lời – xoá dòng này)
- Khách cung cấp thiếu thông tin:
```
