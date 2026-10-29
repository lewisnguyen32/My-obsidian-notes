---
duration_minutes: 90
phase: rehearsal
status: todo
paper_version: arxiv-2510.02252v1
tags:
  - GMR
  - rehearsal
  - questions-and-answers
---

# Block 07 - Ôn hỏi đáp và luyện phần còn yếu - 90 phút

[[00_START_HERE|Về mục lục]] · Trước: [[06_REHEARSE]]

## Mục tiêu và điều kiện bắt đầu

Đây là block **ôn tập cuối**, dùng ghi chú đã đọc và deck đã hoàn thiện. Luyện trả lời bằng tiếng Việt, chỉ đúng bằng chứng và nhận biết giới hạn hiểu biết của mình. Giữ đúng thứ tự đọc → làm slide → ôn tập; không mở một hướng nghiên cứu mới hoặc dựng thêm slide trong block này.

- [ ] Tôi đã làm xong các block đọc 01-03 và có ghi chỗ còn vướng.
- [ ] Tôi đã làm xong các block slide 04-05 và có file trình chiếu/PDF.
- [ ] Tôi đã luyện toàn bài ở [[06_REHEARSE]] và có danh sách đoạn còn yếu.

**90 phút** là thời lượng của block hỏi đáp, không phải thời lượng bài báo cáo. Hiện chưa có thông tin xác nhận giới hạn thời lượng bài nói do thầy yêu cầu; không tự đặt một giới hạn rồi coi đó là yêu cầu thật.

## Nguồn dùng để ôn

- [[01_READ_OVERVIEW]]: vấn đề, đóng góp, reference và vai trò RL.
- [[02_READ_METHOD]]: matching/alignment/scaling, hai giai đoạn IK, sequence và điểm ký hiệu toán cần thận trọng.
- [[03_READ_EVIDENCE]]: setup, metric, kết quả, ngoại lệ, giới hạn.
- [Checklist đọc GMR](../GMR_READING_CHECKLIST.md): các câu hỏi của lượt 1-7; đặc biệt phần tự giải thích và câu hỏi cuối lượt 7.
- [Bản thảo slide](../PRESENTATION_SLIDE.md): các mục “Phải giải thích được”, phụ lục 16-19 và bảng gộp 12 slide. Số **O** trong ghi chú là slide gốc; số **S** là slide rút gọn.
- Nguồn gốc khi cần kiểm tra một điểm cụ thể: [PDF GMR v1, 9 trang](../tmp/2510.02252v1.pdf), Section III-IV, trang 3-5; kết quả/giới hạn, trang 5-8.

## Làm gì trong 90 phút

| Phút | Việc làm | Cách thực hiện / đầu ra |
| ---: | --- | --- |
| 5 | Chọn điểm yếu cần luyện | Lấy tối đa ba điểm từ block 06; phân loại: thiếu kiến thức, nhớ sai số liệu hay diễn đạt chưa rõ. Dùng ngân hàng câu hỏi bên dưới để chọn đúng mục. |
| 20 | Ôn miệng phần phương pháp | Trả lời câu 1-3 trước khi mở đáp án. Mỗi câu bắt đầu bằng ý chính rồi giải thích bằng một ví dụ hoặc sơ đồ hiện có. Đối chiếu note 01-02; ghi từ khóa còn thiếu. |
| 20 | Ôn miệng phần bằng chứng và phạm vi | Trả lời câu 4-8. Với kết quả phải nói kèm metric, điều kiện, đơn vị và ngoại lệ; với liên hệ nhóm phải phân biệt kết quả paper với đề xuất của mình. Đối chiếu note 03. |
| 5 | Nghỉ | Nghỉ mắt và giọng nói. |
| 20 | Hỏi đáp giả lập | Chọn năm câu khó nhất, mỗi câu một lượt tối đa 4 phút gồm trả lời, một câu hỏi tiếp và tự kiểm tra. Che đáp án, dùng slide để chỉ bằng chứng. Ghi câu nào chưa trả lời đủ ý. |
| 15 | Luyện lại đúng đoạn còn yếu | Chọn tối đa ba đoạn đã vấp. Với mỗi đoạn, nói lại ý chính và bằng chứng bằng lời của mình. Tra đúng ghi chú đã có nếu quên, rồi đóng lại để trả lời lần nữa. |
| 5 | Chốt | Viết ba ý nhớ cuối và đánh dấu câu vẫn chưa chắc. Xác nhận có thể tìm đúng slide/nguồn khi được hỏi. |
| **90** | **Tổng, gồm nghỉ và đối chiếu đáp án.** | |

> [!tip] Cấu trúc trả lời ngắn
> **Trả lời trực tiếp → giải thích cơ chế hoặc bằng chứng → nêu phạm vi kết luận.** Với điểm toán chưa chắc, nói rõ mình hiểu đến đâu; không thêm một định nghĩa tự đoán để làm câu trả lời có vẻ đầy đủ.

## Ngân hàng câu hỏi để luyện

