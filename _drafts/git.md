---
title: Quy trình phát triển của một dự án sử dụng Git 
author: huynhtancuong
categories: [Blogging, Tutorial]
tags: [git]
math: true
mermaid: true
---

### Git Flow khi làm việc một mình 

Khi phát triển tính năng cho sản phẩm, ta nên phát triển ở branch riêng để tránh tình trạng branch chính chứa những commit *bẩn*. Sau đây là cách phân chia branch được gợi ý.

* Các branch chính: 
  - Branch Master: Là branch chỉ dùng để theo dõi và đánh tag. Code ở đây là code ổn định nhất và chúng ta không phát triển tính năng trên branch này.
  - Branch Develop: Là branch dùng để  phát triển các tính năng mới cho phiên bản hiện tại. Đây là nhánh mẹ của các nhánh feature. 
  - Branch Release: Là branch được tạo ra khi merge nhánh Develop và nhánh Master. Đây là sản phẩm dành cho người dùng sử dụng.

* Các branch riêng: 
	- Branch feature: Là nhánh được tách ra từ nhánh Develop để phát triển các tính năng mới.
	- Branch bugfix: Là nhánh dùng để fixbug trong quá trình phát triển nhánh Develop 
	- Branch hotfix: Là nhánh dùng để fix các bug quan trọng. Cần phải fix gấp. 

