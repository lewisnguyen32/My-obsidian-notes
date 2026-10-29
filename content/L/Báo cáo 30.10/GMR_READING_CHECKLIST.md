# Checklist đọc GMR để chuẩn bị báo cáo paper

Mục tiêu: hiểu phương pháp và bằng chứng của **Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking**, sau đó diễn đạt bằng lời của mình. Slide dùng tiếng Anh; phần ghi chú học và thuyết trình dùng tiếng Việt. Buổi báo cáo này không yêu cầu code hoặc demo.

## Phiên bản và nguồn dùng xuyên suốt

- **Bản đang đọc: arXiv 2510.02252v1, nộp ngày 02/10/2025, PDF 9 trang.** Mọi số trang dưới đây đếm theo PDF, bắt đầu từ 1.
- [Mở PDF v1 đã tải](tmp/2510.02252v1.pdf).
- [Mở trang 5 dạng ảnh để kiểm tra công thức](tmp/extracted/visuals/page-005.png).
- [Bản trích xuất TXT có mốc trang](tmp/extracted/2510.02252v1.txt) và [hướng dẫn đọc tổng quan](tmp/extracted/READING_GUIDE.md).
- Bản PDF trên trang tác giả có 8 trang và khác v1. Không trộn số trang, hình, phương trình, kết quả hoặc các nhận định như **70 Hz** và **ablation 3%** từ bản khác vào báo cáo v1 này.

Mỗi lượt dưới đây phục vụ một **phần nội dung**, không quy định số slide hoặc thời hạn hoàn thành. Chỉ mở tài liệu nền khi một khái niệm cụ thể đang cản việc giải thích GMR. Với công thức, hình và bảng, đối chiếu PDF hoặc ảnh trang tương ứng thay vì chỉ dựa vào TXT.

## Đối chiếu với bản thảo slide

[PRESENTATION_SLIDE.md](PRESENTATION_SLIDE.md) chia bài nói thành năm phần với **15 slide chính được đề xuất**, có chữ tiếng Anh, gợi ý visual và ghi chú nói tiếng Việt. Các số dưới đây để nối việc đọc với việc soạn, không phải yêu cầu số slide cố định của thầy.

| Lượt đọc | Slide bản thảo | Phần cần soạn sau khi hiểu |
| --- | --- | --- |
| 1 | 1–3 | Giới thiệu, vấn đề và câu hỏi nghiên cứu |
| 2 | 4 | GMR tạo reference và RL tracking |
| 3 | 5–6 | Matching, rest-pose alignment và scaling |
| 4 | 7 | IK hai giai đoạn và xử lý sequence |
| 5 | 8–9 | Thiết kế thí nghiệm và metric |
| 6 | 10–12 | Success/failure, tracking error và user study |
| 7 | 13–15 | Giới hạn, liên hệ TonyPi và kết luận |

## Bản đồ để tránh nhầm vai trò

| Công việc | Đầu vào và đầu ra | Vai trò trong paper |
| --- | --- | --- |
| **GMR retargeting** | Chuyển động skeleton người và mô tả cấu trúc robot; tạo chuỗi root pose và giá trị khớp robot làm reference motion | Matching, alignment, scaling và inverse kinematics có giới hạn khớp; đây là lõi phương pháp GMR |
| **RL motion tracking** | Dùng reference motion để huấn luyện policy; policy nhận quan sát và mục tiêu chuyển động để chọn hành động điều khiển | BeyondMimic là pipeline huấn luyện/đánh giá dùng để nghiên cứu tác động của chất lượng retargeting |

Reference là chuyển động đích để controller bám theo, chưa đồng nghĩa robot đã thực hiện được chuyển động đó. GMR không phải phương pháp retargeting học bằng RL. Kết quả controller trong v1 được trình bày dưới các điều kiện mô phỏng và sim-to-sim.

## Lượt 1 — Hiểu vấn đề và câu hỏi của paper

**Phần trình bày phục vụ:** *Paper Overview*, *Problem and Motivation*, *Main Idea and Contributions*.

