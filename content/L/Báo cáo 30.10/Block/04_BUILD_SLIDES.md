---
duration_minutes: 120
phase: slides
status: todo
paper_version: arxiv-2510.02252v1
---

# Block 4 — Dựng bản nháp đầy đủ 12 slide

[[00_START_HERE]] · Trước: [[03_READ_EVIDENCE]] · Sau: [[05_FINALIZE_SLIDES]]

**Thời lượng: 120 phút.** Bắt đầu sau ba block đọc. Việc chính là dựng deck từ ghi chú đã có, không mở một lượt nghiên cứu mới. Dùng [bản thảo](../PRESENTATION_SLIDE.md), đặc biệt mục **Phương án rút xuống 12 slide nếu cần**. **S** là số rút gọn; **O** là số gốc.

## Mục tiêu

Có đủ **12 slide dạng nháp dùng được**, chữ tiếng Anh và nguồn đúng. Phần diễn giải tiếng Việt không dán thành đoạn dài lên slide. Đây là mục tiêu hoàn thành trong block, không phải khẳng định deck hiện đã tồn tại.

## Làm gì trong 120 phút

| Phút | Việc làm | Đầu ra |
| ---: | --- | --- |
| 10 | Chọn một template đơn giản, thống nhất font, màu nhấn cho GMR và bố cục. | Một theme dùng suốt deck. |
| 10 | Tạo đủ 12 trang, đặt tiêu đề theo bảng dưới. Mở ghi chú ba block đọc cạnh bản thảo. | Khung S1–S12. |
| 20 | Dựng S1–S4: tên bài, vấn đề, câu hỏi/đóng góp, workflow. | Câu chuyện mở đầu. |
| 25 | Dựng S5–S6: matching/alignment/scaling và IK hai giai đoạn. | Sơ đồ phương pháp đọc được. |
| 10 | Nghỉ ngắn. | |
| 10 | Dựng S7: setup và metric tối thiểu để đọc kết quả. | Người nghe biết đang đo gì. |
| 20 | Dựng S8–S10: bảng success, biểu đồ tracking error, Figure 4. | Ba loại bằng chứng. |
| 10 | Dựng S11–S12: giới hạn/liên hệ và takeaways. | Có kết luận đầy đủ. |
| 5 | Lưu bản nháp, rà xem có slide trống, hình mất nhãn hay chỗ chưa có nguồn; ghi danh sách sửa cho block 5. | Deck đủ 12 slide và log cần sửa. |
| **120** | **Tổng** | |

## Làm từng slide

