---
type: study-plan
paper_version: arxiv-2510.02252v1
total_minutes: 600
status: todo
---

# GMR — Bảy block chuẩn bị báo cáo

## Dùng bộ note này

Bộ note bám **bảy block trong ảnh Calendar của bạn**, tổng **600 phút**: đọc **240 phút** → làm slide **180 phút** → ôn tập **180 phút**. Chỉ ghi thời lượng bằng phút, không ấn định giờ bắt đầu. Đây là kế hoạch học, không xác nhận bạn đã đọc xong hoặc deck đã hoàn thành.

| Thứ tự   | Note                   | Loại việc                           |    Phút |
| -------- | ---------------------- | ----------------------------------- | ------: |
| 1        | [[01_READ_OVERVIEW]]   | Đọc tổng quan                       |      60 |
| 2        | [[02_READ_METHOD]]     | Đọc phương pháp                     |     120 |
| 3        | [[03_READ_EVIDENCE]]   | Đọc thí nghiệm, kết quả và giới hạn |      60 |
| 4        | [[04_BUILD_SLIDES]]    | Dựng deck                           |     120 |
| 5        | [[05_FINALIZE_SLIDES]] | Hoàn thiện và xuất file             |      60 |
| 6        | [[06_REHEARSE]]        | Luyện trình bày                     |      90 |
| 7        | [[07_QA_REVIEW]]       | Ôn hỏi đáp và phần còn yếu          |      90 |
| **Tổng** |                        |                                     | **600** |

Trong mỗi block, tổng các hàng phân bổ bằng đúng thời lượng block. Câu hỏi tự kiểm tra, đối chiếu đáp án và nghỉ ngắn đều nằm trong ngân sách đó. Tự trả lời trước khi xem đáp án. Tự kiểm tra ở block đọc là kiểm tra hiểu bài bằng ghi chú; việc dựng deck và luyện một bài nói hoàn chỉnh nằm ở block sau.

Các đầu ra là **mục tiêu dự kiến trong 600 phút**, không phải bảo đảm một người mới sẽ hiểu hết hoặc làm xong mọi chi tiết đúng thời lượng. Ưu tiên câu chuyện chính, cơ chế hai giai đoạn IK và bằng chứng đã chọn; ghi rõ phần chưa hiểu/chưa xong. Hết phút của một block không tự làm các ô hoàn thành trở thành đúng.

## Nguồn và thứ tự ưu tiên

1. **Nguồn gốc:** [GMR arXiv 2510.02252v1, PDF 9 trang](../tmp/2510.02252v1.pdf). Mọi số trang trong notes là thứ tự trang PDF, bắt đầu từ 1.
2. **Đối chiếu việc đọc:** [GMR_READING_CHECKLIST.md](../GMR_READING_CHECKLIST.md), bảy lượt đọc.
3. **Đối chiếu việc làm slide:** [PRESENTATION_SLIDE.md](../PRESENTATION_SLIDE.md), bản thảo 15 slide chính và phương án gộp thành 12 ở cuối file.
4. **Hỗ trợ:** [READING_GUIDE.md](../tmp/extracted/READING_GUIDE.md) và [bản dịch tiếng Việt không chính thức](../GMR_vi.md). Khi có khác biệt, đối chiếu PDF v1.

Không trộn bản v1 này với bản tác giả 8 trang. Các con số, hình và công thức trong notes không lấy từ bản conference khác. Các đáp án là diễn giải bằng tiếng Việt để học, không phải bản trích nguyên văn của tác giả.

**Lưu ý số slide:** bảng ở cuối `READING_GUIDE.md` dùng một khung slide cũ, chưa khớp hệ O/S dưới đây. Chỉ dùng tài liệu đó để hỗ trợ đọc nội dung; lấy số slide từ `PRESENTATION_SLIDE.md` và bảng mapping trong bộ note này.

## Đối chiếu với checklist và bản thảo

| Block | Checklist gốc | Slide bản thảo 15 slide | Slide rút gọn 12 slide |
| --- | --- | --- | --- |
| 1 | Lượt 1–2 | 1–4 | 1–4 |
| 2 | Lượt 3–4 | 5–7 | 5–6 |
| 3 | Lượt 5–7 | 8–15 | 7–12 |
| 4–5 | Dùng ghi chú từ lượt 1–7 | Dùng phương án gộp cuối bản thảo | Dựng và hoàn thiện 1–12 |
| 6–7 | Câu hỏi và phần kiểm tra cuối checklist | Phần kiểm tra trước khi trình bày | Luyện nói và hỏi đáp trên deck 12 slide |

