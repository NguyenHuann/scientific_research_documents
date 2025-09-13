# 8. Đánh giá hiệu năng (Performance evaluation)

Việc đánh giá hệ thống CBIR nên được thực hiện dựa trên các công thức được xác định trước, **không phụ thuộc vào sự can thiệp của con người**, bởi vì sự can thiệp thủ công dễ bị sai sót, tốn thời gian và mang tính chủ quan.

Mặc dù có một tập hợp các tiêu chí nổi tiếng để đánh giá hiệu năng và độ chính xác của hệ thống CBIR, việc lựa chọn công thức đánh giá phù hợp nhất phụ thuộc vào nhiều yếu tố: **phương pháp được sử dụng, bản thân thuật toán, và lĩnh vực bài toán**.

Dưới đây là các thước đo được sử dụng phổ biến nhất:

---

### (I) Precision (P) – Độ chính xác

Là **tỉ lệ số ảnh liên quan trong tập ảnh được truy hồi** trên **tổng số ảnh được truy hồi** (Haji et al., 2019).

$$
P = \frac{\text{Số ảnh liên quan}}{\text{Tổng số ảnh truy hồi}}
\tag{9}
$$

---

### (II) Recall (R) – Độ truy hồi

Là **tỉ lệ số ảnh liên quan được truy hồi** trên **tổng số ảnh liên quan trong toàn bộ tập dữ liệu** (ElAdel et al., 2016; Bala & Kaur, 2016).

$$
R = \frac{\text{Số ảnh liên quan}}{\text{Tổng số ảnh liên quan trong tập dữ liệu}}
\tag{10}
$$

---

### (III) Average Precision (AP) – Độ chính xác trung bình

Là một thước đo nổi tiếng khác. AP cho một truy vấn $q$ được định nghĩa là **giá trị trung bình của Precision tại mỗi ảnh liên quan** (Latif et al., 2019).

$$
AP_q = \frac{1}{NRI} \sum_{q=1}^{NRI} P_q R_q
\tag{11}
$$

Trong đó:

- **NRI**: số ảnh liên quan trong cơ sở dữ liệu cho truy vấn $q$.
- **R_q**: biến nhị phân, bằng 1 nếu ảnh thứ q được truy hồi là liên quan, và bằng 0 nếu không liên quan.

---

### (IV) Mean Average Precision (MAP) – Độ chính xác trung bình toàn cục

MAP là **trung bình của AP trên tất cả các truy vấn** (NQ) (Alzu’bi et al., 2015).

$$
MAP = \frac{1}{NQ} \sum_{q=1}^{NQ} AP_q
\tag{12}
$$

---

### (V) F1-score (F-measure)

Là sự kết hợp giữa Precision và Recall trong một thước đo duy nhất, được định nghĩa là **trung bình điều hòa** (Makhoul et al., 1999).

$$
F = \frac{(1 + \beta^2)PR}{\beta^2 P + R}
\tag{13}
$$

Trong đó, $\beta \geq 0$. Thông thường $\beta = 1$, khi đó thước đo được gọi là **F1-score**:

$$
F1 = \frac{2PR}{P + R}
\tag{14}
$$

---

### (VI) Computational Cost – Chi phí tính toán (thời gian chạy)

Là một yếu tố quan trọng trong đánh giá CBIR, đặc biệt với các ứng dụng thời gian thực.

- Có thể xét theo **thời gian trích xuất đặc trưng** (Sharif et al., 2019).
- Hoặc **thời gian trích xuất đặc trưng + thời gian truy hồi tổng** (Mehmood et al., 2018; Ahmed et al., 2019).
- Hoặc chỉ xét **thời gian truy hồi tổng** (Yousuf et al., 2018; ElAdel et al., 2016).

Tuy nhiên, tiêu chí này ít được thảo luận trong nghiên cứu.

---

### (VII) Confusion Matrix – Ma trận nhầm lẫn

Là một **ma trận 2D** thường dùng để tóm tắt hiệu năng của bộ phân loại (Sammut & Webb, 2017).

- Một chiều biểu diễn **lớp thực tế**,
- Chiều còn lại biểu diễn **lớp dự đoán**.

## Bảng 7. Ví dụ về ma trận nhầm lẫn hai lớp

| **Lớp thực tế (Actual Classes)** | **Dự đoán: A** | **Dự đoán: B** |
| -------------------------------- | -------------- | -------------- |
| **A**                            | 9              | 1              |
| **B**                            | 2              | 8              |

---

Giải thích ngắn gọn:

- Có **10 ảnh thuộc lớp A** trong dữ liệu thực tế → mô hình dự đoán đúng 9 ảnh (A→A) và nhầm 1 ảnh thành B (A→B).
- Có **10 ảnh thuộc lớp B** trong dữ liệu thực tế → mô hình dự đoán đúng 8 ảnh (B→B) và nhầm 2 ảnh thành A (B→A).
