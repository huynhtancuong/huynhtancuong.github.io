---
title: Lịch sử ra đời của Linux
author: huynhtancuong
date: 2022-07-15 09:30:00 +0300
categories: [Courses, UNIX and Linux in Infocommunication]
tags: [unix, linux. history]
math: true
mermaid: true
image: 
    path: /assets/img/posts/history-of-linux/history-of-linux-thumbnail.png
---

> Bài viết này là một phần của khóa học UNIX and Linux in Infocommunication được dạy bởi trường đại học ITMO. Bạn có thể xem thêm các bài viết của khóa học này trong cùng category của bài viết.
{: .prompt-info}


Khi nói về lịch sử của Linux, chúng ta có thể nhớ lại một câu nói nổi tiếng.
> We make our inventions stand on the shoulders of giants.

Tạm dịch là "*Chúng tôi sáng chế ra những phát minh trên vai của những người khổng lồ*." Đây là một câu nói ẩn dụ có ý nghĩa là sử dụng sự hiểu biết của các nhà tư tưởng lớn đã đi trước để đạt được những tiến bộ hơn về trí tuệ. Nhưng chúng ta cần phải hiểu rằng nhiều trong số những người khổng lồ đó đã ngã xuống. Nhưng sự ngã xuống đó có thể là một bài học tốt cho những developer kế tiếp. 

### Dự án MULTICS

Một trong những kẻ khổng lồ đó chính là dự án **MULTICS**. Dự án MULTICS bắt đầu phát triển vào năm 1965 như là một dự án nghiên cứu bởi Đại học MIT, General Electric và phòng thí nghiệm Bell Labs với mục đích là tạo ra một hệ điều hành phân bổ thời gian (time-sharing), đa tiến trình (multiprocessing) và phục vụ được đồng thời nhiều người dùng (multiuser interactive). 

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8b/Multics-logo.svg/1024px-Multics-logo.svg.png){: style="max-width: 50%" .right}

Sau vài năm phát triển, sự nhiệt huyết của những nhà phát triển trong dự án càng ngày càng giảm bởi vì hệ thống mà nhóm này phát triển đã trở nên ngày càng phức tạp và nhóm này ngày càng không tin rằng dự án này có thể hoàn thành. Cuối cùng, Bell Labs kết thúc dự án vào năm 1969, nhưng bù lại thì những người tham gia vào dự án đã có được rất nhiều kinh nghiệm từ nó. Một trong số bọn họ là Ken Thompson và Dennis Ritchie - nhà sáng lập của hệ điều hành UNIX. 

### Sự ra đời của hệ điều hành UNIX

