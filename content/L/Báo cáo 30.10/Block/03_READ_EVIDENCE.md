---
duration_minutes: 60
phase: reading
status: todo
paper_version: arxiv-2510.02252v1
---

# Block 03 - Đọc thiết kế thí nghiệm, kết quả và giới hạn

[[00_START_HERE|Về mục lục]] · Trước: [[02_READ_METHOD]] · Tiếp: [[04_BUILD_SLIDES]]

> [!info] Phạm vi
> **60 phút, chỉ đọc và ghi chú học.** Đây là bản đọc chọn lọc từ lượt 5–7 của checklist để phục vụ bài báo cáo gọn; không có nghĩa đã hoàn thành toàn bộ checklist gốc. Các câu hỏi và việc đối chiếu đáp án đã nằm trong 60 phút.

## Nguồn và cách đối chiếu

- Nguồn chính: [GMR arXiv v1, PDF 9 trang](../tmp/2510.02252v1.pdf). Mọi số trang tính từ trang đầu PDF.
- [Checklist](../GMR_READING_CHECKLIST.md): lượt 5 về setup/metric, lượt 6 về bằng chứng, lượt 7 về giới hạn/liên hệ.
- [Bản thảo slide](../PRESENTATION_SLIDE.md): **slide gốc 8–15**, tương ứng **slide rút gọn 7–12**. Trong block này chỉ ghi nội dung để dùng sau; chưa dựng slide.
- Đối chiếu trực quan [trang 6: Table I–II](../tmp/extracted/visuals/page-006.png) và [trang 7: Figure 3–4, Table III](../tmp/extracted/visuals/page-007.png).

## Làm gì trong 60 phút

| Phút | Việc cần làm | Ghi lại vào đâu / cần thu được gì |
| ---: | --- | --- |
| 12 | Đọc chọn lọc **III-A–E, trang 3–4**. Ở III-A–B, lấy tên baseline, nguồn dữ liệu, robot và lưu ý chuyển đổi dữ liệu; ở III-C–E, đọc kỹ điều kiện đánh giá, success, tracking errors và user study. | Một bảng ngắn: **dataset → robot → retargeters → huấn luyện → điều kiện đo → metric**. |
| 12 | Đọc **Table I, trang 6**, caption và đoạn tương ứng trong **V-A–B, trang 5–6**. Chọn hai hàng **Run (stop & go)** và **Dance 5**, chỉ lấy cột **sim2sim**. Xem **Figure 3(c), trang 7** để nhận diện lỗi của GMR. | Một kết quả tốt, một ngoại lệ và loại artifact mà tác giả liên hệ với ngoại lệ đó. |
| 10 | Đọc **III-D, trang 4**, caption và hàng **Mean của E_g-mpbpe** ở **Table II, trang 6**. Đọc đoạn V-A giải thích vì sao success chưa đủ. | Phân biệt **hoàn tất reference** và **bám reference chính xác**; ghi đơn vị, điều kiện đo và bốn số mean. |
| 8 | Đọc **III-E, trang 4**, **V-C và Figure 4, trang 7**. Nhìn legend và cả ba nhóm phương pháp đối chiếu. | User study đo mức giống nguồn; ghi N = 20 và thông điệp so với PHC, ProtoMotions, Unitree. |
| 5 | Đọc **V-D/Table III, trang 7** và **VI. Conclusion, trang 7–8**. | Một lưu ý về start frame, hai giới hạn benchmark và một bài học tiềm năng cho TonyPi. |
| 3 | Nghỉ ngắn. | Dừng đọc, rời mắt khỏi màn hình. |
| 10 | Che đáp án ở cuối note, tự trả lời 8 câu bằng từ khóa; sau đó mở đáp án và kiểm tra trực tiếp nguồn của câu còn sai. Ưu tiên câu 3–6 nếu hết thời gian. | Đánh dấu **đã hiểu / còn vướng**; sửa các nhầm lẫn về điều kiện, đơn vị và phạm vi kết luận. |
| **60** | **Tổng, đã gồm nghỉ và tự kiểm tra.** | |

## Ghi chú đầu ra

