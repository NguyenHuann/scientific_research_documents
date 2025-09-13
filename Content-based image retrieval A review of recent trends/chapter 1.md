# 1. Giới thiệu

Một lượng khổng lồ cơ sở dữ liệu hình ảnh đã được tạo ra bởi các lĩnh vực giáo dục, công nghiệp, y tế, xã hội và nhiều lĩnh vực khác trong đời sống. Tất cả các kho dữ liệu hình ảnh này đều đòi hỏi một cơ chế tìm kiếm ảnh mạnh mẽ. Có hai phương pháp tìm kiếm phổ biến:

**Phương pháp thứ nhất** dựa trên từ khóa để gắn nhãn cho ảnh, được gọi là truy hồi ảnh dựa trên văn bản (Text-Based Image Retrieval – TBIR) (Y. Liu và cộng sự, 2007). Tuy nhiên, phương pháp này tồn tại nhiều nhược điểm:

1. Việc gắn nhãn thủ công cho các cơ sở dữ liệu lớn là không khả thi.
2. Người dùng cuối phải thực hiện việc gắn nhãn, khiến cho phương pháp này phụ thuộc vào nhận thức chủ quan của con người.
3. Các nhãn chú thích chỉ có thể áp dụng cho một ngôn ngữ duy nhất.

**Phương pháp thứ hai** là “truy hồi ảnh dựa trên nội dung” (Content-Based Image Retrieval – CBIR), được khuyến nghị cao nhằm khắc phục những nhược điểm của phương pháp dựa trên văn bản (Raghunathan & Acton, 1999).

CBIR được sử dụng để tìm kiếm trong cơ sở dữ liệu hình ảnh, nhằm truy xuất những hình ảnh có nội dung thị giác tương tự với hình ảnh truy vấn được chỉ định (Jenni và cộng sự, 2015; Ali và cộng sự, 2020). Phương pháp này hoàn toàn tự động. Tuy nhiên, nó gặp phải vấn đề “**khoảng cách ngữ nghĩa**”, tức là khoảng cách giữa các đặc trưng mức thấp mô tả hình ảnh và các khái niệm mức cao (nhận thức) chứa trong hình ảnh (Bai và cộng sự, 2018), dẫn đến việc truy hồi ảnh không chính xác. Trong ba thập kỷ qua, khoảng cách này đã trở thành trọng tâm của nhiều nghiên cứu (Shrivastava & Tyagi, 2017).

Nhiều phương pháp đã được phát minh để chuyển đổi các khái niệm mức cao trong hình ảnh thành các đặc trưng. Các đặc trưng này chính là nền tảng của CBIR. Nói chung, đặc trưng được chia thành **đặc trưng toàn cục (global features)** và **đặc trưng cục bộ (local features)**, tùy thuộc vào phương pháp trích xuất đặc trưng:

- **Đặc trưng toàn cục** (ví dụ: màu sắc, kết cấu, hình dạng, và thông tin không gian) đại diện cho toàn bộ hình ảnh. Ưu điểm của chúng là tốc độ trích xuất và tính toán độ tương đồng nhanh (Datta và cộng sự, 2008). Tuy nhiên, chúng không phân biệt được giữa đối tượng và nền trong ảnh (các phần khác nhau của ảnh). Điều này khiến chúng không phù hợp cho việc truy hồi trong các cảnh phức tạp hoặc nhận dạng đối tượng (Halawani và cộng sự, 2006), nhưng lại thích hợp cho phân loại và phát hiện đối tượng (Ghrabat và cộng sự, 2019).

- **Đặc trưng cục bộ** thì phù hợp hơn cho truy hồi ảnh, các nhiệm vụ so khớp và nhận dạng (Halawani và cộng sự, 2006). “Nhận dạng đối tượng là nhiệm vụ nhận diện và gán nhãn cho đối tượng trong ảnh” (Bansal và cộng sự, 2020), trong khi phát hiện đối tượng quan tâm đến sự tồn tại của một đối tượng thuộc lớp đã định sẵn trong ảnh cùng với vị trí của nó (Mittal và cộng sự, 2019). Vì vậy, phân loại là một tiểu nhiệm vụ của phát hiện đối tượng (Mittal và cộng sự, 2019). Đặc trưng cục bộ được định nghĩa là các điểm đặc trưng hoặc một số phần trong ảnh, chẳng hạn như góc, vùng nổi (blobs), và biên cạnh. Chúng bền vững trước sự thay đổi về tỷ lệ, xoay, tịnh tiến, thay đổi nền, sự rối loạn và che khuất một phần (Halawani và cộng sự, 2006).

