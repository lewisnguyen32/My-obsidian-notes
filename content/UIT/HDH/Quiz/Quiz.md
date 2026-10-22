# BỘ 60 CÂU HỎI TRẮC NGHIỆM HỆ ĐIỀU HÀNH

Quy ước: Đáp án đúng được gạch chân. Giữ nguyên thứ tự và các lựa chọn A, B, C, D theo đề gốc.

# PHẦN I – TỔNG QUAN HỆ ĐIỀU HÀNH (40 CÂU)

### Câu 1. Một hệ thống máy tính có thể chia thành 4 thành phần. Thứ tự từ thấp đến cao nào sau đây là đúng?

- A. Hệ điều hành – Phần cứng – Ứng dụng – Người dùng
    
- B. Phần cứng – Chương trình ứng dụng – Hệ điều hành – Người dùng
    
- C. Phần cứng – Hệ điều hành – Chương trình ứng dụng – Người dùng
    
- D. Người dùng – Ứng dụng – Hệ điều hành – Phần cứng
    

### Câu 2. Một máy chủ có 2 processor (chip vật lý), mỗi processor là CPU 8 lõi (core). Tổng số lõi tính toán của máy chủ là bao nhiêu và hệ thống này được xếp vào loại nào?

- A. 16 lõi, hệ thống đa bộ xử lý (multiprocessor) với CPU đa lõi (multicore)
    
- B. 2 lõi, hệ thống đa lõi
    
- C. 8 lõi, hệ thống đơn bộ xử lý
    
- D. 10 lõi, hệ thống gom cụm (clustered)
    

### Câu 3. Mục đích chính của bộ nhớ thứ cấp (secondary storage) là gì?

- A. Lưu trữ interrupt vector
    
- B. Tăng tốc độ xung nhịp CPU
    
- C. Mở rộng cho bộ nhớ chính, cung cấp khả năng lưu trữ không bay hơi với dung lượng lớn
    
- D. Thay thế thanh ghi của CPU
    

### Câu 4. Ngắt chuyển điều khiển đến trình phục vụ ngắt (interrupt service routine) thông qua cấu trúc nào?

- A. Ready queue
    
- B. Process Control Block
    
- C. Bảng trang (page table)
    
- D. Interrupt vector – bảng chứa địa chỉ của các service routine
    

### Câu 5. Ngắt do phần mềm tạo ra vì một lỗi hoặc một yêu cầu của người dùng được gọi là gì?

- A. Hardware interrupt
    
- B. Trap hoặc exception
    
- C. Spooling
    
- D. Context switch
    

### Câu 6. NUMA là viết tắt của thuật ngữ nào?

- A. Network Unified Memory Architecture
    
- B. Non-Uniform Memory Access
    
- C. Non-Unified Multiprocessing Architecture
    
- D. Nested User Mode Access
    

### Câu 7. Phân biệt các khái niệm: "Core" là gì?

- A. Một con chip vật lý chứa nhiều CPU
    
- B. Đơn vị tính toán cơ bản của CPU
    
- C. Thành phần phần mềm điều phối tiến trình
    
- D. Hệ thống có nhiều bộ xử lý
    

### Câu 8. Phát biểu nào đúng về bộ nhớ chính (main memory)?

- A. Là thiết bị lưu trữ dung lượng lớn duy nhất mà CPU truy xuất trực tiếp, truy xuất ngẫu nhiên và thường dùng công nghệ DRAM
    
- B. Là thiết bị lưu trữ thứ cấp
    
- C. Chỉ được truy xuất tuần tự giống băng từ
    
- D. Là bộ nhớ không bay hơi, giữ dữ liệu khi mất điện
    

### Câu 9. Phát biểu nào đúng về chương trình hệ thống (system program)?

- A. Chỉ có trên các hệ điều hành di động
    
- B. Là một phần của nhân và luôn chạy ở chế độ kernel
    
- C. Là mọi chương trình không liên kết với hoạt động của hệ thống
    
- D. Được đóng gói cùng hệ điều hành nhưng không phải là một phần của nhân
    

### Câu 10. Sắp xếp các thiết bị lưu trữ sau theo tốc độ truy xuất giảm dần: (1) Thanh ghi, (2) Bộ nhớ chính, (3) Cache, (4) Đĩa cứng HDD.

