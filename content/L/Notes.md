# Ghi chú đọc paper — TonyPi / RGB-D / motion retargeting

Đọc tệp này trước để chọn bài và câu hỏi. Sau đó xem `INDEX.md`, dùng `rg` tìm từ khóa trong TXT tương ứng rồi chỉ nạp đoạn/trang cần thiết; không cần đưa toàn bộ khoảng 125 trang vào context. TXT là bản trích xuất để tra cứu, PDF gốc là nguồn đối chiếu khi cần hình, công thức hoặc bảng. Các mốc dưới đây là **trang PDF, đếm từ 1**, không phải số trang in của hội nghị. Ghi chú này tổng hợp lượt đọc đã hoàn thành; số liệu thuộc đúng phiên bản PDF trong thư mục.

## 1. SMPL — `SMPL2015_fixed.pdf`

- Mục tiêu/phương pháp: mô hình cơ thể tham số, kết hợp hình dáng, tư thế và hiệu chỉnh biến dạng theo khớp; đầu ra là mesh/skeleton, có thể làm biểu diễn trung gian trước retargeting.
- Quy mô: 6.890 đỉnh, 72 tham số pose (tr.4). Huấn luyện/đánh giá dùng 1.786 scan của 40 người và dữ liệu CAESAR 1.700 nam, 2.100 nữ (tr.6).
- Kết quả: so sánh SMPL–BlendSCAPE có khác biệt khoảng 0,5 mm trong thí nghiệm bề mặt (Hình 11–12, tr.10); sinh mesh mất 4–7 ms (Hình 14, tr.12).
- Giới hạn: thời gian trên chỉ là sinh mesh, chưa gồm ước lượng từ ảnh hay điều khiển robot; xem tr.14. Từ khóa: `6890`, `BlendSCAPE`, `milliseconds`, `limitations`.

## 2. AMASS — `AMASS.pdf`

- Mục tiêu/phương pháp: chuẩn hóa nhiều kho motion capture vào mô hình cơ thể bằng MoSh++, phục hồi hình dáng, pose và chuyển động mô mềm.
- Bản v1/2019 này có 15 kho, 346 người, 11.451 chuyển động, 2.488,01 phút ≈ 41,47 giờ; văn bản làm tròn 42 giờ (Bảng 1, tr.8). Không dùng số lượng của các bản AMASS phát hành sau để mô tả PDF này.
- Sai số bề mặt MoSh → MoSh++: shape 12,1 → 7,4 mm; pose 10,5 → 8,1 mm; dynamic 10,24 → 7,3 mm (tr.7–8, Hình 6). Đây không phải sai số khớp robot.
- Chi phí: stage I khoảng 25 phút/sequence; stage II 0,5 giây/frame, hoặc 2 giây khi thêm dynamics (tr.11). Tr.12 dùng 16 hệ số shape và 8 dynamic. Tr.3 ghi pose 90D nhưng tr.4 ghi 159 gồm root translation: phải kiểm tra model/file thực tế trước viết parser. Từ khóa: `Table 1`, `2488`, `159`, `dynamic`.

## 3. RGB-D pose cho học tác vụ — `3D Human Pose Estimation in RGBD Images for Robotic Task Learning.pdf`

- Phương pháp: khớp 2D từ RGB, kết hợp depth và CNN 3D để suy ra khớp người, sau đó dựng biểu diễn tác vụ cho PR2.
- Bảng II, tr.4: sai số Captury/hard/MKV lần lượt 11,2/11,6/6,1 cm; lấy depth đơn giản là 14,7/15,2/8,8; RGB-only 22,7/21,9/15,1.
- Không coi đây là ablation cô lập depth: thuật toán và đầu vào giữa các nhánh khác nhau. Tính khả thi IK 95,12–98,92% (Bảng III, tr.6) không đồng nghĩa thành công tác vụ.
- Demo ghi 10 Hz, rồi xử lý graph/GMM offline; chưa chứng minh điều khiển toàn thân trực tiếp. Từ khóa: `Captury`, `Table II`, `feasible`, `GMM`.

## 4. HUMROB — `GenerativemotionReatargetingRGBD.pdf`

- Phương pháp: khớp mô hình bề mặt người mang cấu trúc/giới hạn khớp robot với point cloud RGB-D; xuất góc khớp NAO.
- Camera 30 fps nhưng xử lý Matlab khoảng **3 giây/frame** trên i7 3,6 GHz, RAM 32 GB (tr.10, trang in 51508). Robot NAO V5 chạy chậm theo giả định gần tĩnh.
- Joint tracking trên SMMC10: 32,67 mm, so với Ye 34,02; PDT: 42,23 so với 46,42 (Bảng 2–3, tr.12). Đây là tracking người, chưa phải sai số bắt chước robot. Sai số mesh nam/nữ 18,9/15,5 mm (tr.6–7).
- Chưa có ràng buộc tương tác như tự chạm cơ thể. Từ khóa: `HUMROB`, `3 seconds`, `SMMC`, `PDT`.

## 5. Koenemann — `koenemann14icra.pdf`

- Phương pháp: chuyển động người từ bộ đồ Xsens → scale → IK → điều chỉnh trọng tâm/chân trụ cho NAO. Hữu ích làm baseline hình học có xét thăng bằng.
- Chạy 30 Hz; sai số tay 1,4 cm, chân 1,6 cm qua 10 lần lặp (tr.5–6). Tính toán 3,30 ± 3,57 ms, tối đa 29,21 ms trên 1.000 frame (Bảng I, tr.6).
- Chi phí này không gồm perception thị giác; nguồn là Xsens. Các tư thế tĩnh ổn định không tự chứng minh khả năng bắt chước đi bộ động liên tục. Từ khóa: `Xsens`, `Table I`, `29.21`, `center of mass`.