![Máy tính PDP7](https://habrastorage.org/getpro/habr/post_images/930/ba8/0df/930ba80dfbd79c7ac1956897576cf166.jpg){: style="max-width: 50%" .right}

Điều này có vẻ khó tin, nhưng sự ra đời của hệ điều hành UNIX liên quan chặt chẽ đến trò chơi điện tử. Đầu năm 1969, khi Ken Thompson phát hiện ra một cái máy tính PDP-7 nằm giữa một đống lộn xộn trong một góc của phòng thí nghiệm và ông muốn sử dụng nó để chơi trò "Space Travel". Nhưng điều này đồng nghĩa với việc ông phải viết một hệ điều hành để chạy nó. Và Ken Thompson đã làm điều đó, vào giữa đêm ngày 1 tháng 1 năm 1970, kỷ nguyên của Unix đã bắt đầu. Kể từ thời khắc này, tất cả các đồng hồ của các hệ thống Unix-like đều bắt đầu đếm ngược, bao gồm cả chiếc điện thoại di động của bạn. Ban đầu, hệ điều hành chỉ là một hệ điều hành đơn tiến trình, được viết bằng ngôn ngữ Assembly và được gọi là UNICS như là một sự đối lập với sự phức tạp của MULTICS. 

![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ee/Pdp-11-40.jpg/800px-Pdp-11-40.jpg){: style="max-width: 30%" .left}

Sau đó, team của Ken Thompson và Dennis Ritchie đã nhận được một chiếc máy tính DEV PDP11 mới để phát triển một hệ thống xử lý văn bản cho bộ phận cấp bằng sáng chế của Bell Labs. Trong 3 tháng đầu, chiếc máy tính mới này chỉ nằm trong một góc phòng chỉ vì nó cần phải chờ một cái ổ cứng đang được ship đến thì mới có thể chạy được. Để không lãng phí thời gian, đội ngũ trong phòng thí nghiệm dùng thời gian này để chọn một ngôn ngữ lập trình mới, vì chiếc máy tính này có một kiến trúc hoàn toàn mới nên họ không thể tận dụng lại hệ điều hành cũ đã viết cho chiếc PDP7. 

Ngôn ngữ lập trình được chọn là một ngôn ngữ có tên là **BCPL**. Đây là một ngôn ngữ lập trình bậc cao, chú trọng vào tính di động. Phần lớn thành phần của ngôn ngữ này được viết bởi chính ngôn ngữ đó, và chỉ một phần nhỏ là được viết bởi ngôn ngữ Assembly. Để cho chiếc máy tính mới có thể chạy được, chỉ 1/5 trình compiler là phải được viết lại nên chỉ tốn khoảng 2-5 tháng để phát triển. 

Sau đó, Ken Thompson dựa trên BCPL để phát triển một ngôn ngữ mới - ngôn ngữ B. Vào năm 1971, Dennis Ritchie bắt đầu cải tiến ngôn ngữ **B**, kết quả là một ngôn ngữ mới mang tên ngôn ngữ **C**. Tiếp đó vào năm 1973, nhân kernel của UNIX đã được viết lại bằng ngôn ngữ C để theo đuổi tính di động - phần lớn thành phần của ngôn ngữ không phụ thuộc vào kiến trúc của máy tính (machine independent language)

> Machine Independent language - là một ngôn ngữ mà có thể chạy trên bất kỳ máy tính nào. Một ví dụ chính là Java, vì máy ảo Java (Java virtual machine) nhận code đã được biên dịch  của ứng dụng Java và thực thi nó. Chứ code của ứng dụng Java không thể chạy trực tiếp trên máy tính.

### Berkeley Software Distribution (BSD)

Mã nguồn của hệ điều hành sau đó được phân phối giữa các trường đại học với nhau (với một khoảng phí không đáng kể), và trở nên phổ biến vào những năm 80. Phần lớn các nhà phát triển hệ thống máy tính mới kể từ thời kỳ này đều sử dụng UNIX như là một nền tảng cho ứng dụng của họ. Nổi tiếng nhất phải kể đến chính là **Berkeley Software Distribution (BSD)** được phát triển bởi Đại học California và dựa trên Unix phiên bản thứ 6 với *copyleft license*[^copyleft-license] của chính nó. Và hầu hết các nhà cung cấp phần cứng của những năm 1980 đã sử dụng BSD làm hệ điều hành cơ bản cho các máy tính mới của họ. 

UNIX không phải là một phần quan trọng trong hoạt động kinh doanh của Bell Labs nên việc đó tạm thời chưa có vấn đề gì. Nhưng vào những năm 1980, phòng thí nghiệm Bell Labs của AT&T đã tách ra thành nhiều công ty nhỏ hơn do một sự kiện chống lại AT&T. Một trong số đó là công ty UNIX System Laboratories và phát triển một tiêu chuẩn UNIX System V mới. Vì UNIX là lĩnh vực kinh doanh chính của công ty này nên họ đã nhanh chóng đưa tiêu chuẩn mới này ra thị trường. Và điều đó chính là nguyên nhân của **cuộc chiến UNIX** chống lại những nhà phát triển phi thương mại bao gồm cả **BSD**. 

Việc thương mại hóa UNIX và việc chuyển từ mô hình phát triển và phân phối *mở* sang mô hình phát triển và phân phối *kín* đã dẫn đến sự ra đời của một hệ thống thay thế UNIX - dự án **GNU**.

### Sự thay thế của UNIX - dự án GNU

GNU là cái gì? Nếu bạn tìm trên Google thì sẽ ra hình ảnh của những con Linh dương đầu bò. Nhưng nó cũng là viết tắt của một cái tên theo dạng đệ quy "**GNU is Not Unix**". Dự án này được thành lập bởi Richard Stallman vào năm 1978 tại Đại học MIT. Dự án GNU là một sáng kiến để phát triển một bộ sưu tập đồ sộ các phần mềm miễn phí. Mục tiêu đầu tiên của dự án là phát triển một bộ phần mềm tương tự như bộ phần mềm tiện ích của UNIX. 

Vào năm 1991, một sinh viên Phần Lan là Linus Torvalds đã tự tạo ra nhân kernel hệ điều hành của riêng anh ta với mục đích ban đầu là chỉ cho vui. Nhân kernel này tương thích với hệ điều hành UNIX và được gọi là **Linux**. 

Sau đó, nhân Linux kernel này kết hợp với bộ phần mềm tiện ích từ dự án GNU, đóng vai trò là cơ sở để tạo ra một hệ điều hành hoàn chỉnh, có khả năng ngang với hệ điều hành Unix và thậm chí còn vượt trội hơn.

### Reverse Footnotes

[^copyleft-license]: **Copyleft** (còn gọi là **bản quyền bên trái**) là một cách [chơi chữ](https://www.wikiwand.com/vi/L%E1%BB%99ng_ng%E1%BB%AF "Lộng ngữ") đúp từ chữ [copyright](https://vi.wiktionary.org/wiki/copyright "wikt:copyright") trong tiếng Anh có nghĩa là [bản quyền](https://www.wikiwand.com/vi/Quy%E1%BB%81n_t%C3%A1c_gi%E1%BA%A3 "Quyền tác giả"), trong đó chữ _[left](https://vi.wiktionary.org/wiki/left "wikt:left")_ (bên trái) phản nghĩa với nghĩa của từ _[right](https://vi.wiktionary.org/wiki/right "wikt:right")_ (bên phải), mặc dù chữ "right" copyright có nghĩa là "quyền lợi" chứ không mang nghĩa "bên phải". Đồng thời copyleft còn có thể hiểu là _copy left_ (nghĩa là _bản sao cho dùng_, _bản sao được phép dùng_). Copyleft mô tả cách sử dụng luật bản quyền để loại bỏ tất cả các hạn chế về phân phối bản sao và các phiên bản tác phẩm đã được chỉnh sửa cho mọi người và yêu cầu phải bảo lưu quyền tự do như vậy trong các phiên bản chỉnh sửa. 