**Đọc đúng chỗ**

- **Abstract** và **I. Introduction**, trang **1–2**.
- Lướt **VI. Conclusion**, trang **7–8**, để biết kết luận và phạm vi; chưa cần ghi nhớ số liệu.

**Câu hỏi phải tự trả lời**

1. Paper nghiên cứu điều gì, nếu phải nói trong một câu cho người chưa biết GMR?
2. Người và humanoid khác nhau ở những đặc điểm nào khiến việc chép chuyển động trực tiếp gặp khó khăn?
3. Retargeting tạo ra reference motion để làm gì? Reference có thể chứa lỗi nào?
4. Vì sao bắt một policy bám theo reference có lỗi có thể khiến việc học hoặc vận hành khó hơn?
5. Tác giả muốn kiểm tra ảnh hưởng của retargeting và đề xuất GMR như thế nào?
6. Những phát biểu nào trong Abstract là kết luận tác giả tuyên bố, còn cần kiểm tra bằng thí nghiệm?

**Điều phải giải thích bằng lời**

- Giải thích *embodiment gap* bằng ví dụ người có tay dài hơn hoặc giới hạn khớp khác robot.
- Giải thích một lỗi dễ hình dung: reference yêu cầu bàn chân nằm dưới mặt đất dù robot phải giữ tiếp xúc vật lý hợp lệ.
- Phân biệt chuyển động đích với chuyển động robot thực sự tạo ra khi controller bám theo.
- Kể câu chuyện nghiên cứu trong khoảng 1–2 phút: vấn đề, giả thuyết, cách kiểm tra và đóng góp.

**Đầu ra ghi chú:** một đoạn **5–7 câu tiếng Việt** về bài toán; **một câu tiếng Anh** mô tả paper; **2–3 ý đóng góp** có ghi rõ đây là tuyên bố của tác giả.

**Hoàn thành khi**

- [ ] Đã trả lời cả 6 câu hỏi bằng lời của mình.
- [ ] Có thể kể câu chuyện nghiên cứu mà không đọc Abstract.
- [ ] Đã ghi một chỗ chưa hiểu để quay lại ở lượt sau, thay vì đoán nghĩa.

## Lượt 2 — Nhìn toàn hệ thống và tách GMR khỏi RL

**Phần trình bày phục vụ:** *System Overview* và phần nối từ ý tưởng sang phương pháp.

**Đọc đúng chỗ**

- Ba câu hỏi **Q1–Q3** đầu **III. Evaluation Method**, trang **3**.
- **Figure 2** và phần mở đầu **IV. General Motion Retargeting**, trang **4**; lướt toàn Section IV tới hết trang **5**.
- [Ảnh trang 4 có Figure 2](tmp/extracted/visuals/page-004.png).

**Câu hỏi phải tự trả lời**

1. Q1, Q2 và Q3 kiểm tra ba khía cạnh nào của retargeting?
2. GMR cần dữ liệu chuyển động người và thông tin robot nào ở đầu vào?
3. Figure 2 có năm bước nào? Đầu ra cuối cùng của năm bước là gì?
4. BeyondMimic và RL xuất hiện ở công đoạn nào của nghiên cứu?
5. Khác nhau thế nào giữa huấn luyện policy và chạy policy đã huấn luyện để đánh giá?
6. Dữ liệu camera RGB-D hoặc TonyPi có nằm trong benchmark v1 này không?

**Điều phải giải thích bằng lời**

- Theo một chuỗi động tác người qua GMR để nhận được chuỗi cấu hình robot làm reference.
- Sau đó giải thích reference ấy được dùng để huấn luyện và đánh giá policy tracking ra sao.
- Chỉ ra phần nào tạo dữ liệu đích, phần nào tạo hành động điều khiển robot khi policy chạy.
- Nối Q1 với performance, Q2 với artifacts và Q3 với mức giống hình thức chuyển động nguồn.

