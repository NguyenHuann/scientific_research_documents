# 6. Các thước đo độ tương đồng/khác biệt (Similarity/Dissimilarity measures)

Hiệu năng của hệ thống truy hồi ảnh (CBIR) bị ảnh hưởng bởi **quá trình trích xuất đặc trưng** cũng như **phép đo độ tương đồng**. Phép đo độ tương đồng quyết định hình ảnh nào trong cơ sở dữ liệu được xem là liên quan nhất đến ảnh truy vấn và cần được trả về. Vì vậy, phép đo tương đồng **gián tiếp quyết định độ chính xác** của CBIR và tác động đến **độ phức tạp tính toán** của hệ thống.

Việc lựa chọn thước đo tương đồng bị ảnh hưởng bởi **cấu trúc vector đặc trưng** (loại và số chiều dữ liệu đầu vào). Đây là một trong những thách thức lớn được ghi nhận trong nhiều nghiên cứu.

Các thước đo độ tương đồng thường được chia thành hai nhóm:

- **Distance measure (khoảng cách)** – đo sự khác biệt.
- **Similarity metric (độ tương đồng)** – đo sự giống nhau (Sergyan, 2008).

---

## 6.1. Distance measures

Khoảng cách thường được dùng để đo **sự khác biệt (dissimilarity)** giữa hai vector đặc trưng. Giá trị càng nhỏ thì ảnh càng giống với ảnh truy vấn.

Distance measures được chia thành hai loại chính:

1. **Bin-by-bin**: so sánh từng cặp phần tử tương ứng của hai vector.

   - Đơn giản, dễ tính toán.
   - Nhưng nhạy cảm với thay đổi tỷ lệ, lượng tử hóa, nhiễu, biến dạng hình dạng và thay đổi ánh sáng (Tyagi, 2017).

2. **Cross-bin**: xem xét mối quan hệ giữa các phần tử không tương ứng trong vector.

   - Mô tả tốt hơn, bền vững hơn.
   - Nhược điểm: chi phí tính toán cao.

---

### 6.1.1. Minkowski Family

Minkowski là nhóm khoảng cách **bin-by-bin** phổ biến trong CBIR vì tính đơn giản.

Công thức tổng quát:

$$
L_p(X,Y) = \left( \sum_{i=1}^N |x_i - y_i|^p \right)^{\frac{1}{p}}
$$

- **L2 (Euclidean distance)**: khi $p=2$. Bất biến với phép biến đổi trực giao.
- **L1 (Manhattan/City block/Taxi-cab distance)**: khi $p=1$. Bền vững với phản xạ và tịnh tiến, nhưng biến đổi theo xoay hệ tọa độ.
- **L∞ (Chebyshev/Chessboard distance)**: khi $p \to ∞$.

$$
L_\infty(X,Y) = \max_i |x_i - y_i|
$$

Ví dụ: trên bàn cờ 2D, L∞ biểu diễn số bước tối thiểu mà quân vua cần di chuyển từ ô này sang ô khác.

- **Fractional distance (0 < p < 1):** không được xem là metric (không thỏa bất đẳng thức tam giác), nhưng được ưa dùng khi dữ liệu có số chiều cao vì nó **mạnh nhất trước nhiễu** (Howarth & Rüger, 2005; Tyagi, 2017).

---

### 6.1.2. Chi-square Statistic

Được dùng rộng rãi để so sánh histogram (Pele & Werman, 2010).

$$
\chi^2(X,Y) = \sum_{i=1}^N \frac{(x_i - y_i)^2}{x_i + y_i}
$$

Ứng dụng thành công trong: phân loại hình dạng, so khớp descriptor cục bộ, phát hiện biên, nhận diện ảnh trùng lặp, phân loại kết cấu và đối tượng.

---

### 6.1.3. Histogram Intersection

Do Swain & Ballard (1991) đề xuất:

$$
D(X,Y) = \sum_{i=1}^N \min(x_i, y_i)
$$

- Bền vững với nhiễu nền, thay đổi độ phân giải, che khuất, thay đổi góc nhìn.
- Dùng nhiều trong truy hồi ảnh, phân đoạn, phân cụm, phân loại và tạo codebook.

---

### 6.1.4. Mahalanobis Distance

Do P. C. Mahalanobis (1936) đề xuất, đo khoảng cách giữa vector đặc trưng và một phân phối:

$$
D(X) = \sqrt{(v - m)^T C^{-1} (v - m)}
$$

- $v$: vector đặc trưng
- $m$: vector trung bình
- $C$: ma trận hiệp phương sai

Nhược điểm: tính toán tốn kém với dữ liệu có số chiều cao vì phải tính nghịch đảo ma trận hiệp phương sai.

---

### 6.1.5. Canberra Distance

Do Lance & Williams (1966, 1967) đề xuất:

$$
D(X,Y) = \sum_{i=1}^N \frac{|x_i - y_i|}{|x_i| + |y_i|}
$$

- Nhạy cảm với giá trị gần 0.
- Phù hợp khi sự khác biệt về dấu biểu thị sự khác biệt về lớp dữ liệu.

---

### 6.1.6. Squared Chord Distance

$$
D(X,Y) = \sum_{i=1}^N \left( \sqrt{x_i} - \sqrt{y_i} \right)^2
$$

- Dùng trong truy hồi ảnh.
- Không phù hợp với vector đặc trưng có giá trị âm.

---

## 6.2. Similarity measures

Khác với các độ đo trên (đo **dissimilarity**), **cosine similarity** đo độ giống nhau.

$$
Sim(X,Y) = \frac{X \cdot Y}{||X|| \, ||Y||}
$$

- Giá trị càng lớn → ảnh càng giống.
- Đo góc giữa hai vector thay vì khoảng cách.

---

## 6.3. Thảo luận

Việc chọn thước đo phù hợp vẫn là một **thách thức mở**:

- **Rana et al. (2019):** so sánh Canberra, Chi-square, Manhattan, Euclidean → Euclidean cho độ chính xác cao nhất.
- **Raza et al. (2018):** so sánh L1, L2, L1 có trọng số, Chi-square, Squared Chord, Extended Canberra → Weighted L1 là tốt nhất vì cân bằng độ chính xác và chi phí tính toán.
- **Zhao et al. (2016):** gán trọng số khác nhau cho đặc trưng màu, kết cấu, hình dạng để tăng hiệu quả.

Mặc dù đã có nhiều nghiên cứu (Arevalillo-Herráez et al., 2008; Rui et al., 2008), việc lựa chọn thước đo tương đồng tối ưu vẫn là **một lĩnh vực nghiên cứu mở** cần được khám phá thêm.

Chi tiết hơn về các công thức toán học có thể xem trong (Cha, 2007); tổng quan các metric trong CBIR tham khảo (Alzu’bi et al., 2015).

---
