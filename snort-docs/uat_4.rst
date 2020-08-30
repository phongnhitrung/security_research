UAT 4: 
================================

UAT này hướng dẫn sử dụng PSNNIDS để phát hiện tấn công website.

Mô hình kiểm tra
--------------------------------------------

- Lưu lượng thực tế: lấy từ mirror port

- Mô phỏng giả lập:

Bước 1: PHÁT HIỆN
-------------------------------------------

- Theo dõi đồ thị cảnh báo NIDS phát hiện cảnh báo tấn công web.

  .. image:: images/web_attack_alert.png

Bước 2: TRUY VẾT
------------------------------------------

- Kiểm tra chi tiết các các cảnh báo trong bảng “NIDS - Alert Summary”

  .. image:: images/web_attack_detail.png

  => Thông tin về source/dest IP, source/dest port của request tấn công

- Lọc toàn bộ các event theo source/dest IP, source/dest port tìm được

  .. image:: images/web_attack_filter.png

  .. image:: images/web_attack_info.png

  => Request tấn công cố tình upload shell script lên website để gửi thông tin về địa chỉ 19ce033f.ngrok.io

  => Địa chỉ 19ce033f.ngrok.io là địa chỉ nguy hại (tham khảo tại https://any.run/report/a333db8d323fc11afb10f94248d922e769a5bd5fa6d31dc0ac3a396f48d3014b/c371c218-c241-485c-8f64-6b7ad6f592ef)

Bước 3: ĐÁNH GIÁ ẢNH HƯỞNG
------------------------------------------

- Kiểm tra đồ thị flow (connections), lọc tất cả các flow liên quan đến các source/dest IP trong event để xác định phạm vi ảnh hưởng