**Đầu ra ghi chú:** một sơ đồ tay hoặc sơ đồ văn bản có **hai luồng rõ ràng**: retargeting tạo reference; huấn luyện/đánh giá policy bám reference. Ghi input/output dưới mỗi khối và một câu tiếng Việt giải thích mỗi mũi nối.

**Hoàn thành khi**

- [ ] Đã trả lời cả 6 câu hỏi và chép Q1–Q3 thành lời dễ hiểu.
- [ ] Có thể giải thích Figure 2 mà không gọi GMR là thuật toán RL.
- [ ] Sơ đồ ghi chú phân biệt được reference motion, policy và hành động điều khiển.

## Lượt 3 — Hiểu matching, alignment và scaling

**Phần trình bày phục vụ:** *Method Details — Representation and Scaling*.

**Đọc đúng chỗ**

- **IV, Step 1: Human-Robot Key Body Matching**, trang **4–5**.
- **Step 2: Human-Robot Cartesian Space Rest Pose Alignment** và **Step 3: Human Data Non-Uniform Local Scaling**, trang **5**.
- **Equation (2)–(3)**, trang **5**; kiểm tra trên [ảnh trang 5](tmp/extracted/visuals/page-005.png).

**Câu hỏi phải tự trả lời**

1. *Key body* là gì và mapping giữa người với robot được xác định thế nào?
2. Vì sao ghép đúng tên bộ phận vẫn chưa đủ để đảm bảo hướng của chúng khớp nhau?
3. Rest-pose alignment điều chỉnh thông tin hướng/vị trí nào trước khi retarget?
4. Trong Eq. (2), phần vị trí tương đối với root khác phần chuyển động root ở điểm nào?
5. Các ký hiệu `h`, `h_ref`, `s_b`, `s_root`, `p_source` và `p_target` có ý nghĩa gì?
6. Vì sao tác giả dùng local scaling khác nhau theo key body nhưng nhấn mạnh uniform scaling cho root translation?

**Điều phải giải thích bằng lời**

- Dùng ví dụ ghép bàn tay người với bàn tay robot; xác định rõ vị trí và hướng là hai thông tin khác nhau.
- Minh họa việc một người và robot cùng ở rest pose nhưng hệ trục của một đoạn cơ thể vẫn có thể khác nhau.
- Dùng ví dụ một người đứng yên rồi giơ tay: phần nào liên quan tới root, phần nào là vị trí của tay so với root?
- Giải thích trực giác Eq. (2)–(3) theo từng thành phần trước khi đọc lại toàn công thức; nêu liên hệ với foot sliding là nhận xét của tác giả.

**Đầu ra ghi chú:** một ví dụ tư thế mẫu có nhãn người/robot/root/key bodies; bảng **ký hiệu — ý nghĩa — xuất hiện ở đâu trong Eq. (2)–(3)**; đoạn giải thích khoảng **1 phút** về local scaling và root scaling. Nếu dùng số tự đặt, ghi rõ đó là ví dụ minh họa, không phải kết quả paper.

**Hoàn thành khi**

- [ ] Đã trả lời cả 6 câu hỏi và kiểm tra ký hiệu trực tiếp trên ảnh/PDF.
- [ ] Có thể nói input/output và mục đích của từng Step 1–3.
- [ ] Có thể giải thích ví dụ mà không nhầm root translation với chuyển động tương đối của tay/chân.

## Lượt 4 — Hiểu IK hai giai đoạn và xử lý chuỗi chuyển động

**Phần trình bày phục vụ:** *Method Details — Two-Stage IK*.

**Đọc đúng chỗ**

- **IV, Step 4: Solving Robot IK with Rotation Constraints**, **Step 5: Fine Tuning using Rotation & Translation Constraints**, trang **5**.
- **Equation (4)–(6)** và đoạn **Application to Motion Sequences**, trang **5**.
- Dùng [ảnh trang 5](tmp/extracted/visuals/page-005.png) để đối chiếu tập key bodies, trọng số và giới hạn; không suy diễn ký hiệu từ TXT bị xuống dòng.

**Câu hỏi phải tự trả lời**

