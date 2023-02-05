---
title: Hành trình chế một cái nồi chiên không dầu điều khiển bằng điện thoại
author: huynhtancuong
date: 2023-01-07 03:10:00 +0300
categories: [DIY]
tags: [DIY, Air Fryer]
image: 
    path: /assets/img/posts/diy-smart-air-fryer/DIY-smart-air-fryer.jpg
---


### Tại sao lại có cái này?
Khoảng tầm hè năm 2022 thì mình có mua một cái nồi chiên không dầu của Trung Quốc với giá khá rẻ. Mới đầu về sử dụng khá là ngon, nhưng tầm 2 tháng sau thì nó lăn ra chết, cắm điện không thấy đèn báo hiệu lên nữa. Mình đoán có thể là do mình cắm điện liên tục không rút ra. Nhưng lý do chính chắc là do nó cùi ^^.

![Hình ảnh của chiếc nồi chiên không dầu](https://apptradeinc.com/storage/2022/07/8-16.jpg)

### Sơ qua về cái nồi chiên không dầu
Nói qua về tính năng của chiếc nồi chiên không dầu này thì cũng rất là xịn (so với giá tiền). Nhiệt độ tối đa mà nó có thể đạt đến là khoảng 200 độ C. Màn hình led 7 thanh để hiển thị nhiệt độ và thời gian. Có nút bấm cảm ứng điện dung để có thể cài đặt thời gian và nhiệt độ. Có những profile được cài đặt sẵn, ví dụ như để nướng gà, cá,... thì sẽ cần nhiệt độ và thời gian khác nhau. Nồi có dung tích phần trong là 3.5L và phần ngoài là 5L, rất to, nên nướng gà thì khá là thoải mái. 

![Nướng gà!!!](/assets/img/posts/diy-smart-air-fryer/chicken.jpg){: style="max-width: 60%"}


### Nguyên lý hoạt động của nồi chiên không dầu
Muốn sửa thì trước hết phải hiểủ nguyên lý hoạt động của nó đã. Thay vì sử dụng dầu để chiên thức ăn như thông thường thì nồi chiên không dầu làm chín thức ăn bằng cách sử dụng thanh gia nhiệt kết hợp với quạt để tạo ra dòng khí nóng trong nồi, luân chuyển nhanh khắp bề mặt của thực phẩm giúp làm chín nó.

![Nguyên lý hoạt động của nồi chiên không dầu](https://cdn.tgdd.vn/Files/2018/03/26/1077320/noi-chien-khong-dau-la-gi-co-gi-dac-biet--1.jpg){: style="max-width: 80%"}
*Nguyên lý hoạt động của nồi chiên không dầu*


### Rồi làm sao để sửa nó?
Đầu tiên là tháo nó ra thôi. Để tiếp cận với phần bo mạch điều khiển thì khá là dễ dàng, chỉ cần cái tua vít và tháo vài con ốc là xong rồi.


![Tháo tung](/assets/img/posts/diy-smart-air-fryer/disassembly.jpg){: style="max-width: 80%"}
*Tổng quan*

![Bảng mạch mặt trước](/assets/img/posts/diy-smart-air-fryer/front-panel.jpg){: style="max-width: 80%"}
*Bảng mạch mặt trước*

![Bảng mạch mặt sau](https://gcdnb.pbrd.co/images/rqqyNxpkBhUU.png?o=1){: style="max-width: 80%"}
*Bảng mạch mặt sau*

Sau một hồi sử dụng các biện pháp nghiệp vụ thì mình đã xác định được linh kiện gây ra lỗi chính là con vi xử lý của nó. Xui vãi! Đoạn này mình sẽ phân tích một chút, tại sao lại xui. Nếu hư những linh kiện bình thường khác thì mình có thể mua cái mới về thay vào, nhưng khi đã hư vi điều khiển thì việc mua về thay thế là điều không thể. Vì bên trong vi điều khiển còn chứa chương trình để điều khiển hoạt động của nồi chiên. Nên nếu có mua được vi điều khiển mới thì mình cũng không có chương trình để nạp vào bên trong cho nó chạy. Nếu bệnh này mà gặp thợ tay non thì cũng chịu chết. Nhưng mình học cơ điện tử mà :)) kỹ sư là nghề của mình, nên mình xem đây là môt cơ hội để học thêm.

Biện pháp của mình là mình sẽ lập trình một con vi điều khiển mới rồi gắn vào thay thế cho con vi điều khiển cũ. May mắn là lúc trước mình có mua một con ESP32, mãi chưa dùng đến, bây giờ thì có việc dùng rồi. Nói sơ qua về con này thì con chip này ngoài các chức năng như mấy con vi điều khiển thông thường thì nó còn hỗ trợ cả WiFi và Bluetooth nữa. Nên mình dự định sẽ thêm vào cả tích năng điều khiển bằng web thông qua WiFi luôn ^^.

![ESP32](https://static.insales-cdn.com/images/products/1/4801/230855361/esp32-wroom-wifi-devkit.1.jpg){: style="max-width: 60%"}
*ESP32*

### Bắt đầu thôi!
Đầu tiên là mình sẽ tháo con vi điều khiển cũ ra khỏi bo mạch. Đoạn này mình không có máy khò chuyên dụng nên một số chân pin đã bị đứt phần chân đồng. Nhưng mình sẽ cố gắng xử lý phần này sau.

![Tháo vi điều khiển](https://gcdnb.pbrd.co/images/WbYhIDZ6At9H.jpg?o=1){: style="max-width: 80%"}
*Bảng mạch sau khi đã tháo vi điều khiển*

Sau đấy là hàn dây vào những chân của vi điều khiển cũ

![Hàn dây](https://gcdnb.pbrd.co/images/0z35MSj1SPQQ.jpg?o=1){: style="max-width: 80%"}

Và đây là thành quả!

![Thành quả](https://gcdnb.pbrd.co/images/w8baCPBH28q8.jpg?o=1){: style="max-width: 80%"}
*Bảng mạch sau khi đã hàn dây*

Tiếp theo thì mình sẽ tiến hành đo và đánh dấu các chân. Mục đích là để biết được chân nào kết nối với thành phần nào trên mạch. Một số chân sẽ phụ trách việc bật tắt đèn led, chân thì dùng để bật bộ gia nhiệt, chân thì kết nối với cảm biến nhiệt độ.

![Tiến hành đánh dấu chân pin](https://gcdnb.pbrd.co/images/Mhbfl3bihVAE.jpg?o=1){: style="max-width: 80%"}
*Đánh dấu chân*

Bước sau đó là kết nối dây với chip điều khiển mới.

![Kết nối với ESP32](/assets/img/posts/diy-smart-air-fryer/connect-to-esp32.jpg){: style="max-width: 80%"}
*Kết nối với ESP32*

Tiếp đó là làm quen với việc điều khiển đèn led trên bảng mạch này. Việc điều khiển này cũng không dễ dàng lắm, vì led được mắc theo dạng ma trận, nên để điều khiến được nó thì mình sẽ phải bật tắt các led tuần tự với nhau một cách nhanh chóng để đánh lừa mắt người (cái này gọi là multiplexing). Nhưng mình gặp một vấn đề đó là nếu tăng tần số quét lên thì vi điều khiển của mình không đáp ứng được (mình lập trình bằng RTOS, nên bị dính lỗi watchdog triggered, nếu ai biết hướng giải quyết thì chỉ mình với)

<iframe src="https://www.veed.io/embed/ed8bed0e-fdd0-4239-9b43-970581c803bc" width="100%" height="400" frameborder="0" title="Led Matrix" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


Ban đầu mình định làm bảng điều khiển giống cũ, nhưng vì giới hạn phần cứng nên đành phải từ bỏ. Mình chuyển sang hướng điều khiển nồi chiên bằng web.

Để làm được web thì bắt buộc phải dính đến HTML, CSS, Javascript. Nên mình quyết định dành hẵn một ngày để học sơ qua mấy cái này. Cộng với những tutorial trên mạng nữa thì đây là thành quả sau 2 ngày của mình. Một cái web interface có chức năng chọn nhiệt độ, thời gian và trạng thái của nồi chiên không dầu, bao gồm cả một biểu đồ về nhiệt độ đo được trong nồi cập nhật sau mỗi 2 giây.

![Web interface](/assets/img/posts/diy-smart-air-fryer/web-interface.png)
*Giao diện điều khiển web của nồi chiên không dầu*

Nhưng làm sao để kết nối với nồi chiên không dầu thông qua điện thoại hay là máy tính? Mình đã lập trình sao cho vi điều khiển trở thành một điểm kết nối Wifi. Khi điện thoại kết nối vào điểm Wifi này thì có thể mở giao diện điều khiển và tương tác với nó.

Bên dưới là video demo hoạt động của nồi chiên.

<iframe src="https://www.veed.io/embed/dd437a2d-8264-484f-b8af-11fe4c4eeca6" width="100%" height="504" frameborder="0" title="Demo" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

### Mã nguồn
Đây là [link](https://github.com/huynhtancuong/webserver-air-fryer) đến repository chứa code của nồi chiên không dầu.

### Kết luận
Thông qua quá trình làm dự án này thì mình có cơ hội áp dụng những kiến thức mà trước đây mình học vào thực tế.
- Học thêm được HTML, CSS, Javascript (DOM).
- Ôn lại kiến thức về C.
- Học được cách thiết kế hệ thống. Ở đây là State Machine Design Pattern. 
- Biết được những khó khăn trong việc lập trình led 7 thanh.

Tóm lại, mình đã chuyển một cái nồi chiên giao diện nút bấm bình thường thành giao diện web. Mặc dù không thiết thực lắm khi mỗi lần đảo đồ ăn thì phải cầm lấy cái điện thoại để bấm nút thì nó mới chạy. Nhưng được cái là tự tay mình sửa thì nó vui ^^.

---
---

### Những cập nhật sau này...
Nếu bạn là một người đọc phổ thông thì phần này không dành cho bạn đâu nha ^^.
#### Add cache feature
Vì mình có một file javascript khá là nặng dùng để phục vụ việc plot graph nên mỗi lần refresh lại trang thì con ESP32 đều phải gửi lại dữ liệu này cho client. Gây nên việc quá tải cho ESP. Để giải quyết vấn đề này thì mình đã thêm vào tính năng cache. Vậy nên khi người dùng tải web lần đầu thì những file tài nguyên sẽ được lưu lại và được sử dụng cho những lần sau. Kết quả là viêc tải trang sẽ diễn ra nhanh hơn.

Dưới đây là so sánh giữa việc có cache và không có cache. Như bạn có thể thấy thì việc load trang đã diễn ra nhanh hơn gấp 4-5 lần.

![Không có cache](/assets/img/posts/diy-smart-air-fryer/feature-no-cache.jpg){: style="max-width: 80%"}
*Không có cache. Thời gian load là 2.3s*

![Có cache](/assets/img/posts/diy-smart-air-fryer/feature-with-cache.jpg){: style="max-width: 80%"}
*Có cache. Thời gian load là 0.5s*

#### Add OTA feature
Sau khi hoàn thành xong thì mình đã lắp mạch vào trong máy, nên nếu muốn cập nhật thêm tính năng và phải nạp lại code thì mình phải tháo bung nồi chiên không dầu ra để tiếp cận được với mạch. Nhưng như thế khá là mất công, nên sau khi tìm hiểu thì mình đã tìm ra giải pháp đó chính là nạp code thông qua phương thức OTA (Over the Air). Với phương pháp này thì mỗi lần nạp code thì mình không phải tháo bung mạch ra nữa. Mình làm theo [hướng dẫn](https://randomnerdtutorials.com/esp32-ota-over-the-air-vs-code/) này, nếu bạn nào có hứng thú thì xem nha. 