- A. 4 – 2 – 3 – 1
    
- B. 3 – 1 – 2 – 4
    
- C. 2 – 1 – 3 – 4
    
- D. 1 – 3 – 2 – 4
    

### Câu 11. Thành phần nào sau đây là ví dụ của chương trình ứng dụng (application program)?

- A. Hệ quản trị cơ sở dữ liệu (database system)
    
- B. Bộ nạp khởi động (bootstrap loader)
    
- C. Trình điều khiển ngắt (interrupt handler)
    
- D. Bit chế độ (mode bit)
    

### Câu 12. Theo bài giảng, khi CPU đang thực thi mã của ứng dụng người dùng thì bit chế độ (mode bit) có giá trị bao nhiêu?

- A. 2
    
- B. Không xác định
    
- C. 0 (hạt nhân)
    
- D. 1 (người dùng)
    

### Câu 13. Thuật ngữ "high-availability" khi nói về hệ thống gom cụm nghĩa là:

- A. Hệ thống có giá thành thấp
    
- B. Mọi tiến trình đều được ưu tiên như nhau
    
- C. Dịch vụ được cung cấp liên tục cho dù một phần cứng trong cụm bị hỏng
    
- D. Hệ thống có nhiều bộ nhớ trống
    

### Câu 14. Thuật ngữ "middleware" trong một số hệ điều hành hiện đại dùng để chỉ:

- A. Phần cứng nằm giữa CPU và bộ nhớ chính
    
- B. Chương trình người dùng chạy ở chế độ hạt nhân
    
- C. Một tập các khung phần mềm (software framework) cung cấp dịch vụ bổ sung cho nhà phát triển ứng dụng như cơ sở dữ liệu, đa phương tiện, đồ họa
    
- D. Lớp bộ nhớ đệm giữa thanh ghi và cache
    

### Câu 15. Thuật ngữ tiếng Anh "volatility" trong phân cấp lưu trữ đề cập đến đặc tính nào?

- A. Dung lượng tối đa của thiết bị
    
- B. Tốc độ truy xuất ngẫu nhiên
    
- C. Khả năng lưu giữ dữ liệu khi không có nguồn điện
    
- D. Giá thành trên mỗi byte
    

### Câu 16. Trong gom cụm bất đối xứng (asymmetric clustering), máy ở chế độ "hot-standby" có vai trò gì?

- A. Chạy tất cả ứng dụng của cụm
    
- B. Lưu trữ toàn bộ dữ liệu của cụm
    
- C. Định thời CPU cho các máy còn lại
    
- D. Giám sát và sẵn sàng thay thế khi máy đang chạy ứng dụng bị hỏng
    

### Câu 17. Trong hệ thống đa chương (multiprogramming), khi công việc đang chạy phải chờ I/O thì hệ điều hành làm gì?

- A. Để CPU rảnh cho đến khi I/O hoàn tất
    
- B. Chuyển (switch) sang thực thi một công việc khác trong bộ nhớ
    
- C. Khởi động lại máy
    
- D. Hủy công việc đang chờ I/O
    

### Câu 18. Trong máy tính hiện đại, CPU và các bộ điều khiển thiết bị (device controller) kết nối với nhau thông qua thành phần nào để truy xuất bộ nhớ chia sẻ?

- A. Interrupt vector
    
- B. Mạng lưu trữ SAN
    
- C. Ngắt
    
- D. Bus
    

### Câu 19. Trong mô hình đa xử lý đối xứng (symmetric multiprocessing – SMP):

- A. Mỗi bộ xử lý cùng thực hiện tất cả các công việc
    
- B. Mỗi bộ xử lý chỉ thực thi một loại công việc khác nhau
    
- C. Các bộ xử lý không dùng chung bộ nhớ
    
- D. Chỉ có một bộ xử lý chạy hệ điều hành, các bộ xử lý khác ở chế độ hot-standby
    

### Câu 20. Ưu điểm nào sau đây KHÔNG phải là ưu điểm của hệ thống đa bộ xử lý?

- A. Loại bỏ hoàn toàn nhu cầu đồng bộ giữa các bộ xử lý
    
- B. Tăng năng suất hệ thống (throughput)
    