1. IK tìm biến `q` nào? Trong bài, `q` gồm những thành phần nào ngoài các giá trị khớp?
2. Eq. (4) giảm những loại sai số nào và áp dụng lên những tập bộ phận nào?
3. Giai đoạn đầu có xét vị trí bàn tay/bàn chân không, dù tên Step 4 nhấn mạnh rotation?
4. Eq. (6) khác Eq. (4) ở tập vị trí được xét, trọng số và điểm khởi đầu như thế nào?
5. Eq. (5) giải vận tốc tổng quát `q_dot` để cập nhật cấu hình ra sao, và giới hạn khớp được giữ thế nào?
6. Khi xử lý một sequence, nghiệm frame trước và bước sửa độ cao sau toàn chuỗi có vai trò gì?

**Điều phải giải thích bằng lời**

- Giải thích FK là tính vị trí/hướng từ cấu hình robot; IK là tìm cấu hình để bám mục tiêu vị trí/hướng.
- Dùng ví dụ robot vươn tay: giảm sai số bám mục tiêu đồng thời tôn trọng giới hạn khớp; trọng số thể hiện mức ưu tiên các mục tiêu.
- So sánh hai giai đoạn bằng một bảng: mục tiêu hướng, mục tiêu vị trí, trọng số, khởi tạo. Giai đoạn đầu đã xét vị trí end-effectors; giai đoạn sau xét vị trí mọi key body.
- Phân biệt cập nhật từng frame, warm start từ frame trước và hậu xử lý độ cao sau khi đã retarget cả sequence.

**Đầu ra ghi chú:** bảng so sánh hai giai đoạn; một ví dụ tư thế qua cả hai bước; chú giải ngắn cho `q`, `q_dot`, `e`, `J`, `W`, `q_min/q_max` và `Delta t`. Nêu được mục tiêu/biến cần tìm/ràng buộc của mỗi công thức. Suy diễn ma trận dài có thể để phần hỏi đáp.

**Hoàn thành khi**

- [ ] Đã trả lời cả 6 câu hỏi và chỉ đúng thành phần trên Eq. (4)–(6).
- [ ] Có thể giải thích vì sao hai giai đoạn khác nhau bằng một tư thế mẫu.
- [ ] Không đồng nhất `Delta t` của solver với khoảng thời gian giữa hai frame nguồn; không bỏ qua hậu xử lý cả sequence khi mô tả khả năng vận hành online.

## Lượt 5 — Hiểu thiết kế thí nghiệm và metric

**Phần trình bày phục vụ:** *Experimental Setup and Metrics*.

**Đọc đúng chỗ**

- **III-A. Retargeting Methods**, trang **3**; chỉ tra **II. Related Work**, trang **2–3**, khi cần một định nghĩa hoặc khác biệt baseline cụ thể.
- **III-B. Data Processing**, trang **3–4**; **III-C. Motion Tracking Evaluation**, **III-D. Metrics**, **III-E. User Study Evaluation**, trang **4**.
- **Figure 1**, trang **4**, về cách hỏi người tham gia; đọc **phần chú thích Table I–II**, trang **6**, để kiểm tra điều kiện đo. Eq. (1), trang **3**, mô tả baseline PHC và không phải công thức lõi GMR cần ưu tiên học.

**Câu hỏi phải tự trả lời**

1. Benchmark dùng nguồn chuyển động và robot nào; số sequence và loại chuyển động được chọn có giới hạn gì?
2. PHC, ProtoMotions, GMR và dữ liệu Unitree giữ vai trò gì; mã thuật toán retargeting của Unitree có sẵn cho nghiên cứu này không?
3. Giữ cùng BeyondMimic giúp kiểm tra tác động của retargeting thế nào; những điểm chuyển đổi dữ liệu/xử lý baseline nào vẫn cần chú ý?
4. `sim`, `sim-dr` và `sim2sim` khác nhau thế nào, chạy bao nhiêu lượt trên mỗi policy, và điều kiện nào là robot thật?
5. Success được định nghĩa thế nào; ba tracking errors khác nhau về thứ đo, hệ quy chiếu và đơn vị ra sao?
6. User study hỏi người tham gia điều gì, cho họ xem dữ liệu gì và khác phép đo tracking ở đâu?

