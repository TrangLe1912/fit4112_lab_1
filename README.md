# FIT4112 – Lab 1: Khai phá luật kết hợp từ dữ liệu giỏ hàng

**Học phần:** Khai phá dữ liệu (Data Mining)  
**Chủ đề:** Association Rule Mining với Apriori  
**Mục tiêu:** Từ giao dịch bán lẻ, tìm quy luật mua kèm và giải thích ý nghĩa kinh doanh.

> Phiên bản **Student Friendly** được thiết kế lại từ [shopping_cart_analysis](https://github.com/TrangLe1912/shopping_cart_analysis). **Không dùng Papermill**, không bắt buộc dashboard, không yêu cầu viết lại thuật toán Apriori từ đầu.

## 1. Kết quả học tập

Sau lab, sinh viên có thể:
1. Phát hiện và xử lý một số giao dịch không hợp lệ.
2. Chuyển dữ liệu **dòng giao dịch** thành ma trận **hóa đơn × sản phẩm** (0/1).
3. Chạy Apriori và tạo luật kết hợp bằng `mlxtend`.
4. Giải thích **support, confidence, lift**, thử hai ngưỡng `min_support`.
5. Đề xuất cách bán kèm/bố trí sản phẩm từ kết quả, đồng thời nhận ra giới hạn của dữ liệu.

## 2. Cấu trúc repo

```text
fit4112_lab_1/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── raw/
│       └── transactions_demo.csv       # dữ liệu giả lập, có thể chạy ngay
├── notebooks/
│   ├── 01_preprocessing_and_eda.ipynb   # đọc, làm sạch, khám phá
│   ├── 02_basket_preparation.ipynb       # giao dịch -> basket 0/1
│   └── 03_apriori_rules.ipynb            # Apriori -> luật -> phân tích
└── docs/
    ├── LAB01_STUDENT.md                 # đề bài, rubric, câu hỏi
    └── REPORT_TEMPLATE.md               # mẫu báo cáo ngắn
```

Khi chạy, notebook tự tạo `data/processed/` với các file trung gian. **Không sửa file trong `data/processed/` bằng tay.**

## 3. Cài đặt một lần

Yêu cầu Python 3.11 hoặc 3.12. Mở terminal **tại thư mục gốc của repo**:

```bash
git clone https://github.com/TrangLe1912/fit4112_lab_1.git
cd fit4112_lab_1
python -m venv .venv
```

Kích hoạt môi trường:
- **Windows (PowerShell):** `.venv\Scripts\Activate.ps1`
- **macOS/Linux:** `source .venv/bin/activate`

```bash
python -m pip install -r requirements.txt
jupyter lab
```

Trong JupyterLab (hoặc VS Code đã cài Jupyter extension), mở và chạy lần lượt **01 → 02 → 03** bằng *Run All* hoặc từng cell. Từng notebook có giải thích và câu hỏi kiểm tra hiểu bài.

### Không muốn cài nhiều thư viện?

Có thể dùng Google Colab: tải 3 notebook lên Colab và tải thư mục `data/raw` vào môi trường làm việc; cần giữ đúng cấu trúc thư mục `data/`, `notebooks/` và cài `mlxtend`. **Khuyến nghị học trên máy tính bằng JupyterLab/VS Code** để tránh phải cấu hình đường dẫn Drive.

## 4. Dữ liệu

**Mặc định** là `data/raw/transactions_demo.csv`: bộ dữ liệu giả lập nhỏ, do học liệu tạo để người mới quan sát được các bước. **Không dùng kết quả của dữ liệu mẫu để khẳng định hành vi mua sắm thực tế.**

**Tự chọn – mở rộng trên dữ liệu thật:** tải `online_retail.csv` từ [repo gốc](https://github.com/TrangLe1912/shopping_cart_analysis/blob/main/data/raw/online_retail.csv), đặt tại `data/raw/online_retail.csv`, rồi trong notebook 01 đổi `DATA_FILE = "online_retail.csv"`. Với dữ liệu thật, notebook 02 giới hạn số hóa đơn và sản phẩm để tránh thiếu bộ nhớ; notebook 03 có thể cần giảm `MIN_SUPPORT`.

## 5. Các bước thực hành (bắt buộc)

| Notebook | Sản phẩm đầu ra | Việc cần hiểu |
|---|---|---|
| 01 – Làm sạch | `cleaned_transactions.csv` | Vì sao lọc hóa đơn hủy, số lượng/đơn giá âm? |
| 02 – Basket | `basket_bool.csv` | Một hàng là gì? Tại sao đổi số lượng thành 0/1? |
| 03 – Apriori | `association_rules.csv` | Luật nào đáng chú ý theo support/confidence/lift? |

**Bài tập cần nộp:** chạy đủ 3 notebook; chọn **5 luật** tiêu biểu; so sánh số luật ở **hai ngưỡng min_support**; giải thích **2 luật** và đề xuất **1 cách áp dụng**. Xem chi tiết tại [docs/LAB01_STUDENT.md](docs/LAB01_STUDENT.md).

## 6. Nộp bài

Nộp **3 file notebook đã chạy** (có kết quả/biểu đồ) và một báo cáo ngắn theo [mẫu](docs/REPORT_TEMPLATE.md), hoặc đường dẫn repository GitHub cá nhân chứa các file đó. Không nộp môi trường `.venv`, dữ liệu giao dịch dung lượng lớn hoặc thư mục cache.

**Nâng cao (không bắt buộc):** phân tích dữ liệu Online Retail thật; so sánh Apriori và FP-Growth; lọc luật theo lift/đề xuất combo sâu hơn.

## 7. Sự cố thường gặp

- **`FileNotFoundError`**: kiểm tra `data/raw/transactions_demo.csv`, đồng thời chạy từ thư mục gốc hoặc từ `notebooks/`.
- **Chưa có `cleaned_transactions.csv`**: chạy notebook 01 trước notebook 02.
- **Chưa có `basket_bool.csv`**: chạy notebook 02 trước notebook 03.
- **`ModuleNotFoundError: mlxtend`**: cài `python -m pip install -r requirements.txt` vào đúng kernel.
- **Không có luật**: thử giảm `MIN_SUPPORT` hoặc `MIN_CONFIDENCE`; **không được tự bịa luật**.
- **Máy chậm khi dùng dữ liệu thật**: giảm `MAX_INVOICES` và `TOP_PRODUCTS` trong notebook 02.

---

**Nguồn ý tưởng và dữ liệu tham khảo:** [TrangLe1912/shopping_cart_analysis](https://github.com/TrangLe1912/shopping_cart_analysis). Phiên bản này ưu tiên năng lực đọc hiểu, thử nghiệm và giải thích, không ưu tiên tự động hóa hệ thống.
