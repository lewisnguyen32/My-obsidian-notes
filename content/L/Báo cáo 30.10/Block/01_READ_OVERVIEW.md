---
duration_minutes: 60
phase: reading
status: todo
paper_version: arxiv-2510.02252v1
---

# Block 1 — Đọc tổng quan và nắm câu chuyện nghiên cứu

[[00_START_HERE]] · Tiếp theo: [[02_READ_METHOD]]

**Thời lượng: 60 phút.** Chỉ đọc và ghi chú học. Đối chiếu **lượt 1–2** trong [checklist](../GMR_READING_CHECKLIST.md), phục vụ **O1–O4 / S1–S4** trong [bản thảo](../PRESENTATION_SLIDE.md). O là số slide gốc; S là số slide rút gọn.

## Mục tiêu

Hiểu vấn đề, đóng góp, ba câu hỏi nghiên cứu và hai công việc: GMR tạo reference; BeyondMimic dùng RL để học tracking. Chưa cần thuộc công thức hay số liệu.

## Làm gì trong 60 phút

|   Phút | Việc làm                                                                                                                                            | Ghi lại                                                                                                                                             |
| -----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
|      5 | Mở [PDF v1](../tmp/2510.02252v1.pdf), kiểm tra nhãn v1 ở trang 1 và PDF có 9 trang. Xem bản đồ đọc trong index.                                     | Phiên bản và câu hỏi trung tâm.                                                                                                                     |
|     18 | Đọc kỹ **Abstract và I. Introduction, trang 1–2**; dừng trước Related Work.                                                                         | Embodiment gap; vấn đề của reference có artifacts; hai đóng góp.                                                                                    |
|      5 | Lướt **II. Related Work, trang 2–3**. Chỉ xác định bối cảnh copying joint rotations, IK và các retargeter; chưa học Eq. 1 của PHC.                  | Retargeting có nhiều cách; paper đang so sánh những lựa chọn nào.                                                                                   |
|      7 | Đọc **Q1–Q3 đầu III. Evaluation Method, trang 3**.                                                                                                  | Viết lại mỗi câu hỏi bằng một câu tiếng Việt.                                                                                                       |
|     10 | Xem [Figure 2, trang 4](../tmp/extracted/visuals/page-004.png), đọc mở đầu **IV. General Motion Retargeting**. Nhìn tên năm bước và đầu vào/đầu ra. | Một sơ đồ ghi chú: human motion → GMR → robot reference → RL tracking → đánh giá. Sơ đồ này là diễn giải của mình, không phải toàn bộ Figure 2 gốc. |
|      3 | Lướt **VI. Conclusion, trang 7–8**.                                                                                                                 | Một kết luận chính và một giới hạn cần kiểm tra kỹ ở block 3.                                                                                       |
|     10 | Trả lời ngắn các câu ôn tập dưới đây bằng ghi chú, sau đó mở đáp án để đối chiếu.                                                                   | Đánh dấu câu chưa giải thích được.                                                                                                                  |
|      2 | Chốt đoạn tóm tắt **5–7 câu tiếng Việt**.                                                                                                           | Vấn đề → ý tưởng → cách kiểm chứng → giới hạn; không chép Abstract.                                                                                 |
| **60** | **Tổng**                                                                                                                                            |                                                                                                                                                     |

## Đầu ra và điểm dừng

- [ ] Có đoạn 5–7 câu bằng lời của mình và Q1–Q3 bằng tiếng Việt.
- [ ] Ghi đúng hai đóng góp: phương pháp GMR và nghiên cứu so sánh ảnh hưởng chất lượng retargeting.
- [ ] Sơ đồ tách được retargeting, reference và policy tracking.
- [ ] Có danh sách câu chưa hiểu để quay lại đúng chỗ, không tự điền một giải thích chưa kiểm chứng.

Đây là kiểm tra đọc hiểu; luyện một bài nói hoàn chỉnh nằm ở block 6. Nếu hết thời lượng mà còn vướng, ghi đúng câu hỏi và nguồn cần tra; không coi việc đã đọc qua là đã hiểu.

## Câu hỏi ôn tập

1. Nếu chỉ dùng một câu, paper nghiên cứu điều gì?
2. Vì sao chép nguyên góc khớp người sang robot có thể không tạo ra chuyển động phù hợp?
3. Reference motion khác chuyển động robot thực sự tạo ra ở điểm nào? Nêu một artifact.
4. Q1, Q2 và Q3 lần lượt hỏi điều gì?
5. Hai đóng góp chính là gì? Một phát biểu mạnh trong Abstract cần được kiểm tra bằng bằng chứng nào?
6. GMR nhận gì và tạo ra gì? Figure 2 có năm bước nào?
7. RL nằm ở đâu? Huấn luyện policy khác chạy policy để đánh giá thế nào?
8. Paper này đã chứng minh hệ RGB-D/TonyPi của nhóm hoạt động chưa?

