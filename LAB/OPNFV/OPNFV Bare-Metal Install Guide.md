# OPNFV Install Guide
=================================

## 1. Phần cứng làm lab (Nhóm dựng lab bare metal, ko phải trên VM)

Cài đặt hệ thống OPNFV Colorado thử nghiệm theo mô hình 3 node.
+ 1 Fuel Jumphost
Core 2 Duo E7500 2.93Ghz 
HDD: 1x250GB
Memory: 4x1GB 1066
OS: CentOS

+ 1 Compute - IBM
Phần cứng
Server: IBM X3100 M5
Core: Xeon E3
Memory: 16GB
HDD: 4TB
OS: Ubuntu

+ 1 Controller
Phần cứng:
Core i5  3330 3Ghz 2 cores 4 threads
HDD: 500GB
Memory: 1x4GB
OS: Ubuntu

## 2. Tham khảo 1 số cách thức triển khai OPNFV

## 3. Các bước cài đặt OPNFV#
### 3.1 Chuẩn bị môi trường cài đặt

Hiện trên trang chủ của OPNFV có 4 cách cài đặt OPNFV (bản Colorado) và nhóm chọn cách cài đặt OpenStack bằng Fuel (tool native của OpenStack)

1. Đầu tiên, ta cần download file iso của OPNFV từ đây: (ISO)[https://www.opnfv.org/software/downloads] (1 file duy nhất được đóng gói sẵn)

2. Đánh USB cài đặt bằng Rufus
<img src="http://imgur.com/uOaXhZb">

3. Chuẩn bị thiết bị mạng
  * 1 router ra Internet
  * 2 switch 8 port

Note: 
* Tối thiểu sử dụng 2 NIC/node nhưng tốt nhất nên sử dụng 5 NIC/node, trong đó 4 Network sử dụng Tag-Vlan có thể chung một NIC. Riêng un-tagged VLAN đóng vai trò PXE boot cần 1 NIC riêng.
* Tắt tất cả DHCP Server trong các đường mạng (OPNFV JumpHost sẽ đóng vai trò PXE Server).

4.  Cấu hình khởi động bằng PXE trên tất cả các máy con (trừ JumpHost)

5.  Cài đặt Fuel trên JumpHost
Boot JumpHost từ USB.

< chèn hình >
Ấn Tab để điều chỉnh.
Do OPNFV Colorado 3.0 đã bỏ option Fuel USB Installation, ta đổi 2 instance từ cdrom thành hd:sdc1:/ (với sdc1 là phân vùng usb tùy vào từng máy).
inst.repo = hd:sdc1:/
inst.ks = hd:sdc1:/ks.cfg

Chi tiết: https://ask.opnfv.org/question/1203/error-while-installing-colorado-fuel-from-usb/

Còn lại theo hướng dẫn của OPNFV:
http://artifacts.opnfv.org/fuel/colorado/3.0/docs/installationprocedure/index.html#document-installation.instruction#opnfv-software-installation-and-deployment

Note: Nhấn check ở từng bước nhất là các bước Network Setup, DNS & Hostname và Bootstrap Image. 

Lỗi có thể có: Bootstrap Image Build Fail:
[Nghi ngờ] 
File "/etc/fuel-bootstrap-cli/fuel_bootstrap_cli.yaml" cấu hình sai hoặc 127.0.0.1:8080 chạy web server để build bootstrap image có vấn đề ? 
https://ask.opnfv.org/question/1301/fail-to-build-bootstrap-image-in-the-first-booting/

[Giải pháp]
Tham khảo file /etc/fuel-bootstrap-cli/fuel_bootstrap_cli.yaml.sample để cấu hình lại file “/etc/fuel-bootstrap-cli/fuel_bootstrap_cli.yaml” với link trực tiếp thay vì localhost như mặc định.

Do thiếu phần cứng nên nhóm ko thể tiếp tục triển khai tiếp OPNFV mà chuyển sang cài đặt mô hình bằng tay.
Hy vọng nếu còn thời gian, nhóm có thể thực hiện tiếp việc triển khai OPNFV này.
......

## Tham khảo
So sánh các cách cài đặt OPNFV
https://blog.vietstack.vn/OPNFV-Installer-Compare/

OPNFV Colorado
https://www.opnfv.org/software/downloads

Fuel Complete: 
https://docs.openstack.org/developer/fuel-docs/userdocs/fuel-install-guide/install/install_install_fuel_master_node.html