- **Setup:** …
- **Kết quả tốt và điều kiện đo:** …
- **Ngoại lệ và artifact:** …
- **Tracking accuracy bổ sung điều gì:** …
- **User study bổ sung điều gì:** …
- **Giới hạn và bài học tiềm năng cho nhóm:** …
- **Chỗ còn vướng + mục/trang cần hỏi:** …

## Hoàn thành block khi

- [ ] Tôi ghi đúng motion, điều kiện, đơn vị và số lượt cho các số dùng trong báo cáo.
- [ ] Tôi phân biệt success, tracking accuracy và user preference.
- [ ] Tôi trình bày được ưu điểm kèm ngoại lệ; không kết luận GMR luôn tốt nhất.
- [ ] Tôi biết chỗ còn vướng và nguồn cần hỏi; không đánh dấu mọi mục checklist gốc là đã xong chỉ vì hết 60 phút.

## Câu hỏi ôn tập

Trả lời ngắn trước khi mở phần đáp án. Việc này là tự kiểm tra đọc hiểu, chưa phải luyện bài nói.

1. Benchmark dùng dữ liệu, robot và bốn nguồn retarget nào? Điều gì được giữ chung, điều gì vẫn cần thận trọng khi so sánh?
2. `sim`, `sim-dr` và `sim2sim` khác nhau ra sao, có bao nhiêu rollout/policy? Điều kiện nào trong ba điều kiện là robot thật?
3. Success được tính thế nào? Vì sao success cao chưa đủ để nói tracking chính xác? Ba tracking errors có đơn vị gì?
4. Hai hàng Run (stop & go) và Dance 5 ở cột sim2sim cho phép kết luận gì? Tác giả liên hệ Dance 5 với artifact nào?
5. Mean global tracking error của GMR trong Table II là bao nhiêu, đo trong điều kiện nào, tốt hơn và kém hơn ai?
6. User study đo gì, có bao nhiêu người? Các phần trăm trong Figure 4 là tỷ lệ gì; GMR có được ưu tiên hơn Unitree không?
7. Table III đổi start frame cho cùng policy hay huấn luyện lại? Nêu một ví dụ số và ý nghĩa của nó.
8. Nêu hai giới hạn và một bài học tiềm năng cho nhóm teleoperation; điều gì chưa được chứng minh cho TonyPi/RGB-D?

## Đáp án đối chiếu

> [!tip] Cách dùng
> Che phần này khi tự trả lời. Đáp án là diễn giải tiếng Việt từ v1 và bản thảo, không phải trích nguyên văn paper.

**1.** LAFAN1, 21 sequences, Unitree G1; PHC, GMR, ProtoMotions và dữ liệu Unitree đã retarget. Cùng framework BeyondMimic, nhưng policy riêng cho từng clip đã retarget. Chuyển đổi BVH sang SMPL/SMPL-X và hậu xử lý PHC là các khác biệt cần lưu ý; thuật toán Unitree là đóng. **Nguồn:** III-A–C, trang 3–4; Table I, trang 6.

**2.** `sim`: IsaacSim tắt domain randomization, 100 rollout; `sim-dr`: IsaacSim bật domain randomization, 4096 rollout; `sim2sim`: MuJoCo/ROS, 100 rollout. **Cả ba đều là mô phỏng.** **Nguồn:** III-C, trang 4; caption Table I, trang 6.

**3.** Success là đi hết reference mà độ cao/hướng anchor body không lệch quá ngưỡng chấm dứt. Hoàn tất vẫn có thể bám lệch, nên cần đọc cùng tracking errors. Global và root-relative body-position errors dùng **mm**; joint-rotation angular error `E_mpjpe` trong v1 dùng **10^-3 rad**. Errors chỉ tính trên frame policy còn hoạt động. **Nguồn:** III-D, trang 4; Table II, trang 6.

**4.** Run (stop & go): GMR 100%, bằng Unitree, cao hơn PHC 74% và ProtoMotions 26%. Dance 5: GMR 51%, ba nhánh còn lại 100%. Vì vậy GMR không luôn tốt nhất. V-B liên hệ Dance 5 với nhảy đột ngột giá trị khớp eo, nhấn mạnh waist roll; Figure 3(c) hiển thị roll/pitch. Phân tích này không phải ablation cô lập nguyên nhân. **Nguồn:** Table I và V-B, trang 6; Figure 3(c), trang 7.

