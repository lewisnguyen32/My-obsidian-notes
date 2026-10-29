# Bản thảo slide báo cáo GMR

Đề tài: **Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking**.

Bản dùng để soạn nội dung: **arXiv:2510.02252v1, 02/10/2025, PDF 9 trang**. Mọi số trang bên dưới đếm từ 1 trong PDF. Slide tiếng Anh; phần giải thích và luyện nói bằng tiếng Việt.

## Cách dùng bản thảo

- Chỉ đưa nội dung trong khối **Text on slide** lên slide. Các mục giải thích, nguồn, câu hỏi và chuyển ý là ghi chú để chuẩn bị/thuyết trình, không phải đoạn văn để dán lên slide.
- Mỗi slide có một nhiệm vụ chính, một visual chiếm phần lớn diện tích và tối đa khoảng ba ý ngắn. Mục tiêu khoảng 15–30 từ nội dung, ngoài tiêu đề, tên tác giả, nhãn dữ liệu và nguồn.
- Không giới hạn việc hiểu paper ở số chữ trên slide. Chi tiết nằm trong phần nói, đáp án checklist đọc và các slide dự phòng.
- Đây là đề xuất **15 slide chính và 5 slide dự phòng**; chưa có thời lượng hoặc số slide bắt buộc từ thầy. Nếu cần rút xuống 12 slide, xem phương án gộp cuối file.
- Bản thảo gắn với [GMR_READING_CHECKLIST.md](GMR_READING_CHECKLIST.md). Hoàn thành lượt đọc liên quan trước khi dùng slide để luyện nói.

## Nguồn để soạn slide

