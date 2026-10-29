---
duration_minutes: 120
phase: reading
status: todo
paper_version: arxiv-2510.02252v1
tags:
  - GMR
  - paper-reading
  - presentation-preparation
---

# Block 02 - Đọc kỹ phương pháp GMR - 120 phút

[[00_START_HERE|Về mục lục]] · Trước: [[01_READ_OVERVIEW]] · Tiếp: [[03_READ_EVIDENCE]]

## Mục tiêu và nguồn đối chiếu

Đọc xong phải mô tả được **đầu vào, xử lý, đầu ra và mục đích của năm bước GMR**, phân biệt được hai giai đoạn IK và cách xử lý một chuỗi chuyển động. Block này dành cho đọc, ghi chú và tự kiểm tra; dựng slide ở block 04.

- **Nguồn chính:** [GMR arXiv v1, PDF 9 trang](../tmp/2510.02252v1.pdf), **Section IV, trang 4-5**. Mọi số trang đếm từ đầu PDF.
- **Hình/công thức cần mở:** [Figure 2, trang 4](../tmp/extracted/visuals/page-004.png) và [Eq. 2-6, trang 5](../tmp/extracted/visuals/page-005.png).
- **Đối chiếu checklist:** [GMR_READING_CHECKLIST.md](../GMR_READING_CHECKLIST.md), **lượt 3 và lượt 4**.
- **Đối chiếu bản thảo:** [PRESENTATION_SLIDE.md](../PRESENTATION_SLIDE.md), **slide gốc 5-7**; tương ứng **slide rút gọn 5-6**. Chỉ dùng bảng gộp 12 slide ở cuối bản thảo để đổi số; không coi slide gốc 6 là slide rút gọn 6.

> [!important] Phạm vi trong 120 phút
> Ưu tiên cơ chế và ý nghĩa các thành phần. Checklist có 12 câu của lượt 3-4; mười câu bên dưới gộp các chủ đề chính để tự kiểm tra trong quỹ thời gian này. Đây là kế hoạch đọc rút gọn, không đồng nghĩa đã hoàn thành mọi chi tiết toán trong checklist. Với chỗ chưa chắc, ghi câu hỏi cụ thể và nguồn cần xem lại.

## Làm lần lượt trong 120 phút

| Việc | Phút | Làm gì cụ thể | Ghi lại được gì |
| --- | ---: | --- | --- |
| Chuẩn bị khái niệm | 5 | Mở Figure 2 và trang 5. Phân biệt **vị trí**, **hướng**, **root**, **key body**, **FK/IK** bằng bảng thuật ngữ bên dưới. | Một tư thế minh họa: người đứng yên và giơ một tay. Ghi rõ đây là ví dụ học, không phải kết quả paper. |
| Matching và alignment | 15 | Đọc **Step 1** ở trang 4-5 và **Step 2** ở trang 5. Xác định ai thiết lập mapping, vì sao cần offset hướng và khi nào có offset vị trí. | Hai dòng: “matching ghép phần nào” và “alignment chỉnh cái gì”. |
| Local/root scaling | 20 | Đọc **Step 3, Eq. 2-3**, trang 5. Dùng ngón tay tách phần vị trí body tương đối với root và phần root trong không gian. Đối chiếu ký hiệu trực tiếp với ảnh. | Bảng ký hiệu; một câu phân biệt local scaling với root translation scaling. |
| Nghỉ | 5 | Rời màn hình, nghỉ mắt. | Không thêm đầu việc. |
| Hai giai đoạn IK | 30 | Đọc **Step 4-5, Eq. 4-6**, trang 5. So sánh tập body có mục tiêu hướng, tập body có mục tiêu vị trí, trọng số, khởi tạo và giới hạn. Eq. 5 ưu tiên vai trò giải vận tốc để cập nhật cấu hình. | Bảng so sánh hai giai đoạn bên dưới bằng lời của mình. |
| Motion sequence | 10 | Đọc **Application to Motion Sequences**, trang 5. Tách warm start từng frame khỏi sửa độ cao sau cả sequence. | Ba mũi tên: frame trước → khởi tạo frame sau → hậu xử lý toàn chuỗi. |
| Nghỉ | 5 | Nghỉ ngắn trước phần tự kiểm tra. | Không thêm đầu việc. |
| Ôn tập cuối block | 20 | Che phần đáp án. Dành **12 phút** trả lời mười câu; dành **8 phút** mở đáp án và đối chiếu đúng đoạn nguồn. Câu chưa đủ ý đánh dấu để block ôn tập xử lý. | Danh sách câu đã hiểu/chưa hiểu; không đánh dấu hoàn thành chỉ vì đã đọc đáp án. |
| Chốt kiến thức | 10 | Viết bảng năm bước với cột **input → xử lý → output → vì sao cần**. Dùng tư thế giơ tay để kiểm tra tính liên tục của luồng. Ghi tối đa ba chỗ vướng cụ thể. | Một bảng phương pháp và nhật ký chỗ vướng; chưa làm slide. |
| **Tổng** | **120** | Đã gồm **10 phút nghỉ**, câu hỏi và kiểm tra đáp án. | |

