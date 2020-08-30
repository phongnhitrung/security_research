UAT 1: 
================================

UAT này hướng dẫn sử dụng PSNNIDS để phát hiện việc dò quét website và các IP dò quét website.

Mô hình kiểm tra
--------------------------------------------

- Lưu lượng thực tế

- Mô phỏng giả lập

Bước 1: PHÁT HIỆN
-------------------------------------------

- Theo dõi đồ thị cảnh báo NIDS thấy số lượng cảnh báo tăng bất thường.

  .. image:: images/detect_scan_website.png

Bước 2: TRUY VẾT
------------------------------------------

- Kiểm tra chi tiết các các cảnh báo trong bảng “NIDS - Aler Summary”

  .. image:: images/check_black_ip.png

  => Phát hiện các IP nằm trong danh sách đen bị báo cáo bởi nhiều nguồn tham chiếu trên thế giới   (https://www.dshield.org/block.txt)

Bước 3: ĐÁNH GIÁ ẢNH HƯỞNG
------------------------------------------

- Kiểm tra đồ thị flow (connections), lọc tất cả các flow liên quan đến các black IP để xác định phạm vi ảnh hưởng

  .. image:: images/scan_web_affect.png

  => Tất cả các black IP đều chưa thiết lập được kết nối hoàn chỉnh (ESTABLISHED) đến hệ thống

  => Các black IP chỉ mới scan port ứng dụng của hệ thống, cần tiếp tục giám sát vì việc dò quét là bước đầu tiên cho các cuộc tấn công quy mô
