# Tổng quan bài báo Retargeting Matters

Bài báo hỏi **chất lượng chuyển động mẫu ảnh hưởng thế nào đến khả năng robot hình người học và bám động tác của người**. Nhóm tác giả đề xuất **General Motion Retargeting (GMR)** để tạo chuyển động mẫu phù hợp hơn với robot. Trên 21 chuỗi thử nghiệm với Unitree G1 trong mô phỏng, dữ liệu từ GMR nhìn chung giúp robot bám tốt hơn dữ liệu từ PHC và ProtoMotions. Chuyển động GMR cũng được đánh giá là giống chuyển động người hơn hai phương pháp này, với tỷ lệ bám thành công và độ giống bản gốc gần mốc dữ liệu Unitree. [Tóm tắt và Mục I, V của arXiv v1](https://arxiv.org/html/2510.02252v1)

## Tác giả, hội nghị và xếp hạng

| Thông tin | Chi tiết |
| --- | --- |
| Tên đầy đủ | *Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking* |
| Tác giả | João Pedro Araújo, Yanjie Ze, Pei Xu, Jiajun Wu và C. Karen Liu, Stanford University. [Trang của nhóm tác giả](https://jaraujo98.github.io/retargeting_matters/) |
| Bản đọc trong project | Bản tiền ấn phẩm **arXiv:2510.02252v1**, đăng ngày **02/10/2025**. [Hồ sơ arXiv v1](https://arxiv.org/abs/2510.02252v1) |
| Công bố chính thức | Kỷ yếu **2026 IEEE International Conference on Robotics and Automation (ICRA)**, tr. **6097–6104**. IEEE Xplore đưa bài lên ngày **30/09/2026**. [IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/11697263) · [DBLP](https://dblp.org/rec/conf/icra/AraujoZXWL26) |
| Hội nghị | **ICRA 2026**, diễn ra từ **01–05/06/2026** tại **Vienna, Áo**. ICRA là hội nghị chủ lực của IEEE Robotics and Automation Society. [Trang hội nghị](https://2026.ieee-icra.org/contribute/call-for-icra-2026-papers-now-accepting-submissions/) |
| Hạng hội nghị | **A\*** theo **ICORE 2026**. Hồ sơ cũng ghi **A\*** theo **CORE 2023**. Hạng này áp dụng cho hội nghị ICRA. [ICORE Conference Portal](https://portal.core.edu.au/conf-ranks/2051/) |
| DOI của bản kỷ yếu | [`10.1109/ICRA57385.2026.11697263`](https://doi.org/10.1109/ICRA57385.2026.11697263) |

Các mục dưới đây theo nội dung, tên phép đối chiếu và số hình, bảng của **arXiv v1**. Bản kỷ yếu gọi phương pháp đối chiếu là **ProtoMotions2**, bổ sung phép đo thời gian xử lý và thí nghiệm về vai trò của hai giai đoạn động học nghịch. [arXiv v1](https://arxiv.org/html/2510.02252v1) · [Bản ICRA do tác giả lưu](https://www.jiajunwu.com/papers/gmr_icra.pdf)

## Bài toán và thuật ngữ

Người và robot có tỷ lệ cơ thể, cấu trúc và giới hạn khớp khác nhau. Để robot học một động tác của người, trước hết cần tạo mẫu chuyển động dành cho chính robot. Mẫu này quyết định động tác mà bộ điều khiển sẽ học để thực hiện. [Mục I, arXiv v1](https://arxiv.org/html/2510.02252v1#S1)

**Chuyển động của người → chuyển đổi sang robot → quỹ đạo mẫu của robot → huấn luyện chính sách điều khiển → robot thực hiện động tác.**

| Thuật ngữ | Cách nói tiếng Việt | Nghĩa trong bài |
| --- | --- | --- |
| **Retargeting** | **Chuyển đổi chuyển động từ người sang robot** | Điều chỉnh dữ liệu chuyển động của người cho phù hợp với cơ thể và khớp của robot. Đầu ra là quỹ đạo tham chiếu, tức chuyển động mẫu của robot theo thời gian. |
| **Artifacts** | **Lỗi phát sinh khi chuyển đổi chuyển động** | Những bất thường nằm trong quỹ đạo mẫu. Ví dụ, chân trụ trượt trên sàn, bàn chân xuyên sàn, hai chân xuyên nhau hoặc góc khớp đổi đột ngột. |
| **Motion tracking policies** | **Các chính sách điều khiển bám chuyển động** | Các mô hình điều khiển được huấn luyện bằng học tăng cường. Ở mỗi bước, chính sách dùng thông tin về robot và mục tiêu tham chiếu để chọn hành động giúp robot bám động tác. |
| **General Motion Retargeting (GMR)** | **Phương pháp chuyển đổi chuyển động tổng quát** | Phương pháp nhóm tác giả đề xuất để tạo quỹ đạo mẫu cho robot. BeyondMimic dùng quỹ đạo này ở bước huấn luyện chính sách. |

## GMR tạo quỹ đạo mẫu như thế nào

1. **Ghép các bộ phận tương ứng** giữa người và robot, chẳng hạn thân, tay và chân.
2. **Căn chỉnh tư thế nghỉ** để hướng của các bộ phận tương ứng khớp nhau tại tư thế chuẩn.
3. **Điều chỉnh tỷ lệ theo từng bộ phận**. GMR dùng hệ số riêng cho vị trí của từng bộ phận so với gốc cơ thể, để thích ứng với khác biệt về tỷ lệ thân, tay và chân.
4. **Tìm tư thế robot bằng động học nghịch**. Giai đoạn đầu giảm sai lệch về hướng của các bộ phận chính và vị trí của bàn tay, bàn chân, trong giới hạn khớp của robot.
5. **Tinh chỉnh tư thế** từ nghiệm trước bằng cách xét cả vị trí lẫn hướng của các bộ phận chính đã ghép.

Xem sơ đồ quy trình ở **Hình 2**, trang PDF 4, và mô tả ở Mục IV. [Mục IV, arXiv v1](https://arxiv.org/html/2510.02252v1#S4)

## Thí nghiệm và kết quả

Nhóm dùng **21 chuỗi LAFAN1**, từ đi bộ đến chạy, nhảy và múa, để so sánh dữ liệu tạo bởi **PHC, ProtoMotions, GMR** và **dữ liệu Unitree** được tạo bằng một phương pháp đóng. Mỗi quỹ đạo tham chiếu có một chính sách được huấn luyện riêng cho **Unitree G1** bằng cùng quy trình **BeyondMimic**, với hàm thưởng giữ chung để đánh giá ảnh hưởng của dữ liệu đầu vào. [Mục III, arXiv v1](https://arxiv.org/html/2510.02252v1#S3)

- **Tỷ lệ thành công** là phần trăm lượt robot đi hết chuỗi mà sai lệch về độ cao và hướng của bộ phận dùng làm mốc so với mẫu vẫn trong ngưỡng cho phép. Trong Bảng I, **14/21 chuỗi** có tỷ lệ thành công trên 98% cho mọi nguồn dữ liệu ở các thiết lập mô phỏng. Chênh lệch thấy rõ ở một số chuỗi có lỗi trong mẫu. [Mục III-D và V-A, arXiv v1](https://arxiv.org/html/2510.02252v1#S5)
- **Sai số bám** đo độ lệch giữa chuyển động robot thực hiện và quỹ đạo tham chiếu. Trong mô phỏng IsaacSim ở Bảng II, GMR có sai số trung bình thấp hơn PHC và ProtoMotions ở cả ba chỉ số vị trí hoặc góc khớp. Dữ liệu Unitree có sai số trung bình thấp nhất ở cả ba chỉ số. [Mục V-A, Bảng II](https://arxiv.org/html/2510.02252v1#S5)
- **Độ giống chuyển động người** được đánh giá bằng khảo sát **20 người**. GMR được đánh giá là giống bản gốc hơn PHC và ProtoMotions. Dữ liệu Unitree vẫn nhỉnh hơn trong phép so sánh này. [Mục V-C, Hình 4](https://arxiv.org/html/2510.02252v1#S5)

### Ví dụ về lỗi trong quỹ đạo mẫu

Tỷ lệ thành công dưới đây thuộc thiết lập **sim2sim** dùng MuJoCo qua ROS. [Bảng I và Hình 3, arXiv v1](https://arxiv.org/html/2510.02252v1#S5)

| Chuỗi | Lỗi quan sát được trong quỹ đạo mẫu | PHC | GMR | ProtoMotions | Unitree |
| --- | --- | ---: | ---: | ---: | ---: |
| Dance 1 | Bàn chân xuyên sàn trong mẫu PHC | 0% | 100% | 100% | 100% |
| Run (stop & go) | Hai chân xuyên nhau trong mẫu ProtoMotions | 74% | 100% | 26% | 100% |
| Dance 5 | Góc nghiêng ở eo thay đổi đột ngột trong mẫu GMR | 100% | 51% | 100% | 100% |

## Phạm vi kết luận

Các tỷ lệ trên được đo trong mô phỏng **Unitree G1** trên những chuỗi được chọn. Phạm vi chính là chuyển động toàn thân ít tương tác phức tạp với vật thể hay môi trường. **Dance 5** cho thấy GMR vẫn có thể sinh lỗi từ bước tối ưu. Trạng thái ở khung hình đầu cũng có thể làm thay đổi tỷ lệ thành công vì robot bắt đầu từ tư thế mặc định. [Mục III-B, V-B và V-D, arXiv v1](https://arxiv.org/html/2510.02252v1)

## Tài liệu đọc cùng

- [PDF arXiv v1 trong project](./2510.02252v1.pdf) và [văn bản đã trích theo trang](./2510.02252v1-extract/noi-dung.txt).
- [Hình 2 về quy trình GMR, trang 4](./2510.02252v1-extract/trang/trang-4.png) và [Hình 3 về các lỗi, trang 7](./2510.02252v1-extract/trang/trang-7.png).
- [Trang dự án của tác giả, có minh họa chuyển động](https://jaraujo98.github.io/retargeting_matters/) và [mã nguồn GMR](https://github.com/YanjieZe/GMR).