## Bảng thuật ngữ để dùng khi đọc

| Thuật ngữ | Cách hiểu ngắn trong block này |
| --- | --- |
| Key body | Phần cơ thể được chọn làm mốc bám vị trí/hướng, ví dụ torso, đầu, tay hoặc bàn chân. Không đồng nghĩa mọi joint. |
| Root pose | Vị trí và hướng của gốc cơ thể. Phân biệt root đi trong không gian với một body chuyển động tương đối so với root. |
| FK | Từ cấu hình robot, tính vị trí/hướng các body. |
| IK | Tìm cấu hình robot để giảm sai lệch so với các mục tiêu vị trí/hướng trong những ràng buộc đã đặt. |
| `q` | Các tọa độ tổng quát: **root translation, root rotation và joint values**, không chỉ là vector góc khớp. |
| `q_dot` | Vận tốc tổng quát mà differential IK giải để khi tích phân sẽ làm giảm cost. |
| `q_min/q_max` | Cách gọi dễ đọc cho các giới hạn `q⁻/q⁺` được dùng trong bài. Khi trích công thức, giữ ký hiệu gốc. |
| Weight | Trọng số thể hiện mức ưu tiên tương đối giữa các sai số. |

### Những ký hiệu scaling cần đối chiếu trực tiếp

| Ký hiệu trong Eq. 2-3 | Ý nghĩa theo đoạn Step 3 |
| --- | --- |
| `h` | Chiều cao skeleton người nguồn. |
| `h_ref` | Chiều cao tham chiếu được giả định khi thiết lập các scale factors. Không tự đổi nghĩa thành chiều cao robot. |
| `s_b` | Scale factor riêng cho key body `b`. |
| `s_root` | Scale factor dùng cho root translation. |
| `p_source`, `p_target` | Vị trí ở dữ liệu nguồn và vị trí mục tiêu sau scaling. |

**Đọc Eq. 2 bằng hai phần:** phần thứ nhất scale vị trí body nguồn tương đối với root; phần thứ hai scale root translation rồi đưa vị trí về không gian toàn cục. Trong đúng bản v1, cả hai phần có hệ số `h/h_ref`. Khi body là root, phần tương đối bằng không và được Eq. 3 rút gọn. Các scale cục bộ có thể khác nhau giữa key bodies; root translation dùng tỷ lệ đồng đều. Đoạn Step 3 nhấn mạnh việc scale root đồng đều giúp tránh tạo foot sliding. Đây là nhận xét của tác giả; không biến thành bảo đảm loại hết mọi artifact.

### Bảng so sánh hai giai đoạn IK cần tự viết lại

