# 9. Thảo luận và định hướng nghiên cứu trong tương lai (Discussion and future research directions)

Truy hồi ảnh dựa trên văn bản (Text-based image retrieval) là nền tảng của nhiều công cụ tìm kiếm hình ảnh. Mặc dù phương pháp này chưa thực sự thỏa đáng, nó vẫn là cách tiếp cận phổ biến. Nhu cầu về một hệ thống **truy hồi ảnh dựa trên nội dung (CBIR)** hiệu quả đã thúc đẩy nhiều nhà nghiên cứu phát triển các hệ thống như vậy. Tuy nhiên, các hệ thống CBIR hiện tại vẫn gặp nhiều hạn chế, chẳng hạn như:

- Cần có **phương pháp lựa chọn và trích xuất đặc trưng phù hợp**, vốn là nền tảng của bất kỳ kỹ thuật CBIR nào.
- Trích xuất đặc trưng hiện nay chủ yếu dựa trên hai cách:

  1. **Trích xuất đặc trưng thủ công (handcrafted features)**, dựa vào đặc trưng toàn cục hoặc cục bộ.
  2. **Sử dụng các thuật toán học máy**, nhằm tạo ra biểu diễn đặc trưng tự động.

Việc lựa chọn các đặc trưng phù hợp, phản ánh được cả **ý nghĩa ngữ nghĩa** và **nhận thức trực quan** trong hình ảnh vẫn là một thách thức nghiên cứu mở.

---

## 9.1. Hướng nghiên cứu về đặc trưng toán học

Một hướng đi đầy tiềm năng là trích xuất đặc trưng dựa trên **đa thức trực giao rời rạc (discrete orthogonal polynomials)** để cải thiện độ chính xác của CBIR.
Các ví dụ tiêu biểu:

- Đa thức **Kravchuk** (Mahmmod et al., 2020)
- Đa thức **Meixner** (Abdulhussain & Mahmmod, 2021)
- Đa thức **Charlier** (Abdul-Hadi et al., 2020)
- Đa thức **Tchebichef** (Abdulhussain et al., 2017)
- Đa thức kết hợp **Kravchuk–Tchebichef** (Abdulhussain, Ramli, Mahmmod et al., 2019)
- **Kernel ảnh tích hợp đa thức trực giao** (Abdulhussain, Ramli, Hussain et al., 2019)

Những kỹ thuật này đã chứng minh khả năng **tăng độ chính xác và giảm chi phí tính toán** trong các lĩnh vực thị giác máy tính khác (Abdulhussain et al., 2021).

---

## 9.2. Vấn đề giảm chiều dữ liệu

Dựa vào **một đặc trưng duy nhất** là **không đủ** để đạt hiệu năng truy hồi cao. Việc **kết hợp nhiều đặc trưng (feature fusion)** có thể cải thiện độ chính xác, nhưng cũng làm tăng số chiều của vector đặc trưng → gây ra vấn đề "lời nguyền chiều cao" (curse of dimensionality).

Do đó:

- Các phương pháp **giảm chiều (dimensionality reduction)** là một hướng nghiên cứu cần được quan tâm nhiều hơn.
- Cần tập trung vào việc cải thiện **biểu diễn ảnh hiệu quả với vector đặc trưng có số chiều thấp đến trung bình**, vừa chính xác vừa tiết kiệm chi phí.

---

## 9.3. Vai trò của học máy

Trong những năm gần đây, các thuật toán truy hồi thông tin đã được hưởng lợi từ việc áp dụng nhiều thuật toán học máy khác nhau, chẳng hạn như:

- **Học sâu (Deep Learning)**,
- **SVM**,
- **K-means**.

Các phương pháp này được dự đoán sẽ tiếp tục nhận được nhiều sự quan tâm hơn trong tương lai.

---

## 9.4. Relevance Feedback (phản hồi liên quan)

Để **cải thiện sự hài lòng của người dùng và tăng độ chính xác**, nhiều thuật toán CBIR tích hợp giai đoạn **relevance feedback**.

- Ở giai đoạn này, người dùng can thiệp để xác định đâu là ảnh liên quan và không liên quan trong tập ảnh truy hồi.
- Hệ thống sẽ **cập nhật hoặc điều chỉnh trọng số đặc trưng/metric**, rồi tính toán lại kết quả.

Tuy nhiên, đây là một **nhiệm vụ đầy thách thức**, vì cần đảm bảo sự hài lòng của người dùng với **ít lần lặp lại nhất**.

---

## 9.5. CBIR trong các lĩnh vực đặc thù

Hệ thống CBIR trong các **miền ứng dụng chuyên biệt** có nhiều đặc trưng riêng cần được chú ý ngay từ khâu thiết kế, ví dụ:

- **Ảnh y tế (medical images)**: yêu cầu độ chính xác cao, đặc thù trong chẩn đoán.
- Các lĩnh vực khoa học, kỹ thuật, an ninh…

Một thách thức quan trọng khác là **xây dựng các tập dữ liệu mới** phù hợp với yêu cầu của từng lĩnh vực chuyên biệt này.
