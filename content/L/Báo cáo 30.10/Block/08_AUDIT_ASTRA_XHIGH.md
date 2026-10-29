---
type: audit
status: completed
audit_result: pass_with_clarifications
audit_date: 2026-10-29
configured_model: gpt-6-astra
configured_reasoning_effort: xhigh
paper_version: arxiv-2510.02252v1
---

# Audit cuối bộ note GMR

[[00_START_HERE|Về mục lục]]

**Đã thực hiện audit cuối và kiểm tra lại sau sửa.** Bộ note đạt các yêu cầu nội dung và cấu trúc đã kiểm tra; không phát hiện lỗi nội dung nghiêm trọng còn tồn tại trong phạm vi này. Các điểm làm rõ dưới đây đã được sửa. Kết quả này không phải bảo đảm tuyệt đối không còn sai sót, cũng không xác nhận người học đã đọc xong hoặc có deck hoàn chỉnh.

Agent audit riêng được khởi chạy với **model `gpt-6-astra`, reasoning effort `xhigh`**. Cấu hình này được agent điều phối xác nhận từ lời gọi công cụ khởi chạy, không suy ra từ tên file. Audit được thực hiện sau khi các note 00–07 đã được soạn xong.

## Phạm vi và nguồn đã kiểm tra

- Đọc đầy đủ [[00_START_HERE]], [[01_READ_OVERVIEW]], [[02_READ_METHOD]], [[03_READ_EVIDENCE]], [[04_BUILD_SLIDES]], [[05_FINALIZE_SLIDES]], [[06_REHEARSE]] và [[07_QA_REVIEW]].
- Bắt đầu từ [INDEX của cache](../../PAPERS/extracted/INDEX.md), [NOTES của cache](../../PAPERS/extracted/NOTES.md) và [AGENTS.md](../../AGENTS.md).
- Đối chiếu [memory báo cáo](../memory_presentation.md), toàn bộ [checklist đọc](../GMR_READING_CHECKLIST.md), toàn bộ [bản thảo slide](../PRESENTATION_SLIDE.md), gồm phương án gộp 12 slide, và [hướng dẫn đọc](../tmp/extracted/READING_GUIDE.md).
- Nguồn khoa học: [PDF GMR arXiv v1, 9 trang](../tmp/2510.02252v1.pdf), [manifest](../tmp/extracted/manifest.json) và các trang TXT liên quan trong cache báo cáo. Đã tính lại SHA-256 của PDF và khớp manifest: `cc910a8606c2de1d87c5f34a9e1753165f3cdbefe2b1d61f1bf608dbd419f0a5`.
- Đọc các đoạn nội dung cần đối chiếu ở trang 1–3 và phần kết luận trang 8. **Đã xem trực tiếp đầy đủ ảnh trang 4–7**, không chỉ dựa vào TXT để đọc hình, bảng và công thức.

| Trang PDF | Ảnh đã xem | Nội dung đối chiếu |
| ---: | --- | --- |
| 4 | [page-004.png](../tmp/extracted/visuals/page-004.png) | Figure 1–2; III-C–E; protocol, metric và cách hỏi user study; đầu Step 1. |
| 5 | [page-005.png](../tmp/extracted/visuals/page-005.png) | Step 1–5; Eq. 2–6; ký hiệu scaling; khởi tạo; differential IK; xử lý cả sequence. |
| 6 | [page-006.png](../tmp/extracted/visuals/page-006.png) | Caption và dữ liệu chọn từ Table I–II; V-A–B; ngoại lệ Dance 5. |
| 7 | [page-007.png](../tmp/extracted/visuals/page-007.png) | Figure 3–4; Table III; V-C–D; kết luận và giới hạn. |

Không dùng số liệu hoặc công thức từ bản tác giả 8 trang để bổ sung cho v1.

## Kết quả kiểm tra kế hoạch

| Block | Phút trong frontmatter | Tổng bảng phân bổ | Loại việc |
| --- | ---: | ---: | --- |
| 01 | 60 | 60 | Đọc |
| 02 | 120 | 120 | Đọc |
| 03 | 60 | 60 | Đọc |
| 04 | 120 | 120 | Làm slide |
| 05 | 60 | 60 | Làm slide |
| 06 | 90 | 90 | Luyện trình bày |
| 07 | 90 | 90 | Ôn hỏi đáp |
| **Tổng** | **600** | **600** | **Đọc 240 → slide 180 → ôn tập 180** |