| Nội dung | Giai đoạn 1 - Step 4, Eq. 4 | Giai đoạn 2 - Step 5, Eq. 6 |
| --- | --- | --- |
| Mục tiêu hướng | Hướng các key bodies trong mapping `M`. | Tiếp tục xét hướng các key bodies. |
| Mục tiêu vị trí | Chỉ end-effectors trong `M_ee`: **tay và chân**. | **Tất cả key bodies** trong mapping. |
| Trọng số | Bộ trọng số giai đoạn 1. | Bộ trọng số khác cho giai đoạn 2. |
| Khởi tạo | Phần root ban đầu lấy vị trí đã scale và yaw của root người; với sequence, dùng kết quả frame trước làm khởi tạo Step 4. | Lấy nghiệm giai đoạn 1 làm điểm bắt đầu. |
| Ràng buộc | Giới hạn giá trị khớp theo bài; đôi khi tác giả thu hẹp phạm vi để tránh động tác không tự nhiên. | Cũng chịu các giới hạn đã đặt. |

> [!warning] Điểm chưa nên tự suy diễn
> Bản v1 có cách ghi cần thận trọng ở định nghĩa sai số orientation, cách gọi `e(q)` quanh Eq. 5 và ký hiệu trong Eq. 6. Mục tiêu học ở đây là hiểu đúng vai trò của sai số, Jacobian `J`, ma trận trọng số `W`, vận tốc tổng quát và giới hạn sau cập nhật. Không tự viết lại định nghĩa toán hoặc khẳng định đã chứng minh công thức từ một ký hiệu khó hiểu. `Delta t` được bài nói rõ là tham số solver, **không nhất thiết bằng khoảng thời gian giữa hai frame nguồn**. Nguồn: Step 4-5, trang 5; lưu ý phụ lục 16 trong bản thảo slide.

## Kiểm tra hoàn thành và ghi chỗ vướng

- [ ] Tôi phân biệt được matching, alignment và scaling, không gộp ba bước thành “đổi kích thước”.
- [ ] Tôi chỉ ra được hai phần local/root trong Eq. 2 và ý nghĩa các hệ số chính.
- [ ] Tôi giải thích được khác nhau giữa hai giai đoạn IK, bao gồm vị trí tay/chân ở giai đoạn đầu.
- [ ] Tôi phân biệt được xử lý từng frame và hậu xử lý toàn sequence.
- [ ] Tôi đã tự trả lời trước khi mở đáp án, và đánh dấu trung thực câu còn vướng.

| Chỗ chưa hiểu cụ thể | Nguồn cần đối chiếu | Cần hỏi/kiểm tra điều gì |
| --- | --- | --- |
| | | |
| | | |
| | | |

Nếu một điểm toán còn chưa chắc, giữ nguyên trong bảng này thay vì tự viết một đáp án suy đoán. Chuyển sang [[03_READ_EVIDENCE]] sau khi đã dùng hết 120 phút; trạng thái “đã dùng thời gian” và “đã hiểu” được theo dõi riêng bằng checklist trên.

## Câu hỏi ôn tập cuối block

Che các đáp án bên dưới trước khi làm. Mỗi câu cần trả lời bằng lời của mình; nếu chỉ nhớ tên bước nhưng không nói được mục đích, đánh dấu chưa chắc.

1. **Matching:** key body là gì? Mapping do ai xác định, và được dùng cho việc gì?
2. **Alignment:** vì sao ghép đúng bàn tay người với bàn tay robot vẫn chưa đủ? Step 2 điều chỉnh gì?
3. **Scaling:** Eq. 2 có hai phần vị trí nào? Khi người đứng yên và giơ tay, phần nào mô tả tay so với root?
4. **Ký hiệu/tỷ lệ:** `h`, `h_ref`, `s_b`, `s_root` là gì? Vì sao cần scale khác nhau theo body và scale root đồng đều?
5. **FK/IK và biến:** FK khác IK thế nào? Trong bài này `q` có những thành phần nào?
6. **Hai giai đoạn:** cả hai cùng xét hướng hay không? Những vị trí nào được xét ở mỗi giai đoạn? Trọng số và khởi tạo khác thế nào?
7. **Differential IK:** Eq. 5 tìm `q` hay `q_dot`? `J`, `W` và `Delta t` giữ vai trò gì ở mức trực giác?
8. **Sequence:** frame trước được dùng ở đâu? Sửa độ cao diễn ra trước hay sau khi retarget toàn chuỗi?
9. **Giới hạn kết luận:** joint limits và hai giai đoạn có bảo đảm không tự va chạm, giữ cân bằng hoặc tìm tối ưu toàn cục không?
10. **Ví dụ xuyên suốt:** với người đứng yên giơ một tay, hãy đi lần lượt năm bước và nói đầu ra cuối cùng dùng làm gì.