- C. Độ tin cậy cao khi một bộ xử lý hỏng
    
- D. Kinh tế do dùng chung tài nguyên như đĩa
    

### Câu 21. Chương trình duy nhất luôn chạy tại mọi thời điểm khi máy tính hoạt động được gọi là gì?

- A. Nhân (kernel)
    
- B. Device driver
    
- C. Shell
    
- D. Middleware
    

### Câu 22. Cụm từ "interrupt driven" khi nói về hệ điều hành có nghĩa là:

- A. Hệ điều hành không bao giờ bị ngắt
    
- B. Hệ điều hành hoạt động định hướng theo ngắt
    
- C. Hệ điều hành chỉ xử lý ngắt phần mềm
    
- D. Hệ điều hành chỉ chạy khi người dùng nhấn phím
    

### Câu 23. Đa nhiệm (multitasking) được mô tả như thế nào so với đa chương?

- A. Chỉ áp dụng cho hệ thống gom cụm
    
- B. Là cách gọi khác của đơn chương
    
- C. Là sự mở rộng của đa chương, CPU chuyển đổi công việc thường xuyên hơn để người dùng có thể tương tác với từng công việc khi nó đang chạy
    
- D. Không cho phép nhiều chương trình nằm trong bộ nhớ
    

### Câu 24. Đặc điểm của hệ thống đơn chương (uniprogramming) là gì?

- A. Nhiều chương trình nằm trong bộ nhớ và CPU luân phiên giữa chúng
    
- B. Chỉ một công việc được nạp vào bộ nhớ tại một thời điểm và các công việc thi hành tuần tự
    
- C. CPU chuyển đổi công việc rất thường xuyên để người dùng tương tác
    
- D. Nhiều CPU cùng thực thi một chương trình
    

### Câu 25. Hai chế độ hoạt động cơ bản (modes of operation) của hệ điều hành là:

- A. Batch mode và interactive mode
    
- B. User mode và kernel mode
    
- C. Safe mode và normal mode
    
- D. Single mode và multi mode
    

### Câu 26. Hai mục tiêu chính của hệ điều hành là gì?

- A. Thay thế phần cứng và loại bỏ nhu cầu dùng chương trình ứng dụng
    
- B. Biên dịch chương trình và kết nối Internet
    
- C. Tăng tốc độ xung nhịp CPU và mở rộng dung lượng bộ nhớ
    
- D. Giúp người dùng dễ dàng sử dụng hệ thống và quản lý, cấp phát tài nguyên hệ thống một cách hiệu quả
    

### Câu 27. Hệ điều hành được định nghĩa là gì?

- A. Chương trình ứng dụng giúp người dùng soạn thảo văn bản và duyệt web
    
- B. Tập hợp các thiết bị phần cứng như CPU, bộ nhớ và thiết bị nhập/xuất
    
- C. Trình biên dịch dịch mã nguồn sang mã máy
    
- D. Chương trình trung gian giữa phần cứng máy tính và người sử dụng, điều khiển và phối hợp việc sử dụng phần cứng, cung cấp dịch vụ cơ bản cho ứng dụng
    

### Câu 28. Hệ thống đa bộ xử lý (multiprocessor systems) còn có tên gọi khác là gì?

- A. Loosely-coupled systems
    
- B. Batch systems
    
- C. Distributed clusters
    
- D. Parallel systems hoặc tightly-coupled systems
    

### Câu 29. Hệ thống gom cụm (clustered systems) thường chia sẻ không gian lưu trữ thông qua thành phần nào?

- A. Interrupt vector
    
- B. Bus hệ thống nội bộ của một CPU
    
- C. Mạng lưu trữ khu vực (storage-area network – SAN)
    
- D. Thanh ghi dùng chung
    

### Câu 30. Hệ thống lưu trữ được tổ chức phân cấp dựa trên những tiêu chí nào?

- A. Loại hệ điều hành và loại ứng dụng
    
- B. Màu sắc, kích thước vật lý và nhà sản xuất
    
- C. Số lõi CPU, số tiến trình và số người dùng
    
- D. Tốc độ truy xuất (speed), chi phí (cost) và khả năng giữ dữ liệu khi mất điện (volatility)
    

### Câu 31. Hệ thống xử lý theo lô (batch system), lưu trữ trên băng từ, xuất hiện ở thế hệ nào?