1. **GMR có phải phương pháp retargeting bằng RL không? Reference khác action như thế nào?**
2. **Vì sao cần scaling và hai giai đoạn IK? Giai đoạn đầu có vị trí tay/chân không?**
3. **Eq. 5 làm gì? Nếu bị hỏi sâu một ký hiệu toán còn chưa chắc, nên trả lời đến đâu?**
4. **Success rate cao có đồng nghĩa bám chính xác không? Tracking errors được tính trên những frame nào?**
5. **Sim2sim có phải thử nghiệm robot thật không? Ba điều kiện đánh giá khác nhau thế nào?**
6. **GMR có luôn tốt nhất không? Hãy dùng Dance 5 và mean global tracking error để trả lời.**
7. **Giữ cùng BeyondMimic có nghĩa là dùng cùng một policy và cùng weights không? So sánh đã cô lập hoàn hảo mọi yếu tố chưa?**
8. **Nhóm teleoperation có thể học gì cho TonyPi, và paper chưa chứng minh điều gì cho nhóm?**

## Đáp án và giới hạn cần giữ

> [!answer]- 1. GMR, RL, reference và action
> **Không.** GMR dùng matching, alignment, scaling và IK có giới hạn để tạo robot reference motion. BeyondMimic dùng reference để huấn luyện tracking policy bằng RL; khi chạy, policy chọn hành động điều khiển để bám reference. Reference là chuỗi mục tiêu root pose/joint values, chưa đồng nghĩa action cuối cùng hoặc chuyển động robot đã thực hiện thành công. **Nguồn:** Figure 2/Section IV, trang 4-5; III-C, trang 4. **Ôn lại:** [[01_READ_OVERVIEW]], câu 6-7; [[02_READ_METHOD]], câu 10.

> [!answer]- 2. Scaling và hai giai đoạn IK
> Người và robot khác tỷ lệ cơ thể nên mục tiêu hình học phải được điều chỉnh. GMR dùng scale riêng theo key body và root translation được scale đồng đều. IK tìm root pose và joint values để giảm sai số trong giới hạn đã đặt. **Giai đoạn 1:** hướng các key bodies và vị trí end-effectors, tức tay/chân. **Giai đoạn 2:** hướng và vị trí mọi key body, dùng trọng số khác và nghiệm giai đoạn 1 làm khởi tạo. Không nói giai đoạn 1 chỉ có rotation; hai giai đoạn cũng không bảo đảm tối ưu toàn cục, cân bằng hay tránh mọi tự va chạm. **Nguồn:** Step 3-5, Eq. 2-6, trang 5. **Ôn lại:** [[02_READ_METHOD]], câu 3-6 và 9.

> [!answer]- 3. Eq. 5 và câu trả lời trung thực khi chưa chắc ký hiệu
> Ở mức cơ chế, differential IK giải vận tốc tổng quát `q_dot` để khi tích phân sẽ làm giảm cost; ràng buộc giữ cấu hình sau cập nhật trong giới hạn. `J` biểu diễn quan hệ biến thiên ở mức tuyến tính hóa, `W` biểu diễn trọng số, và `Delta t` là tham số solver, không nhất thiết là khoảng thời gian giữa hai frame nguồn. Bản v1 có cách ghi orientation error và `e(q)` cần thận trọng; không tự suy ra một định nghĩa toán chắc chắn từ cách ghi đó. Có thể nói: **“Em hiểu vai trò của bước này là giải vận tốc để giảm sai số và giữ giới hạn. Với định nghĩa chính xác của ký hiệu này, em chưa đủ chắc để suy diễn thêm.”** Đây là cách diễn đạt đề xuất khi ôn, không phải câu trích của tác giả. **Nguồn:** Step 4/Eq. 5, trang 5; lưu ý phụ lục 16 trong bản thảo. **Ôn lại:** [[02_READ_METHOD]], câu 7 và phần “Điểm chưa nên tự suy diễn”.

> [!answer]- 4. Success và tracking accuracy
> **Không đồng nghĩa.** Success đo tỷ lệ rollout đi hết reference mà độ cao hoặc hướng anchor body không vượt ngưỡng chấm dứt; một rollout hoàn tất vẫn có thể bám lệch. Tracking errors bổ sung mức sai lệch và được tính trên các frame policy còn hoạt động. Vì vậy phải đọc success và errors cùng nhau, không chỉ nhìn một mean error. Global/root-relative body-position errors dùng **mm**; joint-rotation angular error trong v1 dùng **10^-3 rad**. **Nguồn:** III-D, trang 4; Table II, trang 6. **Ôn lại:** [[03_READ_EVIDENCE]], câu 3 và 5.

> [!answer]- 5. Sim, sim-dr và sim2sim
> **Cả ba đều là mô phỏng trong nghiên cứu v1 này.** `sim`: IsaacSim, tắt domain randomization, 100 rollout/policy. `sim-dr`: IsaacSim, bật domain randomization, 4096 rollout/policy. `sim2sim`: MuJoCo/ROS, 100 rollout/policy, dùng thiết lập gần với đường triển khai để đánh giá an toàn. Việc sử dụng ROS hoặc mô tả gần điều kiện triển khai không biến nó thành bằng chứng thử nghiệm robot thật. **Nguồn:** III-C, trang 4; caption Table I, trang 6. **Ôn lại:** [[03_READ_EVIDENCE]], câu 2.

