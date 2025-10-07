Truy cập trang web bẳng Burp Suite Browser.
Đây là 1 trang web có chức năng upload file.

Thử upload 1 file .txt lên.
<img width="680" height="495" alt="image" src="https://github.com/user-attachments/assets/5b757730-c4f4-4288-9687-61c25317917c" />

Bấm vào file vừa upload, file sẽ tự động được tải về.

Vào Burp Suite Proxy -> HTTP history, có thể thấy 1 request GET /download?name=/app/file/1759851256_get.txt 
<img width="1122" height="980" alt="image" src="https://github.com/user-attachments/assets/7dd7ec03-fb74-4c7b-9beb-b6db79687320" />

Send request đến Repeater

Đổi đường dẫn của request thành /download?name=/etc/passwd
<img width="1122" height="1006" alt="image" src="https://github.com/user-attachments/assets/732e2aae-ff03-4cf9-b8a3-9bf0698981cd" />

Response trả về nội dung của /etc/passwd. Đây chính là lỗ hổng path traversal.

Trong file /etc/passwd có 1 đoạn dữ liệu lạ:
dMOsbSBnw6wgxJHhuqV5LCBjw6FpIG7DoHkgw6AgIm1pbmlDVEZ7VGgzX0g0cHB5XyIgbuG6v3UgbXXhu5FuIHRow6ptIHRow6wgeGVtIHRow7RuZyB0aW4gY3B1IHRo4butIHhlbSAoZ+G7o2kgw70gL3Byb2MxKQ==
Có thể thấy đoạn dữ liệu được mã hóa base64

Giải mã bằng https://www.base64decode.org/
Chuỗi dữ liệu sau khi được giải mã:
tìm gì đấy, cái này à "miniCTF{Th3_H4ppy_" nếu muốn thêm thì xem thông tin cpu thử xem (gợi ý /proc1)

Part 1 của flag là: miniCTF{Th3_H4ppy_

Để xem thông tin của cpu như đã được gợi ý trong /etc/passwd, truy cập đường dẫn: /download?name=/proc1/cpuinfo
<img width="1123" height="703" alt="image" src="https://github.com/user-attachments/assets/4508973e-39e5-4dee-9298-a8b4a90d82c6" />

Thu được 1 chuỗi dữ liệu cũng được mã hóa base64: cDR0aF8wZl8=
Chuỗi sau khi được giải mã: p4th_0f_

Part 2 của flag là: p4th_0f_

Trong file /proc1/cpuinfo không có gợi ý như file /etc/passwd. 

Sử dụng công cụ Wappalyzer, có thể thấy được web được lập trình bằng các ngôn ngữ lập trình Python và PHP.
<img width="1118" height="999" alt="image" src="https://github.com/user-attachments/assets/cdccbd07-bbe7-47d5-8ead-ee28658f13ba" />

Để chạy được file Python trên web, cần có các câu lệnh khởi chạy. Để xem các câu lệnh, vào đường dẫn /download?name=/proc/1/cmdline
<img width="1123" height="563" alt="image" src="https://github.com/user-attachments/assets/cb46657c-d86d-444c-be01-26339b1afc55" />

Câu lệnh để chạy file Python là: python app.py

Cần phải tìm đường dẫn chính xác của app.py. Vì đường dẫn để download 1 file là /download?name=/app/file/1759851256_get.txt, nên Document Root của web là /app/ => đường dẫn của app.py là /app/app.py.
<img width="1941" height="1438" alt="image" src="https://github.com/user-attachments/assets/e30afea7-0dfd-4844-84ef-a4f795246c91" />

Trong file app.py có rất nhiều chuỗi dữ liệu được mã hóa base64 và được comment lại. Giải mã từng chuỗi dữ liệu.

Tại dòng 96, có chuỗi mã hóa #IyBM4bqleSB0aW1lc3RhbXAgdOG7qyB0w6puIGZpbGUgZDFzYzB2M3J5fQ==
Giải mã chuỗi, thu được: # Lấy timestamp từ tên file d1sc0v3ry}

Part 3 của flag là: d1sc0v3ry}

Flag: miniCTF{Th3_H4ppy_p4th_0f_d1sc0v3ry}