- A. Thế hệ 1
    
- B. Thế hệ 4
    
- C. Thế hệ 5
    
- D. Thế hệ 2
    

### Câu 32. Khái niệm đa chương và hệ điều hành chia sẻ thời gian (như CTSS của MIT, MULTICS, UNIX) ra đời ở thế hệ nào?

- A. Thế hệ 2 (1955–1965)
    
- B. Thế hệ 5 (1990–nay)
    
- C. Thế hệ 1 (1945–1955)
    
- D. Thế hệ 3 (1965–1980)
    

### Câu 33. Khi bộ điều khiển thiết bị hoàn tất thao tác, nó báo cho CPU biết bằng cách nào?

- A. Chờ CPU kiểm tra định kỳ bộ đệm cục bộ
    
- B. Ghi trực tiếp vào thanh ghi PC của CPU
    
- C. Khởi động lại hệ thống
    
- D. Phát sinh một ngắt (interrupt)
    

### Câu 34. Lệnh đặc quyền (privileged instruction) có đặc điểm gì?

- A. Chỉ dùng cho các thiết bị I/O
    
- B. Chỉ được thực thi ở chế độ hạt nhân
    
- C. Chỉ chạy ở chế độ người dùng
    
- D. Có thể chạy ở cả hai chế độ người dùng và hạt nhân
    

### Câu 35. Lợi ích chính của đa chương (multiprogramming) là gì?

- A. Tận dụng thời gian rảnh, tăng hiệu suất sử dụng CPU (CPU utilization)
    
- B. Giúp chương trình chạy ở chế độ hạt nhân
    
- C. Loại bỏ nhu cầu dùng ngắt
    
- D. Giảm dung lượng bộ nhớ cần dùng
    

### Câu 36. Lý do chính của việc có nhiều chế độ hoạt động (user mode/kernel mode) là gì?

- A. Tiết kiệm năng lượng
    
- B. Tăng tốc độ thực thi chương trình người dùng
    
- C. Giảm số lượng ngắt
    
- D. Cho phép hệ điều hành bảo vệ chính nó và các thành phần khác của hệ thống
    

### Câu 37. Mỗi loại bộ điều khiển thiết bị (device controller) được hệ điều hành quản lý thông qua thành phần nào?

- A. Job scheduler
    
- B. Mode bit
    
- C. Interrupt vector
    
- D. Device driver
    

### Câu 38. Một chương trình người dùng gọi lời gọi hệ thống để đọc file. Chuỗi thay đổi bit chế độ nào sau đây là đúng?

- A. 1 → 1 → 1
    
- B. 0 → 0 → 0
    
- C. 0 → 1 → 0
    
- D. 1 → 0 → 1
    

### Câu 39. Một chương trình thực hiện phép chia cho 0 trong lúc chạy. Sự kiện được phát sinh trong trường hợp này thuộc loại nào?

- A. Trap/exception do phần mềm gây ra
    
- B. Ngắt phần cứng từ bộ điều khiển đĩa
    
- C. Tín hiệu hoàn tất DMA
    
- D. Ngắt đồng hồ (clock interrupt)
    

### Câu 40. Một hệ thống chỉ chạy một chương trình tại một thời điểm. Chương trình dùng CPU 20 ms rồi chờ I/O 80 ms, lặp lại liên tục. Hiệu suất sử dụng CPU xấp xỉ bao nhiêu và giải pháp được đề cập trong chương 1 để tăng hiệu suất này là gì?

- A. 25%; tăng dung lượng đĩa
    
- B. 100%; không cần giải pháp gì
    
- C. 80%; dùng đơn chương
    
- D. 20%; dùng đa chương để CPU thực thi công việc khác khi đang chờ I/O
    

# PHẦN II – CẤU TRÚC VÀ DỊCH VỤ HỆ ĐIỀU HÀNH (20 CÂU)

### Câu 1. Trong cấu trúc microkernel, các module ở user space giao tiếp với nhau bằng cơ chế nào? Điều này dẫn tới hạn chế tiềm ẩn gì?

- A. Ngắt phần cứng; mất dữ liệu
    
- B. Truyền thông điệp (message passing); có thể giảm hiệu năng do chi phí chuyển thông điệp giữa user space và kernel
    
