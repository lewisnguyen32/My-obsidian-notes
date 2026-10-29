# Vai trò của chuyển đổi chuyển động — GMR cho bám chuyển động ở robot hình người

**Tên gốc:** *Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking*.

**Tác giả:** João Pedro Araújo†, Yanjie Ze†, Pei Xu†, Jiajun Wu*, C. Karen Liu* — Đại học Stanford.

† Đóng góp ngang nhau. * Đồng hướng dẫn.

**Nguồn và phiên bản:** [arXiv:2510.02252v1](https://arxiv.org/abs/2510.02252v1), ngày 02/10/2025, PDF 9 trang. [PDF dùng để dịch](<D:/Projects/iTwinLab/Physical AI/REPORT_2026-10-30/tmp/2510.02252v1.pdf>).

**Ghi công và thay đổi:** Bản gốc do các tác giả trên công bố theo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Đây là bản dịch tiếng Việt không chính thức do Codex biên soạn ngày 28/10/2026, chuyển sang Markdown; không hàm ý các tác giả đã phê duyệt bản dịch. Các mục nội dung, công thức (1)–(6), số liệu trong Bảng I–III và chú thích Hình 1–4 được giữ để đối chiếu. Tên bài và thông tin xuất bản trong danh mục tham khảo giữ bằng ngôn ngữ gốc. Bảng I được tách thành ba bảng theo điều kiện đánh giá, Bảng II tách theo chỉ số; số liệu không thay đổi. Ghi chú của người dịch, nếu có, được đánh dấu riêng.

**Quy ước thuật ngữ:** *motion retargeting* được dịch là **chuyển đổi chuyển động** và đôi khi giữ từ **retargeting**; *motion tracking* là **bám chuyển động**; *policy* là **chính sách điều khiển**; *reference motion* là **chuyển động tham chiếu**; *artifact* là **lỗi phát sinh**; *root* là **gốc của mô hình**. Thuật ngữ tiếng Anh được giữ ở những chỗ giúp tra cứu.

## Tóm tắt

Các chính sách bám chuyển động của robot hình người đóng vai trò trung tâm trong việc xây dựng các pipeline teleoperation (điều khiển từ xa) và bộ điều khiển phân cấp. Tuy nhiên, chúng đối mặt với một thách thức căn bản: sự khác biệt về cấu trúc cơ thể giữa người và robot hình người (*embodiment gap*). Các cách tiếp cận hiện nay xử lý khác biệt này bằng cách chuyển đổi dữ liệu chuyển động người sang cấu trúc cơ thể của robot, sau đó huấn luyện các chính sách học tăng cường (*reinforcement learning*, RL) để bắt chước các quỹ đạo tham chiếu đó. Tuy nhiên, những lỗi phát sinh trong quá trình retargeting, chẳng hạn trượt chân, các bộ phận cơ thể xuyên vào nhau và chuyển động bất khả thi về vật lý, thường vẫn được giữ trong quỹ đạo tham chiếu và để cho chính sách RL tự khắc phục.

Mặc dù các công trình trước đã cho thấy khả năng bám chuyển động, chúng thường cần thiết kế hàm thưởng và ngẫu nhiên hóa miền ở mức đáng kể để thành công. Trong bài này, chúng tôi đánh giá có hệ thống ảnh hưởng của chất lượng retargeting tới hiệu năng chính sách khi hạn chế việc tinh chỉnh hàm thưởng quá mức. Để xử lý các vấn đề được xác định ở những phương pháp retargeting hiện có, chúng tôi đề xuất một phương pháp mới mang tên **General Motion Retargeting (GMR)**. Chúng tôi đánh giá GMR cùng hai phương pháp mã nguồn mở là PHC và ProtoMotions, cũng như một bộ dữ liệu chất lượng cao được tạo bằng phương pháp mã nguồn đóng của Unitree. Sử dụng BeyondMimic để huấn luyện chính sách, chúng tôi tách ảnh hưởng của retargeting mà không tinh chỉnh hàm thưởng.

Thí nghiệm trên một tập con đa dạng của LAFAN1 cho thấy mặc dù phần lớn chuyển động có thể được bám theo, các lỗi trong dữ liệu sau retargeting làm giảm đáng kể độ vững của chính sách, đặc biệt đối với các chuỗi dài hoặc có động tác mạnh. GMR vượt các phương pháp mã nguồn mở hiện có về cả hiệu năng bám chuyển động và độ trung thành với chuyển động nguồn; mức giống nhau theo cảm nhận và tỷ lệ thành công của chính sách tiến gần tới phương pháp đối chứng mã nguồn đóng.

Trang dự án: [jaraujo98.github.io/retargeting_matters](https://jaraujo98.github.io/retargeting_matters/). Mã nguồn: [YanjieZe/GMR](https://github.com/YanjieZe/GMR).

## I. Giới thiệu

Việc phát triển các chính sách cho robot hình người có khả năng khái quát hóa thực sự sang môi trường thực đòi hỏi học từ dữ liệu ghi lại tương tác vật lý với thế giới. Nhờ sự tương đồng về hình thái giữa người và robot hình người, các công trình gần đây [1]–[8] đã tận dụng dữ liệu chuyển động người 3D, thu từ motion capture [9] hoặc khôi phục chuyển động người từ video [7], [8], [10], làm dữ liệu trình diễn để huấn luyện robot thực hiện các chuyển động toàn thân đòi hỏi khả năng thăng bằng và linh hoạt giống người. Những chính sách bám chuyển động này là công cụ nền tảng để xây dựng pipeline teleoperation hoặc hệ điều khiển phân cấp.

Tuy nhiên, người và robot hình người vẫn khác nhau đáng kể về chiều dài xương, biên độ chuyển động của khớp, cấu trúc động học, hình dáng cơ thể, phân bố khối lượng và cơ cấu chấp hành. Khoảng cách về cấu trúc cơ thể này là rào cản lớn đầu tiên cần vượt qua để dữ liệu chuyển động người 3D phát huy đầy đủ giá trị trong việc học của robot.

Cách thông thường để vượt qua khác biệt đó là retargeting về mặt động học từ chuyển động người nguồn sang cơ thể robot đích. Với dữ liệu đã chuyển đổi, một thực hành phổ biến trong nghiên cứu robot hiện nay là dùng RL để học chính sách có thể thực hiện tác vụ mong muốn thông qua bắt chước chuyển động tham chiếu. Trong phần lớn trường hợp, ngoại trừ chẳng hạn [11], chính sách sau đó được triển khai trực tiếp sang thế giới thực mà không cần huấn luyện bổ sung (*zero-shot*). Cách làm này hoặc bỏ qua các lỗi rõ rệt do retargeting gây ra — như trượt chân, xuyên sàn và chuyển động bất khả thi do tự xuyên cơ thể — khiến chính sách RL phải bắt chước chuyển động bất khả thi trong khi vẫn tuân thủ ràng buộc vật lý, hoặc loại bỏ dữ liệu retargeting kém [7].

Các nghiên cứu trước [12]–[14], [11] cho thấy có thể huấn luyện chính sách trên dữ liệu retargeting có lỗi nghiêm trọng trong mô phỏng, nhưng để chuyển sang robot thật cần nhiều thử nghiệm, định hình hàm thưởng và tinh chỉnh tham số. Từ thực tế đó, chúng tôi đặt giả thuyết rằng **nếu đầu tư đủ vào thiết kế hàm thưởng và ngẫu nhiên hóa miền, phần lớn lỗi do retargeting gây ra có thể được giảm hoặc loại bỏ; nhưng khi không có những nỗ lực kỹ thuật này, chất lượng retargeting giữ vai trò đáng kể**.

Trong bài này, chúng tôi tiến hành thí nghiệm và phân tích chặt chẽ để kiểm chứng giả thuyết. Chúng tôi so sánh ba phương pháp chuyển đổi chuyển động người sang robot trong các bài toán bám chuyển động không có tương tác với vật thể hoặc cảnh phức tạp: **PHC**, được nhiều công trình bám chuyển động robot hình người sử dụng [2], [11]; **ProtoMotions**, được dùng để retarget các tác vụ có chuyển động mạnh và khó [8]; và **GMR**, phương pháp tổng quát do chúng tôi đề xuất để xử lý những vấn đề tìm thấy ở hai phương pháp còn lại.

Cụ thể, chúng tôi nhận thấy cách PHC và ProtoMotions điều chỉnh tỷ lệ từ người sang robot tạo ra một số lỗi chuyển động gây ảnh hưởng xấu tới hiệu năng. GMR khắc phục bằng quy trình thay đổi tỷ lệ cục bộ không đồng đều, đơn giản nhưng linh hoạt, sau đó tối ưu hai giai đoạn để tìm chuyển động robot bám theo chuyển động tham chiếu đã được đổi tỷ lệ. Chúng tôi cũng so sánh ba phương pháp với bộ dữ liệu retarget chất lượng cao do một phương pháp mã nguồn đóng, không công khai của Unitree tạo ra.

Để tách riêng ảnh hưởng của phương pháp retargeting, chúng tôi sử dụng BeyondMimic [15] để huấn luyện và đánh giá các chính sách RL bám theo chuyển động tham chiếu. BeyondMimic không phụ thuộc vào việc tinh chỉnh hàm thưởng và được phát triển độc lập với các phương pháp retargeting đang xét, nên phù hợp để đánh giá chúng một cách công bằng. Chúng tôi huấn luyện chính sách cho từng quỹ đạo riêng lẻ trên một tập con đa dạng của LAFAN1, loại trừ các chuyển động có tiếp xúc ngoài bàn chân. Bộ dữ liệu cuối gồm 21 chuỗi dài từ khoảng 5 giây đến 2 phút.

Khi đánh giá, chúng tôi so sánh tỷ lệ thành công theo một định nghĩa rất nghiêm ngặt: chính sách phải hoàn tất toàn bộ chuyển động tham chiếu thì lượt chạy mới được coi là thành công. Mỗi chính sách được đánh giá nhiều lần trong những điều kiện xét tới nhiễu quan sát, gồm nhiễu cảm biến và nhiễu từ thuật toán ước lượng trạng thái, sai số ước lượng tham số mô hình và độ trễ mạng trong bộ điều khiển. Chúng tôi còn tiến hành nghiên cứu người dùng để đánh giá độ trung thành theo cảm nhận của chuyển động retarget so với chuyển động người nguồn. Điều này cũng cho biết chính sách có đang học đúng chuyển động dự định hay một biến thể có thể dễ hoặc khó bám hơn.

Các thí nghiệm xuyên suốt toàn quy trình cho thấy lựa chọn phương pháp retargeting ảnh hưởng quan trọng tới hiệu năng robot. Nhìn chung, chính sách được huấn luyện trên chuyển động do các phương pháp khác nhau retarget có thể bám nhiều loại chuyển động, từ các chuyển động đơn giản đến các chuyển động rất linh hoạt và biến đổi nhanh (*highly dynamic*), phù hợp với kết quả trước đây. Tuy nhiên, ở một số ngoại lệ, lỗi retargeting khiến việc học khó hơn, thậm chí không thể học hiệu quả. Những trường hợp này cho thấy khi không có mức đầu tư lớn vào hàm thưởng như ở các công trình trước, lỗi retargeting gây khó khăn cho một số chuyển động và làm giảm hiệu năng chính sách.

Chúng tôi xác định bàn chân xuyên sàn, các bộ phận cơ thể tự xuyên vào nhau và các đỉnh vận tốc đột ngột là những lỗi quan trọng cần tránh trong retargeting. Chúng tôi cũng nhận thấy frame đầu của chuyển động tham chiếu ảnh hưởng lớn tới việc chính sách có thể bắt đầu bám chuyển động hay thất bại ngay, bất kể phương pháp retargeting nào được dùng; hiện tượng này đã được quan sát trong [7]. Cuối cùng, GMR tiến rất gần bộ dữ liệu Unitree về cả điểm trung thành và tỷ lệ thành công, đồng thời có tỷ lệ thành công cao hơn và sai số bám chuyển động thấp hơn các phương pháp còn lại.

Các đóng góp của công trình gồm:

- Một phương pháp retargeting tổng quát mới, GMR, xử lý những vấn đề của các phương pháp khác và tạo chuyển động retarget chất lượng cao từ nhiều loại chuyển động người.
- Một nghiên cứu toàn diện về ảnh hưởng của chất lượng chuyển động tham chiếu sau retargeting tới hiệu năng các chính sách bám chuyển động ở robot hình người.

**Thông tin tác giả trong bản gốc:** Các tác giả thuộc Khoa Khoa học Máy tính, Trường Kỹ thuật, Đại học Stanford, 353 Jane Stanford Way, Stanford, CA 94305, Hoa Kỳ. Liên hệ: `jparaujo@stanford.edu`.

## II. Các công trình liên quan

Chuyển đổi chuyển động là kỹ thuật xử lý dữ liệu phổ biến cho hoạt hình nhân vật trong đồ họa máy tính. Các phương pháp kinh điển [16]–[19] dựa trên tối ưu hóa và các ràng buộc động học được xác định theo kinh nghiệm để ánh xạ chuyển động sang nhân vật có khớp. Cùng với tiến bộ của học sâu, các phương pháp dựa trên dữ liệu nhận được nhiều chú ý trong những năm gần đây. Tuy vậy, chúng thường đòi hỏi dữ liệu ghép cặp để học có giám sát [20], [21], cần nhãn ngữ nghĩa để huấn luyện mô hình theo cách không giám sát [22]–[24], hoặc dùng mô hình ngôn ngữ và kỹ thuật kết xuất khả vi để đánh giá bằng hình ảnh [25]. Ngoài retargeting cho một nhân vật gồm các vật rắn, các nghiên cứu trước còn phát triển phương pháp cho nhiều nhân vật tương tác [26]–[28] và nhân vật có hình dạng biến dạng được [29]–[31].

Trong cộng đồng robot, mặc dù các phương pháp dựa trên dữ liệu đã được sử dụng rộng rãi để điều khiển robot hình người [2]–[8], [10], [15] tạo chuyển động giống người thông qua học bắt chước, khó khăn trong việc thu thập dữ liệu chuyển động ghép cặp hoặc có nhãn ngữ nghĩa trên robot thật hạn chế việc áp dụng chúng vào retargeting. Một số công trình [32]–[34] khảo sát retargeting bằng học máy cho robot hình người, nhưng chỉ tập trung vào các chuyển động đơn giản của tay và thân trên. Trong bài này, chúng tôi tập trung vào retargeting toàn thân có chuyển động di chuyển và không cần thu thập trước bất kỳ dữ liệu nào.

Các cách đơn giản [3], [5] sao chép trực tiếp phép quay khớp từ chuyển động người nguồn sang không gian khớp của robot đích. Tuy nhiên, khác biệt về cấu trúc liên kết và hình thái thường gây ra những lỗi như cơ thể lơ lửng, bàn chân xuyên sàn hoặc trượt, và đầu mút tay chân bị trôi. Ngoài ra, cần thêm xử lý để chuyển không gian khớp $SO(3)$ của người sang robot, vốn thường chỉ có các khớp quay một trục.

Bằng cách giải bài toán động học nghịch (*inverse kinematics*, IK), các phương pháp retargeting hình học toàn thân (*whole-body geometric retargeting*, WBGR) cho phép chuyển đổi toàn thân ngay cả khi không gian khớp nguồn và đích không thẳng hàng. WBGR cơ bản [35], [1] bỏ qua khác biệt kích thước trong không gian Descartes và giải IK chỉ để khớp hướng của các đoạn cơ thể chính. Ngược lại, HumanMimic [36] giải IK để khớp vị trí các điểm chính trong không gian Descartes, đồng thời dùng các hệ số đặt thủ công để đổi tỷ lệ chuyển động nguồn.

Tận dụng các tiến bộ trong biểu diễn cơ thể người của đồ họa máy tính, H2O [2] dùng mô hình SMPL [37] để khớp hình dạng robot dưới dạng cơ thể người, rồi dùng mô hình đó đổi tỷ lệ chuyển động trước khi giải IK. Một bản cài đặt tham chiếu nằm trong mã nguồn PHC [38]; trong toàn bài, chúng tôi gọi đó là **phương pháp retargeting PHC**. Phương pháp dùng hạ gradient để giải IK thông qua động học thuận, tốn thời gian và hạn chế khả năng ứng dụng thời gian thực.

Mặc dù được nhiều công trình tiếp theo sử dụng [14], [13], [39], [11], PHC không xét trạng thái tiếp xúc trong quá trình retargeting, nên có thể tạo lỗi lơ lửng, trượt chân và xuyên sàn. Hơn nữa, SMPL được thiết kế để biểu diễn cơ thể người, nên không mô tả tốt các robot có hình thái khác biệt lớn so với người.

Một số công trình khác [40], [8], [6] sử dụng bộ giải IK vi phân [41]. Các phương pháp này đổi tỷ lệ vị trí khớp của chuyển động nguồn trong không gian Descartes, rồi tính vận tốc suy rộng sao cho khi được tích phân tại trạng thái hiện tại, sai số vị trí và hướng giữa chuyển động nguồn đã đổi tỷ lệ và robot giảm đi. ProtoMotions [40] sử dụng các hệ số tỷ lệ toàn cục theo từng trục để đổi tỷ lệ vị trí khớp nguồn trong không gian Descartes, sau đó giảm thiểu tổng có trọng số của sai số vị trí và hướng giữa các bộ phận chính tương ứng của người và robot. KungfuBot [8] dùng cách của ProtoMotions nhưng tắt bước đổi tỷ lệ.

## III. Phương pháp đánh giá

Mục tiêu đánh giá của bài báo là trả lời những câu hỏi sau:

- **Q1.** Lựa chọn phương pháp retargeting có ảnh hưởng tới hiệu năng của các chính sách bám chuyển động không?
- **Q2.** Những lỗi retargeting nào ảnh hưởng xấu tới chính sách và ngăn chính sách học được?
- **Q3.** Các phương pháp retargeting khác nhau giữ được “diện mạo” của chuyển động nguồn tới mức nào?

Để trả lời, chúng tôi retarget dữ liệu bằng PHC, ProtoMotions và GMR (Mục IV), đồng thời sử dụng một bộ dữ liệu được retarget bằng phương pháp mã nguồn đóng của Unitree. Chúng tôi huấn luyện chính sách bám chuyển động bằng pipeline BeyondMimic [15], vốn đã được chứng minh hoạt động với mọi loại chuyển động tham chiếu được xét trong các công trình trước mà không cần tinh chỉnh hàm thưởng hoặc ngẫu nhiên hóa miền ở mức lớn. Điều quan trọng là BeyondMimic được phát triển độc lập với các phương pháp retargeting đang nghiên cứu.

### A. Các phương pháp retargeting

**PHC [38], [2], [14], [11].** Phương pháp PHC được thiết kế cho chuyển động ở định dạng SMPL [37]. SMPL là mô hình cơ thể người có tham số $f_{\mathrm{SMPL}}$: với vector tham số hình dạng $\boldsymbol\beta^h$ và tham số tư thế $\boldsymbol\theta^h$, nó trả về tọa độ 3D các đỉnh của lưới cơ thể người ở tư thế tương ứng:

$$
\mathbf v^h=f_{\mathrm{SMPL}}(\boldsymbol\beta^h,\boldsymbol\theta^h).
$$

Từ tọa độ đỉnh, một bộ hồi quy khớp $J\in\mathbb R^{(n_j\times3)\times(n_v\times3)}$ suy ra vị trí 3D các khớp, $\mathbf j^h=J\mathbf v^h$, được coi là gốc của các bộ phận chính. Vì vậy, một chuyển động SMPL là tệp chứa tham số hình dạng cơ thể và tensor tham số tư thế, trong đó một chiều tương ứng với thời gian.

Bước đầu tiên là khớp một bộ tham số hình dạng $\boldsymbol\beta^r$ với skeleton robot. Sau đó, với tham số tư thế của chuyển động người $\boldsymbol\theta_t^h$, mô hình SMPL tính các tọa độ 3D mục tiêu cho khớp robot theo thời gian:

$$
\mathbf p_t^{\mathrm{target}}=Jf_{\mathrm{SMPL}}(\boldsymbol\beta^r,\boldsymbol\theta_t^h).
$$

Bước thứ hai tối ưu vị trí tịnh tiến gốc robot $\mathbf p_t$, hướng $R_t$ và góc khớp $\mathbf q_t$ ở từng thời điểm để giảm thiểu sai số vị trí giữa các khớp của robot đã tạo tư thế, tính bằng động học thuận, với mục tiêu tính từ mô hình SMPL có hình dạng robot:

$$
\begin{aligned}
\min_{\mathbf p_t,R_t,\mathbf q_t}\quad &
\frac1T\sum_{t=1}^{T}
\left\|\mathbf p_t^{\mathrm{target}}-\mathrm{FK}(\mathbf p_t,R_t,\mathbf q_t)\right\|_2\\
\text{với ràng buộc}\quad &\mathbf q^-\leq\mathbf q_t\leq\mathbf q^+.
\end{aligned}
\tag{1}
$$

Bản cài đặt PHC dùng hạ gradient trên chuẩn L2 của sai số, lấy trung bình trên tất cả frame, để giải bài toán này. Bộ tối ưu cho tư thế gốc là Adam, còn cho giá trị khớp là Adadelta. Ràng buộc giới hạn khớp được thực thi bằng chặn giá trị (*clamping*). Sau tối ưu, động học thuận tính độ cao của tất cả bộ phận robot trong clip đã retarget; độ cao thấp nhất được trừ khỏi vị trí tịnh tiến gốc.

**ProtoMotions [40].** Gói ProtoMotions tập hợp các bản cài đặt chuẩn của những phương pháp phổ biến để huấn luyện chính sách bắt chước chuyển động. Nó đi kèm thuật toán retargeting dựa trên tối ưu hóa. Chuyển động nguồn được đổi tỷ lệ bằng một hệ số riêng cho từng trục của hệ tọa độ thế giới. Tiếp theo, Mink [41] giảm thiểu sai số vị trí khớp và hướng giữa các bộ phận chính của người đã đổi tỷ lệ và robot. Tương tự PHC, phương pháp có bước hậu xử lý độ cao; nhưng thay vì đặt độ cao thấp nhất bằng 0, nó đặt bằng độ cao thấp nhất của chuyển động nguồn.

**GMR.** Chúng tôi cũng đánh giá GMR, phương pháp do mình đề xuất. Động lực chính là khắc phục các lỗi rõ rệt trong chuyển động do hai phương pháp kia tạo ra: lệch khỏi chuyển động nguồn, trượt chân, xuyên sàn và tự xuyên cơ thể. Mục IV mô tả chi tiết GMR. Khác biệt chính so với hai phương pháp trước là cách đổi tỷ lệ chuyển động nguồn, vốn được chúng tôi xác định là nguyên nhân của nhiều lỗi. Sau đó là tối ưu hai giai đoạn để tìm chuyển động robot.

**Unitree.** Dù không được tiếp cận quy trình retargeting, chúng tôi nhận thấy bản retarget LAFAN1 của Unitree đã được dùng trong các bài gần đây như BeyondMimic và VideoMimic [10]. Chúng tôi đưa nó vào làm đối chứng để đánh giá mức cạnh tranh của các phương pháp mở so với phương pháp độc quyền.

### B. Xử lý dữ liệu

Chúng tôi chọn một mẫu đa dạng từ LAFAN1 [42], từ chuyển động đơn giản như đi bộ, quay người đến chuyển động mạnh và phức tạp như võ thuật, đá chân và nhảy múa. Chúng tôi không đưa vào các chuyển động có tương tác phức tạp với môi trường như bò hoặc đứng dậy từ sàn. Có một ngoại lệ là chuỗi nhào lộn sang bên (*cartwheel*), vì robot chỉ có chân hoặc tay tiếp xúc sàn tại một thời điểm, không có cả hai. Danh sách đầy đủ nằm trong Bảng I.

Mỗi chuỗi được retarget sang Unitree G1. Tệp LAFAN1 ở định dạng BVH, tương thích trực tiếp với GMR. PHC và ProtoMotions đều đòi hỏi dữ liệu nguồn ở định dạng SMPL; ProtoMotions hỗ trợ thêm SMPL-X [43]. Chúng tôi chuyển BVH sang SMPL(-X) theo cách tương tự PHC. Trước hết, các tham số hình dạng $\boldsymbol\beta$ của SMPL(-X) được khớp với skeleton BVH bằng cách giảm thiểu sai số vị trí khớp giữa hai skeleton. Chúng tôi cũng phạt $\|\boldsymbol\beta\|_2$ vì các giá trị lớn gây biến dạng mạnh lưới cơ thể người.

Sau đó, tận dụng việc skeleton LAFAN1 có cùng cấu trúc động học với SMPL(-X), chúng tôi sao chép các phép quay khớp 3D tương ứng. Cuối cùng, vị trí tịnh tiến gốc được tính là độ lệch giảm thiểu sai số vị trí giữa skeleton LAFAN1 và SMPL(-X) ở cùng tư thế. Chúng tôi dùng PHC và ProtoMotions để tạo chuyển động G1 cuối cùng. SMPL-X khớp skeleton LAFAN1 tốt hơn SMPL, nên được dùng làm nguồn cho ProtoMotions.

Mặc dù PHC có bước hậu xử lý để khắc phục lỗi bàn chân xuyên sàn, chúng tôi thấy ở một số chuỗi nó gây lơ lửng nghiêm trọng, từ 30 cm trở lên. Chúng tôi sửa bằng cách chạy động học thuận trên chuỗi đã retarget, lưu độ cao bộ phận thấp nhất ở từng frame, rồi dịch toàn bộ chuyển động theo trung bình các độ cao nhỏ nhất đó. Chuyển động tạo bởi các phương pháp còn lại không cần hậu xử lý tương tự.

### C. Đánh giá bám chuyển động

Chúng tôi sử dụng BeyondMimic để huấn luyện một chính sách bắt chước riêng cho từng chuyển động đã retarget trong IsaacSim. Chúng tôi đo độ vững trước nhiễu quan sát và thay đổi miền (*domain shift*). Cụ thể, mỗi chính sách được đánh giá 100 lần khi tắt ngẫu nhiên hóa miền (**sim**) và 4.096 lần khi bật (**sim-dr**). Robot bắt đầu mỗi lượt đánh giá từ tư thế mặc định. Chính sách chạy cho tới khi robot ngã hoặc chuyển động tham chiếu kết thúc.

Bản phát hành BeyondMimic có một gói độc quyền để triển khai chính sách lên Unitree G1 thông qua ROS, xử lý cả ước lượng trạng thái lẫn suy luận. Để kiểm tra độ vững trước khi triển khai, gói này còn có một ROS node chạy MuJoCo. Chúng tôi tận dụng nó để đánh giá kỹ lưỡng và an toàn trong một cấu hình mô phỏng cách dùng ngoài đời thực; gọi điều kiện này là **sim2sim**.

Với mỗi chính sách, chúng tôi chạy 100 lượt trong môi trường ROS này và ghi trạng thái robot trong mô phỏng. Tương tự sim, robot bắt đầu từ tư thế mặc định. Tính ngẫu nhiên đến từ thời điểm và đồng bộ hóa liên quan tới ROS, cùng nhiễu của module ước lượng trạng thái. Không tinh chỉnh các tham số mô phỏng; bộ điều khiển không có quyền truy cập thông tin đặc quyền của mô phỏng, chẳng hạn tư thế gốc toàn cục chuẩn.

### D. Các chỉ số đánh giá

Chúng tôi đánh giá cả khả năng duy trì thăng bằng lẫn hiệu năng bám chuyển động. Mỗi lượt được coi là thành công nếu chính sách đi đến cuối episode mà độ cao hoặc hướng của bộ phận neo (*anchor body*) không lệch khỏi tham chiếu quá ngưỡng quy định; vượt ngưỡng thì episode bị kết thúc. **Tỷ lệ thành công** là số lượt thành công chia tổng số lượt chạy.

Theo [8], chúng tôi còn đánh giá:

- Sai số vị trí trung bình của các bộ phận cơ thể trong hệ tọa độ toàn cục, $E_{\mathrm{g\text{-}mpbpe}}$, đơn vị mm.
- Sai số vị trí trung bình của các bộ phận so với vị trí gốc, $E_{\mathrm{mpbpe}}$, đơn vị mm.
- Sai số góc trung bình của các phép quay khớp, $E_{\mathrm{mpjpe}}$, đơn vị $10^{-3}$ rad.

Sai số bám được tính trên mọi frame mà chính sách vẫn chưa bị kết thúc.

![Hình 1 — So sánh video chuyển động tham chiếu và video retarget](<D:/Projects/iTwinLab/Physical AI/REPORT_2026-10-30/tmp/gmr_vi_assets/figure-01.png>)

**Hình 1.** Trong nghiên cứu người dùng, người tham gia xem video chuyển động tham chiếu (a), rồi chọn video retarget (b) giống tham chiếu hơn.

### E. Đánh giá bằng nghiên cứu người dùng

Để trả lời Q3, chúng tôi cho người tham gia xem clip tham chiếu dài 5 giây được kết xuất bằng mô hình SMPL-X khớp với dữ liệu LAFAN1, cùng hai clip đã retarget: một bằng GMR và một bằng Unitree, PHC hoặc ProtoMotions (Hình 1). Người tham gia không được biết phương pháp nào tạo video nào; thứ tự video được ngẫu nhiên hóa. Họ chọn video gần với tham chiếu hơn hoặc chọn không phân biệt được. Các clip tham chiếu 5 giây được lấy ngẫu nhiên từ 15 chuyển động. Mỗi người so sánh cả ba phương pháp với GMR trên từng chuyển động, trả lời tổng cộng 45 câu hỏi.

## IV. General Motion Retargeting

Phần này trình bày pipeline GMR được đề xuất. Hình 2 cung cấp cái nhìn tổng thể; từng bước được giải thích bên dưới.

![Hình 2 — Pipeline GMR gốc](<D:/Projects/iTwinLab/Physical AI/REPORT_2026-10-30/tmp/gmr_vi_assets/figure-02.png>)

**Hình 2.** Pipeline General Motion Retargeting. Đầu vào là vị trí tịnh tiến và phép quay các bộ phận cơ thể người. Các bước gồm ghép bộ phận chính người–robot, căn chỉnh trong không gian Descartes, đổi tỷ lệ cục bộ không đồng đều, giải IK với ràng buộc phép quay, rồi giải IK với cả ràng buộc phép quay và vị trí tịnh tiến. Đầu ra là tư thế gốc và các giá trị khớp robot (góc khớp đối với khớp quay). Phần diễn giải các nhãn này dịch từ sơ đồ gốc.

### Bước 1. Ghép các bộ phận chính giữa người và robot

Từ danh sách bộ phận trong skeleton người nguồn, lấy từ hệ motion capture hoặc tệp BVH/SMPL, và skeleton robot đích trong tệp mô tả XML hoặc URDF, người dùng xác định ánh xạ $\mathcal M$ giữa các bộ phận chính của người và robot, thường gồm thân, đầu, chân, bàn chân, cánh tay và bàn tay. Thông tin này thiết lập bài toán tối ưu cho bộ giải IK. Người dùng cũng có thể cung cấp trọng số cho sai số bám vị trí và hướng của các bộ phận đó.

### Bước 2. Căn chỉnh tư thế nghỉ trong không gian Descartes

Chúng tôi bù hướng các bộ phận người để chúng khớp hướng của các bộ phận robot khi cả hai ở tư thế nghỉ (*rest pose*). Trong một số trường hợp, chúng tôi còn thêm độ lệch cục bộ cho vị trí bộ phận. Việc này giúp giảm các lỗi như mũi bàn chân hướng vào trong được mô tả ở [2].

### Bước 3. Đổi tỷ lệ cục bộ không đồng đều cho dữ liệu người

Chúng tôi nhận thấy phần lớn lỗi ở những phương pháp retargeting còn lại phát sinh khi đổi tỷ lệ chuyển động nguồn, cho thấy tầm quan trọng của việc đổi tỷ lệ đúng. Đầu tiên, chúng tôi tính hệ số tỷ lệ chung dựa trên chiều cao skeleton người nguồn. Hệ số này điều chỉnh một hệ số cục bộ tùy chỉnh cho từng bộ phận chính. Các hệ số riêng cho phép xét tới khác biệt tỷ lệ, chẳng hạn giữa thân dưới và thân trên. Vị trí bộ phận mục tiêu trong không gian Descartes là:

$$
\mathbf p_b^{\mathrm{target}}=
\frac{h}{h_{\mathrm{ref}}}\,s_b
\left(\mathbf p_j^{\mathrm{source}}-\mathbf p_{\mathrm{root}}^{\mathrm{source}}\right)
+\frac{h}{h_{\mathrm{ref}}}\,s_{\mathrm{root}}\mathbf p_{\mathrm{root}}^{\mathrm{source}}.
\tag{2}
$$

Trong đó, $h$ là chiều cao skeleton người nguồn; $h_{\mathrm{ref}}$ là chiều cao tham chiếu giả định khi thiết lập hệ số tỷ lệ; $\mathbf p_b$ là vị trí bộ phận; $s_b$ là hệ số tỷ lệ tương ứng với bộ phận $b$. Khi bộ phận là gốc, công thức rút gọn thành:

$$
\mathbf p_{\mathrm{root}}^{\mathrm{target}}=
\frac{h}{h_{\mathrm{ref}}}\,s_{\mathrm{root}}\mathbf p_{\mathrm{root}}^{\mathrm{source}}.
\tag{3}
$$

Chúng tôi nhận thấy đổi tỷ lệ vị trí tịnh tiến gốc bằng một hệ số đồng đều là yếu tố quan trọng để tránh tạo lỗi trượt chân.

### Bước 4. Giải IK robot với ràng buộc phép quay

Chúng tôi cần tìm các tọa độ suy rộng $\mathbf q$ của robot, gồm vị trí tịnh tiến gốc, phép quay gốc và giá trị khớp, để giảm thiểu sai số vị trí và hướng của các bộ phận so với tham chiếu. Nhằm tránh các cực tiểu cục bộ của tối ưu, chúng tôi dùng quy trình hai giai đoạn. Với một tư thế mục tiêu, giai đoạn đầu giải bài toán sau, chỉ xét hướng các bộ phận và vị trí các đầu mút tay chân:

$$
\begin{aligned}
\min_{\mathbf q}\quad &
\sum_{(i,j)\in\mathcal M}(w_1)^R_{i,j}
\left\|R_i^h\ominus R_j(\mathbf q)\right\|_2^2\\
&+\sum_{(i,j)\in\mathcal M_{\mathrm{ee}}}(w_1)^p_{i,j}
\left\|\mathbf p_i^{\mathrm{target}}-\mathbf p_j(\mathbf q)\right\|_2^2\\
\text{với ràng buộc}\quad &\mathbf q^-\leq\mathbf q\leq\mathbf q^+.
\end{aligned}
\tag{4}
$$

Ở đây, $R_i^h\in SO(3)$ là hướng của bộ phận người $i$; $\mathbf p_j(\mathbf q)$ và $R_j(\mathbf q)\in SO(3)$ lần lượt là vị trí Descartes và hướng của bộ phận robot $j$, tính bằng động học thuận. $R_i\ominus R_j$ là biểu diễn ánh xạ mũ của chênh lệch hướng giữa $R_i$ và $R_j$, với định nghĩa được bản v1 ghi là $R_i\ominus R_j:=\exp(R_i^{-1}R_j)$ trong $so(3)$. $\mathcal M_{\mathrm{ee}}$ là tập con của $\mathcal M$ chỉ chứa các đầu mút, tức bàn tay và bàn chân. $(w_1)^p_{i,j}$ và $(w_1)^R_{i,j}$ là trọng số sai số vị trí và hướng ở giai đoạn tối ưu đầu.

Các thành phần vị trí và hướng gốc trong $\mathbf q$ được khởi tạo bằng vị trí đã đổi tỷ lệ $\mathbf p_{\mathrm{root}}^{\mathrm{target}}$ và thành phần yaw của hướng bộ phận gốc người. Tối ưu tuân thủ các giá trị khớp nhỏ nhất và lớn nhất $\mathbf q^-$, $\mathbf q^+$. Đôi khi cần siết chặt khoảng này để tránh các chuyển động không giống người.

Chúng tôi giải bài toán bằng Mink, một bộ giải IK vi phân. Nghĩa là thay vì trực tiếp tìm $\mathbf q$ giảm thiểu hàm chi phí, chúng tôi tính vận tốc suy rộng $\dot{\mathbf q}$ sao cho tích phân chúng làm giảm chi phí. Điều này được thực hiện bằng bài toán:

$$
\begin{aligned}
\min_{\dot{\mathbf q}}\quad &
\left\|e(\mathbf q)+J(\mathbf q)\dot{\mathbf q}\right\|_W^2\\
\text{với ràng buộc}\quad &
\mathbf q^-\leq\mathbf q+\dot{\mathbf q}\Delta t\leq\mathbf q^+.
\end{aligned}
\tag{5}
$$

Trong đó, $e(\mathbf q)$ là hàm mất mát của Công thức (4); $J(\mathbf q)=\partial e/\partial\mathbf q$ là ma trận Jacobian của hàm mất mát theo $\mathbf q$; $W$ là ma trận trọng số được xác định từ $(w_*)^p_{i,j}$ và $(w_*)^R_{i,j}$. $\Delta t$ là tham số của bộ giải IK vi phân, không nhất thiết bằng khoảng thời gian giữa hai frame tham chiếu.

Bộ giải chạy đến khi hội tụ — thay đổi của giá trị hàm nhỏ hơn ngưỡng 0,001 — hoặc đạt tối đa 10 vòng lặp.

### Bước 5. Tinh chỉnh với ràng buộc phép quay và vị trí tịnh tiến

Cuối cùng, chúng tôi dùng nghiệm ở bài toán trước làm giá trị khởi đầu để giải:

$$
\begin{aligned}
\min_{\mathbf q}\quad &
\sum_{(i,j)\in\mathcal M}\Big[
(w_2)^R_{i,j}\left\|R_i^h\ominus R_j(\mathbf q)\right\|_2^2\\
&\hspace{28mm}+(w_2)^p_{i,j}
\left\|\mathbf p_i^{\mathrm{target}}-\mathbf p_j(\mathbf q^r)\right\|_2^2\Big]\\
\text{với ràng buộc}\quad &\mathbf q^-\leq\mathbf q\leq\mathbf q^+.
\end{aligned}
\tag{6}
$$

Bài toán dùng các trọng số $(w_2)^p_{i,j}$ và $(w_2)^R_{i,j}$ khác giai đoạn đầu, đồng thời xét vị trí của tất cả bộ phận chính. Điều kiện kết thúc giống giai đoạn tối ưu trước.

### Áp dụng cho chuỗi chuyển động

Phương pháp trên mô tả retargeting một tư thế. Với chuỗi chuyển động, phương pháp được áp dụng lần lượt cho từng frame; kết quả retarget của frame trước làm giá trị khởi đầu cho tối ưu ở Bước 4 của frame sau. Sau khi retarget cả chuyển động, động học thuận tính độ cao tất cả bộ phận robot theo thời gian. Độ cao nhỏ nhất sau đó được trừ khỏi vị trí tịnh tiến toàn cục để sửa lỗi độ cao, như lơ lửng hoặc xuyên sàn.

**Ghi chú của người dịch về ký hiệu:** Công thức (2) của bản v1 dùng $\mathbf p_j^{\mathrm{source}}$ dù vế trái mang chỉ số $b$; phần định nghĩa $\ominus$ ghi ánh xạ `exp`; Công thức (6) dùng $\mathbf q^r$ trong số hạng vị trí. Bản v1 còn gọi $e(\mathbf q)$ trong Công thức (5) là “loss function” (hàm mất mát); cách gọi này cần được làm rõ khi diễn giải toán. Những cách ghi này được giữ theo PDF v1, chưa tự hiệu chỉnh. Khi nghiên cứu sâu về toán hoặc cài đặt, nên đối chiếu thêm định nghĩa và mã nguồn tác giả; các ký hiệu trên không phải kết luận hiệu chỉnh của bản dịch.

## V. Kết quả đánh giá

Tỷ lệ thành công trong ba cấu hình sim, sim-dr và sim2sim được trình bày ở Bảng I. Thống kê sai số bám trên 21 chuyển động nằm trong Bảng II.

### Bảng I. Tỷ lệ thành công trong ba điều kiện đánh giá

Tỷ lệ thành công tính bằng %. **sim**: IsaacSim, không ngẫu nhiên hóa miền, 100 lượt cho mỗi chính sách. **sim-dr**: IsaacSim, có ngẫu nhiên hóa miền, 4.096 lượt cho mỗi chính sách. **sim2sim**: MuJoCo/ROS, 100 lượt cho mỗi chính sách. **PM** = ProtoMotions; **U** = Unitree. Dấu **\***: xem Mục V-D. Tên chuỗi được giữ theo bản gốc để tra cứu.

**I-a. sim**

| Chuyển động | Độ dài (s) | PHC | GMR | PM | U |
| --- | ---: | ---: | ---: | ---: | ---: |
| Walk 1 | 33 | 100 | 100 | 100 | 100 |
| Walk 2 | 5.5 | 23 | 100 | 100 | 100 |
| Turn 1 | 12.3 | 93 | 100 | 100 | 100 |
| Turn 2 | 12.3 | 100 | 100 | 100 | 100 |
| Walk (old) | 33 | 100 | 100 | 100 | 100 |
| Walk (army) | 13 | 100 | 100 | 100 | 100 |
| Hop | 13 | 95 | 100 | 100 | 100 |
| Walk (knees) | 19.58 | 100 | 100 | 100 | 100 |
| Dance 1 | 118 | 0 | 100 | 100 | 99 |
| Dance 2 | 130.5 | 0 | 100 | 100 | 100 |
| Dance 3 | 120 | 100 | 100 | 100 | 100 |
| Dance 4 | 20 | 100 | 100 | 100 | 100 |
| Dance 5 | 68.4 | 100 | 96 | 100 | 100 |
| Run (slow) | 50 | 100 | 100 | 100 | 100 |
| Run | 11 | 100 | 100 | 100 | 100 |
| Run (stop & go) | 37 | 17 | 98 | 20 | 100 |
| Hop around | 18 | 100 | 100 | 100 | 100 |
| Hopscotch | 10 | 100 | 100 | 100 | 100 |
| Jump and rotate | 21 | 100 | 100 | 100 | 100 |
| Kung fu | 8.6 | 100 | 100 | 100 | 100 |
| Various sports | 42.58 | 100 | 100 | 100 | 100 |

**I-b. sim-dr**

| Chuyển động | PHC | GMR | PM | U |
| --- | ---: | ---: | ---: | ---: |
| Walk 1 | 100 | 100 | 100 | 100 |
| Walk 2 | 53.54 | 100 | 99.98 | 100 |
| Turn 1 | 87.18 | 99.98 | 99.95 | 100 |
| Turn 2 | 99.95 | 99.98 | 100 | 99.98 |
| Walk (old) | 100 | 100 | 100 | 100 |
| Walk (army) | 99.85 | 98.63 | 99.95 | 99.95 |
| Hop | 92.97 | 100 | 100 | 100 |
| Walk (knees) | 99.98 | 100 | 100 | 100 |
| Dance 1 | 0 | 99.46 | 99.24 | 99.95 |
| Dance 2 | 0.02 | 99.9 | 99.88 | 99.98 |
| Dance 3 | 100 | 100 | 99.95 | 100 |
| Dance 4 | 100 | 100 | 100 | 100 |
| Dance 5 | 100 | 92.75 | 99.98 | 100 |
| Run (slow) | 99.19 | 99.88 | 99.95 | 99.98 |
| Run | 99.98 | 100 | 99.95 | 100 |
| Run (stop & go) | 20.46 | 91.24 | 40.26 | 99.83 |
| Hop around | 100 | 100 | 100 | 100 |
| Hopscotch | 100 | 100 | 100 | 99.98 |
| Jump and rotate | 99.98 | 100 | 99.9 | 100 |
| Kung fu | 100 | 99.95 | 100 | 100 |
| Various sports | 99.98 | 99.98 | 99.95 | 100 |

**I-c. sim2sim**

| Chuyển động | PHC | GMR | PM | U |
| --- | ---: | ---: | ---: | ---: |
| Walk 1 | 100 | 100 | 100 | 100 |
| Walk 2 | 100* | 100* | 100* | 100* |
| Turn 1 | 100* | 100* | 99* | 100* |
| Turn 2 | 99 | 100 | 100 | 99 |
| Walk (old) | 100 | 100 | 100 | 100 |
| Walk (army) | 100 | 100 | 99 | 100 |
| Hop | 100 | 100 | 100 | 100 |
| Walk (knees) | 100 | 100 | 100 | 100 |
| Dance 1 | 0 | 100 | 100 | 100 |
| Dance 2 | 0 | 100 | 100 | 100 |
| Dance 3 | 99 | 100 | 100 | 100 |
| Dance 4 | 99 | 100 | 100 | 100 |
| Dance 5 | 100 | 51 | 100 | 100 |
| Run (slow) | 100 | 100 | 100 | 100 |
| Run | 100 | 100 | 100 | 100 |
| Run (stop & go) | 74 | 100 | 26 | 100 |
| Hop around | 100 | 100 | 100 | 100 |
| Hopscotch | 100 | 100 | 100 | 100 |
| Jump and rotate | 99 | 100 | 100 | 99 |
| Kung fu | 100 | 100 | 100 | 100 |
| Various sports | 100 | 100 | 100 | 99 |

### Bảng II. Sai số bám của các chính sách

Sai số được đo trên 100 lượt đánh giá ở điều kiện **sim**. Giá trị thấp hơn tốt hơn. Giá trị tốt nhất được **in đậm**; tốt thứ hai được <u>gạch chân</u>.

**II-a. Sai số vị trí toàn cục $E_{\mathrm{g\text{-}mpbpe}}$, mm**

| Thống kê | PHC | GMR | PM | U |
| --- | ---: | ---: | ---: | ---: |
| Nhỏ nhất | 71.8 | <u>59.9</u> | 66.0 | **51.1** |
| Trung vị | 111.9 | <u>91.2</u> | 101.9 | **73.4** |
| Trung bình | 247.8 | <u>104.1</u> | 139.7 | **77.2** |
| Lớn nhất | 1062.3 | <u>200.0</u> | 915.6 | **131.4** |

**II-b. Sai số vị trí tương đối với gốc $E_{\mathrm{mpbpe}}$, mm**

| Thống kê | PHC | GMR | PM | U |
| --- | ---: | ---: | ---: | ---: |
| Nhỏ nhất | 20.9 | **18.1** | 24.1 | <u>18.2</u> |
| Trung vị | 29.9 | <u>27.6</u> | 30.4 | **23.1** |
| Trung bình | 40.2 | <u>28.1</u> | 33.2 | **23.2** |
| Lớn nhất | 134.4 | <u>48.0</u> | 107.9 | **28.9** |

**II-c. Sai số góc khớp $E_{\mathrm{mpjpe}}$, $10^{-3}$ rad**

| Thống kê | PHC | GMR | PM | U |
| --- | ---: | ---: | ---: | ---: |
| Nhỏ nhất | 569.5 | <u>362.0</u> | 499.0 | **355.5** |
| Trung vị | 739.8 | <u>546.0</u> | 599.7 | **467.2** |
| Trung bình | 778.5 | <u>561.7</u> | 641.8 | **483.0** |
| Lớn nhất | 1336.1 | <u>1044.8</u> | 1397.9 | **678.5** |

### A. Ảnh hưởng của phương pháp retargeting tới hiệu năng chính sách

Trong 21 chuyển động được thử nghiệm, 11 chuyển động — “Turn 2”, “Walk (army)”, “Walk (knees)”, “Dance 3”, “Dance 4”, “Run (slow)”, “Run”, “Hopscotch”, “Jump and rotate”, “Kung fu”, “Various sports” — có tỷ lệ thành công trên 98% ở mọi phương pháp retargeting; ba chuyển động đạt kết quả hoàn hảo là “Walk 1”, “Walk (old)” và “Hop around”. Với bảy chuyển động còn lại, hiệu năng khác nhau lớn giữa các phương pháp.

Chính sách huấn luyện trên dữ liệu Unitree đạt kết quả gần hoàn hảo trên mọi chuyển động, xác nhận kết quả của BeyondMimic. Theo sát là chính sách huấn luyện trên dữ liệu do GMR và ProtoMotions retarget, với một vài ngoại lệ: “Dance 5” đối với GMR và “Run (stop & go)” đối với ProtoMotions. PHC có hiệu năng thấp nhất. Chuyển động dài tự nó không phải trở ngại, vì chính sách học từ bản PHC retarget của “Dance 3”, dài hai phút, vẫn thành công trong mọi cấu hình. Việc không học được cách bám thành công “Dance 1” và “Dance 2”, cùng các trường hợp giảm hiệu năng cụ thể ở GMR và ProtoMotions, được giải thích bằng lỗi retargeting; Mục V-B trình bày chi tiết.

Tỷ lệ thành công không phản ánh toàn bộ bức tranh: để thành công, chính sách chỉ cần đi đến cuối episode mà không ngã. Bảng II cho thấy các chính sách học từ dữ liệu PHC hoặc ProtoMotions có thể có sai số bám lớn trong cả không gian toàn cục lẫn cục bộ, cho thấy khó khăn trong việc bám tham chiếu gốc mà vẫn ổn định.

Những kết quả này cho thấy tuy có thể huấn luyện chính sách bám thành công nhiều loại chuyển động, điều đó có thể phải đánh đổi bằng sai số bám cao hơn; ở một số trường hợp, việc học chính sách bám chuyển động vững từ dữ liệu đã retarget khó hơn rõ rệt. Vì vậy, chúng tôi có thể trả lời **có** đối với Q1.

### B. Ảnh hưởng của các lỗi retargeting

Để trả lời Q2, chúng tôi nhận thấy điểm số thấp trong đánh giá sim2sim có thể liên hệ trực tiếp với các lỗi trong chuyển động đã retarget (Hình 3):

- Bản PHC retarget của “Dance 1” và “Dance 2” có lỗi **xuyên sàn** rõ rệt; một trường hợp lên tới 60 cm.
- Hai chân robot **xuyên vào nhau** trong bản ProtoMotions retarget của “Run (stop & go)”.
- Bản GMR retarget của “Dance 5” có nhiều lần giá trị góc roll của eo **nhảy đột ngột**.

Mặc dù những lỗi này thường không làm chuyển động tham chiếu trở nên hoàn toàn không thể bám, ngoại trừ các chuỗi nhảy múa dài do PHC retarget, cả ba loại lỗi — độ cao không nhất quán về vật lý, tự xuyên và giá trị khớp nhảy đột ngột — đều cần tránh để có cơ hội thành công tốt nhất.

Các lần nhảy đột ngột ở GMR hiếm xảy ra: trong clip con của “Dance 5”, chúng xuất hiện trong đoạn 10 giây, chiếm dưới 2% toàn bộ tập dữ liệu chuyển động. Lỗi được tạo ra trong giai đoạn tối ưu. Vì tất cả thí nghiệm dùng cùng bộ trọng số tối ưu, một số chuyển động có thể cần tinh chỉnh thêm trọng số để đạt kết quả tốt nhất.

![Hình 3 — Ví dụ lỗi xuyên sàn, tự xuyên và giá trị khớp nhảy đột ngột](<D:/Projects/iTwinLab/Physical AI/REPORT_2026-10-30/tmp/gmr_vi_assets/figure-03.png>)

**Hình 3.** Ví dụ lỗi trong các chuyển động tham chiếu đã retarget có tỷ lệ thành công thấp: (a) xuyên sàn ở PHC, “Dance 1”; (b) tự xuyên ở ProtoMotions, “Run (stop & go)”; (c) góc roll và pitch của eo nhảy đột ngột ở GMR, “Dance 5”. Trong đồ thị, trục ngang là frame, trục đứng là góc khớp (rad), đường đứt màu đỏ là giới hạn khớp.

### C. Nghiên cứu người dùng

Có 20 người tham gia nghiên cứu; kết quả ở Hình 4. Người tham gia đánh giá GMR trung thành với chuyển động tham chiếu hơn các bản retarget của PHC hoặc ProtoMotions. Bản Unitree được đánh giá trung thành hơn GMR, nhưng người tham gia cũng khó phân biệt hai phương pháp hơn. Sự kết hợp giữa tỷ lệ thành công cao và điểm trung thành gần nhau cho thấy GMR là một phương án thay thế khả thi cho dữ liệu do Unitree retarget.

![Hình 4 — Kết quả nghiên cứu người dùng](<D:/Projects/iTwinLab/Physical AI/REPORT_2026-10-30/tmp/gmr_vi_assets/figure-04.png>)

**Hình 4.** Kết quả nghiên cứu người dùng ($N=20$), so sánh GMR với các bản retarget khác về độ trung thành với chuyển động nguồn. Chiều cao cột là tỷ lệ phần trăm câu trả lời. Chú giải gốc: xanh dương = thích GMR hơn; xanh lá = không có ưu tiên; cam = thích phương pháp còn lại hơn.

### Bảng III. Ảnh hưởng của frame bắt đầu

Tỷ lệ thành công (%) trong sim2sim (MuJoCo) theo frame bắt đầu của chuyển động tham chiếu. PM = ProtoMotions; U = Unitree.

| Chuyển động | Frame bắt đầu | PHC | GMR | PM | U |
| --- | ---: | ---: | ---: | ---: | ---: |
| Walk 2 | 0 | 100 | 64 | 100 | 100 |
| Walk 2 | 7 | 100 | 100 | 100 | 100 |
| Turn 1 | 0 | 14 | 100 | 86 | 47 |
| Turn 1 | 49 | 100 | 100 | 99 | 100 |

### D. Frame đầu của chuyển động tham chiếu

Cuối cùng, như đã được ghi nhận trong [7], frame bắt đầu của chuyển động tham chiếu có thể ảnh hưởng lớn tới hiệu năng chính sách. Bảng III cho thấy tỷ lệ thành công của cùng một chính sách ở điều kiện sim2sim (MuJoCo), nhưng dùng các frame bắt đầu khác nhau. Chúng tôi khuyến nghị bảo đảm tư thế đầu của tham chiếu là tư thế robot có thể đạt an toàn khi bắt đầu suy luận chính sách. Tương tự, nên kết thúc chuyển động tham chiếu ở một tư thế ổn định để có thể ngừng hoạt động robot an toàn.

## VI. Kết luận

Trong bài này, chúng tôi đánh giá ảnh hưởng của retargeting chuyển động tới hiệu năng các chính sách bám chuyển động. Phân tích bao gồm GMR do chúng tôi giới thiệu, thuật toán PHC phổ biến, thuật toán ProtoMotions và dữ liệu được Unitree retarget chính thức. Chúng tôi retarget một tập đa dạng về độ dài và độ khó, rồi dùng BeyondMimic huấn luyện chính sách bám cho từng clip. Mỗi chính sách được đánh giá kỹ về độ vững trước nhiễu quan sát, sai khác mô hình, độ trễ mạng và hiệu năng bám.

Chúng tôi nhận thấy mặc dù có thể huấn luyện thành công các chính sách cho nhiều chuyển động được tạo bằng tất cả phương pháp đang xét, một số lỗi quan trọng làm tăng mạnh độ khó của việc học: xuyên sàn, tự xuyên và giá trị khớp nhảy đột ngột. Nghiên cứu người dùng cũng cho thấy PHC và ProtoMotions tạo chuyển động ít trung thành với nguồn hơn GMR. Dù trong một số trường hợp hiếm GMR vẫn cần tinh chỉnh để loại bỏ lỗi tối ưu, các tham số mặc định hoạt động tốt với nhiều chuyển động, vừa tạo tham chiếu tốt để huấn luyện chính sách, vừa giữ độ trung thành với nguồn — điều không đạt được ở cùng mức độ với các phương pháp còn lại.

Công trình có một số giới hạn. Dù xét nhiều loại chuyển động, tất cả đều từ một nguồn duy nhất là LAFAN1. Cần nghiên cứu thêm với các nguồn khác, như AMASS hoặc chuyển động người được khôi phục từ video đơn nhãn (một camera). Một giới hạn khác là chỉ xét Unitree G1, chủ yếu do mã nguồn BeyondMimic, vì các phương pháp retargeting khác cũng có sẵn cho Unitree H1. Tuy nhiên, BeyondMimic và các thuật toán được so sánh đều có tính tổng quát; do đó, nên mở rộng phân tích sang các robot hình người khác trong tương lai. Một hướng nữa là nghiên cứu ảnh hưởng của retargeting lên các chuỗi có tương tác, chẳng hạn với môi trường xung quanh, vật thể hoặc robot khác.

## Lời cảm ơn

Công trình được hỗ trợ một phần bởi Stanford Institute for Human-Centered AI (HAI), Stanford Wu-Tsai Human Performance Alliance, ONR MURI N00014-22-1-2740, Google và Meta Reality Labs.


## Tài liệu tham khảo

Tên bài, tác giả và thông tin xuất bản dưới đây giữ theo ngôn ngữ gốc để tra cứu; ngắt dòng của PDF đã được nối lại. Các số [1]–[43] tương ứng với trích dẫn trong nội dung.

[1] K. Darvish, Y. Tirupachuri, G. Romualdi, L. Rapetti, D. Ferigo, F. J. A. Chavez, and D. Pucci, “Whole-body geometric retargeting for humanoid robots,” in 2019 IEEE-RAS 19th International Conference on Humanoid Robots (Humanoids). IEEE, 2019, pp. 679–686.

[2] T. He, Z. Luo, W. Xiao, C. Zhang, K. Kitani, C. Liu, and G. Shi, “Learning human-to-humanoid real-time whole-body teleoperation,” arXiv preprint arXiv:2403.04436, 2024.

[3] X. Cheng, Y. Ji, J. Chen, R. Yang, G. Yang, and X. Wang, “Expressive whole-body control for humanoid robots,” arXiv preprint arXiv:2402.16796, 2024.

[4] I. Radosavovic, T. Xiao, B. Zhang, T. Darrell, J. Malik, and K. Sreenath, “Real-world humanoid locomotion with reinforcement learning,” Science Robotics, vol. 9, no. 89, p. eadi9579, 2024.

[5] Z. Fu, Q. Zhao, Q. Wu, G. Wetzstein, and C. Finn, “Humanplus: Humanoid shadowing and imitation from humans,” in Conference on Robot Learning (CoRL), 2024.

[6] Y. Ze, Z. Chen, J. P. Araújo, Z. ang Cao, X. B. Peng, J. Wu, and C. K. Liu, “Twist: Teleoperated whole-body imitation system,” arXiv preprint arXiv:2505.02833, 2025.

[7] T. Zhang, B. Zheng, R. Nai, Y. Hu, Y.-J. Wang, G. Chen, F. Lin, J. Li, C. Hong, K. Sreenath, and Y. Gao, “Hub: Learning extreme humanoid balance,” arXiv preprint arXiv:2505.07294, 2025.

[8] W. Xie, J. Han, J. Zheng, H. Li, X. Liu, J. Shi, W. Zhang, C. Bai, and X. Li, “Kungfubot: Physics-based humanoid whole-body control for learning highly-dynamic skills,” arXiv preprint arXiv:2506.12851, 2025.

[9] N. Mahmood, N. Ghorbani, N. F. Troje, G. Pons-Moll, and M. J. Black, “AMASS: Archive of motion capture as surface shapes,” in International Conference on Computer Vision, Oct. 2019, pp. 5442–5451.

[10] A. Allshire, H. Choi, J. Zhang, D. McAllister, A. Zhang, C. M. Kim, T. Darrell, P. Abbeel, J. Malik, and A. Kanazawa, “Visual imitation enables contextual humanoid control,” arXiv preprint arXiv:2505.03729, 2025.

[11] T. He, J. Gao, W. Xiao, Y. Zhang, Z. Wang, J. Wang, Z. Luo, G. He, N. Sobanbabu, C. Pan, Z. Yi, G. Qu, K. Kitani, J. Hodgins, L. J. Fan, Y. Zhu, C. Liu, and G. Shi, “Asap: Aligning simulation and real-world physics for learning agile humanoid whole-body skills,” arXiv preprint arXiv:2502.01143, 2025.

[12] X. Gu, Y.-J. Wang, and J. Chen, “Humanoid-gym: Reinforcement learning for humanoid robot with zero-shot sim2real transfer,” arXiv preprint arXiv:2404.05695, 2024.

[13] T. He, W. Xiao, T. Lin, Z. Luo, Z. Xu, Z. Jiang, C. Liu, G. Shi, X. Wang, L. Fan, and Y. Zhu, “Hover: Versatile neural whole-body controller for humanoid robots,” arXiv preprint arXiv:2410.21229, 2024.

[14] T. He, Z. Luo, X. He, W. Xiao, C. Zhang, W. Zhang, K. Kitani, C. Liu, and G. Shi, “Omnih2o: Universal and dexterous human-to-humanoid whole-body teleoperation and learning,” arXiv preprint arXiv:2406.08858, 2024.

[15] T. E. Truong, Q. Liao, X. Huang, G. Tevet, C. K. Liu, and K. Sreenath, “Beyondmimic: From motion tracking to versatile humanoid control via guided diffusion,” arXiv preprint arXiv:2508.08241, 2025.

[16] Z. Popović and A. Witkin, “Physically based motion transformation,” in Proceedings of the 26th Annual Conference on Computer Graphics and Interactive Techniques, ser. SIGGRAPH ’99. USA: ACM Press/Addison-Wesley Publishing Co., 1999, p. 11–20.

[17] S. Tak and H.-S. Ko, “A physically-based motion retargeting filter,” ACM Trans. Graph., vol. 24, no. 1, p. 98–117, Jan. 2005.

[18] E. Lyard and N. Magnenat-Thalmann, “Motion adaptation based on character shape,” Comput. Animat. Virtual Worlds, vol. 19, no. 3–4, p. 189–198, Sept. 2008.

[19] K.-J. Choi and H.-S. Ko, “On-line motion retargetting,” in Proceedings. Seventh Pacific Conference on Computer Graphics and Applications (Cat. No.PR00293), 1999, pp. 32–42.

[20] S. Uk Kim, H. Jang, and J. Kim, “A variational u-net for motion retargeting,” Computer Animation and Virtual Worlds, vol. 31, no. 4–5, p. e1947, 2020.

[21] S. Lee, T. Kang, J. Park, J. Lee, and J. Won, “Same: Skeleton-agnostic motion embedding for character animation,” in SIGGRAPH Asia 2023 Conference Papers, 2023, pp. 1–11.

[22] R. Villegas, J. Yang, D. Ceylan, and H. Lee, “Neural kinematic networks for unsupervised motion retargetting,” in Proceedings of the IEEE conference on computer vision and pattern recognition, 2018, pp. 8639–8648.

[23] K. Aberman, P. Li, D. Lischinski, O. Sorkine-Hornung, D. Cohen-Or, and B. Chen, “Skeleton-aware networks for deep motion retargeting,” ACM Transactions on Graphics (TOG), vol. 39, no. 4, pp. 62–1, 2020.

[24] L. Hu, Z. Zhang, C. Zhong, B. Jiang, and S. Xia, “Pose-aware attention network for flexible motion retargeting by body part,” IEEE Transactions on Visualization and Computer Graphics, 2023.

[25] H. Zhang, Z. Chen, H. Xu, L. Hao, X. Wu, S. Xu, Z. Zhang, Y. Wang, and R. Xiong, “Semantics-aware motion retargeting with vision-language models,” in Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, 2024, pp. 2155–2164.

[26] C. K. Liu, A. Hertzmann, and Z. Popović, “Composition of complex optimal multi-character motions,” in Proceedings of the 2006 ACM SIGGRAPH/Eurographics symposium on Computer animation, 2006, pp. 215–222.

[27] Y. Zhang, D. Gopinath, Y. Ye, J. Hodgins, G. Turk, and J. Won, “Simulation and retargeting of complex multi-character interactions,” in ACM SIGGRAPH 2023 Conference Proceedings, 2023, pp. 1–11.

[28] I. Jang, S. Choi, S. Hong, C. Kim, and J. Noh, “Geometry-aware retargeting for two-skinned characters interaction,” ACM Transactions on Graphics (TOG), vol. 43, no. 6, pp. 1–17, 2024.

[29] Z. Liu, A. Mucherino, L. Hoyet, and F. Multon, “Surface based motion retargeting by preserving spatial relationship,” in Proceedings of the 11th ACM SIGGRAPH Conference on Motion, Interaction and Games, 2018, pp. 1–11.

[30] R. Villegas, D. Ceylan, A. Hertzmann, J. Yang, and J. Saito, “Contact-aware retargeting of skinned motion,” in Proceedings of the IEEE/CVF International Conference on Computer Vision, 2021, pp. 9720–9729.

[31] J. Zhang, J. Weng, D. Kang, F. Zhao, S. Huang, X. Zhe, L. Bao, Y. Shan, J. Wang, and Z. Tu, “Skinned motion retargeting with residual perception of motion semantics & geometry,” in Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, 2023, pp. 13 864–13 872.

[32] M. Stanley, L. Tao, and X. Zhang, “Robust motion mapping between human and humanoids using cycleautoencoder,” in 2021 IEEE International Conference on Robotics and Biomimetics (ROBIO). IEEE, 2021, pp. 93–98.

[33] Y. Yan, E. V. Mascaro, and D. Lee, “Imitationnet: Unsupervised human-to-robot motion retargeting via shared latent space,” in 2023 IEEE-RAS 22nd International Conference on Humanoid Robots (Humanoids). IEEE, 2023, pp. 1–8.

[34] S. Yagi, M. Tada, E. Uchibe, S. Kanoga, T. Matsubara, and J. Morimoto, “Unsupervised neural motion retargeting for humanoid teleoperation,” arXiv preprint arXiv:2406.00727, 2024.

[35] L. Penco, B. Clément, V. Modugno, E. M. Hoffman, G. Nava, D. Pucci, N. G. Tsagarakis, J.-B. Mouret, and S. Ivaldi, “Robust real-time whole-body motion retargeting from human to humanoid,” in 2018 IEEE-RAS 18th International Conference on Humanoid Robots (Humanoids). IEEE, 2018, pp. 425–432.

[36] A. Tang, T. Hiraoka, N. Hiraoka, F. Shi, K. Kawaharazuka, K. Kojima, K. Okada, and M. Inaba, “Humanmimic: Learning natural locomotion and transitions for humanoid robot via wasserstein adversarial imitation,” in 2024 IEEE International Conference on Robotics and Automation (ICRA). IEEE, 2024, pp. 13 107–13 114.

[37] M. Loper, N. Mahmood, J. Romero, G. Pons-Moll, and M. J. Black, “SMPL: A skinned multi-person linear model,” ACM Trans. Graphics (Proc. SIGGRAPH Asia), vol. 34, no. 6, pp. 248:1–248:16, Oct. 2015.

[38] Z. Luo, J. Cao, A. W. Winkler, K. Kitani, and W. Xu, “Perpetual humanoid control for real-time simulated avatars,” in International Conference on Computer Vision (ICCV), 2023.

[39] Z. Jiang, Y. Xie, J. Li, Y. Yuan, Y. Zhu, and Y. Zhu, “Harmon: Whole-body motion generation of humanoid robots from language descriptions,” arXiv preprint arXiv:2410.12773, 2024.

[40] C. Tessler, J. Juravsky, Y. Guo, Y. Jiang, E. Coumans, and X. B. Peng, “Protomotions: Physics-based character animation,” https://github.com/NVLabs/ProtoMotions/, 2024.

[41] K. Zakka, “Mink: Python inverse kinematics based on MuJoCo,” May 2025. [Online]. Available: https://github.com/kevinzakka/mink

[42] F. G. Harvey, M. Yurick, D. Nowrouzezahrai, and C. Pal, “Robust motion in-betweening,” vol. 39, no. 4, 2020.

[43] G. Pavlakos, V. Choutas, N. Ghorbani, T. Bolkart, A. A. A. Osman, D. Tzionas, and M. J. Black, “Expressive body capture: 3d hands, face, and body from a single image,” in Proceedings IEEE Conf. on Computer Vision and Pattern Recognition (CVPR), 2019.