> [!answer]- 6. Kết quả tốt, ngoại lệ và phạm vi kết luận
> GMR **không luôn tốt nhất**. Ở Table I, cột **sim2sim**: Run (stop & go) đạt **100%**, bằng Unitree và cao hơn PHC **74%**, ProtoMotions **26%**; Dance 5 chỉ **51%**, trong khi ba nhánh còn lại **100%**. Tác giả liên hệ Dance 5 với nhảy đột ngột giá trị khớp eo; đây là phân tích artifact, không phải ablation cô lập mọi nguyên nhân. Ở Table II, **Mean E_g-mpbpe trong sim**, GMR **104.1 mm**, thấp hơn PHC **247.8 mm** và ProtoMotions **139.7 mm**, nhưng cao hơn Unitree **77.2 mm**. Giữ riêng điều kiện sim và sim2sim khi trả lời. **Nguồn:** Table I-II và V-B, trang 6; Figure 3(c), trang 7. **Ôn lại:** [[03_READ_EVIDENCE]], câu 4-5.

> [!answer]- 7. Cùng framework khác cùng policy weights
> Tác giả dùng cùng framework BeyondMimic để huấn luyện **policy riêng cho từng retargeted motion**. Điều được giữ chung là framework/thiết kế đánh giá được mô tả, không phải một bộ weights cho mọi nhánh. Điều này giúp nghiên cứu tác động của retargeting, nhưng không phải phép cô lập hoàn hảo mọi khác biệt: PHC/ProtoMotions cần chuyển dữ liệu BVH sang SMPL/SMPL-X, PHC có điều chỉnh hậu xử lý như III-B mô tả, còn thuật toán retarget Unitree là đóng. Không suy ra riêng một thành phần GMR gây ra toàn bộ cải thiện chỉ từ phép so sánh này. **Nguồn:** III-A-C, trang 3-4. **Ôn lại:** [[03_READ_EVIDENCE]], câu 1.

> [!answer]- 8. Liên hệ với TonyPi teleoperation
> **Phân tích/đề xuất của người trình bày:** nhóm có thể học cách thiết lập mapping, xử lý tỷ lệ và giới hạn khớp, kiểm tra artifacts của reference, đồng thời tách đánh giá reference khỏi controller. Việc áp dụng cần mô hình phần cứng, mapping, dữ liệu và kiểm chứng riêng. **Kết quả paper:** benchmark dùng LAFAN1/G1 và đánh giá controller trong mô phỏng/sim2sim; chưa chứng minh độ lợi depth, pipeline RGB-D tới TonyPi hoặc policy triển khai được trực tiếp trên TonyPi. Một thí nghiệm nhóm có thể đề xuất là so sánh cách scaling trong cùng pipeline, nhưng phải gọi rõ đó là đề xuất kiểm chứng tiếp. **Nguồn:** III-B-C, trang 3-4; Section IV, trang 4-5; VI, trang 7-8. **Đối chiếu:** slide gốc O14 / slide rút gọn S11 trong bản thảo; [[03_READ_EVIDENCE]], câu 8.

## Phiếu tự đánh giá hỏi đáp

| Câu | Đã trả lời trực tiếp? | Có cơ chế/bằng chứng đúng? | Có nêu phạm vi/điểm chưa chắc? | Cần luyện lại điều gì? |
| --- | --- | --- | --- | --- |
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |
| 6 | | | | |
| 7 | | | | |
| 8 | | | | |

## Kiến thức cần giữ trước khi kết thúc

- **Reference quality → tracking performance** là câu chuyện nghiên cứu; reference và action là hai vai trò khác nhau.
- **Stage 1 đã có vị trí tay/chân**; stage 2 mở rộng vị trí sang mọi key body và đổi trọng số.
- **Success, tracking error, user preference** là ba loại bằng chứng; metric/đơn vị/điều kiện phải đi cùng số liệu.
- **GMR có ngoại lệ; sim2sim vẫn là mô phỏng; liên hệ TonyPi là đề xuất cần kiểm chứng.**
- Một câu trả lời đúng phạm vi, biết chỉ nguồn và thừa nhận chỗ chưa chắc có giá trị hơn một câu trả lời đầy đủ nhưng suy đoán.

## Hoàn thành block khi

- [ ] Tôi trả lời được các câu chính bằng lời của mình, thay vì đọc nguyên đáp án.
- [ ] Tôi biết đúng slide/nguồn để chỉ ra khi bị hỏi về một cơ chế hoặc con số.
- [ ] Tôi đã luyện lại tối đa ba đoạn yếu nhất từ block 06.
- [ ] Tôi có ba ý nhớ cuối và ghi trung thực điểm còn chưa chắc.

**Ba ý nhớ cuối:**

1. …
2. …
3. …

**Điểm còn chưa chắc và cách giới hạn câu trả lời:** …
