# Ngôn ngữ Markdown
Ngôn ngữ này khá đơn giản, bạn có thể đọc tại [đây](https://daringfireball.net/projects/markdown/syntax) 
Nhưng với tôi, tôi không dùng hết từng ấy thứ cho nên tôi chỉ nhớ một số cái tôi hay dùng, cách tôi dùng như sau:
Tạo một file có tên bất kỳ với đuôi .md. Có thể dùng `notepad`, `notepad++`, `vi`, `namo`,... hay bất cứ thứ gì mà bạn muốn.
Một số phương pháp tôi hay dùng để viết:
### 1. Thẻ tiêu đề
Markdown sử dụng kí tự # để bắt đầu cho các thẻ tiêu đề, có thể dùng từ 1 đến 6 ký tự # liên tiếp. Mức độ riêu đề giảm dần từ 1 đến 6

Tùy mục đích và ý thích bạn có thể sử dụng cách này để thể hiện các chỉ mục khác nhau.

Ví dụ:

```
# 1. Tiêu đề cấp 1
```
# 1. Tiêu đề cấp 1
```
## 2. Tiêu đề cấp 2
```
## 2. Tiêu đề cấp 2
```
###### 6. Tiêu đề cấp 6
```
###### 6. Tiêu đề cấp 6

### 2. Chèn link chèn ảnh
Để chèn hyperlink bạn chỉ cần paste luôn linh đó vào file .md
```
https://github.com
```
https://github.com

Hoặc bạn cũng có thể sử dụng cú pháp sau để thu ngắn đường dẫn của link
```
[Github](https://github.com)
```
Kết quả là:
[Github](https://github.com)
Để chèn ảnh thì bạn hãy sử dụng cú pháp sau:
```
<img src="link_anh_cua_ban">
```
<img src = "data:image/jpeg;base64,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">

cách khác:
```
![text](file ảnh)
```

Kết quả: 

![ảnh mèo](/HuyNV/Markdown/Docs/meme%20mèo.jpg)

Tôi thường sử dụng công cụ [Lightshot](https://app.prntscr.com/en/index.html) để chụp ảnh màn hình và up hình đó lên trang http://i.imgur.com/ để lấy đường dẫn ảnh đưa vào Github

Hai công cụ này khá dễ sử dụng, bạn chỉ cần chụp màn hình bằng Lightshot ấn Ctrl + C để copy và Ctrl + V để paste vào trình duyệt tại trang web http://i.imgur.com/

### 3. Ký tự in đậm, in nghiêng
- Để in đậm một đoạn text bạn chỉ cần làm như sau:
```
**từ cần in đậm**
```

**từ cần in đậm**

- Để in nghiên một đoạn text bạn chỉ cần làm như sau:
```
*từ cần in nghiêng*
```

*từ cần in nghiêng*

### 4. Trích dẫn, bo chữ

Để bo một đoạn text thì bạn chỉ cần sử dụng cú pháp sau:
```
`đoạn cần bo`
```
Kết quả là:

`đoạn cần bo`

Để làm nổi bật một đoạn, chẳng hạn như một đoạn shell hay file cấu hình bạn có thể sử dụng cú pháp như ví dụ sau:
``````
```sh
auto eth0
iface eth0 inet static
ipaddress 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 8.8.8.8
``````

Kết quả như sau:

```sh
auto eth0
iface eth0 inet static
ipaddress 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 8.8.8.8
```
### 5. Gạch đầu dòng
Để sử dụng gạch đầu dòng bạn chỉ cần sử dụng cú pháp sau:

```
- Gạch đầu dòng thứ nhất
  
  - Thụt với đầu dòng 1
  
  - Thụt với đầu dòng 1
 
- Gạch đầu dòng thứ hai
  
  - Thụt với đầu dòng 2
  
  - Thụt với đầu dòng 2
```

- Gạch đầu dòng thứ nhất
  
  - Thụt với đầu dòng 1
  
  - Thụt với đầu dòng 1
 
- Gạch đầu dòng thứ hai
  
  - Thụt với đầu dòng 2
  
  - Thụt với đầu dòng 2

### 6. Tạo bảng

Bạn có thể sử dụng cú pháp sau để tạo bảng:

| Cột 1 hàng 1 | Cột 2 | Cột 3 | Cột 4 |
|--------|---------|--------|---------|
| Hàng 2 | 2x1 | 2x2 | 2x3 | 2x4 |
| Hàng 3 | 3x1 | 3x2 | 3x3 | 3x4 |
| Hàng 4 | 4x1 | 4x2 |4x3 | 4x4|

_Tài liệu tham khảo_: [github](https://github.com/hocchudong/git-github-for-sysadmin)