## Đáp án đối chiếu

> [!answer]- 1. Key body, mapping và người thiết lập
> Key body là body được chọn làm mốc tương ứng để bám vị trí/hướng, thường gồm torso, đầu, chân, bàn chân, tay và bàn tay. Người dùng xác định mapping `M` giữa skeleton nguồn và skeleton robot; mapping giúp thiết lập bài toán IK. Người dùng còn có thể cung cấp trọng số sai số vị trí/hướng. Nguồn: Section IV, Step 1, trang 4-5.

> [!answer]- 2. Rest-pose alignment
> Cùng tên body không đảm bảo hệ trục và hướng chuẩn trùng nhau. Step 2 thêm offset hướng để body người khớp hướng body robot khi cả hai ở rest pose; trong một số trường hợp còn thêm offset vị trí cục bộ. Bước này chuẩn hóa mục tiêu trước scaling/IK, không thay thế việc xử lý tỷ lệ và giới hạn khớp. Nguồn: Step 2, trang 5.

> [!answer]- 3. Hai phần trong Eq. 2
> Phần thứ nhất dùng vị trí body nguồn **trừ vị trí root nguồn**, rồi scale bằng hệ số chung và scale riêng của body. Phần thứ hai đưa vào root translation đã scale. Với ví dụ người đứng yên giơ tay, biến đổi vị trí tay tương đối với root nằm ở phần thứ nhất; ví dụ này chỉ minh họa cách đọc công thức. Nguồn: Step 3, Eq. 2-3, trang 5.

> [!answer]- 4. Chiều cao và scale factors
> `h` là chiều cao skeleton người nguồn; `h_ref` là chiều cao tham chiếu khi thiết lập scale factors; `s_b` là hệ số của body; `s_root` là hệ số của root. Các body có thể cần tỷ lệ khác nhau để phản ánh khác biệt tỷ lệ phần trên/phần dưới cơ thể. Bài nhấn mạnh root translation phải scale đồng đều để tránh tạo foot sliding. Không tự thay tỷ lệ `h/h_ref` của bản v1 bằng một tỷ lệ suy đoán khác. Nguồn: Step 3, Eq. 2-3, trang 5.

> [!answer]- 5. FK, IK và q
> FK tính vị trí/hướng body từ cấu hình; IK tìm cấu hình để bám mục tiêu. `q` trong GMR gồm root translation, root rotation và joint values. Do đó gọi `q` đơn giản là “các góc khớp” sẽ thiếu root pose. Nguồn: Step 4, trang 5.

> [!answer]- 6. So sánh hai giai đoạn
> Cả hai xét hướng key bodies. Giai đoạn 1 chỉ xét thêm vị trí end-effectors là tay/chân; giai đoạn 2 xét thêm vị trí **mọi key body**. Giai đoạn 2 dùng trọng số khác và nghiệm giai đoạn 1 làm khởi tạo. Cả hai giữ các giới hạn đã đặt. Không đọc tên Step 4 rồi kết luận giai đoạn 1 chỉ có rotation. Nguồn: Step 4-5, Eq. 4 và 6, trang 5.

> [!answer]- 7. Vai trò differential IK
> Solver giải `q_dot`, là vận tốc tổng quát, để khi tích phân sẽ giảm cost thay vì giải trực tiếp một cấu hình tối ưu cuối cùng trong một bước. Ở mức trực giác, `J` liên hệ thay đổi cấu hình với thay đổi sai số; `W` thể hiện trọng số; ràng buộc kiểm tra cấu hình sau bước cập nhật nằm trong giới hạn. `Delta t` là tham số solver và không nhất thiết là khoảng thời gian giữa frame nguồn. Cách ghi chính xác của `e(q)` và orientation error trong v1 cần đọc thận trọng; câu trả lời này diễn giải vai trò, không phải suy diễn đầy đủ công thức. Nguồn: Step 4, Eq. 5 và đoạn giải thích, trang 5.