- C. Gọi hàm trực tiếp; không có hạn chế
    
- D. Chia sẻ thanh ghi; tốn bộ nhớ
    

### Câu 2. Loader và debugger thuộc nhóm chương trình hệ thống nào?

- A. Nạp, thực thi và giúp tìm lỗi chương trình
    
- B. Thông tin trạng thái
    
- C. Giao tiếp
    
- D. Quản lý hệ thống file
    

### Câu 3. Trong cấu trúc phân lớp (layered approach), phát biểu nào đúng?

- A. Lớp dưới cùng là phần cứng, lớp trên cùng là giao tiếp người dùng; một lớp chỉ gọi hàm của lớp dưới và được gọi bởi lớp trên
    
- B. Lớp trên cùng là phần cứng, lớp dưới cùng là giao tiếp người dùng
    
- C. Một lớp có thể gọi tùy ý hàm của bất kỳ lớp nào
    
- D. Các lớp hoàn toàn độc lập, không gọi nhau
    

### Câu 4. Chương trình nào sau đây được xếp vào nhóm "hỗ trợ ngôn ngữ lập trình" trong các chương trình hệ thống?

- A. Compiler, assembler, interpreter
    
- B. Web browser
    
- C. Lệnh date, time
    
- D. File editor
    

### Câu 5. Vì sao hệ điều hành cần hệ thống lưu trữ thứ cấp?

- A. Vì thiết bị I/O không có bộ đệm
    
- B. Vì bộ nhớ chính có kích thước nhỏ và là môi trường lưu trữ không bền vững
    
- C. Vì bộ nhớ chính có tốc độ quá nhanh
    
- D. Vì CPU không thể truy xuất bộ nhớ chính
    

### Câu 6. Ý tưởng chính của cấu trúc microkernel là gì?

- A. Chia hệ điều hành thành các lớp chỉ gọi lớp dưới
    
- B. Loại bỏ hoàn toàn kernel
    
- C. Đưa toàn bộ chức năng hệ điều hành vào kernel
    
- D. Chuyển bớt chức năng từ kernel space sang user space, kernel chỉ giữ chức năng tối thiểu như quản lý tiến trình, bộ nhớ và cơ chế giao tiếp giữa các tiến trình
    

### Câu 7. Các cơ chế buffering, caching, spooling thuộc thành phần nào của hệ điều hành?

- A. Quản lý tiến trình
    
- B. Hệ thống bảo vệ
    
- C. Quản lý hệ thống I/O
    
- D. Quản lý file
    

### Câu 8. Nhiệm vụ nào sau đây là của hệ điều hành trong quản lý đĩa?

- A. Buffering, caching, spooling
    
- B. Job scheduling, context switching, aging
    
- C. Login control, accounting, authentication
    
- D. Free space management, storage allocation, disk scheduling
    

### Câu 9. Dịch vụ "sao lưu và phục hồi dữ liệu" thuộc thành phần nào của hệ điều hành?

- A. Quản lý tiến trình
    
- B. Hệ thống thông dịch lệnh
    
- C. Quản lý file
    
- D. Quản lý bộ nhớ chính
    

### Câu 10. Điểm khác biệt cơ bản giữa tiến trình (process) và chương trình (program) là gì?

- A. Tiến trình là chương trình đang thực thi (thực thể chủ động), còn chương trình là thực thể bị động lưu trên đĩa
    
- B. Chương trình là thực thể chủ động, tiến trình là thực thể bị động
    
- C. Tiến trình và chương trình hoàn toàn giống nhau
    
- D. Chương trình luôn nằm trong bộ nhớ chính còn tiến trình nằm trên đĩa
    

### Câu 11. Thuật ngữ tiếng Anh "disk scheduling" có nghĩa là gì?

- A. Quản lý không gian trống
    
- B. Cấp phát không gian lưu trữ
    
- C. Định thời hoạt động cho đĩa
    
- D. Định dạng đĩa
    

### Câu 12. Lời gọi hệ thống (system call) có vai trò gì?

- A. Là chương trình ứng dụng chạy nền
    
- B. Cung cấp giao diện giữa người dùng và phần cứng mà không qua hệ điều hành
    