**5.** **104.1 mm**, Mean `E_g-mpbpe`, **sim**, tính từ 100 evaluation rollout/policy. Thấp hơn PHC 247.8 mm và ProtoMotions 139.7 mm, cao hơn Unitree 77.2 mm. Metric đo policy bám reference, không phải trực tiếp human-to-robot pose similarity. **Nguồn:** III-D, trang 4; caption và Table II, trang 6.

**6.** Mức giống chuyển động nguồn, **20 người**. Phần trăm là tỷ lệ **câu trả lời**, không phải tỷ lệ người hoặc success robot. GMR được ưu tiên hơn PHC và ProtoMotions. So với Unitree: 25% chọn GMR, 37% không ưu tiên, 38% chọn Unitree; không nói GMR thắng Unitree. **Nguồn:** III-E, trang 4; V-C/Figure 4, trang 7.

**7.** Cùng policy, đổi start frame khi đánh giá. GMR Walk 2: frame 0 đạt 64%, frame 7 đạt 100% trong sim2sim. Tư thế mở đầu và khả năng robot chuyển an toàn từ default pose tới reference có thể ảnh hưởng kết quả; không suy thành đã huấn luyện lại. **Nguồn:** III-C, trang 4; V-D/Table III, trang 7.

**8.** Hai giới hạn tiêu biểu: chỉ LAFAN1 và G1; đánh giá controller vẫn là mô phỏng/sim2sim. Nhóm có thể **đề xuất kiểm chứng** cách scaling/mapping và đánh giá reference trước controller. Cần kiểm tra phần cứng/dữ liệu riêng; paper này chưa chứng minh depth giúp bao nhiêu hoặc có policy chạy được trên TonyPi. **Nguồn:** III-B–C, trang 3–4; VI, trang 7–8; phần liên hệ là phân tích theo bản thảo slide gốc 14.

## Kiến thức cần nhớ sau khi đọc

### 1. Thiết kế so sánh

- Benchmark có **21 motion sequences từ LAFAN1**, retarget sang **Unitree G1**. So sánh **PHC, GMR, ProtoMotions và dữ liệu đã retarget của Unitree**; tác giả không có thuật toán retarget đóng của Unitree. Nguồn: III-A–C, trang 3–4; Table I, trang 6.
- Dùng **cùng framework BeyondMimic**, nhưng huấn luyện **policy riêng cho từng retargeted clip**; không phải một policy có cùng weights chạy mọi nhánh. Nguồn: III-C, trang 4.
- Cùng framework giúp nghiên cứu tác động của retargeting, nhưng dữ liệu baseline vẫn có khác biệt xử lý: BVH được chuyển sang SMPL/SMPL-X cho PHC/ProtoMotions; PHC có điều chỉnh hậu xử lý độ cao như III-B mô tả. Vì vậy không gọi đây là phép cô lập hoàn hảo từng thành phần GMR. Nguồn: III-B, trang 3–4.

| Điều kiện | Môi trường | Số rollout mỗi policy |
| --- | --- | ---: |
| `sim` | IsaacSim, tắt domain randomization | 100 |
| `sim-dr` | IsaacSim, bật domain randomization | 4096 |
| `sim2sim` | MuJoCo/ROS, vẫn là mô phỏng | 100 |

Nguồn: III-C, trang 4; caption Table I, trang 6.

### 2. Ba loại bằng chứng khác nhau

| Đại lượng | Đọc thế nào |
| --- | --- |
| **Success rate** | Tỷ lệ rollout đi hết reference mà sai lệch **độ cao hoặc hướng của anchor body** không vượt ngưỡng chấm dứt. Đây là tỷ lệ hoàn tất reference theo tiêu chí của benchmark. |
| **E_g-mpbpe** | Sai số vị trí trung bình các body parts trong hệ toàn cục, **mm**, thấp hơn tốt hơn. |
| **E_mpbpe** | Sai số vị trí trung bình các body parts tương đối với root, **mm**, thấp hơn tốt hơn. |
| **E_mpjpe trong v1 này** | Sai số góc trung bình của joint rotations, **10^-3 rad**, thấp hơn tốt hơn. Đọc theo định nghĩa của v1, không đoán đơn vị từ tên viết tắt. |
| **User study** | Người xem so sánh mức giống chuyển động nguồn; đây là cảm nhận về hình thức chuyển động. |