## 6. Whole-body geometric — `Whole-Body Geometric Retargeting for Humanoid Robots.pdf`

- Phương pháp: IK có ràng buộc bám hướng các đoạn cơ thể, giảm phụ thuộc tỷ lệ người; phối hợp với controller whole-body của iCub.
- IK 200 Hz, controller 100 Hz; iCub 53 DoF, tốc độ đi 0,23 m/s (tr.4–5).
- Khi robot bước, gain retargeting được đặt **0** (tr.6; Hình 11, tr.8). Vì vậy demo không chứng minh vừa đi vừa sao chép toàn thân liên tục.
- Giá trị cho TonyPi là cách dùng hướng đoạn và giới hạn khớp; phải đánh giá riêng phần bước chân, thăng bằng và độ trễ camera. Từ khóa: `200`, `retargeting gain`, `walking`, `0.23`.

## 7. GMR — `2510.02252v1.pdf`

- Phương pháp: rest pose, scale cục bộ không đồng đều/root đồng đều, IK hai giai đoạn với Mink, warm start và giới hạn khớp; nghiên cứu ảnh hưởng chất lượng retargeting đến policy tracking.
- Benchmark: 21 sequence LAFAN1 dài 5,5–130,5 giây trên G1. Global tracking error GMR/PHC/Proto/Unitree là 104,1/247,8/139,7/77,2 mm (Bảng II, tr.6): GMR không thấp nhất mọi chỉ số.
- Run-stop-go sim-to-sim đạt 100% so với PHC 74%, Proto 26%; Dance5 của GMR chỉ 51%.
- Giới hạn: benchmark trên một robot và mô phỏng; chưa có kiểm chứng robot thật hoặc depth. Từ khóa: `Table II`, `104.1`, `Dance5`, `Mink`.

## 8. H2O — `H2O_paper.pdf`

- Phương pháp: retarget/lọc chuyển động AMASS theo tính khả thi, học RL cho H1, rồi điều khiển từ người qua RGB.
- Bảng III, tr.6: trên 10.000 chuyển động retarget chưa lọc, success 72,5%, root-relative MPJPE 91,7 mm, global MPJPE 166,7 mm. Success theo ngưỡng lệch ≤ 0,5 m là chỉ số tracking mô phỏng, không phải tỷ lệ hoàn thành tác vụ thật.
- Người được quan sát bằng RGB 30 Hz, nhưng trạng thái robot còn dùng **MoCap 50 Hz** (tr.6–7). Không mô tả là hệ hoàn toàn chỉ-camera.
- Bài nhấn mạnh lọc chuyển động khả thi. Từ khóa: `Table III`, `MoCap`, `91.7`, `0.5`.

## 9. OmniH2O — `OmniH2O_paper.pdf`

- Phương pháp: teacher–student/DAgger, lịch sử trạng thái, mục tiêu đầu–hai tay; mở rộng teleoperation, bàn tay, thu demonstration và tự hành.
- Bảng 1, tr.6: student 94,10% success, root/global MPJPE 77,82/141,11 mm trên khoảng 14.000 chuyển động tăng cường; H2O baseline cùng dataset đạt 87,52%, không phải 72,5% từ bài gốc.
- Bảng 2, tr.6: 20 động tác đứng có global error 87,33 → 47,94 mm, root 53,32 → 41,87. Bảng 3, tr.8: DDPM trung bình 8/10, BC 1/10 qua bốn tác vụ.
- OmniH2O-6: 40 phút, sáu tác vụ, RGB-D 30 Hz; policy 50 Hz/20 ms (Phụ lục A). Vẫn cần root odometry. Từ khóa: `94.10`, `odometry`, `DDPM`, `OmniH2O-6`.

## 10. HumanPlus — `HumanPlus.pdf`

- Phương pháp: controller bắt chước chuyển động người và policy thị giác học tác vụ từ demonstration; tham khảo tốt cho khâu thu dữ liệu.
- WHAM 25 fps, HaMeR 10 fps trên RTX 4090 (tr.5); không suy ra tốc độ trên máy TonyPi.
- Bảng 5, tr.9: 25–40 demonstration/tác vụ, 10 lần thử/tác vụ. Thành công robot: gấp 100%, sắp xếp 90%, gõ AI 80%, chào 90%, kho hàng 90%, mang giày + đi 60%.
- Đây là kết quả tác vụ cụ thể với mẫu thử nhỏ; hệ dùng RGB, chưa chứng minh lợi ích depth. Từ khóa: `Table 5`, `WHAM`, `HaMeR`, `Warehouse`.

## Quy tắc dùng lại

Phân biệt surface/mesh error, joint tracking, root-relative/global MPJPE, success mô phỏng và success robot thật. Chỉ so sánh trực tiếp khi cùng dữ liệu, định nghĩa và protocol. Với đề tài TonyPi, lợi ích depth vẫn cần thí nghiệm RGB/RGB-D có kiểm soát; đo riêng perception, retargeting, truyền lệnh và đáp ứng robot. Mọi tần số camera/IK/policy ở trên thuộc từng thành phần, không tự bằng độ trễ toàn pipeline.