**Trích xuất đặc trưng** là quá trình đầu tiên trong CBIR, nhằm chuyển đổi nhận thức của con người thành mô tả số mà máy có thể xử lý. Độ chính xác của các ảnh được truy hồi chịu ảnh hưởng lớn bởi các đặc trưng được trích xuất (Piras & Giacinto, 2017). Tuy nhiên, việc lựa chọn này phụ thuộc vào yêu cầu của người dùng. Việc đưa các đặc trưng đã trích xuất vào các thuật toán học máy (có giám sát hoặc không giám sát) có thể cải thiện hiệu năng của CBIR (D. Zhang và cộng sự, 2012).

Các xu hướng nghiên cứu gần đây về truy hồi ảnh tập trung vào việc sử dụng **học sâu (deep learning)** để cải thiện độ chính xác, nhưng phải đánh đổi bằng thời gian xử lý lâu hơn (Markowska-Kaczmar & Kwaśnicka, 2018).

Một vấn đề khác ảnh hưởng tiêu cực đến hiệu năng CBIR (ví dụ: sử dụng bộ nhớ, khả năng mở rộng, tốc độ, độ chính xác) là **tính chất đa chiều cao** của các đặc trưng thường được sinh ra khi cố gắng chuyển đổi nội dung thị giác của ảnh thành dạng đặc trưng số. Các biểu diễn đặc trưng đa chiều này, còn được gọi là **“lời nguyền chiều” (curse of dimensionality)**, thường có bản chất phân bố thưa (Zhuo và cộng sự, 2014). **Giảm chiều dữ liệu (dimensionality reduction)** là một giải pháp cho vấn đề này (Zhuo và cộng sự, 2014).

Trong các tài liệu, đã có nhiều nghiên cứu toàn diện bàn về các phương pháp giảm chiều khác nhau (Zhuo và cộng sự, 2014; Perronnin và cộng sự, 2012).

**Đo lường độ tương đồng (similarity measure)** cũng là một quy trình quan trọng khác ảnh hưởng đến hiệu năng CBIR. Vì việc đo này được xác định bởi cấu trúc của vector đặc trưng, nên nếu chọn sai thước đo sẽ dẫn đến việc trả về các ảnh ít giống nhau, làm giảm độ chính xác của hệ thống CBIR. Ngược lại, khi sử dụng thước đo phù hợp, có thể đạt được độ chính xác cao.

Vì nhiều bộ dữ liệu đã được dùng trong các khung CBIR, các chỉ số như **precision (độ chính xác)**, **recall (độ bao phủ)**, và **thời gian chạy** thường được sử dụng để đánh giá hiệu quả của CBIR, vốn bị ảnh hưởng bởi lựa chọn bộ dữ liệu ảnh (J. Z. Wang và cộng sự, 2000; Jain và cộng sự, 2011; Oliva và Torralba, 2001; Srivastava và Khare, 2017; Das và Thepade, 2016; Yang và cộng sự, 2018; Fei-Fei và cộng sự, 2007; Griffin và cộng sự, 2007; Ashraf và cộng sự, 2020).

Ngày càng có nhiều nghiên cứu được tiến hành trong lĩnh vực CBIR, với nhiều hướng đi mới. Nhiều khảo sát và nghiên cứu đã báo cáo những thách thức lớn và xem xét các phương pháp hiện tại (Alzu’bi và cộng sự, 2015; Tarawneh và cộng sự, 2020; Latif và cộng sự, 2019; Ghosh và cộng sự, 2018; Tian, 2018).

Bài báo này nhằm trả lời những câu hỏi sau:

- Làm thế nào việc **kết hợp đặc trưng (feature fusing)** giúp thu hẹp khoảng cách ngữ nghĩa và cải thiện độ chính xác của truy hồi?
- Việc sử dụng **các thuật toán học máy mới nhất** ảnh hưởng tích cực thế nào đến độ chính xác của hệ thống, và chúng ảnh hưởng ra sao đến chi phí tính toán và sử dụng bộ nhớ?
- Việc sử dụng **các thước đo bền vững và bộ dữ liệu phù hợp** cải thiện hiệu năng hệ thống như thế nào về tính đặc hiệu, sử dụng bộ nhớ và chi phí tính toán?
- Những **xu hướng nghiên cứu tương lai** có thể là gì?

**Cấu trúc bài báo**:

- Phần 2: mô tả ngắn gọn khung CBIR.
- Phần 3: xem xét các nghiên cứu gần đây nhất về CBIR trong 6 năm qua theo phương pháp truy hồi ảnh.
- Phần 4: khám phá các thuật toán học máy mới nhất được triển khai trong lĩnh vực này.
- Phần 5: so sánh các kỹ thuật CBIR khác nhau.
- Phần 6: tập trung vào các thước đo độ tương đồng.
- Phần 7: xem xét chi tiết các bộ dữ liệu ảnh được dùng để đánh giá hiệu năng.
- Phần 8: khám phá các biện pháp được dùng để đánh giá hiệu năng.
- Phần 9: thảo luận các vấn đề then chốt trong CBIR cùng với những hướng nghiên cứu quan trọng.
- Phần 10: kết luận bài báo.
