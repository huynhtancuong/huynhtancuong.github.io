## Environment variable
Biến môi trường (environment variable) là một cặp key-value giữa NAME và VALUE.
NAME của biến môi trường có thể là chữ cái, số, hoặc dấu gạch dưới.
VALUE của biến môi trường chỉ có thể là string.
Biến môi trường có thể có phạm vi trong toàn cục hoặc là cục bộ.

## Thao tác với biến môi trường
Đặt một dấu $ trước tên của biến môi trường
```bash 
$ echo $USER
// output: user 
```
Nếu biến môi trường chưa có giá trị, một empty string sẽ được trả về
```bash
$ echo TEST
// output: 
```
Set giá trị cho biến môi trường.
```bash
$ TEST=123
$ echo $TEST // 123
```
In ra giá trị của tất cả biến môi trường 
```bash
$ set
$ set | less
$ env 
```
### Biến toàn cục
Ta thử tạo một bash script.
```bash
$ cat > test
#!/bin/sh

echo TEST:
echo $TEST

# sau đó thực thi 
$ sh test
TEST:

# Ta không thấy giá trị của biến TEST được in ra. Vì giá trị của biến này không được kế thừa từ SHELL hiện tại đến SHELL sh mới.
# Ta sử dụng lệnh export để làm điều đó.
$ export TEST=4567
$ sh test
TEST:
4567
$ echo $TEST
4567
```
Nếu trước đó giá trị của biến được set theo cách toàn cục nhưng được set lại theo cách cục bộ. Ở trong shell hiện tại, giá trị của biến cục bộ sẽ theo cục bộ. "Phép vua thua lệ làng"
### Xóa giá trị của biến môi trường
```bash
$ unset TEST # xóa giá trị của biến trên cả global và local
```
## Ứng dụng của biến môi trường
Biến môi trường là phương pháp đơn giản nhất được dùng để giao tiếp liên tiến trình.
Một số biến môi trường thông dụng
- PATH – list of directory paths with executables separated by ":" 
- HOME – indicate where a user's home directory is located in the file system. 
- LANG, LC_ALL... – language locale 
- TZ – time zone 
- EDITOR, VISUAL – preferred editor 
- TERM – specifies the type of computer terminal or terminal emulator being used (e.g., vt100, ansi or dumb) 
- LINES, COLUMNS – size of screen in symbols 
- PS1 and PS2 – specifies how the prompt is displayed in the Bourne shell and variants

Biến môi trường PATH là nơi để lưu đường dẫn đến các thư mục. Hệ thống sẽ đến những đường dẫn đó để tìm những file thực thi. Trong hệ thống Windows, hệ thống sẽ tự tìm trong thư mục hiện tại file để thực thi. Nhưng đối với hệ thống UNIX-like, một chức năng như vậy là một ý tưởng tồi. Tại sao lại là một ý tưởng tồi? Hãy tưởng tượng trong một hệ thống mà bạn là quản lý (root), có một user có ý đồ xấu, anh ta tải về trong thư mục của anh ta một file mã độc có tên là `ls`. Anh ta không có quyền để thực thi tệp tin này. Nhưng vì sự tò mò của bạn, bạn vào thư mục của anh ta, bạn dùng lệnh `ls` để xem bên trong thư mục của anh ta có gì...và boom! Bạn vừa dùng quyền root để thực thi file mã độc của kẻ xấu đó. Đó là lý do UNIX coi đây là một chức năng tồi. Vì vậy trong biến môi trường PATH không tồn tại đường dẫn `.`.