Block đọc gộp các mục tiêu của checklist để vừa ngân sách 240 phút. Đây **không phải cam kết hoàn thành toàn bộ 42 câu hỏi và mọi đầu ra của checklist gốc với cùng độ sâu**. Mỗi note chọn các câu cốt lõi; phần còn vướng được ghi lại, không đánh dấu đã hiểu. Tài liệu gốc vẫn được giữ nguyên để tra chi tiết.

## Hai hệ số slide — tránh nhầm

Trong bộ note, **S** là slide của deck rút gọn 12 slide; **O** là số trong bản thảo gốc 15 slide.

| Slide S | Lấy từ O | Tiêu đề dự kiến | Nội dung chính |
| ---: | --- | --- | --- |
| S1 | O1 | Paper Overview | Tên paper, tác giả, phiên bản, người trình bày |
| S2 | O2 | The Embodiment Gap | Khác cơ thể và lỗi reference |
| S3 | O3 | Research Questions and Contributions | Q1–Q3, hai đóng góp |
| S4 | O4 | GMR and Policy Tracking | Retargeting tạo reference; RL học tracking |
| S5 | O5 + O6 | Matching, Alignment and Scaling | Một ví dụ xuyên suốt |
| S6 | O7 | Two-Stage Inverse Kinematics | Mục tiêu, hai giai đoạn, giới hạn khớp |
| S7 | O8 + O9 | Experimental Setup and Metrics | Dataset, robot, so sánh, metric |
| S8 | O10 | Success Rates and a Failure Case | Hai hàng Table I, điều kiện sim2sim |
| S9 | O11 | Tracking Accuracy | Mean global error Table II, điều kiện sim |
| S10 | O12 | Perceived Motion Faithfulness | User study, Figure 4 |
| S11 | O13 + O14 | Limitations and Project Relevance | Phạm vi bằng chứng và bài học cho teleoperation |
| S12 | O15 | Key Takeaways | Ba thông điệp kết thúc |

Phương án 12 slide là lựa chọn làm việc để tiết kiệm thời gian, chưa phải yêu cầu số slide hay thời lượng do thầy quy định. Chưa có thông tin về thời lượng bài nói; không tự coi 12 slide tương đương một số phút trình bày cố định.

## Quy tắc kiểm chứng xuyên suốt

- **GMR:** hình học và IK có giới hạn khớp; **BeyondMimic/RL:** huấn luyện và đánh giá tracking policy.
- Giữ riêng **reference** và chuyển động thực sự của policy; **success**, **tracking error** và **user preference** đo các khía cạnh khác nhau.
- S8 dùng **sim2sim**; S9 dùng **sim**. Giữ motion, metric, đơn vị và nguồn bên cạnh số liệu.
- Kể cả kết quả tốt và ngoại lệ của GMR. Không suy ra tối ưu toàn cục, bảo đảm ổn định động lực học hoặc tránh mọi va chạm từ giới hạn khớp.
- Phần TonyPi là **liên hệ nguyên lý/đề xuất của người trình bày**; paper v1 chưa chứng minh lợi ích RGB-D/depth hoặc kết quả trên TonyPi.

## Dùng trong Obsidian

Mở thư mục `REPORT_2026-10-30` làm vault, hoặc chép cả thư mục báo cáo vào vault đang dùng để giữ các liên kết tương đối tới PDF, checklist, bản thảo và hình. Nếu chỉ chép riêng thư mục notes, các liên kết `../...` tới nguồn sẽ cần được sửa hoặc chép kèm nguồn tương ứng. Liên kết wiki giữa các note hoạt động khi cả bảy note và index cùng có trong vault.

Các đáp án đặt trong callout thu gọn khi phù hợp để bạn tự trả lời trước. Thời gian đọc các đáp án vẫn tính vào phần tự kiểm tra của block, không phải thêm ngoài lịch.

## Ghi chỗ chưa hiểu

| Block | Câu hỏi cụ thể | Trang/mục cần tra | Trạng thái |
| --- | --- | --- | --- |
| | | | Chưa kiểm chứng |

## Audit cuối

Kết quả kiểm tra cuối được ghi tại [[08_AUDIT_ASTRA_XHIGH]]. Trạng thái audit chỉ được cập nhật sau khi audit thực sự hoàn tất; không phải bảo đảm rằng mọi ký hiệu toán mơ hồ trong nguồn đã được giải quyết.