| Slide | Lấy từ bản thảo | Cần đặt lên slide | Hình/dữ liệu và điều phải giữ |
| --- | --- | --- | --- |
| S1 — Paper Overview | O1 | Tên bài, tác giả, arXiv v1, tên người trình bày/lab theo thông tin thật. | Nền đơn giản; chưa có tên/lab thì để ô chờ, không tự bịa. |
| S2 — The Embodiment Gap | O2 | Khác cơ thể, khác giới hạn, reference có artifacts. | Nếu dùng Figure 3(a)/(b), trang 7, giữ nhãn PHC/ProtoMotions và motion; không gắn lỗi đó cho GMR. |
| S3 — Research Questions and Contributions | O3 | Q1 performance; Q2 harmful artifacts; Q3 faithfulness; hai đóng góp. | Đóng góp phương pháp và nghiên cứu so sánh; kết quả sẽ trình bày sau. |
| S4 — GMR and Policy Tracking | O4 | Human motion → GMR → robot reference → RL tracking → simulation evaluation. | Đây là sơ đồ diễn giải của người trình bày từ III–IV. Figure 2 gốc mô tả năm bước GMR, không phải toàn bộ sơ đồ RL này. |
| S5 — Matching, Alignment and Scaling | O5 + O6 | Ghép bộ phận, căn chỉnh rest pose, local/root scaling. | Một ví dụ người giơ tay; minh họa tự soạn phải ghi là illustration. Có thể dùng crop Figure 2 và Eq. 2–3 khi đọc được. |
| S6 — Two-Stage Inverse Kinematics | O7 | Stage 1: hướng + vị trí tay/chân. Stage 2: hướng + vị trí toàn bộ key bodies. Joint limits. | Nguồn IV/Eq. 4–6, trang 5. Giới hạn khớp không tự bảo đảm cân bằng động lực học hoặc tránh tự va chạm. |
| S7 — Experimental Setup and Metrics | O8 + O9 | LAFAN1, 21 motions, G1; bốn phương pháp; cùng framework BeyondMimic; success/tracking/user preference. | Ghi ngắn sim/sim-dr/sim2sim; chi tiết rollout/đơn vị ở notes. Framework chung không có nghĩa dùng một policy có cùng weights. |
| S8 — Success Rates and a Failure Case | O10 | Hai hàng Run (stop & go) và Dance 5; bốn phương pháp. | **Table I, trang 6, cột sim2sim, 100 trials/policy.** Dùng bảng dữ liệu bên dưới. |
| S9 — Tracking Accuracy | O11 | Mean global body-position error; mm; lower is better. | **Table II, trang 6, điều kiện sim**, hàng Mean của E_g-mpbpe. Trục cột bắt đầu từ 0. |
| S10 — Perceived Motion Faithfulness | O12 | User study, 20 participants, faithfulness to source motion. | Crop Figure 4, trang 7; giữ đủ ba nhóm, legend và tỷ lệ. Đây là tỷ lệ câu trả lời. |
| S11 — Limitations and Project Relevance | O13 + O14 | Một nguồn dữ liệu, một robot benchmark; bằng chứng mô phỏng/sim2sim; nguyên lý có thể học cho TonyPi. | Tách **kết quả paper** khỏi **potential lessons for our project**. Không dùng mục tiêu nhóm như kết quả đã chạy được. |
| S12 — Key Takeaways | O15 | Reference quality affects policy tracking; GMR combines scaling and constrained IK; better retargeting still needs validation. | Ba câu kết của bản thảo; giữ phạm vi kết luận của v1. |

## Dữ liệu cố định để dựng S8–S9

### S8 — Table I, sim2sim, success (%)

| Motion | PHC | GMR | ProtoMotions | Unitree |
| --- | ---: | ---: | ---: | ---: |
| Run (stop & go) | 74 | 100 | 26 | 100 |
| Dance 5 | 100 | 51 | 100 | 100 |

Caption: `Araújo et al., arXiv:2510.02252v1, Table I, p.6 · sim2sim · 100 trials/policy`.

### S9 — Table II, sim, Mean E_g-mpbpe (mm)

| Method | Error (mm) |
| --- | ---: |
| PHC | 247.8 |
| GMR | 104.1 |
| ProtoMotions | 139.7 |
| Unitree | 77.2 |

Caption: `Araújo et al., arXiv:2510.02252v1, Table II, p.6 · sim · lower is better`.

Hai bảng này được đối chiếu tại [[03_READ_EVIDENCE]]. Khi dựng biểu đồ, giữ đúng metric và điều kiện; không gộp số của S8 và S9 thành một phép đo.

## Nguồn hình đã có

- [Trang 4: Figure 1–2](../tmp/extracted/visuals/page-004.png).
- [Trang 5: Eq. 2–6](../tmp/extracted/visuals/page-005.png).
- [Trang 6: Table I–II](../tmp/extracted/visuals/page-006.png).
- [Trang 7: Figure 3–4, Table III](../tmp/extracted/visuals/page-007.png).

Đây là ảnh **toàn trang**, cần crop đúng vùng. Khi crop giữ legend, nhãn phương pháp, metric/đơn vị và điều kiện cần để hiểu hình. Không dùng ảnh AI thay bằng chứng thực nghiệm.

## Điểm dừng

- [ ] Đủ 12 slide theo đúng mapping S/O, có phần mở đầu và kết luận.
- [ ] Mỗi slide có một nhiệm vụ, tối đa khoảng ba ý ngắn; hình/bảng đủ lớn.
- [ ] Dữ liệu S8/S9 đúng bảng trên; S10 giữ đủ nhóm Unitree.
- [ ] Có nguồn và phân biệt sơ đồ tự diễn giải với figure gốc.
- [ ] Deck đã lưu; chỗ còn cần sửa được ghi cho block 5.

Phụ lục O16–O20 trong bản thảo là tùy chọn, không phải đầu ra bắt buộc của 120 phút này. Giữ PDF nguồn để tra khi cần.
