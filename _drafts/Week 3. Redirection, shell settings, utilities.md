## Input/ output channels redirecting

- `prog > file` - sdtout to file
- `prog < file` - sdtin from file
- `prog >> file` - stdout append to file
- `prog 2> file` - stderr to file
- `prog 2>&1` - connect stdout & stderr
- `prog > file 2>&1` != `prog 2>&1 > file` - 2 lệnh này là khác nhau. Lệnh thứ nhất đưa cả stdout và stderr vào file. Lệnh thứ 2 chỉ đưa stdout vào file, nhưng stderr được in ra màn hình. Vậy nên thứ tự chuyển luồng là quan trọng.

```bash
prog <<END_LABEL 
...
END_LABEL
```
Cẩn thận, dấu khoảng trắng giữa `<<` và `END_LABEL` có thể gây ra lỗi.

## Pipelines
`prog1 | prog2`
Câu lệnh này kết nối `stdout` của `prog1` vào `stdin` của `prog2`.
```bash
prog1 args1... < file1 | prog2 args2... | ... | progN argsN.
```

## Alias
Chúng ta có một công cụ để làm cho câu lệnh gắn đi. Đó là Alias.
Một số ví dụ:
- `alias ll='ls -la'` - gán lệnh `ll` thay cho `ls -la`
- `alias` - hiển thị tất cả các alias
- `unalias ll` - gỡ bỏ alias `ll`
Nhưng mỗi lần login lại vào thì tất cả những thiết lập này sẽ bị mất. Nhưng chúng ta có thể để những lệnh nào vào một file đặc biệt trong phần tiếp theo để nó có hiệu lực mãi.

## Initialization files
`/etc/profile` - system defaults

Bourne: `~/.profile`
Bash: `~/.bash_profile`
C-Shell: `~/.login`

`/etc/bashrc`

bash: `~/.bashrc`
csh: `~/.cshrc`

### Invoked as an interactive login shell, or with --login

When Bash is invoked as an interactive login shell, or as a non-interactive shell with the `--login` option, it first reads and executes commands from the file` /etc/profile`, if that file exists. After reading that file, it looks for `~/.bash_profile`, `~/.bash_login,` and `~/.profile`, in that order, and reads and executes commands from the first one that exists and is readable. The `--noprofile` option may be used when the shell is started to inhibit this behavior.

When an interactive login shell exits, or a non-interactive login shell executes the `exit` builtin command, Bash reads and executes commands from the file `~/.bash_logout`, if it exists.

## Keyboard shortcuts
- erase - [Ctrl]-[H], [Ctrl]-[?], [Backspace] or [Delete]
- werase - [Ctrl]-[W] - xóa một từ
- kill - [Ctrl]-[U] - kill process hiện tại
- rprnt - [Ctrl]-[R] - tìm lệnh từ history
- intr - [Ctrl]-[C] or [Delete]
- quit (with dump) - [Ctrl]-[\\] - kill process hiện tại nhưng với file dump. File dump này có thể được dùng để tìm hiểu về hoạt động bên trong của process bởi debugger.
- stop - [Ctrl]-[S] - dừng process hiện tại.
- start - [Ctrl]-[Q] - bắt đầu process bị dừng
- eof - [Ctrl]-[D]
- susp - [Ctrl]-[Z]
[Linux Bash Terminal Keyboard Shortcuts](https://www.makeuseof.com/linux-bash-terminal-shortcuts/)

## Utilities
![[Pasted image 20221001225403.png]]

## Manuals
Man sections
![[Pasted image 20221001231311.png]]

`man man`
`man printf`
`man 3 printf`
`whatis printf`