Tracking errors được tính trên **các frame mà policy còn hoạt động**, nên phải diễn giải cùng success rate. Nguồn: III-D–E, trang 4.

### 3. Các bằng chứng cần dùng cho báo cáo

**Table I, cột sim2sim, %, 100 rollout/policy:**

| Motion | PHC | GMR | ProtoMotions | Unitree |
| --- | ---: | ---: | ---: | ---: |
| Run (stop & go) | 74 | 100 | 26 | 100 |
| Dance 5 | 100 | 51 | 100 | 100 |

GMR tốt ở Run (stop & go), nhưng không thắng mọi motion. Tác giả liên hệ Dance 5 với những bước nhảy đột ngột của giá trị khớp eo; phần chữ V-B nhấn mạnh **waist roll**, còn Figure 3(c) vẽ **roll và pitch**. Đây là phân tích trường hợp artifact, không phải một ablation có kiểm soát chứng minh riêng một thành phần gây ra mọi khác biệt. Nguồn: Table I và V-B, trang 6; Figure 3(c), trang 7.

**Table II, Mean E_g-mpbpe, điều kiện sim, mm:**

| PHC | GMR | ProtoMotions | Unitree |
| ---: | ---: | ---: | ---: |
| 247.8 | 104.1 | 139.7 | 77.2 |

GMR thấp hơn PHC và ProtoMotions ở mean này; Unitree còn thấp hơn GMR. Đây là sai số **policy bám reference robot**, không phải sai số trực tiếp giữa skeleton người và robot. Nguồn: III-D, trang 4; caption và Table II, trang 6.

**Figure 4, user study N = 20:**

| Phương pháp đối chiếu với GMR | Chọn GMR | Không ưu tiên | Chọn phương pháp kia |
| --- | ---: | ---: | ---: |
| Unitree | 25% | 37% | 38% |
| PHC | 74% | 8% | 18% |
| ProtoMotions | 63% | 13% | 23% |

Đây là **tỷ lệ câu trả lời**, không phải tỷ lệ người. Các số trên hình là số nguyên; hàng ProtoMotions hiển thị tổng 99%, nên giữ nguyên số gốc thay vì tự chuẩn hóa lại. Người tham gia không được biết tên phương pháp; thứ tự clip được đổi ngẫu nhiên. GMR được ưu tiên hơn PHC/ProtoMotions; không kết luận được ưu tiên hơn Unitree. Nguồn: III-E, trang 4; V-C và Figure 4, trang 7.

### 4. Giới hạn và liên hệ phải giữ đúng

- **Cùng policy, đổi start frame** có thể đổi success. Ví dụ GMR Walk 2 trong sim2sim: **64% ở frame 0, 100% ở frame 7**. Những dấu `*` trong Table I cần đọc cùng V-D; Table III không mô tả huấn luyện lại policy. Nguồn: V-D/Table III, trang 7.
- Phạm vi benchmark: **một nguồn LAFAN1, một robot G1**, controller được đánh giá trong **mô phỏng/sim2sim**. Các tương tác phức tạp với môi trường, vật thể hoặc robot khác còn cần nghiên cứu. Nguồn: III-B–C, trang 3–4; VI, trang 7–8.
- **Liên hệ do người trình bày đề xuất:** nhóm teleoperation có thể học cách xử lý tỷ lệ, giới hạn khớp và tách đánh giá reference khỏi controller. Cần mapping/model phần cứng và kiểm chứng riêng cho TonyPi. Benchmark này chưa cung cấp bằng chứng về lợi ích depth hoặc thành công trên TonyPi. Đối chiếu: bản thảo slide gốc 14 và ghi chú báo cáo; không coi đây là kết quả GMR.
