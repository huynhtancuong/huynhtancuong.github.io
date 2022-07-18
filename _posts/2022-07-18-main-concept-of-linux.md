---
title: Những khái niệm chính trong hệ thống UNIX
author: huynhtancuong
date: 2022-07-18 06:10:00 +0300
categories: [Courses, UNIX and Linux in Infocommunication]
tags: [unix, linux, history, UNIX and Linux in Infocommunication]
math: true
mermaid: true
image: 
    path: /assets/img/posts/main-concepts-of-linux/main-concepts-of-linux-thumbnail.png
---

> Bài viết này là một phần của khóa học UNIX and Linux in Infocommunication được dạy bởi trường đại học ITMO. Bạn có thể xem thêm các bài viết của khóa học này trong cùng category của bài viết.
{: .prompt-info}

Ở lớp cao nhất (top layer), các hệ thống UNIX-like[^1] có thể rất thuận tiện cho người dùng phổ thông và thậm chí họ có thể không biết mình đang sử dụng loại hệ điều hành này. Ví dụ, hiện tại các hệ điều hành được sử dụng phổ biến nhất là hệ thống Android dựa trên Linux và hệ thống Apple dựa trên UNIX, trong đó người dùng chỉ nhìn thấy giao diện đồ họa thân thiện với người dùng. Nhưng những người mới bắt đầu mới bắt đầu tìm hiểu các hệ thống UNIX-like để có thể quản trị hệ thống hoặc phát triển phần mềm đôi khi phàn nàn về sự phức tạp của nó. Nhưng đừng sợ! Thực ra những hệ thống như vậy dựa trên những khái niệm khá đơn giản. Chỉ có bốn điều mà bạn cần biết để sử dụng thoải mái với bất kỳ hệ thống UNIX-like nào: 

* User (Người dùng)
* File (Tệp tin)
* Process (Tiến trình)
* Terminal (Cửa sổ dòng lệnh)


### User (Người dùng)
Khái niệm "User" không được người dùng hiện đại biết đến nhiều chỉ vì hiện nay chúng ta có rất nhiều máy tính cá nhân. UNIX được tạo ra vào thời điểm mà máy tính rất hiếm và đắt tiền và một máy tính được nhiều người sử dụng. Do đó, ngay từ đầu, UNIX đã có các chính sách bảo mật mạnh mẽ và các hạn chế về quyền đối với người dùng. Và giờ đây, trên các hệ thống UNIX-like, chúng ta có rất nhiều user (người dùng) và group (nhóm), ngay cả khi bị ẩn bởi hệ thống *autologin*. Và hầu hết trong số họ được gọi là người dùng giả (pseudo-users), cần thiết để khởi động các dịch vụ hệ thống. Như chúng ta sẽ thấy ở phần sau, sự tồn tại của chúng được yêu cầu bởi kiến trúc hệ thống, vì nó dựa trên quyền của người dùng và nhóm mà hệ thống được xây dựng để kiểm soát quyền truy cập vào tài nguyên hệ thống (processes and files).  

Người dùng thông thường có thể đăng nhập bằng tên người dùng và mật khẩu và tương tác với các ứng dụng được cài đặt trên hệ thống. Mỗi người dùng chỉ có toàn quyền (full permissions) trong thư mục chính của họ (home directory) và quyền truy cập hạn chế vào các file và thư mục bên ngoài thư mục đó. Điều này là dễ hiểu - người dùng thông thường không thể phá hủy bất cứ thứ gì trên hệ thống vì họ không có quyền đó. Hơn nữa, họ không thể xem thư mục chính của người dùng khác hoặc các file và thư mục hệ thống được bảo vệ. Để thực hiện các tác vụ quản trị hệ thống, hệ thống có một superuser đặc biệt (thường được gọi là "root") với các quyền bổ sung. Ở cấp hệ thống, mỗi user hoặc group được biểu thị như một số nguyên:
* User Identifier (UID)
* Group Identifier (GID)

### File (Tệp tin)
File là thứ quan trọng tiếp theo đối với các hệ thống UNIX-like. Hầu hết tất cả các tài nguyên hệ thống như file, bao gồm các device và các process trên một số hệ thống. Và các khái niệm cơ bản vẫn giống nhau kể từ đầu kỷ nguyên UNIX. Chúng ta có một hệ thống file phân cấp với một thư mục gốc duy nhất. Tất cả các tài nguyên, bao gồm hệ thống file hiện có trên device hoặc ở cloud bên ngoài, được đính kèm vào hệ thống file này trong các thư mục riêng biệt - thao tác này được gọi là "`mount`". Mặt khác, bạn có thể truy cập một thiết bị  (thực hoặc ảo) dưới dạng một byte stream và làm việc với nó như một file thông thường. Tất cả các file và thư mục đều thuộc sở hữu của *user* (thực hoặc giả) và các *group*, và quyền truy cập đọc, ghi và thực thi chúng được kiểm soát bởi các quyền. 

### Process (Tiến trình)

![](/assets/img/posts/main-concepts-of-linux/listing-runinng-processes-with-top-command.png){: style="max-width: 50%" .right}

Process là một chương trình được khởi chạy từ một file thực thi. Mỗi process thuộc về một người dùng và một nhóm. Mối quan hệ giữa chủ sở hữu của các process và tài nguyên xác định quyền truy cập theo quyền tài nguyên. Tất cả các process sống trong một hệ thống phân cấp dựa trên các mối quan hệ cha-con. Có một quá trình ban đầu trên hệ thống được gọi là 'init' được bắt đầu khi khởi động. Tất cả các dịch vụ hệ thống được bắt đầu từ quá trình ban đầu này. Về cơ bản, có hai loại process trong Linux:
* Foreground process
* Background process

Foreground process (còn được gọi là interactive process) - những process này được khởi tạo và kiểm soát thông qua một terminal. Nói cách khác, phải có một người dùng kết nối với hệ thống để bắt đầu các quá trình đó; chúng không tự động khởi động như một phần của các function/service trong hệ thống. Các process foreground interative (tiến trình tương tác) phải được kết nối vào một phiên terminal (terminal session). 

Background process (còn được gọi là các non-interactive/automatic processes) - là các process không được kết nối với phiên terminal (terminal session); chúng không yêu cầu bất kỳ input nào từ người dùng. Các service của hệ thống luôn là các background process. 

### Terminal (Dòng lệnh)
Vào thời điểm tạo ra UNIX, một thiết bị TTY (teletype) (ban đầu được phát triển vào thế kỷ 19), là kênh giao tiếp chính giữa người dùng và máy tính. Đó là một giao diện rất đơn giản hoạt động với một dòng byte được mã hóa theo bộ ký tự ASCII. Kết nối được thực hiện thông qua serial interface (giao thức serial) (vd: RS232) có tốc độ kết nối cố định. Giao thức này vẫn là giao diện người dùng chính cho các hệ thống UNIX-like. Việc triển khai từng hình thức tương tác người dùng mới, chẳng hạn như device terminal toàn màn hình, hệ thống đồ họa và kết nối mạng, tất cả đều bắt đầu bằng việc triển khai giao diện dòng lệnh TTY đơn giản. Hơn nữa, sự trừu tượng hóa giao thức này cung cấp cho chúng ta một cơ chế rất mạnh mẽ và linh hoạt để giao tiếp giữa các chương trình, có thể không có sự can thiệp của con người.

### Reverse footnotes
[^1]: Unix-like là từ dùng để chỉ các hệ thống có kiến trúc giống với Unix nhưng không phải Unix.