- Thứ tự bảy block khớp chuẩn thời lượng được giao cho audit. Câu hỏi, đối chiếu đáp án và nghỉ đã được tính trong từng block.
- Mỗi block có hành động cụ thể và đầu ra/điểm dừng. Các bước tra lại nguồn trong giai đoạn sau phục vụ kiểm tra hoặc ôn nội dung đã đọc, không mở thêm một lượt nghiên cứu hay thêm slide trong block ôn tập.
- Không có giờ bắt đầu/kết thúc tuyệt đối trong bộ note. Thời lượng luyện nói được ghi bằng phút và không bị coi là thời lượng thầy giao.
- Cả bảy block vẫn có `status: todo`, không có ô hoàn thành được tích sẵn.
- Ba note đọc kết thúc theo thứ tự **câu hỏi ôn tập → đáp án có nguồn → kiến thức cần nhớ**.
- Deck 12 slide là phương án làm việc; thời lượng bài nói, số slide bắt buộc và template của thầy vẫn chưa được xác nhận. Không có yêu cầu code/demo được thêm vào.
- Mapping đúng: O1–O4 → S1–S4; O5+O6 → S5; O7 → S6; O8+O9 → S7; O10–O12 → S8–S10; O13+O14 → S11; O15 → S12.

## Các điểm khoa học quan trọng đã đối chiếu

| Nhóm | Kết quả kiểm tra |
| --- | --- |
| Vai trò GMR/RL | GMR tạo robot reference bằng hình học/IK; BeyondMimic huấn luyện tracking policy. Reference, action và chuyển động policy tạo ra được phân biệt. |
| Scaling, Eq. 2–3 | Giữ đúng `h/h_ref` của v1; `h` là chiều cao skeleton người nguồn, `h_ref` là chiều cao tham chiếu khi thiết lập scale factors. Phân biệt local/body scaling với uniform root translation scaling. |
| Hai giai đoạn IK | Stage 1 xét hướng key bodies và vị trí tay/chân. Stage 2 xét hướng và vị trí mọi key body, đổi trọng số và lấy nghiệm stage 1 làm khởi tạo. `q` gồm cả root pose và joint values. |
| Solver và sequence | `Delta t` không nhất thiết bằng thời gian giữa hai frame nguồn. Warm start dùng frame trước; sửa độ cao được mô tả sau khi retarget cả motion. Joint limits không tự bảo đảm cân bằng, tránh tự va chạm hoặc tối ưu toàn cục. |
| Benchmark | 21 sequences LAFAN1, Unitree G1. Cùng framework BeyondMimic nhưng policy riêng cho từng retargeted clip. Có lưu ý chuyển BVH sang SMPL/SMPL-X và điều chỉnh hậu xử lý PHC; Unitree là dữ liệu từ thuật toán đóng. |
| Protocol và metric | `sim`: 100 rollout/policy; `sim-dr`: 4096; `sim2sim` MuJoCo/ROS: 100. Cả ba là mô phỏng. Success theo ngưỡng sai lệch độ cao/hướng anchor body; errors tính trên frame policy còn hoạt động. Global/root-relative position errors dùng mm; `E_mpjpe` trong v1 dùng `10^-3 rad`. |
| Table I | Cột sim2sim, thứ tự PHC/GMR/ProtoMotions/Unitree: Run (stop & go) = 74/100/26/100; Dance 5 = 100/51/100/100. |
| Table II | Mean `E_g-mpbpe`, điều kiện sim, mm, cùng thứ tự: 247.8/104.1/139.7/77.2. Đây là policy bám reference robot, không phải sai số trực tiếp người–robot. |
| Figure 3 | V-B nhấn mạnh waist roll của GMR Dance 5; Figure 3(c) thể hiện roll và pitch. Notes giữ đúng khác biệt này và không gọi phân tích trường hợp là ablation cô lập nguyên nhân. |
| Figure 4 | N=20; tỷ lệ câu trả lời GMR/không ưu tiên/phương pháp kia: Unitree 25/37/38; PHC 74/8/18; ProtoMotions 63/13/23. Giữ nguyên tổng 99 ở nhóm ProtoMotions như hình in. Không kết luận GMR được ưu tiên hơn Unitree. |
| Table III | Cùng policy, đổi start frame khi đánh giá; GMR Walk 2: 64% ở frame 0 → 100% ở frame 7 trong sim2sim. Không mô tả là huấn luyện lại. |
| Phạm vi kết luận | Có ngoại lệ của GMR; benchmark một nguồn/một robot và mô phỏng. Bài học cho TonyPi/depth được nhận diện là liên hệ/đề xuất cần kiểm chứng riêng. |

