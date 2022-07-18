---
title: Những thành phần trong hệ thống UNIX
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

Triết lý thiết kế chính được sử dụng trong hệ thống UNIX-like là nguyên tắc "**KISS**". Từ **KISS** là viết tắt của "*keep it stupid simple*" hay "*keep it short and simple*". Là một nguyên tắt được dùng bởi Hải quân Hoa Kỳ (U.S. Navy) vào năm 1960. Nguyên tắt KISS nói rằng hầu hết các hệ thống hoạt động tốt nhất nếu chúng là những hệ thống đơn giản thay vì phức tạp. Do đó, sự đơn giản phải là mục tiêu chính (key goal) và ta phải tránh những sự phức tạp không cần thiết.

Ngay từ những ngày đầu của kỷ nguyên UNIX, nó đã có tính mô-đun rất linh hoạt. Các thành phần cơ bản của một hệ thống UNIX-like chỉ bao gồm:
* Kernel 
* Shell
* Libraries
* Utilities

### Kernel - Hạt nhân hệ điều hành
Kernel là một tập mã lệnh của hệ điều hành được load vào bộ nhớ RAM của máy tính và thực thi đầu tiên. Chương trình này sau đó khởi chạy tất cả các process khác trên hệ thống, xử lý các tương tác giữa các tài nguyên hệ thống và vẫn tồn tại trong khi máy tính của chúng ta chạy. Kernel được chạy với đặc quyền cao nhất và có khả năng truy cập vào mọi tài nguyên của hệ thống. Tất cả các process nào hoạt động trong user space[^userspace] thì tương tác với các tài nguyên hệ thống bằng cách gửi những yêu cầu đến kernel thông qua một chức năng phần mềm đặc biệt gọi là "system calls"[^systemcall]. Và kernel phải xử lý những yêu cầu đó dựa theo quyền (permission) giữa process và tài nguyên hệ thống.

### Shell - Cửa sổ dòng lệnh
> UNIX Shell đầu tiên được giới thiệu bởi Ken Thompson vào năm 1971
 {: .prompt-info}

Shell là thứ quan trọng nhất hỗ trợ cho việc giao tiếp giữa người dùng, chương trình và kernel. Shell chỉ là một chương trình được khởi chạy khi người dùng đăng nhập và nó lắng nghe (listen) các sự kiện input (thường là từ bàn phím) và hiển thị kết quả của các lệnh ra output (thường là màn hình). 

"Bourne shell" là một trình shell nổi tiếng, được phát triển bởi Stephen Bourne tại Bell Labs vào năm 1979 và trở thành trình shell mặc định cho UNIX version 7 được phát hành cho các trưởng đại học và cao đẳng. Hỗ trợ biến môi trường (enviroment variables), chuyển hướng luồng input/output, program pipes và khả năng lập trình mạnh mẽ. Tất cả các shell ngày nay (không chỉ riêng các shell UNIX) được thừa hưởng các tính năng này từ Bourne shell.

Shell là một thứ chất kết dính hiệu quả để liên kết các chương trình tiện ích trong một hệ điều hành đa nhiệm. Các chương trình tiện ích này đã được phát triển từ rất sớm kể từ sự ra đời của UNIX. Chúng là những công cụ để chúng ta có thể làm việc với users, groups, files, và processes. Và vì UNIX ban đầu được phát triển để tự động hóa các công việc của bộ phận cấp bằng sáng chế tại Bell Labs nên nó có một bộ công cụ phong phú và mạnh mẽ để xử lý text file và text stream.

Design pattern phổ biến nhất cho các phần mềm tiện ích của UNIX là bộ lọc (filter) giữa standard input và standard output. Vậy nên nhiều phần mềm tiện ích của UNIX có thể kết hợp thành một cái gọi là program pipeline (đường ống phần mềm) và ta có thể sử dụng program pipeline trong shell để giao tiếp giữa các chương trình với nhau. Mỗi chương trình tiện ích riêng lẻ có thể rất đơn giản, nhưng khi kết hợp chúng cùng nhau thì ta có thể tạo ra một hợp chất mạnh mẽ chỉ trên một dòng lệnh duy nhất. Doug Mcllroy là trưởng của Bell Labs Computing Sciences Research Center, và cũng là người phát minh ra UNIX pipe, đã mô tả triết học của UNIX như sau: 
> "Write programs that do one thing and do it well.
Write programs to work together.
Write programs to handle text streams, because that is a universal interface."

Hiện tại, các chương trình tiện ích được sử dụng phổ biến nhất chính là các tiện ích của dự án GNU, chúng được tạo ra sau khi UNIX được thương mại hóa. Trong hầu hết các trường hợp, những tiện ích của dự án GNU mạnh mẽ và nhiều thông số phức tạp hơn các tiện ích của phiên bản UNIX được thương mại.

> Trên các thiết bị nhúng có bộ nhớ nhỏ. Người ta sử dụng "Busybox" để đóng gói các tiện ích lại thành một tệp thực thi duy nhất thay vì để chúng nằm riêng lẻ. Điều này giúp tiết kiệm dung lượng lưu trữ.
 {: .prompt-info}

#### Libraries
Tất cả các tiện ích (utilities) và shell được xây dựng nằm phía trên các software libraries. Những thư viện này có thể là thư viện liên kết động (shared libraries) hoặc là thư viện tĩnh (static).

Trong trường hợp thư viện liên kết động (shared libraries), chúng ta dễ dàng hơn trong việc cập nhật và sửa đổi các thư viện, đồng thời do các ứng dụng sử dụng chung thư viện này nên ta có thể tiết kiệm được dung lượng bộ nhớ hơn là khi dùng thư viện tĩnh.

Trong trường hợp thư viện liên kết tĩnh (static libraries), chúng ta có một chương trình khép kín và ít phụ thuộc vào cấu hình của hệ thống và có thể độc lập với các platform khác nhau hơn.

Chúng ta có thể sử dụng các thư viện liên kết động được phát hành bởi giấy phép GPL để viết các ứng dụng động quyền, nhưng ta không thể sử dụng các thư viện liên kết tĩnh được pháp hành bởi giấy phép GPL để làm điều tương tự.

### Reverse Footnotes
[^userspace]: không gian người dùng. Một hệ điều hành máy tính hiện đại thường tách bộ nhớ ảo thành không gian người dùng và không gian hạt nhân. Về cơ bản, sự tách biệt này nhằm cung cấp khả năng bảo vệ bộ nhớ và bảo vệ phần cứng khỏi hành vi phần mềm độc hại hoặc sai lầm.
[^systemcall]: Trong máy tính, một lời gọi hệ thống (system calls) là việc một chương trình máy tính yêu cầu một dịch vụ từ nhân của hệ điều hành mà nó được thực thi. Điều này có thể bao gồm các dịch vụ liên quan đến phần cứng, tạo và thực thi các tiến trình mới, giao tiếp với các dịch vụ nhân tích hợp như lập lịch xử lý.