[![](https://mermaid.ink/img/pako:eNqdU0FugzAQ_AryOYIALUk5p2rP7ZXLghdsFTAya0QU8feaBCQS0lapT9bszOzsyj6xTHFkMSskvWloRFI79mSqqiRd7qmGOhPOATssVTPVBWZfytANulblCGQ0en3frzlX97uOFeoC1yazuexTUyy8Z49V4T9NH_WoQNZLgyvPKfEHlggter67vVGvK-cejuSxk7Cp6nR-whyCYsQ6S7VkdtVAKLLBb7yvwHvRV80vE6x1U5x3dd7xIssodf05zN_P4_EN3nlcc-zgx20Gv28zWEzgBvM62YbZ_jYMt__iNOoTRgIrTNjI5JiDKWlkDpZqGg6Er1yS0izOoWxxw8CQ-jzWGYtJG5xJBwmFhmoGSwUcrebE6Nhc_mBL1jFTdS6LETe6tLAgatrY88aya_-pMKlr5_FayQVoEt1L5EVBtIcgxGgXwnMY8iz1X_Z58OTnfLf1A2DDMHwDwntG9w)](https://mermaid.live/edit#pako:eNqdU0FugzAQ_AryOYIALUk5p2rP7ZXLghdsFTAya0QU8feaBCQS0lapT9bszOzsyj6xTHFkMSskvWloRFI79mSqqiRd7qmGOhPOATssVTPVBWZfytANulblCGQ0en3frzlX97uOFeoC1yazuexTUyy8Z49V4T9NH_WoQNZLgyvPKfEHlggter67vVGvK-cejuSxk7Cp6nR-whyCYsQ6S7VkdtVAKLLBb7yvwHvRV80vE6x1U5x3dd7xIssodf05zN_P4_EN3nlcc-zgx20Gv28zWEzgBvM62YbZ_jYMt__iNOoTRgIrTNjI5JiDKWlkDpZqGg6Er1yS0izOoWxxw8CQ-jzWGYtJG5xJBwmFhmoGSwUcrebE6Nhc_mBL1jFTdS6LETe6tLAgatrY88aya_-pMKlr5_FayQVoEt1L5EVBtIcgxGgXwnMY8iz1X_Z58OTnfLf1A2DDMHwDwntG9w)

Mô tả quy trình phát triển của hình trên: 
* Bắt đầu bằng branch **main**
* Checkout ra branch **Develop**
* Để phát triển tính năng mới, ta tạo ra branch **feature/xxx**
* Sau khi đã phát triển xong tính năng, ta merge vào branch **Develop**
* Giả sử ta phát hiện trong branch **Develop** có bug, ta tạo ra một branch **fixbug/xxx** để fix bug chứ không fix bug trực tiếp trên branch **Develop**
* Sau khi đã phát triển được cơ số các tính năng, ta quyết định merge vào branch **main** và release phiên bản hiện tại cho người dùng sử dụng tại branch **Release/1.0** (và đánh tag v1.0.0)
* Sau đó ta checkout trở về branch **Develop** để tiếp tục phát triển những phiên bản tiếp theo. Sau đó làm tương tự những điều trên để release ra phiên bản **Release/2.0**
* Nếu người dùng phát hiện bug trong bản release **Release/1.0**, và yêu cầu chúng ta phải fix lỗi gấp.
  - Ta tạo ra một branch **hotfix** để sửa lỗi 
  - Sau khi sử a lỗi xong thì ta merge vào branch **Release/1.0** và cập nhật phiên bản thành v1.0.1
  - Nếu lỗi đó vẫn còn tồn tại ở branch **Develop** thì ta phải merge branch **hotfix** này vào branch **Develop**
  - Xóa branch **hotfix**

### Git tag là gì?

Git tag là một tính năng giúp ta thuận lợi hơn trong việc tìm lại các phiên bản chạy ổn định giữa rất nhiều các commit. 

Ví dụ:

```bash
git tag <v1.0.0>
```

### Quy định về tên version
Tên version của chúng ta có dạng 

$$ \text{Major.Minor.Patch-BuildID} $$

| Từ khóa | Giải thích                                                           |
| ------- | -------------------------------------------------------------------- |
| MAJOR   | Thay đổi khi bạn thay đổi API **không** còn tương thích với chuẩn cũ |
| MINOR   | Thay đổi khi bạn thêm tính năng mới và vẫn tương tích với chuẩn cũ   |
| PATCH   | Thay đổi khi bạn fix lỗi                                             |
| BuildID | Ngày commit dạng YYYYMMDD                                            |

### Các bài toán trong Git 

#### Sửa commit cuối cùng 
Để ghi đè lên commit cuối cùng, ta có thể sử dụng lệnh sau
```bash
git commit --amend 
```

#### Xóa commit hiện tại và quay lại commit trước
Lệnh này sẽ xóa tất cả file của commit hiện tại và trở lại commit trước đó. 

```bash
git reset --hard HEAD~1
```
Trong đó *HEAD* là con trỏ chỉ đến commit mà chúng ta đang làm việc.
*HEAD~1* nghĩa là quay trở lại 1 commit trước.

#### Quay trở lại commit trước và vẫn giữ file của commit hiện tại 
Lệnh này sẽ giữ lại tất cả file của commit hiện tại và trở lại commit trước đó.

```bash
git reset --soft HEAD~1
```

#### Tạo branch, chuyển branch, xóa branch

Liệt kê các branch hiện tại
```bash
git branch
```

Chuyển branch
```bash
git checkout <branch name>
```

Tạo branch mới 
```bash
git branch <branch name>
```

Tạo và chuyển sang branch mới (câu lệnh gộp của 2 lệnh trên)
```bash
git checkout -b <branch name>
```

Xóa branch (ta phải thực hiện lệnh này trên branch khác)
```bash
git branch -D <branch name>
```

Quay trở lại commit gần nhất 
```bash
git reset --hard HEAD
```
hoặc
```bash
git stash
```

#### Chỉnh sửa commit cuối cùng trên remote 

Trước hết ta phải sửa commit cuối cùng trên local 
```bash
git commit --amend 
```
Sau đó push lên remote với tùy chọn force để ghi đè lên remote 
```bash
git push --force origin master 
git push -f origin master 
```

#### Xóa branch trên remote 
Ta chuyển sang một branch khác rồi thực hiện lệnh để xóa branch ở remote
```bash
git push origin -d <branch name>
```
Sau đó ta xóa luôn branch ở local 
```bash
git branch -D <branch name>
```

#### Quay lại commit trong quá khứ và phát triển một branch mới 
Trước hết ta liệt kê ra các commit trong quá khứ bằng lệnh 
```bash
$ git log --oneline

Output: 
753aa46 (HEAD -> master, origin/master, origin/HEAD) add Spaceship plugin
6ad8b76 added tony buoi sang: chuyen o trung dong
e796f4f added link to post from about
19632cb changed date of project post
f972998 commented live.html
```
Giả sử ta muốn quay lại commit 19632cb và tạo branch mới tại đó

```bash
git checkout 19632cb -b <new branch>
```

### Reference 
* DEVIOT