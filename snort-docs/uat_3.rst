UAT 3: 
================================

UAT này hướng dẫn sử dụng PSNNIDS để phát hiện lây lan mã độc trong mạng nội bộ (lateral movement).

Mô hình kiểm tra
--------------------------------------------

- Lưu lượng thực tế

- Mô phỏng giả lập: 

  *tcpreplay -i ens3 lateral_movement.pcap*

  *(với ens3 là network interface sử dụng cho PSNNIDS)*

Bước 1: PHÁT HIỆN
-------------------------------------------

- Theo dõi đồ thị cảnh báo NIDS thấy số lượng cảnh báo tăng bất thường.

  .. image:: images/images/lateral_movement_alert.png

  => Các cảnh chủ yếu là “A Network Trojan was detected”

  => Nghi ngờ lây lan mã độc trong mạng

Bước 2: TRUY VẾT
------------------------------------------

- Kiểm tra chi tiết các các cảnh báo trong bảng “NIDS - Aler Summary”

  .. image:: images/lateral_movement_detail.png

  => Phương thức lây lan sử dụng SMB, nguồn lây từ IP 192.168.110.122 đến IP 192.168.110.115

Bước 3: ĐÁNH GIÁ ẢNH HƯỞNG
------------------------------------------

- Kiểm tra đồ thị flow (connections), lọc tất cả các flow liên quan đến 2 IP 192.168.110.122 và IP 192.168.110.1 để xác định phạm vi ảnh hưởng

  .. image:: images/lateral_movement_affect1.png

  .. image:: images/lateral_movement_affect2.png

  => Mã độc mới lây lan trong 2 IP 192.168.110.122 đến IP 192.168.110.115, chưa lan rộng ra các máy khác trong mạng nội bộ
