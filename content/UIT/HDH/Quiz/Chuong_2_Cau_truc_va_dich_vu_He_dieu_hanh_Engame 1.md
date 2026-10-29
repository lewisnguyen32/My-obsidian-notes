TITLE: Chương 2 - Cấu trúc và dịch vụ hệ điều hành

1. Trong cấu trúc microkernel, các module ở user space giao tiếp với nhau bằng cơ chế nào? Điều này dẫn tới hạn chế tiềm ẩn gì?
A. Ngắt phần cứng; mất dữ liệu
B. Truyền thông điệp (message passing); có thể giảm hiệu năng do chi phí chuyển thông điệp giữa user space và kernel
C. Gọi hàm trực tiếp; không có hạn chế
D. Chia sẻ thanh ghi; tốn bộ nhớ
ANSWER: B

2. Loader và debugger thuộc nhóm chương trình hệ thống nào?
A. Nạp, thực thi và giúp tìm lỗi chương trình
B. Thông tin trạng thái
C. Giao tiếp
D. Quản lý hệ thống file
ANSWER: A

3. Trong cấu trúc phân lớp (layered approach), phát biểu nào đúng?
A. Lớp dưới cùng là phần cứng, lớp trên cùng là giao tiếp người dùng; một lớp chỉ gọi hàm của lớp dưới và được gọi bởi lớp trên
B. Lớp trên cùng là phần cứng, lớp dưới cùng là giao tiếp người dùng
C. Một lớp có thể gọi tùy ý hàm của bất kỳ lớp nào
D. Các lớp hoàn toàn độc lập, không gọi nhau
ANSWER: A

4. Chương trình nào sau đây được xếp vào nhóm "hỗ trợ ngôn ngữ lập trình" trong các chương trình hệ thống?
A. Compiler, assembler, interpreter
B. Web browser
C. Lệnh date, time
D. File editor
ANSWER: A

5. Vì sao hệ điều hành cần hệ thống lưu trữ thứ cấp?
A. Vì thiết bị I/O không có bộ đệm
B. Vì bộ nhớ chính có kích thước nhỏ và là môi trường lưu trữ không bền vững
C. Vì bộ nhớ chính có tốc độ quá nhanh
D. Vì CPU không thể truy xuất bộ nhớ chính
ANSWER: B

6. Ý tưởng chính của cấu trúc microkernel là gì?
A. Chia hệ điều hành thành các lớp chỉ gọi lớp dưới
B. Loại bỏ hoàn toàn kernel
C. Đưa toàn bộ chức năng hệ điều hành vào kernel
D. Chuyển bớt chức năng từ kernel space sang user space, kernel chỉ giữ chức năng tối thiểu như quản lý tiến trình, bộ nhớ và cơ chế giao tiếp giữa các tiến trình
ANSWER: D

7. Các cơ chế buffering, caching, spooling thuộc thành phần nào của hệ điều hành?
A. Quản lý tiến trình
B. Hệ thống bảo vệ
C. Quản lý hệ thống I/O
D. Quản lý file
ANSWER: C

8. Nhiệm vụ nào sau đây là của hệ điều hành trong quản lý đĩa?
A. Buffering, caching, spooling
B. Job scheduling, context switching, aging
C. Login control, accounting, authentication
D. Free space management, storage allocation, disk scheduling
ANSWER: D

9. Dịch vụ "sao lưu và phục hồi dữ liệu" thuộc thành phần nào của hệ điều hành?
A. Quản lý tiến trình
B. Hệ thống thông dịch lệnh
C. Quản lý file
D. Quản lý bộ nhớ chính
ANSWER: C

10. Điểm khác biệt cơ bản giữa tiến trình (process) và chương trình (program) là gì?
A. Tiến trình là chương trình đang thực thi (thực thể chủ động), còn chương trình là thực thể bị động lưu trên đĩa
B. Chương trình là thực thể chủ động, tiến trình là thực thể bị động
C. Tiến trình và chương trình hoàn toàn giống nhau
D. Chương trình luôn nằm trong bộ nhớ chính còn tiến trình nằm trên đĩa
ANSWER: A

