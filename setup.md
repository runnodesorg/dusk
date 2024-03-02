CÀI ĐẶT DUSK

Links tham khảo:

https://docs.dusk.network/itn/node-running-guide

https://github.com/dusk-network/itn-installer

https://wallet.dusk.network/dashboard


[Nếu đã cài đặt Dusk trước mà bị lỗi thì xóa đi]
* Xóa Dusk:
rm -rf /opt/dusk
* Xóa cache ví: 
rm -rf ~/.dusk/rusk-wallet/cache*
* Download code cài đặt bản 0.1.6:
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.6/itn-installer.sh | sudo sh
* Khôi phục ví bằng phrase (tạo ví lấy phrase https://wallet.dusk.network):
rusk-wallet restore
* Để tạo và xuất cặp khóa:
rusk-wallet export -d /opt/dusk/conf -n consensus.keys
* Đặt mật khẩu đồng thuận:
sh /opt/dusk/bin/setup_consensus_pwd.sh
* Khởi chạy Rusk
service rusk start
* Kiểm tra Rusk
service rusk status
[Nếu thấy lỗi Rusk]: không start được thì đổi cổng bằng cách vào file sau:
sudo nano /opt/dusk/conf/rusk.toml
+ Thêm 3 dòng sau vào file cấu hình rusk.toml (thay cổng 8080 bằng 8085 hoặc 80xx)
-------Thêm 3 dòng  vào file rusk.toml như bên dưới------
[http]
listen = true
listen_address = '0.0.0.0:8085'
------------------Hết thêm file-------------------------------------
* Khởi động lại Rusk:
service rusk restart
* Kiểm tra logs:
tail -F /var/log/rusk.{log,err}
* Đồng bộ xong thì stake…