> [!success]- Đáp án gợi ý — tự trả lời trước khi mở
> **1.** Paper nghiên cứu chất lượng chuyển động sau retargeting ảnh hưởng thế nào đến việc học và hiệu năng bám chuyển động của humanoid, đồng thời đề xuất GMR để cải thiện reference. **Nguồn:** Abstract/Introduction, trang 1–2; III, trang 3.
>
> **2.** Góc khớp giống nhau không bù được khác biệt chiều dài đoạn cơ thể, cấu trúc/trục khớp, tầm chuyển động và các đặc tính vật lý; tư thế đích có thể trượt chân, xuyên đất hoặc không phù hợp robot. **Nguồn:** Introduction, trang 1; Related Work, trang 2–3.
>
> **3.** Reference là đích cần bám; controller/policy tạo hành động và robot có thể chỉ bám gần đúng hoặc thất bại. Ví dụ artifact: reference yêu cầu chân xuyên xuống sàn. Đây là lỗi dữ liệu mục tiêu, không phải bằng chứng robot thực đã làm được tư thế đó. **Nguồn:** Introduction, trang 1–2; III-C–D, trang 4.
>
> **4.** Q1: lựa chọn retargeter có ảnh hưởng hiệu năng tracking policy không? Q2: artifacts nào gây hại và cản việc học? Q3: các retargeter giữ được hình thức chuyển động nguồn tới đâu? **Nguồn:** đầu III, trang 3.
>
> **5.** Hai đóng góp: GMR và nghiên cứu so sánh ảnh hưởng reference quality. Abstract tuyên bố GMR tốt hơn các phương pháp mở; phải kiểm tra với Table I–II và Figure 4 trong điều kiện đo tương ứng, đồng thời xem ngoại lệ như Dance 5. Một tuyên bố tổng quát trong Abstract không có nghĩa GMR thắng mọi ô kết quả. **Nguồn:** cuối Introduction, trang 2; kết quả ở trang 6–7, sẽ đọc ở block 3.
>
> **6.** Đầu vào gồm chuyển động/skeleton người và thông tin cấu trúc robot, cùng mapping/cấu hình cần thiết; đầu ra là chuỗi root pose và giá trị khớp robot làm reference. Năm bước: key body matching; rest-pose alignment; non-uniform local scaling; IK giai đoạn đầu; IK tinh chỉnh. Nhãn Step 4 trong Figure 2 nhấn mạnh rotation nhưng công thức còn xét vị trí tay/chân; chi tiết ở block 2. **Nguồn:** Figure 2 và IV, trang 4–5.
>
> **7.** GMR tạo reference bằng hình học/IK. BeyondMimic dùng reference để huấn luyện tracking policy bằng RL; sau đó chạy policy đã huấn luyện trong các rollout để đánh giá. Không đồng nhất reference với action hoặc GMR với thuật toán retargeting bằng RL. **Nguồn:** III, trang 3; III-C và IV, trang 4–5.
>
> **8.** Chưa. V1 đánh giá retargeting/tracking trên LAFAN1 và Unitree G1 với mô phỏng/sim2sim. Liên hệ với nhóm là phân tích của người trình bày, cần kiểm chứng riêng về perception, phần cứng và điều khiển. **Nguồn:** III-B–C, trang 3–4; Conclusion, trang 7–8. **Đối chiếu:** O14 trong bản thảo.

## Kiến thức cần nhớ sau khi đọc

| Từ khóa | Ý nghĩa cần giữ |
| --- | --- |
| Embodiment gap | Người và robot khác tỷ lệ, cấu trúc/giới hạn khớp, hình dạng, phân bố khối lượng và cơ cấu chấp hành. |
| Retargeting | Chuyển chuyển động nguồn sang cấu hình/chuyển động đích phù hợp với embodiment robot. |
| Reference motion | Chuyển động mục tiêu để controller bám; có thể chứa lỗi và chưa phải chuyển động robot đã thực hiện thành công. |
| Retargeting artifact | Lỗi như foot sliding, ground penetration, self-intersection hoặc joint values nhảy đột ngột. |
| GMR | Ghép key bodies → alignment → scaling → IK giai đoạn đầu → IK tinh chỉnh. |
| Tracking policy | Policy được học để chọn hành động điều khiển bám reference; trong nghiên cứu này dùng BeyondMimic/RL. |
| Phạm vi | Câu chuyện của v1 là đánh giá trên benchmark/mô phỏng; chưa phải bằng chứng cho pipeline RGB-D tới TonyPi. |