11. Thuật ngữ tiếng Anh "disk scheduling" có nghĩa là gì?
A. Quản lý không gian trống
B. Cấp phát không gian lưu trữ
C. Định thời hoạt động cho đĩa
D. Định dạng đĩa
ANSWER: C

12. Lời gọi hệ thống (system call) có vai trò gì?
A. Là chương trình ứng dụng chạy nền
B. Cung cấp giao diện giữa người dùng và phần cứng mà không qua hệ điều hành
C. Cung cấp giao diện giữa tiến trình và hệ điều hành, cho phép tiến trình gọi các dịch vụ mà hệ điều hành cung cấp
D. Là phần cứng xử lý ngắt
ANSWER: C

13. Lời gọi hệ thống thường được viết bằng ngôn ngữ nào và được truy cập chủ yếu qua thành phần nào?
A. Python; qua device driver
B. Assembly; qua shell
C. C hoặc C++; qua Application Programming Interface (API)
D. Java; qua trình duyệt web
ANSWER: C

14. Ba loại giao diện người dùng phổ biến của hệ điều hành hiện nay là gì?
A. Win32, POSIX, Java
B. Kernel, Shell, Driver
C. API, ABI, ISA
D. Command-Line Interface (CLI), Graphical User Interface (GUI), Touch-screen
ANSWER: D

15. Hệ điều hành phân lớp có 5 lớp đánh số từ 0 (phần cứng) đến 4 (giao diện người dùng). Một hàm ở lớp 2 được phép gọi trực tiếp hàm của lớp nào?
A. Chỉ lớp 3 và 4
B. Tất cả các lớp từ 0 đến 4
C. Chỉ các lớp 0 và 1 (các lớp bên dưới)
D. Không được gọi lớp nào
ANSWER: C

16. Một lời gọi hệ thống cần truyền 10 tham số trong khi CPU chỉ có 6 thanh ghi dành cho tham số. Phương pháp hợp lý nhất là gì?
A. Bỏ bớt 4 tham số
B. Lưu các tham số vào một vùng nhớ (hoặc đẩy vào stack) và truyền địa chỉ vùng nhớ đó qua thanh ghi
C. Gọi lời gọi hệ thống 10 lần, mỗi lần một tham số
D. Chuyển chương trình sang chế độ hạt nhân để tự đọc tham số
ANSWER: B

17. Hệ điều hành nào được nêu làm ví dụ cho cấu trúc phân lớp?
A. Mach
B. Windows
C. THE
D. Android
ANSWER: C

18. Hai cách trao đổi thông tin giữa các tiến trình mà hệ điều hành cung cấp là gì?
A. Polling và interrupt
B. Paging và segmentation
C. Chia sẻ bộ nhớ (shared memory) và chuyển thông điệp (message passing)
D. Spooling và caching
ANSWER: C

19. Thuật ngữ "spooling" thường gặp nhất trong tình huống nào sau đây?
A. Đưa các tác vụ in vào hàng đợi trên đĩa để máy in xử lý lần lượt trong khi các chương trình tiếp tục chạy
B. Cấp phát vùng nhớ cho biến cục bộ
C. Mã hóa mật khẩu người dùng
D. Chuyển tiến trình từ ready sang running
ANSWER: A

20. Nhiệm vụ nào sau đây là của hệ thống bảo vệ (protection system)?
A. Phân định truy cập tài nguyên hợp pháp và bất hợp pháp (authorized/unauthorized), kiểm soát đăng nhập/xuất, thi hành các chính sách
B. Biên dịch chương trình người dùng
C. Quản lý vùng nhớ heap
D. Định thời CPU cho các tiến trình
ANSWER: A
