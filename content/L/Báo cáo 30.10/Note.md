**① Một giờ đầu: hiểu paper nghiên cứu chuyện gì**

| Thời gian   | Đọc phần nào                                                           | Cần hiểu gì                                                                                             |
| ----------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **20 phút** | **Abstract + I. Introduction**, trang **1–2**                          | Vì sao chuyển động người cần retarget? Reference có lỗi ảnh hưởng tới robot thế nào? Paper đóng góp gì? |
| **5 phút**  | Ba câu hỏi **Q1–Q3**, đầu **III. Evaluation Method**, trang **3**      | Tác giả muốn kiểm tra ba khía cạnh nào?                                                                 |
| **20 phút** | **Figure 2 + đoạn mở đầu IV. General Motion Retargeting**, trang **4** | Nhìn tên và vai trò của năm bước. Xác định đầu vào, đầu ra GMR và vị trí của RL trong nghiên cứu.       |
| **5 phút**  | Lướt **VI. Conclusion**, trang **7–8**                                 | Kết luận chính và phạm vi của kết quả.                                                                  |
| **10 phút** | Đóng paper, tự ghi và nói lại                                          | Tóm tắt bài trong **5–7 câu tiếng Việt**.                                                               |

**Đạt yêu cầu khi:** bạn nói được _paper giải quyết vấn đề gì, GMR tạo ra gì và RL dùng để làm gì_. Giờ này chỉ cần hiểu luồng tổng thể.

**② Hai giờ tiếp theo: đọc kỹ phương pháp GMR**

Tập trung **Section IV, trang 4–5**. Đây là phần cần dành nhiều công sức nhất.

|Thời gian|Đọc phần nào|Cần hiểu gì|
|---|---|---|
|**25 phút**|**Step 1 — Key Body Matching** và **Step 2 — Rest Pose Alignment**|Ghép phần cơ thể nào với phần nào? Vì sao ghép đúng tên vẫn cần căn chỉnh hướng/tư thế?|
|**25 phút**|**Step 3 — Non-Uniform Local Scaling**, **Eq. 2–3**|Phân biệt tỷ lệ từng phần cơ thể với tỷ lệ chuyển động root. Vì sao một tỷ lệ chiều cao chung chưa đủ?|
|**45 phút**|**Step 4–5**, **Eq. 4–6**|IK tìm gì, giảm sai số nào, có giới hạn gì? Hai giai đoạn khác nhau ở đâu?|
|**10 phút**|**Application to Motion Sequences**, trang **5**|Nghiệm frame trước giúp frame sau thế nào? Bước sửa độ cao sau cả chuỗi làm gì?|
|**15 phút**|Tự giải thích bằng một ví dụ giơ tay|Đi qua đủ năm bước, ghi **đầu vào → xử lý → đầu ra**.|

Với công thức, **Eq. 2–3 cần hiểu local/root; Eq. 4 và 6 cần so sánh hai giai đoạn**. Giai đoạn IK đầu đã xét **hướng và vị trí tay/chân**; giai đoạn sau tinh chỉnh vị trí toàn bộ key bodies.

**Eq. 5 ưu tiên hiểu vai trò cập nhật cấu hình robot**. Phần suy diễn Jacobian có thể để học tiếp. Dùng [ảnh trang 5](D:/Projects/iTwinLab/Physical AI/REPORT_2026-10-30/tmp/extracted/visuals/page-005.png) để nhìn rõ công thức.

**③ Một giờ tiếp theo: hiểu thí nghiệm và chọn bằng chứng để trình bày**

|Thời gian|Đọc phần nào|Cần lấy ra|
|---|---|---|
|**15 phút**|**III-A–B đọc lướt; III-C–E đọc kỹ**, trang **3–4**|Dataset, robot, các phương pháp so sánh; success, tracking error và user study đo gì.|
|**20 phút**|**Table I–II**, trang **6**, kèm caption và đoạn giải thích trong **V-A**|Table I: hai hàng **Run (stop & go)** và **Dance 5**, cột **sim2sim**. Table II: hàng **Mean**, chỉ số **global body-position error** ở điều kiện **sim**.|
|**10 phút**|**Figure 3(c), Figure 4** và đoạn **V-B–C**, trang **7**|Vì sao Dance 5 thất bại? User study cho phép kết luận gì?|
|**5 phút**|**V-D/Table III**, trang **7**, và đọc lại Conclusion|Ảnh hưởng của frame bắt đầu và giới hạn benchmark.|
|**10 phút**|Đóng paper, tự nói lại|**Hai kết quả chính, một trường hợp thất bại và một giới hạn.**|

Trong bốn giờ này, **Related Work chỉ tra khi gặp thuật ngữ cần làm rõ**. Hãy đọc sâu đúng các phần trên và ghi chỗ vướng cụ thể để xử lý trong thời gian hỏi đáp sáng mai.