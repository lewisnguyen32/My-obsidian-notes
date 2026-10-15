**Để bám hướng mới nhất, bạn nên đọc Demo kèm comment trước, rồi tài liệu đề tài, sau đó mới đọc paper.** Tôi đã kiểm tra cả hai tài liệu Word, hai sheet Excel và đối chiếu bộ 10 paper với bản trích xuất đã lưu.

Đọc mục tiêu, câu hỏi thực nghiệm, framework, dataset và **cả hai comment của Trang ngày 15/10/2026**, theo giờ Việt Nam:

- **04:09:** xử lý và đánh giá dữ liệu theo hai hướng **có depth / không depth**.
- **04:31:** baseline dùng **rule-based**; phương pháp đề xuất dùng model dự đoán **vector giá trị servo từ action frames**, dưới dạng **multi-target regression**.

Đây là file nên đọc đầu tiên vì các comment bổ sung hướng phương pháp và cách tổ chức thí nghiệm.

Đọc theo thứ tự: **tên đề tài → mục tiêu và contributions → research questions → research gap → bối cảnh**.

Bạn cần hiểu vì sao chọn TonyPi/RGB-D, muốn chứng minh lợi ích của depth thế nào và đánh giá độ trễ ra sao. Chú ý: nội dung chính nhấn mạnh **geometric pipeline**, còn comment mới trong Demo bổ sung **hướng học dự đoán servo**. Quan hệ giữa hai hướng này vẫn cần được làm rõ.

Đọc sheet **Conference 1 trước**, rồi **Literature Review**. Dùng file này để định vị các nhánh tài liệu. Nhiều dòng mới có tên và nguồn paper, nên chưa thể dùng nó để xác định phần việc nào đã hoàn thành.

Sau đó, lướt [NOTES.md](D:/Projects/Clone/Physical AI/PAPERS/extracted/NOTES.md) để có bản đồ tổng quan, rồi đọc paper theo thứ tự sau:

|Thứ tự|Paper|Mục đích đọc|
|---|---|---|
|**4**|RGB-D Pose — D:/Projects/Clone/Physical AI/PAPERS/3D Human Pose Estimation in RGBD Images for Robotic Task Learning.pdf|Hiểu bước **RGB + depth → khớp người 3D**, sát với câu hỏi về depth trong comment mới.|
|**5**|Koenemann — D:/Projects/Clone/Physical AI/PAPERS/koenemann14icra.pdf|Hiểu baseline **chuẩn hóa tỷ lệ → IK → xử lý thăng bằng** trên robot NAO.|
|**6**|D:/Projects/Clone/Physical AI/PAPERS/Whole-Body Geometric Retargeting for Humanoid Robots.pdf|Hiểu ánh xạ orientation giữa người và robot, cùng vai trò của controller.|
|**7**|GMR — D:/Projects/Clone/Physical AI/PAPERS/2510.02252v1.pdf|Hiểu retargeting hiện đại: rest pose, scale, giới hạn khớp và IK. Hữu ích để thiết kế baseline hình học.|
|**8**|SMPL — D:/Projects/Clone/Physical AI/PAPERS/SMPL2015_fixed.pdf|Nắm biểu diễn cơ thể, pose, shape và skeleton để đọc các bài tiếp theo.|
|**9**|HUMROB — D:/Projects/Clone/Physical AI/PAPERS/GenerativemotionReatargetingRGBD.pdf|Xem một cách nối trực tiếp RGB-D với góc khớp robot. Chú ý hệ này xử lý khoảng **3 giây/frame**, nên chủ yếu tham khảo phương pháp.|
|**10**|AMASS — D:/Projects/Clone/Physical AI/PAPERS/AMASS.pdf|Hiểu nguồn dữ liệu chuyển động dùng trong nhánh học điều khiển.|
|**11**|H2O — D:/Projects/Clone/Physical AI/PAPERS/H2O_paper.pdf|Hiểu pipeline retargeting, lọc chuyển động khả thi, học tracking và teleoperation.|
|**12**|OmniH2O — D:/Projects/Clone/Physical AI/PAPERS/OmniH2O_paper.pdf|Hiểu phần mở rộng từ H2O và cách thu demonstration để học tác vụ.|
|**13**|HumanPlus — D:/Projects/Clone/Physical AI/PAPERS/HumanPlus.pdf|Phân biệt bắt chước trực tiếp với học tác vụ tự hành từ demonstration. Đọc để định vị hướng dài hạn của model đề xuất.|

**Nếu cần bắt kịp nhanh, ưu tiên bước 1–7.** Khi đọc, tập trung trả lời ba câu: dữ liệu đầu vào là gì, đầu ra servo được tạo thế nào, và so sánh có/không depth được tổ chức ra sao.

Các file hiện chưa ghi rõ module nào đã chạy thành công hay kết quả đo thực tế. Vì vậy, thứ tự trên bám **hướng nghiên cứu cập nhật tới comment ngày 15/10**; tiến độ triển khai cụ thể vẫn cần thêm context từ bạn.