## Phát hiện và sửa trong lượt audit này

| Mức độ | Điểm cần làm rõ | Sửa đã thực hiện |
| --- | --- | --- |
| Nhẹ — điều hướng | Bảng số slide trong `READING_GUIDE.md` thuộc khung cũ, có thể gây nhầm dù mapping O/S của notes đã đúng. | Thêm cảnh báo trong [[00_START_HERE]]; chỉ dùng bản thảo và bảng O/S hiện tại để đổi số. Giữ nguyên tài liệu nguồn. |
| Nhẹ — kế hoạch | Người mới có thể hiểu các mục tiêu theo phút là lời bảo đảm đọc hiểu/làm xong mọi chi tiết. | [[00_START_HERE]] nêu rõ 600 phút là ngân sách dự kiến; hết thời lượng không đồng nghĩa đã hiểu hoặc hoàn thành. |
| Nhẹ — cấu trúc | Ba note đọc đã có đủ ba phần ôn tập nhưng “kiến thức cần nhớ” chưa nằm sau đáp án. | Sắp lại [[01_READ_OVERVIEW]], [[02_READ_METHOD]], [[03_READ_EVIDENCE]]; giữ nội dung, đưa checklist/log trước bộ phần kết thúc. |
| Nhẹ — trạng thái luyện | Hướng dẫn chưa nói rõ cách ghi nhận nếu hết 25 phút mà chưa nói hết bài. | [[06_REHEARSE]] yêu cầu ghi slide dừng, không đánh dấu luyện toàn bài; vẫn giữ tổng block 90 phút. |

Không cần sửa số liệu hoặc các mô tả phương pháp trọng tâm đã đối chiếu. Các file sửa trong lượt audit: `00_START_HERE.md`, `01_READ_OVERVIEW.md`, `02_READ_METHOD.md`, `03_READ_EVIDENCE.md`, `06_REHEARSE.md`; file audit này được tạo mới. Không sửa PDF, cache trích xuất, checklist hoặc bản thảo gốc.

## Kiểm tra lại và giới hạn của audit

- Đã kiểm tra lại tổng phút/frontmatter và bảng phân bổ sau khi sửa; thứ tự các phần cuối ba note đọc đúng yêu cầu.
- Đã kiểm tra đích của các liên kết Markdown tương đối và wiki trong toàn bộ thư mục notes, gồm file audit; các đích đều tồn tại trên đĩa. Đã rà lại giờ tuyệt đối và trạng thái hoàn thành.
- Phần ký hiệu orientation error, cách gọi `e(q)` quanh Eq. 5 và ký hiệu trong Eq. 6 của v1 vẫn cần thận trọng nếu suy diễn toán sâu. Notes đã nhận diện giới hạn này, không tự sửa công thức của tác giả hoặc khẳng định một định nghĩa chưa được xác minh.
- Audit nội dung khoa học dựa trên PDF v1 và nguồn địa phương nêu trên; không đối chiếu mã triển khai hoặc tái chạy thí nghiệm.
- Đây là audit bộ Markdown, chưa phải kiểm tra render trong ứng dụng Obsidian hay kiểm tra chất lượng một deck PPTX/PDF đã dựng. Khả năng hoàn thành kế hoạch và mức hiểu thực tế của người học chưa được kiểm chứng.

**Trạng thái cuối: đạt trong phạm vi đã kiểm tra, sau các chỉnh sửa làm rõ; các giới hạn còn lại đã được ghi rõ.**
