# I.1 Introduction:
## Ý chính:
- Muốn robot chuyển động tốt, ta có thể cho nó học trực tiếp từ chuyển động người. Bởi lẽ humanoid có cấu trúc "tương đối" giống con người, các nghiên cứu được tham chiếu trong bài này đã tận dụng **Dữ liệu chuyển động người 3D** làm mẫu để huấn luyện robot (Motion caputure, Human motion recovery from video).
	- **"Generalize to real-worl environments"**
- Nhưng thực tế người và robot không cùng "cơ thể": đó là **"embodiment gap"**
	- Khác biệt:
		- Chân ngắn hơn.
		- Giới hạn khớp/servo.
		- Khối lượng phân bổ khác.

#### Vì vậy, cách làm phổ biến (Lúc bài báo này published) là retargeting trước, rồi dùng RL để học điều khiển:

- **Chuyển động người → kinematic retargeting → chuyển động tham chiếu của robot → RL → policy điều khiển robot.**
	- Kinematic retargeting: Chuyển chuyển động của người thành tư thế phù hợp với robot.
	- Đầu ra là reference motion (Tức các chuỗi chuyển động robot được yêu cầu làm theo)
	- Sau đó RL học một policy - bộ điều khiển, để robot thực hiện chuyển động trong môi tường vật lý.
	=> Nhưng chưa đảm bảo được robot sẽ thực hiện ổn định. Khác biệt được nhắc tới ở trên.

#### Vậy vấn đề là gì? Đó là dữ liệu sau retargeting thường vẫn chứa lỗi:

- Những lỗi này trong bài gọi là **retargeting artifacts**:
	-  Foot sliding
	-  Ground penetration
	-  Self-penetration
-  Và cách xử lý thường gặp: Vẫn dùng dữ liệu có lỗi để policy học cách xử lý hoặc loại những retarget kém.

- Hãy tiếp tục ví dụ bước sang bên. Giả sử reference yêu cầu bàn chân robot đi xuống dưới mặt sàn. Policy lúc này phải đáp ứng hai yêu cầu mâu thuẫn:

> 	Bám vị trí bàn chân trong reference, đồng thời tuân theo vật lý vì mặt sàn không cho chân xuyên qua.

- Policy có thể phải lệch khỏi reference để tránh ngã hoặc tránh va chạm. Vì vậy, reference kém khiến bài toán học điều khiển khó hơn.

#### Trong những nghiên cứu trước, ta có thể bù cho vấn đề này bằng nhiều công sức điều chỉnh.

| Khái niệm                               | Hiểu đơn giản                                                                               |
| --------------------------------------- | ------------------------------------------------------------------------------------------- |
| **Reward engineering / reward shaping** | Thiết kế và điều chỉnh cách thưởng–phạt để hướng policy đến hành vi mong muốn.              |
| **Domain randomization**                | Thay đổi điều kiện trong quá trình huấn luyện để policy chịu được sự khác biệt khi sử dụng. |
#### Từ đó tác giả đưa ra giả thuyết:

> Nếu đầu tư đủ công sức vào thiết kế reward và domain randomization, ta có thể khiến policy bù được phần lớn ảnh hưởng của lỗi retargeting. Nhưng khi không dành nhiều công sức điều chỉnh như vậy, chất lượng chuyển động sau retargeting sẽ ảnh hưởng rõ rệt đến kết quả của policy.

Có hai điểm cần giữ đúng:
- **“Mitigated or removed”** nên hiểu trong ngữ cảnh khả năng policy xử lý và giảm biểu hiện/tác động của lỗi. Các bước huấn luyện đó không tự động sửa sạch file chuyển động tham chiếu.
- Đây là **giả thuyết tác giả đặt ra để kiểm tra**, chưa phải kết luận đã được chứng minh tại đoạn này.

# I.2 Introduction:

## So sánh cách retargeting khác nhau

| Đối tượng               | Vai trò                                                                                       |
| ----------------------- | --------------------------------------------------------------------------------------------- |
| **PHC**                 | Phương pháp retargeting đã được nhiều nghiên cứu sử dụng.                                     |
| **ProtoMotions**        | Phương pháp được dùng trong các nghiên cứu chuyển động động, khó.                             |
| **GMR**                 | Phương pháp mới mà paper đề xuất.                                                             |
| **Dữ liệu của Unitree** | Chuyển động đã được retarget bằng quy trình không công khai, dùng làm mốc so sánh chất lượng. |
***Tác giả đánh giá các phương pháp hiện có, đề xuất phương pháp mới để xử lý vấn đề họ tìm thấy..***