**Điều phải giải thích bằng lời**

- Tóm tắt thí nghiệm như một phép kiểm tra giả thuyết: thay retargeter, tạo reference, huấn luyện policy, rồi đánh giá dưới điều kiện đã nêu.
- Giải thích domain randomization là thay đổi điều kiện/tham số mô phỏng để kiểm tra độ bền vững; `sim2sim` vẫn là mô phỏng MuJoCo/ROS.
- Dùng một ví dụ robot bám dáng tương đối tốt nhưng lệch vị trí toàn cục để phân biệt hai metric vị trí.
- Dùng một ví dụ policy hoàn tất reference nhưng còn tracking error để giải thích tại sao success và độ chính xác đều cần được báo cáo.

**Đầu ra ghi chú:** bảng **dataset — robot — retargeters — pipeline huấn luyện — ba điều kiện đánh giá — số lượt — metric — user study**. Ghi riêng định nghĩa success và bảng đơn vị bên dưới.

### Metric và điều kiện đo phải ghi đúng theo v1

| Tên trong paper | Đo điều gì | Đơn vị / cách đọc |
| --- | --- | --- |
| **Success rate** | Tỷ lệ rollout hoàn tất reference mà anchor body không vượt ngưỡng sai lệch độ cao hoặc hướng đã quy định; episode kết thúc nếu vượt ngưỡng | **%**; không phải tỷ lệ hoàn thành một tác vụ robot thật |
| **E_g-mpbpe** | Sai số vị trí trung bình các body parts trong hệ toàn cục | **mm**, thấp hơn tốt hơn |
| **E_mpbpe** | Sai số vị trí trung bình các body parts tương đối với root | **mm**, thấp hơn tốt hơn |
| **E_mpjpe** | Trong chính v1 này, tác giả dùng ký hiệu này cho sai số góc trung bình của joint rotations | **10^-3 rad**, thấp hơn tốt hơn; không đổi thành mm theo thói quen dùng chữ viết tắt ở paper khác |

- Table I: `sim` trong IsaacSim **100** lượt/policy; `sim-dr` trong IsaacSim với domain randomization **4096** lượt/policy; `sim2sim` trong MuJoCo/ROS **100** lượt/policy.
- Table II: tracking errors đo trên **100 evaluation rollouts ở điều kiện sim**, không phải sim2sim. Theo III-D, errors được tính trên các frame policy còn hoạt động; cần nhớ điều này khi diễn giải cùng success rate.
- Figure 4: **tỷ lệ câu trả lời** trong user study với **20 người**; không phải success rate của robot.

**Hoàn thành khi**

- [ ] Đã trả lời cả 6 câu hỏi và điền đủ bảng setup/protocol/metric.
- [ ] Có thể giải thích các đơn vị mà không suy từ chữ viết tắt.
- [ ] Không gọi sim2sim là thử trên robot thật; không gộp mọi điều kiện thành một con số performance.

## Lượt 6 — Đọc kết quả như bằng chứng

**Phần trình bày phục vụ:** *Results and Analysis*.

**Đọc đúng chỗ**

- **V. Evaluation Results**, trang **5–7**; tập trung **V-A. Impact of retargeting method in policy performance**, **V-B. Impact of retargeting artifacts**, **V-C. User study**.
- **Table I–II**, trang **6**; **Figure 3–4**, trang **7**.
- [Ảnh trang 6 có hai bảng kết quả](tmp/extracted/visuals/page-006.png) và [ảnh trang 7 có artifacts/user study](tmp/extracted/visuals/page-007.png).

**Câu hỏi phải tự trả lời**

