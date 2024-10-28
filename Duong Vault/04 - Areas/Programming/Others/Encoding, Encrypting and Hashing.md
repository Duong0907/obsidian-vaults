## Encoding
- Đơn giản là chuyển dữ liệu từ một dạng này sang một dạng khác
- Không sử dụng key
- Có thể chuyển đổi ngược lại
- Ví dụ: BASE64, UNICODE, ASCII, URL ENCODING
## Encrypting
- Là kỹ thuật encode dữ liệu sử dụng kỹ thuật encrypt để chỉ một số người dùng được cấp quyền mới có thể truy cập được
- Có sử dụng một hoặc nhiều key
- Có thể chuyển đổi ngược lại nếu sử dụng key
- Ví dụ: AES Algorithm, RSA Algorithm, Diffie Hellman
## Hashing
- Là kỹ thuật chuyển đổi dữ liệu sang dạng băm bằng các hàm băm
- Không sử dụng key
- Không thể chuyển đổi ngược lại
- Ví dụ: MD5, SHA256, SHA – 3
### Salt in password hashing
- Được sinh ra ngẫu nhiên
- Được thêm vào password trước khi băm

![[salted_pw_hashing.png]]