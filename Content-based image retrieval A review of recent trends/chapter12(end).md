# 10. Kết luận (Conclusion)

Nhu cầu tìm kiếm một cơ chế truy hồi ảnh hiệu quả dựa trên **nội dung hình ảnh** xuất phát từ việc tồn tại một lượng lớn cơ sở dữ liệu ảnh và sự thiếu vắng một phương pháp truy hồi ảnh dựa trên văn bản hiệu quả.

Bài báo này đã trình bày **tổng quan tài liệu** về nhiều nghiên cứu trong lĩnh vực CBIR trong sáu năm gần đây. Đồng thời, bài báo cũng thảo luận về **các giai đoạn trong khung CBIR tổng quát** và những kỹ thuật mới nhất được áp dụng để **giảm khoảng cách ngữ nghĩa (semantic gap)**. Cuối cùng, bài báo đã nhấn mạnh một số vấn đề quan trọng nhất ảnh hưởng đến hiệu năng của CBIR, cũng như tập trung vào các hướng nghiên cứu có thể hỗ trợ phát triển một CBIR thế hệ mới. Tuy nhiên, việc thiết kế một thuật toán vừa đạt **độ chính xác truy hồi cao**, vừa giảm **chi phí tính toán** vẫn là một nhiệm vụ đầy thách thức.

---

## Thách thức chính: Semantic Gap

Vấn đề lớn nhất của bất kỳ thuật toán CBIR nào là **khoảng cách ngữ nghĩa** giữa ý nghĩa mức cao của hình ảnh và các đặc trưng trực quan mức thấp, bởi vì hầu hết các thuật toán CBIR khởi đầu từ những đặc trưng mức thấp (low-level features).

Để thu hẹp khoảng cách này, nhiều nỗ lực nghiên cứu đã được tiến hành:

- Phát triển các thuật toán CBIR sử dụng **đặc trưng mới** hoặc **kết hợp nhiều đặc trưng**.
- Các đặc trưng này được thiết kế và kiểm chứng thực nghiệm, cho thấy cộng đồng nghiên cứu đã có những đóng góp quan trọng.
- Các thuật toán CBIR thường được chia thành hai nhóm chính: **trích xuất đặc trưng toàn cục** và **trích xuất đặc trưng cục bộ**.

  - Cả hai đều là đặc trưng mức thấp.
  - Việc **kết hợp (fusion)** là cần thiết để giảm khoảng cách ngữ nghĩa và nâng cao độ chính xác.
  - Xu hướng kết hợp **đặc trưng toàn cục và cục bộ** đã chứng minh hiệu quả tốt và cần được chú ý hơn nữa.

Do những hạn chế của đặc trưng truyền thống, các nhà nghiên cứu đã áp dụng **thuật toán học máy** để thiết kế CBIR, và kết quả thu được là tích cực. Gần đây, nghiên cứu trong lĩnh vực CBIR tập trung nhiều vào **mạng nơ-ron sâu (Deep Neural Networks)**, vốn đã cho thấy kết quả rất tốt trên nhiều tập dữ liệu ảnh. Các thuật toán này đã phát triển nhanh chóng và hiệu quả trong những năm gần đây.

---

## Yêu cầu để xây dựng CBIR hiệu quả

Để đạt được một khung CBIR hiệu quả, các thành phần trong hệ thống phải được **chọn lựa cân đối**. Nghiên cứu này giúp phân tích những thành phần đó. Một hệ thống CBIR hiệu quả sẽ đóng góp vào nhiều ứng dụng thực tiễn, chẳng hạn như:

- Ứng dụng y tế,
- Tìm kiếm trên web,
- Mạng xã hội.

---

## Tóm lại

Một thuật toán có khả năng **thu hẹp khoảng cách ngữ nghĩa** là yêu cầu cấp thiết. Việc thiết kế thuật toán cần lưu ý:

1. **Trích xuất đặc trưng** và **thước đo tương đồng** phải được cân nhắc, vì chúng trực tiếp ảnh hưởng đến hiệu năng của CBIR.
2. Có thể trích xuất **nhiều đặc trưng hơn** để nâng cao độ chính xác, đồng thời phải duy trì **chi phí tính toán hợp lý**, nhất là đối với ứng dụng thời gian thực.
3. **Kết hợp đặc trưng toàn cục và cục bộ** sẽ giúp thiết kế cân bằng:

   - Đặc trưng cục bộ bền vững hơn với thay đổi tỷ lệ, dịch chuyển, xoay.
   - Đặc trưng toàn cục thì nhanh hơn trong trích xuất và tính toán độ tương đồng.

4. **Thuật toán học máy** có thể được dùng ở nhiều giai đoạn khác nhau để nâng cao độ chính xác, nhưng cần chú ý đến chi phí tính toán.
5. Luôn tồn tại **sự đánh đổi (trade-off)** giữa độ chính xác của hệ thống và chi phí tính toán.