1. [PDF GMR v1](tmp/2510.02252v1.pdf).
2. [Text có mốc trang](tmp/extracted/2510.02252v1.txt) và [ảnh trang nội dung](tmp/extracted/visuals/).
3. [Trang arXiv đúng phiên bản](https://arxiv.org/abs/2510.02252v1).
4. [Báo cáo nhóm ngày 26/10/2026](<tmp/Báo cáo 26102026.pdf>): tham khảo vị trí GMR trong danh sách paper ở trang 7, mục tiêu TonyPi ở trang 10 và mô tả dữ liệu nhóm ở trang 12. Đây là nguồn liên hệ dự án, không phải nguồn kết quả thực nghiệm GMR.

PDF báo cáo nhóm trình bày hướng dự án và nhiều nghiên cứu. Bài nói này tập trung phân tích một paper, nên dùng cấu trúc dưới đây. Có thể dùng phong cách màu/trường/lab của mẫu nếu sau này có yêu cầu; chưa coi PDF đó là template bắt buộc.

## Chia bài nói thành năm phần

| Phần | Tên phần trên slide | Slide | Người nghe cần hiểu sau phần này |
| --- | --- | --- | --- |
| I | Problem and Research Questions | 1–3 | Vì sao chất lượng retargeting đáng nghiên cứu và paper hỏi điều gì |
| II | General Motion Retargeting | 4–7 | GMR nhận gì, xử lý ra sao và tạo ra reference gì |
| III | Evaluation Design | 8–9 | Tác giả kiểm chứng tác động của retargeting bằng cách nào |
| IV | Evidence and Failure Cases | 10–12 | Kết quả ủng hộ điều gì, có ngoại lệ nào và các loại bằng chứng khác nhau ra sao |
| V | Limitations and Project Relevance | 13–15 | Phạm vi kết luận, bài học cho nhóm và những điều còn cần kiểm chứng |

Không cần năm slide phân cách chỉ có tên phần. Ghi nhãn phần nhỏ ở góc trên hoặc chân các slide thuộc phần đó. Khi nói, chuyển phần bằng một câu nối.

## Phần I Problem and Research Questions

### Slide 1 Paper Overview

**Nhiệm vụ:** giới thiệu bài và câu hỏi người trình bày muốn hiểu.

**Text on slide**

```text
Retargeting Matters
General Motion Retargeting for Humanoid Motion Tracking

Araújo, Ze, Xu, Wu and Liu
arXiv:2510.02252v1 · 2025
```

Thêm tên người trình bày và lab bằng thông tin thật khi soạn deck.

**Visual và bố cục:** tiêu đề lớn, nền đơn giản, khoảng trắng rộng. Không bắt buộc chèn ảnh trang trí. Nếu muốn một ảnh nhỏ, dùng một cặp source/retarget ở Figure 1, PDF trang 4, nhưng khi đó không lặp lại nguyên ảnh đó ở các slide sau.

**Phần nói tiếng Việt:** “Em chọn bài này để tìm hiểu ảnh hưởng của retargeting tới việc học điều khiển robot. Em sẽ trình bày cả phương pháp GMR và cách tác giả dùng policy tracking để kiểm chứng chất lượng chuyển động tham chiếu.” Không tuyên bố đã triển khai hay chạy thí nghiệm.

**Nguồn/đọc:** trang 1; lượt đọc 1.

**Chuyển ý:** “Trước hết, vì sao chuyển động người chưa thể dùng trực tiếp cho robot?”

### Slide 2 The Embodiment Gap

**Nhiệm vụ:** làm rõ vấn đề kỹ thuật và hậu quả nhìn thấy được.

**Text on slide**

```text
Different bodies
Different motion constraints
Imperfect reference motions
```

**Visual và bố cục:** hình lớn ở giữa hoặc bên phải; chữ ngắn ở bên trái. Dùng crop Figure 3(a) và 3(b), PDF trang 7: ground penetration của PHC và self-intersection của ProtoMotions. Giữ nhãn phương pháp/chuyển động để người nghe không hiểu nhầm đây đều là lỗi GMR. Có thể chỉ dùng một crop và giải thích lỗi còn lại bằng lời.

**Phần nói tiếng Việt:** giải thích khác biệt tỷ lệ cơ thể, cấu trúc khớp và giới hạn chuyển động. Reference là chuyển động robot được yêu cầu bám theo; reference có lỗi có thể làm việc học khó hơn. Nêu sự khác nhau giữa “chuyển động nhìn giống” và “chuyển động khả thi trong vật lý”. Hình này minh họa vấn đề của các retargeter trong benchmark, chưa phải mô tả pipeline camera của nhóm.

**Phải giải thích được:** retargeting cần giải quyết điều gì ngoài việc chép góc khớp người sang robot?

**Nguồn/đọc:** Introduction trang 1–2; Figure 3 trang 7; lượt 1.

### Slide 3 Research Questions and Contributions

**Nhiệm vụ:** cho người nghe biết paper sẽ kiểm chứng gì.

**Text on slide**

```text
Q1  Policy performance
Q2  Harmful motion artifacts
Q3  Faithfulness to human motion

GMR method and comparative evaluation
```

**Visual và bố cục:** ba dòng được đánh số Q1–Q3, để nhiều khoảng trắng; không cần ảnh. Dòng đóng góp nhỏ hơn bên dưới. Không chèn danh sách 29 paper hoặc bảng tick của báo cáo nhóm.

**Phần nói tiếng Việt:** diễn đạt đầy đủ ba câu hỏi: lựa chọn retargeter có ảnh hưởng tới policy không; lỗi nào gây hại; chuyển động giữ được hình thức nguồn tới đâu. Phân biệt hai đóng góp: đề xuất GMR và thực nghiệm so sánh tác động của retargeting. Đây là những điều cần kiểm chứng bằng kết quả, chưa phải kết luận ở slide này.

**Nguồn/đọc:** đầu Section III trang 3 và Introduction; lượt 1–2.

**Chuyển phần:** “Để hiểu cách kiểm chứng, trước tiên em tách thuật toán GMR khỏi phần policy tracking.”

## Phần II General Motion Retargeting

### Slide 4 GMR and Policy Tracking

**Nhiệm vụ:** phân biệt phần tạo reference với phần học và đánh giá controller.

**Text on slide**

```text
Human motion
GMR
Robot reference motion
RL tracking policy
Simulation evaluation
```

**Visual và bố cục:** một sơ đồ luồng lớn có nhãn nhóm “Retargeting” và “Policy evaluation”. Đường đi là dữ liệu chuyển động người, GMR, reference robot, huấn luyện policy rồi đánh giá policy trong mô phỏng. Đây là sơ đồ diễn giải của người trình bày từ Section III–IV; không gắn nhãn như một figure gốc của paper. Có thể soạn bằng các đối tượng sơ đồ chỉnh sửa được.

**Phần nói tiếng Việt:** GMR nhận skeleton/motion người, mô tả cấu trúc robot và mapping; tạo chuỗi root pose cùng giá trị khớp. BeyondMimic huấn luyện policy bám reference bằng RL. Mỗi clip được dùng để huấn luyện policy riêng trong thiết kế benchmark. Không có camera RGB-D ở đầu vào benchmark này; không mô tả hình như một hệ teleoperation trực tiếp đã triển khai trên TonyPi.

**Phải giải thích được:** reference motion khác lệnh điều khiển thực thi ra sao? RL nằm ở đâu?

**Nguồn/đọc:** Section III trang 3–4; Figure 2 và Section IV trang 4–5; lượt 2.

### Slide 5 Key Body Matching and Rest Pose Alignment

**Nhiệm vụ:** giải thích hai bước chuẩn bị trước scaling và IK.

**Text on slide**

```text
Body correspondences
Rest-pose alignment
Position and orientation offsets
```

**Visual và bố cục:** sơ đồ minh họa người và robot với các phần tương ứng được nối màu giống nhau, kèm trục hướng của một bộ phận trước/sau căn chỉnh. Đây là minh họa tự soạn theo Step 1–2, không phải kết quả đo của tác giả. Nếu chưa có sơ đồ phù hợp, dùng crop hai bước đầu của Figure 2, trang 4, và chỉ vào chúng khi nói. Không gọi tư thế bất kỳ trong Figure 1 là rest pose của GMR.

**Phần nói tiếng Việt:** mapping xác định phần người nào tương ứng phần robot nào và được người dùng thiết lập. Cùng tên bộ phận chưa có nghĩa cùng hệ trục/hướng chuẩn. Alignment chỉnh các offset theo tư thế tham chiếu để mục tiêu hình học có ý nghĩa đối với robot. Bước này chưa giải quyết hết khác biệt tỷ lệ chiều dài và giới hạn khớp.

**Ví dụ để luyện:** chọn cẳng tay hoặc bàn chân; giải thích một trục hướng bị lệch làm mục tiêu retarget sai như thế nào.

**Nguồn/đọc:** Step 1 trang 4–5; Step 2 trang 5; lượt 3.

### Slide 6 Local Scaling and Root Motion

**Nhiệm vụ:** giải thích khác biệt quan trọng về xử lý tỷ lệ.

**Text on slide**

```text
Body-specific local scaling
Uniform root translation scaling
Preserving motion structure
```

**Visual và bố cục:** minh họa skeleton người/robot khác tỷ lệ tay–chân và đánh dấu root. Ghi các nhãn ngắn như `arm scale`, `leg scale`, `root scale`. Hình phải được ghi là illustration nếu không lấy trực tiếp từ dữ liệu paper. Phương án tối giản là trích Eq. 2–3, trang 5, chỉ tô nhấn hai nhóm local và root, không đưa cả đoạn giải nghĩa ký hiệu lên slide.

**Phần nói tiếng Việt:** nói bằng lời trước: mỗi phần cơ thể có thể cần tỷ lệ riêng; chuyển động root được scale đồng đều để tránh làm méo quỹ đạo toàn cục và góp phần hạn chế foot sliding. Phân biệt vị trí tương đối với root và chuyển động root trong không gian. Non-uniform local scaling ở đây không có nghĩa tự đặt ba tỷ lệ x/y/z tùy ý cho mọi phần cơ thể.

**Phải giải thích được:** trong Eq. 2, phần nào điều chỉnh body tương đối với root, phần nào đưa root đi trong không gian? Vì sao chỉ nhân một tỷ lệ chiều cao cho tất cả chưa đủ?

**Nguồn/đọc:** Step 3 và Eq. 2–3, trang 5; lượt 3.

### Slide 7 Two-Stage Inverse Kinematics

**Nhiệm vụ:** giải thích cơ chế tìm cấu hình robot và sự khác nhau giữa hai giai đoạn.

**Text on slide**

```text
Stage 1  Orientations and end-effector positions
Stage 2  Orientations and all key-body positions
Joint limits
```

**Visual và bố cục:** một sơ đồ hai bước lớn, kèm biểu diễn trực quan mục tiêu tay/chân và các key bodies. Có thể dùng crop phần Step 4–5 trong Figure 2 ở trang 4. Chỉ chọn một công thức mục tiêu nếu thật sự cần và đủ thời gian giải thích; công thức differential IK đầy đủ để ở slide 16 dự phòng.

**Phần nói tiếng Việt:** IK tìm root pose và giá trị khớp để giảm sai số so với mục tiêu. Giai đoạn đầu xét hướng các key bodies và vị trí tay/chân; giai đoạn sau tinh chỉnh vị trí của toàn bộ key bodies với trọng số khác. Cả hai chịu giới hạn khớp. Giải thích trực giác tối ưu theo hai giai đoạn và việc dùng nghiệm trước làm điểm bắt đầu; đừng khẳng định luôn tìm được nghiệm tối ưu toàn cục. Khi chạy sequence, frame trước khởi tạo frame sau. Paper còn có hậu xử lý độ cao sau cả sequence; không bỏ qua chi tiết này khi được hỏi về online/offline.

**Phải giải thích được:** biến cần tìm, mục tiêu giảm sai số và ràng buộc là ba thứ nào? Giới hạn khớp không tự đảm bảo mọi chuyển động đều ổn định động lực học hoặc không tự va chạm.

**Nguồn/đọc:** Step 4–5, Eq. 4–6 và Application to Motion Sequences, trang 5; lượt 4.

**Chuyển phần:** “Phương pháp tạo ra reference như vậy; phần tiếp theo kiểm tra reference có giúp policy hoạt động tốt hơn hay không.”

## Phần III Evaluation Design

### Slide 8 Experimental Setup

**Nhiệm vụ:** cho thấy cách tác giả tổ chức so sánh.

**Text on slide**

```text
LAFAN1 · 21 motions · Unitree G1
PHC / ProtoMotions / GMR / Unitree data
Shared BeyondMimic training framework
```

**Visual và bố cục:** một sơ đồ bốn nhánh retargeting hội tụ về cùng framework huấn luyện/đánh giá. Ghi rõ đây là framework chung, không phải cùng một policy có cùng weights. Nhánh Unitree ghi `Closed-source retargeted data`. Dưới sơ đồ có ba nhãn `sim`, `sim-dr`, `sim2sim`.

**Phần nói tiếng Việt:** cùng nguồn chuyển động được đưa qua các cách retarget khác nhau; policy được huấn luyện theo từng clip bằng BeyondMimic. Giải thích `sim` là IsaacSim không bật domain randomization; `sim-dr` có domain randomization; `sim2sim` là MuJoCo/ROS, vẫn là mô phỏng. Unitree cung cấp dữ liệu đã retarget, tác giả không có thuật toán đóng đó. Chi tiết chuyển BVH sang SMPL/SMPL-X và hậu xử lý PHC để ở phần hỏi đáp nếu cần.

**Phải giải thích được:** điều gì được giữ chung để nghiên cứu ảnh hưởng retargeting? Những khác biệt xử lý dữ liệu nào có thể ảnh hưởng cách hiểu so sánh?

**Nguồn/đọc:** Section III-A–C, trang 3–4; lượt 5.

### Slide 9 Evaluation Metrics

**Nhiệm vụ:** định nghĩa kết quả trước khi cho người nghe xem số.

**Text on slide**

```text
Completion success
Tracking error
Perceived faithfulness
```

**Visual và bố cục:** ba dòng với một ký hiệu giải thích đơn giản hoặc một bảng nhỏ gồm metric và đơn vị. Không cần ảnh trang trí. Có thể dùng hình so sánh quỹ đạo reference/robot mang tính minh họa, không gắn số liệu giả. Nếu hiển thị tên metric, giữ đúng ký hiệu và đơn vị của v1.

**Phần nói tiếng Việt:** success là hoàn tất reference mà độ lệch chiều cao/hướng của anchor body không vượt ngưỡng chấm dứt; không phải task success trên robot thật. Sai số vị trí có global và root-relative, tính bằng mm; sai số góc khớp được báo bằng 10^-3 rad. Các sai số tính trên những frame policy còn hoạt động, vì vậy cần đọc kèm success. User study đo người xem thấy giống chuyển động nguồn tới đâu, không đo sai số vị trí vật lý.

**Phải giải thích được:** policy hoàn tất chuyển động nhưng vẫn bám không chính xác có thể xảy ra không? Vì sao không so trực tiếp mm với rad hoặc gộp chúng thành một “độ chính xác”?

**Nguồn/đọc:** Section III-D–E, trang 4; lượt 5. Tên metric đầy đủ ở slide 18 dự phòng.

**Chuyển phần:** “Với các tiêu chí này, em chọn vài kết quả để trả lời ba câu hỏi nghiên cứu.”

## Phần IV Evidence and Failure Cases

### Slide 10 Success Rates and a Failure Case

**Nhiệm vụ:** trả lời Q1 và chỉ ra ngoại lệ quan trọng cho Q2.

**Text on slide**

```text
sim2sim completion success (%)
Run (stop & go)
Dance 5
```

**Visual và bố cục:** dùng bảng 2 hàng dưới đây làm visual chính. Soạn lại thành bảng chỉnh sửa được hoặc crop đúng hai hàng và header `sim2sim` của Table I, trang 6. Giữ thứ tự phương pháp và đánh dấu GMR bằng một màu nhất quán.

| Motion | PHC | GMR | ProtoMotions | Unitree |
| --- | ---: | ---: | ---: | ---: |
| Run (stop & go) | 74 | 100 | 26 | 100 |
| Dance 5 | 100 | 51 | 100 | 100 |

Chú thích nhỏ: `Table I, sim2sim, 100 trials per policy`. Không trộn số từ cột sim hoặc sim-dr.

**Phần nói tiếng Việt:** giải thích cả hai hàng. GMR có kết quả tốt ở Run (stop & go), nhưng Dance 5 là phản ví dụ cho khẳng định “luôn tốt nhất”. Nối kết quả Dance 5 với lỗi nhảy đột ngột giá trị khớp eo được tác giả mô tả. Nếu cần xem hình, mở Figure 3(c), trang 7, từ phụ lục hoặc PDF; không nhét thêm biểu đồ nhỏ khó đọc vào slide chính.

**Phải giải thích được:** các phần trăm đang đo điều gì và có bao nhiêu lượt đánh giá? Vì sao 100% ở một clip không chứng minh tổng quát cho mọi chuyển động hoặc robot thật?

**Nguồn/đọc:** Table I trang 6, Section V-A–B trang 5–6 và Figure 3(c) trang 7; lượt 6.

### Slide 11 Tracking Accuracy

**Nhiệm vụ:** cho thấy completion và chất lượng bám là hai mặt khác nhau.

**Text on slide**

```text
Mean global body-position error
sim evaluation · mm · lower is better
```

**Visual và bố cục:** biểu đồ cột bốn phương pháp, từ hàng Mean của Table II, trang 6, metric E_g-mpbpe. Dữ liệu chính xác:

| Method | Error (mm) |
| --- | ---: |
| PHC | 247.8 |
| GMR | 104.1 |
| ProtoMotions | 139.7 |
| Unitree | 77.2 |

Trục giá trị bắt đầu ở 0; ghi số trên mỗi cột, đơn vị mm, metric, điều kiện sim và nguồn. Biểu đồ này được soạn lại từ bảng, không phải hình gốc paper. Không đặt số cột sim2sim của slide 10 vào biểu đồ này.

**Phần nói tiếng Việt:** GMR có mean global tracking error thấp hơn hai retargeter mở trong bảng, nhưng Unitree thấp hơn GMR. Chỉ số này không phải lỗi trực tiếp giữa skeleton người và skeleton robot; nó đo policy bám reference trong đánh giá mô phỏng. Nêu vì sao cần xem cùng tỷ lệ hoàn tất, và vì sao đọc một giá trị mean chưa mô tả mọi clip.

**Nguồn/đọc:** Table II trang 6, Section III-D trang 4; lượt 5–6.

### Slide 12 Perceived Motion Faithfulness

**Nhiệm vụ:** trả lời Q3 bằng một loại bằng chứng khác với tracking error.

**Text on slide**

```text
Human preference study
20 participants
Faithfulness to the source motion
```

**Visual và bố cục:** crop Figure 4, PDF trang 7, giữ legend `Prefers GMR / No Preference / Prefers Other` và nhãn ba nhóm đối chiếu. Phóng đủ lớn để đọc tỷ lệ; không cắt mất nhóm Unitree.

**Phần nói tiếng Việt:** mỗi người xem các cặp clip được ẩn tên phương pháp và đổi thứ tự; chọn chuyển động giống nguồn hơn hoặc không phân biệt được. Người xem ưu tiên GMR hơn PHC và ProtoMotions. Khi đối chiếu Unitree, **25% câu trả lời chọn GMR, 37% không có ưu tiên và 38% chọn Unitree**; không kết luận GMR được ưu tiên hơn Unitree. Phần trăm là tỷ lệ câu trả lời, không phải tỷ lệ người hay success rate của robot. Nêu quy mô N=20 khi diễn giải phạm vi bằng chứng.

**Phải giải thích được:** “giống chuyển động nguồn” khác “bám reference chính xác” như thế nào?

**Nguồn/đọc:** Section III-E trang 4; Section V-C và Figure 4 trang 7; lượt 5–6.

**Chuyển phần:** “Các bằng chứng này có giá trị trong phạm vi benchmark; em sẽ kết lại bằng giới hạn và phần có thể học cho nhóm.”

## Phần V Limitations and Project Relevance

### Slide 13 Scope and Limitations

**Nhiệm vụ:** xác định phạm vi mà kết quả hỗ trợ.

**Text on slide**

```text
One motion source: LAFAN1
One evaluated robot: Unitree G1
Simulation and sim2sim evidence
```

**Visual và bố cục:** ba dòng ngắn, không bắt buộc có ảnh. Có thể làm một bảng phạm vi nhỏ bằng ba nhãn `Data`, `Robot`, `Evaluation`. Không dùng ảnh robot thật để minh họa như thể paper này đã xác nhận triển khai hardware.

**Phần nói tiếng Việt:** tính tổng quát của phương pháp và phạm vi benchmark là hai việc cần phân biệt. Paper kiểm chứng trên nguồn/robot/điều kiện đã nêu; còn phải xem xét nguồn khác, robot khác, perception có nhiễu và ràng buộc thực tế. GMR còn có thể tạo artifacts, ví dụ Dance 5. Frame bắt đầu cũng ảnh hưởng tới success; Table III để ở slide 19 dự phòng. Không gắn số 70Hz hoặc ablation 3% từ bản tác giả khác vào v1.

**Nguồn/đọc:** Conclusion trang 7–8; V-D trang 7; lượt 7.

### Slide 14 Relevance to TonyPi Teleoperation

**Nhiệm vụ:** nêu bài học cụ thể cho đề tài nhóm, tách khỏi kết quả đã chứng minh của GMR.

**Text on slide**

```text
Joint mapping and limits
Motion quality before control
Retargeting and tracking evaluation
```

**Visual và bố cục:** sơ đồ pipeline dự kiến của nhóm với Perception, Retargeting và Action, tô nhấn Retargeting và phần đánh giá. Nhãn dưới hình: `Potential lessons for our project`. Đây là sơ đồ diễn giải liên hệ của người trình bày, không phải pipeline TonyPi đã được paper GMR kiểm chứng. Không cần ảnh trang trí robot trong báo cáo mẫu.

**Phần nói tiếng Việt:** nhóm có thể học cách xử lý khác biệt tỷ lệ, giới hạn khớp và cách tách chất lượng reference khỏi chất lượng controller. Mục tiêu TonyPi trong báo cáo nhóm gồm làm theo người trước camera và giữ cân bằng; việc đưa các nguyên lý sang TonyPi cần mapping, model phần cứng và kiểm chứng riêng. Báo cáo nhóm có mô tả NTU RGB+D 120 ở trang 12; đó không phải dữ liệu benchmark LAFAN1 của GMR và chưa tự cung cấp nhãn servo robot. Paper GMR không trả lời việc depth giúp nhóm bao nhiêu hoặc tạo trực tiếp policy chạy được trên TonyPi.

**Phải giải thích được:** một điều có thể học ngay về nguyên lý, một điều cần điều chỉnh và một kết luận hiện chưa có bằng chứng.

**Nguồn/đọc:** GMR Section IV và VI; báo cáo nhóm trang 10, 12; lượt 7. Nội dung liên hệ là phân tích của người trình bày.

### Slide 15 Key Takeaways

**Nhiệm vụ:** kết thúc bằng những điều người trình bày hiểu và có thể bảo vệ bằng bằng chứng.

**Text on slide**

```text
Reference quality affects policy tracking
GMR combines scaling and constrained IK
Better retargeting still needs validation
```

**Visual và bố cục:** ba câu ngắn hoặc sơ đồ rút gọn do người trình bày soạn: chất lượng reference, policy tracking, kiểm chứng. Giữ slide này khi chuyển sang hỏi đáp; không cần thêm một slide chỉ có “Thank you”.

**Phần nói tiếng Việt:** kết lại theo ba lớp: câu hỏi paper đặt ra, cơ chế GMR giải quyết và mức bằng chứng hiện có. Nêu nhận xét cá nhân có căn cứ: chất lượng dữ liệu mục tiêu là một phần của bài toán điều khiển, vì controller khó bù mọi lỗi được tạo ở bước trước. Câu này là diễn giải rút ra từ paper, không phải trích dẫn nguyên văn.

**Nguồn/đọc:** Section V–VI; lượt 7.

## Slide dự phòng cho hỏi đáp

Đây là phụ lục, chỉ mở khi cần. Không bắt buộc trình bày hết hoặc chuẩn bị mọi chi tiết với cùng độ sâu.

| Số | Tiêu đề tiếng Anh | Nội dung cần có | Visual/nguồn | Khi nào mở |
| --- | --- | --- | --- | --- |
| 16 | Differential IK Details | Ý nghĩa q, sai số e, Jacobian J, trọng số W, bước cập nhật và giới hạn khớp; phân biệt Eq. 4, 5, 6 | Crop công thức trang 5, giữ số Eq. 4–6 và giải thích ký hiệu | Thầy hỏi cụ thể solver làm gì hoặc hai stage khác nhau thế nào |
| 17 | Retargeting Baselines | So sánh ngắn cách xử lý nguồn/tỷ lệ và optimization của PHC, ProtoMotions, GMR; Unitree ghi là closed-source retargeted data | Section III-A–B trang 3–4; bảng tự soạn, không dùng bảng tick 29 bài | Thầy hỏi vì sao chọn baseline hoặc so sánh có công bằng không |
| 18 | Metric and Protocol Details | E_g-mpbpe và E_mpbpe tính bằng mm; E_mpjpe báo bằng 10^-3 rad; success/termination và alive-frame errors; số rollout | Section III-C–D trang 4; caption Table I–II trang 6 | Thầy hỏi đơn vị, định nghĩa success hoặc chênh lệch điều kiện sim/sim-dr/sim2sim |
| 19 | Initial Reference Frame | Cùng policy nhưng thay frame bắt đầu; ví dụ GMR Walk 2 từ 64% ở frame 0 thành 100% ở frame 7 | Table III và V-D, trang 7; có thể thêm Figure 3(c) nếu cần hỏi lỗi sequence | Thầy hỏi về khởi tạo, chuyển động đầu/cuối hoặc Dance 5 |
| 20 | References | Paper v1, nguồn figure/table và báo cáo nhóm được dùng để liên hệ | Bibliography ngắn, URL hoặc DOI; tên/phiên bản đầy đủ | Tra nguồn hoặc kết thúc phần hỏi đáp |

**Lưu ý khi chuẩn bị phụ lục 16:** đoạn giải nghĩa công thức trong v1 có cách ghi cần làm rõ nếu đi sâu suy diễn, như ký hiệu sai số orientation và cách gọi `e(q)` ở Eq. 5. Đọc công thức cùng đoạn giải thích và đối chiếu ảnh gốc; không sao chép một ký hiệu rồi mặc định đã hiểu định nghĩa toán. Với phần chưa chắc, ghi thành câu hỏi cần làm rõ thay vì tự đưa một suy diễn chưa kiểm chứng lên slide.

## Danh mục hình và dữ liệu để lấy khi soạn deck

Các đường dẫn PNG dưới đây là **ảnh toàn trang**, chưa phải file crop hình. Cắt đúng vùng figure/table khi đặt lên slide; luôn giữ thông tin cần hiểu nguồn và điều kiện.

| Nội dung | Vị trí chính xác | File xem trước | Dùng ở đâu |
| --- | --- | --- | --- |
| GMR pipeline | Figure 2, trang 4 | [page-004.png](tmp/extracted/visuals/page-004.png) | Tham khảo slide 4; crop hai bước đầu/cuối cho 5/7 nếu cần |
| Source và retarget snapshots | Figure 1, trang 4 | [page-004.png](tmp/extracted/visuals/page-004.png) | Tùy chọn slide 1; không gọi đó là rest pose |
| Scaling và IK | Eq. 2–6, trang 5 | [page-005.png](tmp/extracted/visuals/page-005.png) | Slide 6/7 hoặc phụ lục 16 |
| Success rates | Table I, trang 6 | [page-006.png](tmp/extracted/visuals/page-006.png) | Slide 10, chỉ lấy cột sim2sim và hai hàng đã chọn |
| Tracking errors | Table II, trang 6 | [page-006.png](tmp/extracted/visuals/page-006.png) | Slide 11, hàng Mean của E_g-mpbpe, điều kiện sim |
| Failure artifacts | Figure 3, trang 7 | [page-007.png](tmp/extracted/visuals/page-007.png) | Slide 2 dùng a/b; phụ lục có thể dùng c |
| User study | Figure 4, trang 7 | [page-007.png](tmp/extracted/visuals/page-007.png) | Slide 12 |
| Start frame | Table III, trang 7 | [page-007.png](tmp/extracted/visuals/page-007.png) | Phụ lục 19 |

Ưu tiên hình và dữ liệu thật từ paper. Các sơ đồ minh họa phương pháp có thể được người trình bày soạn lại, nhưng cần ghi nguồn ý tưởng và phân biệt với dữ liệu/kết quả tác giả. Không dùng ảnh AI làm bằng chứng thực nghiệm. Tránh lặp nguyên một hình trên nhiều slide, trừ khi chủ đích là zoom vào một phần của sơ đồ để giải thích.

## Quy tắc giữ slide ít chữ

1. Mỗi slide trả lời một câu hỏi hoặc giải thích một bước. Câu trả lời chi tiết nằm trong phần nói.
2. Chỉ để title, các nhãn ngắn, dữ liệu cần đọc và nguồn. Không dán Abstract, Introduction hoặc đoạn ghi chú tiếng Việt lên slide.
3. Visual khoảng 60–75% diện tích khi có hình/bảng phù hợp. Các slide câu hỏi/giới hạn có thể chỉ cần chữ ngắn và khoảng trắng.
4. Tiêu đề khoảng 30–34 pt, nội dung khoảng 24–28 pt; nhãn biểu đồ khoảng 20–24 pt. Cắt bớt nội dung trước khi giảm cỡ chữ. Nguồn nhỏ hơn nhưng vẫn đọc được.
5. Dùng màu nhất quán cho GMR và một màu khác cho baseline. Trong biểu đồ giữ metric, đơn vị, điều kiện và hướng tốt hơn; số liệu hiển thị phải đúng nguồn.
6. Chú thích nguồn ngắn trên slide, ví dụ `Araújo et al., arXiv:2510.02252v1, Table I, p.6`. Ghi nguồn đầy đủ trong notes hoặc slide References.
7. Không dùng cả trang PDF làm hình chiếm nhỏ giữa slide. Crop phần cần phân tích hoặc soạn lại biểu đồ/bảng từ đúng dữ liệu.
8. Chuyển phần bằng lời và nhãn phần nhỏ; không thêm nhiều slide agenda, divider hay trang trí khi không phục vụ nội dung.

## Phương án rút xuống 12 slide nếu cần

Giữ nguyên số của bản thảo 15 slide để đối chiếu, sau đó gộp khi đã biết thời lượng:

| Slide mới | Lấy từ slide bản thảo | Nội dung |
| --- | --- | --- |
| 1–4 | 1–4 | Giới thiệu, vấn đề, câu hỏi và workflow |
| 5 | 5 + 6 | Matching, alignment và scaling, dùng một ví dụ xuyên suốt |
| 6 | 7 | Two-stage IK |
| 7 | 8 + 9 | Setup và metric tối thiểu cần đọc kết quả |
| 8–10 | 10–12 | Success/failure, tracking accuracy, user study |
| 11 | 13 + 14 | Giới hạn và liên hệ nhóm |
| 12 | 15 | Key Takeaways |

Gộp bằng cách bớt chữ và chuyển chi tiết sang lời nói/phụ lục, không thu nhỏ hai slide vào một trang.

## Kiểm tra trước khi trình bày

- [ ] Tôi giải thích được slide 4 mà không nhầm GMR với policy RL.
- [ ] Tôi giải thích được vì sao cần matching, alignment, scaling và hai giai đoạn IK.
- [ ] Tôi biết success, tracking error và user preference đo ba thứ khác nhau.
- [ ] Tôi giữ đúng sim2sim ở slide 10 và sim ở slide 11.
- [ ] Tôi trình bày được cả ví dụ tốt và thất bại của GMR.
- [ ] Tôi không dùng ảnh/bảng trong báo cáo nhóm làm kết quả của paper.
- [ ] Tôi tách rõ bài học đề xuất cho TonyPi khỏi điều GMR đã kiểm chứng.
- [ ] Chữ trên slide là tiếng Anh, còn phần giải thích tiếng Việt nằm trong notes.
- [ ] Tôi có thể nói ý chính của từng slide trong 1–2 câu trước khi đi vào chi tiết.