> [!answer]- 8. Warm start và sửa độ cao
> Kết quả retarget frame trước làm initial guess cho Step 4 ở frame tiếp theo. Sau khi retarget xong cả motion, tác giả dùng FK để lấy độ cao các body theo thời gian và trừ độ cao nhỏ nhất khỏi global translation để sửa floating/ground penetration. Đây là hai công đoạn khác nhau; không suy ra toàn pipeline chỉ dùng thông tin của frame hiện tại. Nguồn: Application to Motion Sequences, trang 5.

> [!answer]- 9. Giới hạn của các ràng buộc
> Không có các bảo đảm đó từ các mục tiêu/ràng buộc đang nêu. Joint limits giữ giá trị khớp trong phạm vi; chúng không tự đảm bảo cân bằng động lực học hoặc tránh tự va chạm. Tác giả dùng hai giai đoạn nhằm tránh vấn đề cực tiểu cục bộ, nhưng không chứng minh luôn tìm được tối ưu toàn cục. Đây là giới hạn suy luận từ phạm vi bài toán, không phải một kết quả thí nghiệm bổ sung. Nguồn đối chiếu: Step 4-5, trang 5; phần “Phải giải thích được” của slide gốc 7 trong bản thảo.

> [!answer]- 10. Ví dụ giơ tay qua năm bước
> (1) Ghép key bodies tương ứng, gồm tay và torso. (2) Căn chỉnh offset hướng ở rest pose và offset vị trí cục bộ nếu cần. (3) Scale mục tiêu vị trí từng body tương đối với root và root translation. (4) Giải IK cho hướng key bodies và vị trí tay/chân, có giới hạn. (5) Dùng nghiệm đó tinh chỉnh hướng và vị trí mọi key body với trọng số khác. Đầu ra một pose là root pose và joint values robot; lặp theo sequence tạo reference motion. Reference chưa đồng nghĩa lệnh điều khiển cuối cùng hoặc robot đã thực hiện thành công. Đây là ví dụ diễn giải để học, không phải motion được định lượng trong paper. Nguồn: Figure 2, trang 4; Section IV, trang 4-5.

## Kiến thức cần nhớ sau khi đọc

- **Mapping do người dùng thiết lập** giữa các key bodies người và robot; có thể cung cấp trọng số vị trí/hướng.
- **Alignment** xử lý offset hướng ở rest pose, đôi khi thêm offset vị trí cục bộ. Nó không tự giải quyết mọi khác biệt tỷ lệ và giới hạn khớp.
- **Local scaling** điều chỉnh mục tiêu theo từng body; **uniform root scaling** xử lý root translation. Không tự diễn giải non-uniform local scaling thành ba tỷ lệ x/y/z tùy ý cho mọi bộ phận.
- **IK tìm cả root pose lẫn giá trị khớp** để giảm sai số; bài dùng hai giai đoạn và Mink differential IK.
- Giai đoạn đầu có **hướng key bodies và vị trí tay/chân**; giai đoạn sau có **hướng và vị trí mọi key body**, dùng trọng số khác và nghiệm trước làm khởi tạo.
- Warm start dùng kết quả **frame trước** cho frame sau; sửa độ cao dùng thông tin **sau khi đã retarget cả chuỗi**. Cần nêu cả hai khi bàn về xử lý online/offline.
- Có giới hạn khớp **không đủ để kết luận** reference luôn ổn định động lực học, không tự va chạm hoặc luôn khả thi để controller thực hiện.
- Hai giai đoạn là thiết kế được tác giả dùng nhằm tránh vấn đề cực tiểu cục bộ; **không phải bảo đảm tìm tối ưu toàn cục**.
