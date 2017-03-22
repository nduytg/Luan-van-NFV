#OPNFV Install Guide#

##1. Phần cứng làm lab (Nhóm dựng lab bare metal, ko phải trên VM)##

Cài đặt hệ thống OPNFV thử nghiệm theo mô hình 3 node.
+ 1 Fuel Jumphost

+ 1 Compute - IBM
Phần cứng
Server: IBM X3100 M5
Core: Xeon E3
Memory: 16GB
HDD: 4TB

+ 1 Controller
Phần cứng:
Core i5  3330 3Ghz 2 cores 4 threads
HDD: 500GB
Memory: 1x4GB


##2. Các bước cài đặt OPNFV##

Hiện trên trang chủ của OPNFV có 4 cách cài đặt OPNFV (bản Colorado) và nhóm chọn cách cài đặt OpenStack bằng Fuel (tool native của OpenStack)

1/ Đầu tiên, ta cần download file iso của OPNFV từ đây: (ISO)[https://www.opnfv.org/software/downloads] (1 file duy nhất được đóng gói sẵn)

2/ Đánh USB cài đặt bằng Rufus
<img src="http://imgur.com/uOaXhZb">

3/ Chuẩn bị môi trường cài đặt

5 VLAN (4 tagged Chu+ 1 untagged):
<ul>
<li>PUBLIC</li>
<li>MGMT</li>
<li>STORAGE</li>
<li>PRIVATE</li>
</ul>
1 un-tagged VLAN for PXE boot, admin network
=> Nhà nghèo thì với cho hết vô 1 NIC/node, dc thì nên chia ra
Note: tắt DHCP cho Router tổng. (Master Node sẽ đóng vai trò PXE Server).
Mô hình (ko HA)
<ul>
<li>1 Fuel master</li>
<li>1 controller</li>
<li>1 compute</li>
</ul>
