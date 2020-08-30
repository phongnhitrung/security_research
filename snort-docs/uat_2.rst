UAT 2: 
================================

UAT này hướng dẫn sử dụng PSNNIDS để phát hiện tấn công DDOS.

Mô hình kiểm tra
--------------------------------------------

- Lưu lượng thực tế

- Mô phỏng giả lập

  *tcpreplay -i ens3 hping_syn.pcap*

  *(với ens3 là network interface sử dụng cho PSNNIDS)*

Bước 1: PHÁT HIỆN
-------------------------------------------

- Theo dõi đồ thị flow (connections) trước thời điểm tấn công.

  .. image:: images/traffic_before_ddos.png

- Theo dõi đồ thị flow (connections) tại thời điểm tấn công.

  .. image:: images/traffic_under_ddos.png

  => Phát hiện lưu lượng tăng đột biến:

    - Số connection đồng thời trên hệ thống ~2000

    - Tổng số connecion tăng 150% trong thời gian ngắn (<10min)

  => Đã xảy ra tấn công DDOS

Bước 2: TRUY VẾT
------------------------------------------

- Kiểm tra đồ thị top source IP trong vòng 15 min quanh thời điểm phát sinh tấn công:

  .. image:: images/top_source_ip.png

  => Phát hiện IP 10.0.0.2 là IP DDOS hệ thống (> 85% lưu lượng)