1. Table I hỗ trợ câu trả lời nào cho Q1; có motion nào không phân biệt được rõ các retargeter không?
2. Với hai motion **Run (stop & go)** và **Dance 5**, cột `sim2sim` cho thấy ưu điểm và ngoại lệ nào của GMR?
3. Table II bổ sung điều gì mà success rate chưa cho biết; GMR có thấp nhất mọi chỉ số so với Unitree không?
4. Figure 3 nối từng artifact với phương pháp và motion nào; nó hỗ trợ Q2 theo cách nào?
5. Figure 4 hỗ trợ Q3 thế nào; người tham gia ưu tiên GMR hơn những phương pháp nào và so với Unitree thì sao?
6. Bằng chứng nào là so sánh định lượng, bằng chứng nào là phân tích trường hợp; phần nào chưa đủ để khẳng định một thành phần riêng lẻ gây ra toàn bộ cải thiện?

**Điều phải giải thích bằng lời**

- Đọc một hàng của Table I theo đúng thứ tự: motion, điều kiện, bốn phương pháp, số lượt và tỷ lệ thành công.
- Dùng Run (stop & go) làm ví dụ kết quả tốt; dùng Dance 5 làm phản ví dụ để giữ kết luận có điều kiện.
- Nối hình ground penetration, self-intersection hoặc joint-value jumps với khó khăn khi policy bám reference; phân biệt phân tích artifact với một thí nghiệm ablation có kiểm soát.
- Giải thích cảm nhận “giống người” trong user study và tracking error là hai loại bằng chứng khác nhau.

**Đầu ra ghi chú:** chọn **2 hàng Table I**, **1 nhóm metric Table II**, **1 artifact Figure 3** và thông điệp Figure 4. Với mỗi mục, viết **câu hỏi — điều kiện đo — bằng chứng — kết luận — ngoại lệ**. Tự viết một câu tiếng Anh làm thông điệp kết quả; giữ số liệu chi tiết trong ghi chú tiếng Việt.

**Hoàn thành khi**

- [ ] Đã trả lời cả 6 câu hỏi và kiểm tra số liệu trực tiếp trên ảnh/PDF.
- [ ] Mọi con số được ghi kèm motion/điều kiện/đơn vị hoặc mẫu số phù hợp.
- [ ] Kết luận có một ngoại lệ rõ ràng; không viết “GMR tốt nhất mọi trường hợp” hoặc đưa ablation từ bản khác sang.

## Lượt 7 — Tổng hợp giới hạn và liên hệ đề tài nhóm

**Phần trình bày phục vụ:** *Limitations*, *Relevance to Our Teleoperation Project*, *Key Takeaways*.

**Đọc đúng chỗ**

- **VI. Conclusion**, trang **7–8**.
- Đọc lại **V-D. First reference frame** và **Table III**, trang **7**; đối chiếu dấu `*` ở Table I, trang **6**.
- Quay lại đúng đoạn method hoặc experiment khi cần bằng chứng; chưa cần đọc toàn bộ các bài được trích dẫn.

**Câu hỏi phải tự trả lời**

1. Benchmark chỉ dùng LAFAN1 và Unitree G1 giới hạn khả năng khái quát kết quả như thế nào?
2. Paper chưa kiểm chứng những loại tương tác môi trường hoặc nguồn chuyển động nào?
3. Table III cho thấy cùng policy nhưng đổi start frame có thể ảnh hưởng ra sao; vì sao cần ghi chú khi trích Table I?
4. Những giới hạn nào do tác giả nêu, những nhận xét nào là suy luận của người đọc?
5. Nhóm TonyPi/RGB-D có thể học nguyên lý nào của GMR và cách đánh giá nào, nhưng cần kiểm tra lại điều kiện gì?
6. Paper đã trả lời Q1–Q3 tới đâu; bạn sẽ giữ lại những kết luận nào khi báo cáo cho thầy?

**Điều phải giải thích bằng lời**

