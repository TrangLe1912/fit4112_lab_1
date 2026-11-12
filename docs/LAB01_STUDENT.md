# FIT4112 – Phiếu thực hành Lab 1

**Tên bài:** Khai phá luật kết hợp từ giỏ hàng (Apriori)  
**Hình thức:** Cá nhân; thực hành với 3 notebook theo thứ tự.

## Mục tiêu
Hiểu được luồng xử lý `giao dịch -> làm sạch -> basket 0/1 -> Apriori -> luật kết hợp -> đề xuất`. Không yêu cầu cài đặt Apriori thủ công và không dùng Papermill.

## Phần A – Làm theo hướng dẫn (40 điểm)

1. Chạy `01_preprocessing_and_eda.ipynb`. Ghi số dòng ban đầu, số dòng sau làm sạch và lý do lọc các giao dịch không hợp lệ.
2. Chạy `02_basket_preparation.ipynb`. Chụp/đính kèm 5 hàng đầu của ma trận basket. Giải thích một hàng, một cột và giá trị 0/1.
3. Chạy `03_apriori_rules.ipynb`. Xác nhận đã tạo các file `cleaned_transactions.csv`, `basket_bool.csv`, `association_rules.csv`.

## Phần B – Thực hiện và so sánh (40 điểm)

1. Từ notebook 03, chọn **5 luật** có ý nghĩa; ghi lại tiền đề, kết quả, support, confidence, lift.
2. Chạy với `MIN_SUPPORT = 0.10`, sau đó `0.20` **trên dữ liệu demo**. Nếu tự chọn dữ liệu thật, chọn hai ngưỡng phù hợp để có thể so sánh.
3. Ghi bảng so sánh: ngưỡng support; số tập mục phổ biến; số luật; nhận xét **vì sao tăng support có thể làm giảm số luật**.
4. Nêu ví dụ một luật có confidence cao nhưng lift không thật sự hấp dẫn (nếu bộ dữ liệu có), hoặc giải thích về mặt lý thuyết tại sao cần xem cả hai.

## Phần C – Diễn giải (20 điểm)

1. Chọn **2 luật** trong bảng; diễn giải bằng tiếng Việt dễ hiểu, tránh diễn giải sai quan hệ nhân quả.
2. Đề xuất **1 hoạt động bán kèm hoặc trưng bày sản phẩm**, nêu điều kiện áp dụng.
3. Nêu ít nhất **1 hạn chế** (ví dụ: dữ liệu giả lập, thiếu thông tin khách hàng, luật không chứng minh nguyên nhân).

## Rubric

| Tiêu chí | Điểm |
|---|---:|
| 3 notebook chạy đúng thứ tự và có kết quả | 20 |
| Giải thích được tiền xử lý và basket | 20 |
| Chọn 5 luật và báo cáo đầy đủ 3 chỉ số | 20 |
| So sánh 2 cấu hình min_support | 20 |
| Diễn giải 2 luật và đề xuất hành động có căn cứ | 20 |
| **Tổng** | **100** |

**Đạt chuẩn không đòi hỏi mô hình có độ chính xác tối ưu, không bắt buộc dashboard.**

## Nâng cao – tự chọn
Dùng dữ liệu thật Online Retail, phân tích ảnh hưởng `min_confidence`, so sánh Apriori với FP-Growth. Giảng viên có thể ghi nhận phần này theo quy định điểm khuyến khích của lớp; không thay thế các yêu cầu cốt lõi.

## Nộp bài

- 3 notebook `.ipynb` đã chạy, **giữ các output cần thiết**.
- `LAB01_REPORT.md` hoặc PDF tối đa khoảng 2 trang theo mẫu.
- Tránh commit môi trường ảo, file dữ liệu thật dung lượng lớn, cache và `data/processed/`.
