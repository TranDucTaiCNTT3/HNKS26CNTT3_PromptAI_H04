# BÀI LÀM PHA 2 (ĐỀ LUYỆN TẬP CHỦ ĐỀ CHẠY AFFILIATE)

- **Họ tên:** Trần Đức Tài 
- **Lớp:** HNKS26CNTT3
- **Link repository Pha2:** https://github.com/TranDucTaiCNTT3/HNKS26CNTT3_PromptAI_H04/blob/409a948fcce409a0c9fef14b1d8cb355f0d6dc23/bai_lam_pha2.md
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):** Gemini

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đăng ký gói Affiliate ra JSON

**KET QUA AI**

```text
[
  {
    "ma_goi": "TT",
    "ngay_bat_dau": "2026-12-20",
    "creator_chinh": 2,
    "thuc_tap_sinh": 1,
    "hang_tai_khoan": "thuong",
    "ghi_chu": null
  },
  {
    "ma_goi": "SP",
    "ngay_bat_dau": "2027-01-08",
    "creator_chinh": 3,
    "thuc_tap_sinh": 0,
    "hang_tai_khoan": null,
    "ghi_chu": "ngồi bàn gần cửa ra vào"
  },
  {
    "ma_goi": "PRO",
    "ngay_bat_dau": null,
    "creator_chinh": 4,
    "thuc_tap_sinh": 0,
    "hang_tai_khoan": "vip",
    "ghi_chu": "mượn thêm đèn trợ sáng và phông xanh để quay mẫu"
  }
]
```

**Link trò chuyện:** https://share.gemini.google/cLl0Tv4p3oa5

## 4.3. Báo giá gói Affiliate bằng Chain-of-Thought

**KET QUA AI**

```text
```python
creator_price = 1_500_000
num_creators = 4
creator_total = num_creators * creator_price

intern_unit = int(creator_price * 0.6)
num_interns = 2 # 16 and 17 years old -> both 15 to <18
intern_total = num_interns * intern_unit

# 7 year old -> under 15, accompanying, waiting area -> free (0)
package_total = creator_total + intern_total

# 4 creators >= 4 -> 10% discount on package_total
discount = int(package_total * 0.10)
after_discount = package_total - discount

# 2 wireless mic sets * 250,000, no discount
mic_unit = 250_000
num_mics = 2
mic_fee = num_mics * mic_unit

grand_total = after_discount + mic_fee

print(f"creator_total: {creator_total:,}")
print(f"intern_unit: {intern_unit:,}, intern_total: {intern_total:,}")
print(f"package_total: {package_total:,}")
print(f"discount: {discount:,}, after_discount: {after_discount:,}")
print(f"mic_fee: {mic_fee:,}")
print(f"grand_total: {grand_total:,}")


```

```text
creator_total: 6,000,000
intern_unit: 900,000, intern_total: 1,800,000
package_total: 7,800,000
discount: 780,000, after_discount: 7,020,000
mic_fee: 500,000
grand_total: 7,520,000


```

* **Tiền Creator chính:** $4 \times 1.500.000 = 6.000.000\text{ đồng}$
* **Tiền thực tập sinh:** $2 \times (1.500.000 \times 60\%) = 2 \times 900.000 = 1.800.000\text{ đồng}$ (bé 7 tuổi đi cùng ngồi khu chờ miễn phí: $0\text{ đồng}$)
* **Tổng tiền gói:** $6.000.000 + 1.800.000 = 7.800.000\text{ đồng}$
* **Giảm giá team:** $7.800.000 \times 10\% = 780.000\text{ đồng}$ (tiền gói sau giảm: $7.800.000 - 780.000 = 7.020.000\text{ đồng}$)
* **Phụ thu thuê mic:** $2 \times 250.000 = 500.000\text{ đồng}$
* **Tổng tiền:** $7.020.000 + 500.000 = 7.520.000\text{ đồng}$

[RESULT: 7.520.000 đồng]
```

**Link trò chuyện:** https://share.gemini.google/XVQHhgw3oH44

### b) Kiểm tra kết quả AI

Ai đã tính toán chính xác

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
"loai_su_co": "sai_phong",
"so_khach": 3,
"so_ca_bi_anh_huong": 2,
"tom_tat": "Nhóm 3 khách gói TT bị xếp sai phòng thiếu đèn livestream và cách âm trong 2 ca thực hành đầu."
}
```

**Link trò chuyện:** https://share.gemini.google/zWTKxxkFVdBQ

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
| --- | --- | --- | --- |
| Đúng thông tin | 0/5,0 | * "Gói TikTok Affiliate bên mình giá chỉ 1.200.000đ/người thôi..." — Sai giá chuẩn (1.500.000 đồng/Creator chính) và gọi sai đối tượng ("người" thay vì "Creator chính").<br>

<br>* "Bạn báo huỷ trước 5 ngày thì được hoàn lại đủ 100% tiền nha..." — Sai chính sách hoàn tiền: huỷ trước từ 3 đến 6 ngày chỉ hoàn 50%, hoàn 100% áp dụng cho mức huỷ trước từ 7 ngày trở lên. | * "Gói TikTok Affiliate (TT) đợt này có mức phí là 1.500.000 đồng/Creator chính ạ."<br>

<br>* "Nếu anh/chị xin huỷ trước ngày bắt đầu 5 ngày (thuộc khung từ 3 đến 6 ngày trước ngày khởi động), trung tâm sẽ hoàn lại 50% phí đăng ký ạ; mức hoàn 100% áp dụng khi báo huỷ trước từ 7 ngày trở lên." |
| Đầy đủ | 1,5/3,0 | * Trả lời có đề cập tới giá và trường hợp huỷ trước 5 ngày (dù sai số liệu), nhưng thiếu hoàn toàn phần mời khách hàng cung cấp ngày đợt thực chiến và số lượng suất muốn đăng ký. | * Bổ sung cuối câu: "Anh/chị vui lòng cho em biết ngày đợt thực chiến anh/chị dự kiến tham gia và số lượng suất muốn đăng ký để em hỗ trợ giữ chỗ cho mình nhé." |
| Giọng điệu | 0/2,0 | * "Dạ hello bạn nha! ... nha, cứ chốt lẹ kẻo hết slot nè!" — Xưng hô suồng sã, thiếu chuyên nghiệp, dùng từ ngữ giục giã ("chốt lẹ", "nha", "nè").<br>

<br>* "...đăng ký xong gắn link là nổ đơn hoa hồng trăm triệu luôn ạ." — Cam kết hoa hồng ảo, thổi phồng kết quả gây hiểu lầm cho khách hàng. | * "Dạ em chào anh/chị ạ. ... Hiệu quả kinh doanh thực tế còn phụ thuộc vào nội dung, tệp khách hàng và cách triển khai của từng Creator, bên em không cam kết mức hoa hồng cố định ạ. Anh/chị cân nhắc đăng ký sớm để giữ suất cho đợt tới nhé." |

Tổng điểm: 1,5/10
```

**Link trò chuyện:** https://share.gemini.google/nGTwhlYPyihM