- Dùng Table III để giải thích ý nghĩa của tư thế khởi đầu có thể đạt an toàn; đây là thay đổi start frame khi đánh giá cùng policy, không tự suy ra đã huấn luyện lại policy.
- Phân biệt “có thể học cách alignment/scaling/đặt giới hạn” với “đã có bằng chứng chạy trực tiếp trên TonyPi”.
- Nêu một phép kiểm chứng có ý nghĩa cho nhóm, chẳng hạn so sánh các cách scaling trong cùng pipeline; ghi rõ đây là đề xuất của mình, không phải kết quả GMR.
- Trình bày lại câu chuyện từ vấn đề, cơ chế, bằng chứng đến giới hạn bằng tiếng Việt; dừng ở chỗ chưa hiểu để ghi câu hỏi cụ thể.

**Đầu ra ghi chú:** ba danh sách ngắn **tác giả đã chứng minh — chưa chứng minh — nhóm có thể kiểm chứng tiếp**; **3 ý Key Takeaways** bằng tiếng Anh và phần giải thích tiếng Việt; **5 câu hỏi thầy có thể hỏi** kèm câu trả lời và vị trí nguồn trong v1.

**Hoàn thành khi**

- [ ] Đã trả lời cả 6 câu hỏi và phân biệt kết luận paper với đề xuất của mình.
- [ ] Phần liên hệ dùng thuật ngữ teleoperation và không gán kết quả G1/mô phỏng cho TonyPi/RGB-D.
- [ ] Có thể trình bày lại các phần chính và chỉ đúng nguồn khi được hỏi về một kết quả.

## Glossary tối thiểu để bắt đầu

| Thuật ngữ | Cách hiểu dùng trong lượt đọc này |
| --- | --- |
| **Embodiment gap** | Khác biệt về tỷ lệ cơ thể, cấu trúc/giới hạn khớp, khối lượng và khả năng chuyển động giữa người với robot |
| **Key body** | Bộ phận được chọn làm mốc tương ứng để bám vị trí/hướng, như torso, tay hoặc bàn chân; không đồng nghĩa mọi joint trong skeleton |
| **Root pose** | Vị trí và hướng của gốc cơ thể; cần phân biệt chuyển động toàn cục của root với vị trí các bộ phận tương đối với root |
| **Rest-pose alignment** | Căn chỉnh các bộ phận/hệ trục khi người và robot ở tư thế tham chiếu, trước khi so sánh và retarget chuyển động |
| **Scaling** | Điều chỉnh tỷ lệ chuyển động người để tạo mục tiêu phù hợp hơn với robot; GMR phân biệt local scaling theo key body và uniform scaling của root translation |
| **FK / IK** | Forward kinematics tính vị trí/hướng từ cấu hình robot; inverse kinematics tìm cấu hình để bám mục tiêu vị trí/hướng trong các ràng buộc |
| **Reference motion / tracking policy** | Reference là chuỗi chuyển động đích; policy là mô hình chọn hành động từ quan sát và mục tiêu để robot bám chuỗi đó. Trong paper, BeyondMimic dùng RL để học policy |
| **Retargeting artifact** | Lỗi xuất hiện trong chuyển động chuyển đổi, như chân trượt/xuyên đất, bộ phận tự xuyên nhau hoặc giá trị khớp nhảy đột ngột |

## Kiểm tra trước khi chuyển ghi chú thành slide

- [ ] Mọi vị trí trích dẫn đều thuộc **v1, PDF 9 trang**; đã mở ảnh/PDF để kiểm tra phương trình và bảng dùng trong báo cáo.
- [ ] Có sơ đồ tách GMR tạo reference với RL huấn luyện/đánh giá tracking policy.
- [ ] Có một ví dụ xuyên suốt giải thích matching, alignment, scaling và IK.
- [ ] Công thức đưa lên slide đều có giải thích biến, mục tiêu, đầu ra và ràng buộc.
- [ ] Các kết quả giữ đúng điều kiện `sim`, `sim-dr`, `sim2sim`, metric và đơn vị; không có con số 70 Hz hoặc ablation 3% từ bản khác.
- [ ] Đã chuẩn bị cả kết quả tốt và ngoại lệ/giới hạn.
- [ ] Slide tiếng Anh có ý chính ngắn; ghi chú và phần nói tiếng Việt giải thích cơ chế và bằng chứng. Không thêm yêu cầu code/demo.

