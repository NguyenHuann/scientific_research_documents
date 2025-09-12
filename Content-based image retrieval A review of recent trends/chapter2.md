# 2. Khung CBIR

## Khung tổng quát của CBIR bao gồm một số giai đoạn bắt buộc và một số giai đoạn tùy chọn, như được minh họa trong **Hình 1**.

![Figure 1](Content-based image retrieval A review of recent trends/figures/figure1.jpg)

- **Giai đoạn đầu tiên** trong CBIR là người dùng gửi ảnh truy vấn (query image). Tất cả các tiến trình được áp dụng cho ảnh truy vấn cũng sẽ được áp dụng cho toàn bộ ảnh trong cơ sở dữ liệu, và theo cùng một thứ tự (Kokare và cộng sự, 2002).

- Thông thường, các tiến trình này được thực hiện trên ảnh truy vấn ngay khi người dùng gửi lên và được gọi là **quy trình trực tuyến (online processes)**; cùng các tiến trình này có thể được áp dụng cho tập dữ liệu ảnh trước khi có ảnh truy vấn, và được gọi là **quy trình ngoại tuyến (offline processes)**.

- Một **giai đoạn tiền xử lý (preprocessing)** tùy chọn có thể được đưa vào trong kiến trúc khung CBIR, bao gồm các thao tác như thay đổi kích thước, phân đoạn (segmentation), khử nhiễu (denoising), và chuẩn hóa tỷ lệ (rescaling)...

- Sau đó là **giai đoạn trích xuất đặc trưng (feature extraction)** – giai đoạn quan trọng nhất – trong đó khái niệm thị giác được chuyển đổi sang dạng số. Các đặc trưng trích xuất có thể thuộc loại đặc trưng mức thấp (màu sắc, hình dạng, kết cấu, thông tin không gian) hoặc các mô tả cục bộ (local descriptors).

- Một giai đoạn tiền xử lý tùy chọn khác có thể diễn ra sau trích xuất đặc trưng, chẳng hạn như **chuẩn hóa (normalization)** hoặc **phân loại (classification)**.

- **Giai đoạn cuối cùng** là đo lường độ tương đồng (similarity measurement) giữa các đặc trưng được trích xuất từ ảnh truy vấn và các ảnh trong cơ sở dữ liệu, nhằm truy hồi ra những ảnh liên quan nhất.

Ngoài ra, còn có thể có một giai đoạn gọi là **phản hồi liên quan (relevance feedback)**. Đây là quá trình cải thiện kết quả nhờ sự can thiệp của người dùng, bằng cách phân loại những ảnh trả về là “liên quan” hoặc “không liên quan”. Nhiều kỹ thuật đã được đề xuất để áp dụng phản hồi liên quan nhằm nâng cao hiệu năng của CBIR (Ciocca & Schettini, 1999; Dacheng và cộng sự, 2006; Su và cộng sự, 2011; Banerjee và cộng sự, 2018; Baig và cộng sự, 2020).