- C. Cung cấp giao diện giữa tiến trình và hệ điều hành, cho phép tiến trình gọi các dịch vụ mà hệ điều hành cung cấp
    
- D. Là phần cứng xử lý ngắt
    

### Câu 13. Lời gọi hệ thống thường được viết bằng ngôn ngữ nào và được truy cập chủ yếu qua thành phần nào?

- A. Python; qua device driver
    
- B. Assembly; qua shell
    
- C. C hoặc C++; qua Application Programming Interface (API)
    
- D. Java; qua trình duyệt web
    

### Câu 14. Ba loại giao diện người dùng phổ biến của hệ điều hành hiện nay là gì?

- A. Win32, POSIX, Java
    
- B. Kernel, Shell, Driver
    
- C. API, ABI, ISA
    
- D. Command-Line Interface (CLI), Graphical User Interface (GUI), Touch-screen
    

### Câu 15. Hệ điều hành phân lớp có 5 lớp đánh số từ 0 (phần cứng) đến 4 (giao diện người dùng). Một hàm ở lớp 2 được phép gọi trực tiếp hàm của lớp nào?

- A. Chỉ lớp 3 và 4
    
- B. Tất cả các lớp từ 0 đến 4
    
- C. Chỉ các lớp 0 và 1 (các lớp bên dưới)
    
- D. Không được gọi lớp nào
    

### Câu 16. Một lời gọi hệ thống cần truyền 10 tham số trong khi CPU chỉ có 6 thanh ghi dành cho tham số. Phương pháp hợp lý nhất là gì?

- A. Bỏ bớt 4 tham số
    
- B. Lưu các tham số vào một vùng nhớ (hoặc đẩy vào stack) và truyền địa chỉ vùng nhớ đó qua thanh ghi
    
- C. Gọi lời gọi hệ thống 10 lần, mỗi lần một tham số
    
- D. Chuyển chương trình sang chế độ hạt nhân để tự đọc tham số
    

### Câu 17. Hệ điều hành nào được nêu làm ví dụ cho cấu trúc phân lớp?

- A. Mach
    
- B. Windows
    
- C. THE
    
- D. Android
    

### Câu 18. Hai cách trao đổi thông tin giữa các tiến trình mà hệ điều hành cung cấp là gì?

- A. Polling và interrupt
    
- B. Paging và segmentation
    
- C. Chia sẻ bộ nhớ (shared memory) và chuyển thông điệp (message passing)
    
- D. Spooling và caching
    

### Câu 19. Thuật ngữ "spooling" thường gặp nhất trong tình huống nào sau đây?

- A. Đưa các tác vụ in vào hàng đợi trên đĩa để máy in xử lý lần lượt trong khi các chương trình tiếp tục chạy
    
- B. Cấp phát vùng nhớ cho biến cục bộ
    
- C. Mã hóa mật khẩu người dùng
    
- D. Chuyển tiến trình từ ready sang running
    

### Câu 20. Nhiệm vụ nào sau đây là của hệ thống bảo vệ (protection system)?

- A. Phân định truy cập tài nguyên hợp pháp và bất hợp pháp (authorized/unauthorized), kiểm soát đăng nhập/xuất, thi hành các chính sách
    
- B. Biên dịch chương trình người dùng
    
- C. Quản lý vùng nhớ heap
    
- D. Định thời CPU cho các tiến trình
    

## BẢNG ĐÁP ÁN TỔNG HỢP

|Câu|Phần I|Phần II|
|---|---|---|
|1|C|B|
|2|A|A|
|3|C|A|
|4|D|A|
|5|B|B|
|6|B|D|
|7|B|C|
|8|A|D|
|9|D|C|
|10|D|A|
|11|A|C|
|12|D|C|
|13|C|C|
|14|C|D|
|15|C|C|
|16|D|B|
|17|B|C|
|18|D|C|
|19|A|A|
|20|A|A|
|21|A|—|
|22|B|—|
|23|C|—|
|24|B|—|
|25|B|—|
|26|D|—|
|27|D|—|
|28|D|—|
|29|C|—|
|30|D|—|
|31|D|—|
|32|D|—|
|33|D|—|
|34|B|—|
|35|A|—|
|36|D|—|
|37|D|—|
|38|D|—|
|39|A|—|
|40|D|—|