## Vấn đề được chú ý tới: cách điều chỉnh tỷ lệ cơ thể - Scaling

Người và robot có chiều dài tay, chân, thân khác nhau rõ rệt. Trước khi tìm tư thế robot tương ứng, ta phải điều chỉnh chuyển động nguồn theo kích thước robot phù hợp.

Ví dụ minh họa: người bước một khoảng phù hợp với chân người, nhưng robot có chân ngắn hơn. Nếu điều chỉnh tỷ lệ không phù hợp, quan hệ giữa chuyển động thân và vị trí bàn chân có thể bị sai, tạo ra hiện tượng trượt chân hoặc xuyên sàn.

Tác giả cho rằng cách PHC và ProtoMotions xử lý scaling gây ra một số artifacts ảnh hưởng đến policy.

GMR được giới thiệu với hai ý chính:
- **Non-uniform local scaling:** điều chỉnh tỷ lệ cục bộ theo các phần cơ thể, cho phép dùng những hệ số khác nhau.
- **Two-stage optimization:** sau khi scale, dùng quá trình tối ưu hai giai đoạn để tìm chuyển động robot bám theo mục tiêu đã điều chỉnh.

Introduction mới giới thiệu hướng xử lý; cách scale cụ thể và hai giai đoạn tối ưu sẽ được giải thích ở phần phương pháp.

## Tác giả dùng BeyondMimic: "To isolate the impact of retargeting methos...."

Có thể hình dung thí nghiệm như sau:

> Cùng một chuyển động người → tạo các reference bằng những cách retargeting khác nhau → huấn luyện policy bằng cùng framework → so sánh kết quả.

## Đánh giá cả khả năng thực hiện và mức độ giống chuyển động người.

Tác giả chọn **21 chuỗi từ LAFAN1**, với độ dài mà Introduction mô tả làm tròn từ khoảng 5 giây đến 2 phút.

Các câu hỏi đánh giá cần được phân biệt:

| Câu hỏi                                                        | Cách đánh giá                  |
| -------------------------------------------------------------- | ------------------------------ |
| Policy có thực hiện được hết chuỗi không?                      | **Success rate**               |
| Robot bám reference chính xác đến đâu?                         | **Tracking error**             |
| Chuyển động sau retargeting còn giống chuyển động người không? | **User study về faithfulness** |
## Những kết quả chính
Họ nhận thấy phần lớn chuyển động có thể được học bằng các nguồn dữ liệu retargeting khác nhau. Tuy nhiên, một số artifacts khiến việc học khó hơn, thậm chí khiến policy không học thành công ở một số trường hợp.

Ba lỗi được nhấn mạnh là:
- **Foot penetration:** chân xuyên sàn.
- **Self-intersection:** các phần cơ thể xuyên nhau.
- **Abrupt velocity spikes:** vận tốc thay đổi đột ngột; chẳng hạn góc khớp nhảy mạnh trong một khoảng thời gian rất ngắn.

Những trường hợp đó hỗ trợ lập luận: **khi không dùng nhiều công sức điều chỉnh reward để bù, lỗi trong reference có thể làm giảm chất lượng policy**.

Tác giả còn nhắc đến **initial frame — frame đầu tiên của reference**. Nếu chuỗi bắt đầu ở một tư thế mà robot khó đạt tới an toàn, policy có thể thất bại ngay khi bắt đầu, bất kể phương pháp retargeting.

Ví dụ minh họa: reference mở đầu ngay ở một tư thế chống một chân rất khó. Robot phải bắt đầu bám từ tư thế đó, nên quá trình khởi động có thể quyết định thành công hay thất bại.

Cuối đoạn, họ cho biết GMR đạt kết quả gần dữ liệu Unitree về **độ trung thành với chuyển động nguồn và tỷ lệ policy thành công**, đồng thời nhìn chung tốt hơn hai phương pháp mã nguồn mở được so sánh. Đây là nhận định tổng thể trong benchmark; phần kết quả sẽ cho thấy cả những trường hợp ngoại lệ.

## Paper chốt lại hai đóng góp.

- **Đóng góp về phương pháp:** đề xuất GMR để tạo chuyển động tham chiếu chất lượng cao từ nhiều loại chuyển động người.
- **Đóng góp về nghiên cứu thực nghiệm:** đánh giá có hệ thống chất lượng reference sau retargeting ảnh hưởng thế nào đến policy bám chuyển động của humanoid.

Xuất hiện trong bài báo cáo: **GMR làm retargeting như thế nào**, và **tác giả dùng bằng chứng gì để cho thấy chất lượng retargeting thực sự quan trọng**.