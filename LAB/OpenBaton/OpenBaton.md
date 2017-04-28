# ABOUT OPENBATON
 https://docs.google.com/document/d/1zMxk0c28_A-juBQ0a_Am9Q857-p7bAXFR02FYRgCvd0

# INSTALLATION
OpenBaton release 3.0 có 2 phiên bản: 
+ Stable: http://openbaton.github.io/documentation/nfvo-installation-deb/ (recommended)
+ For Dev: http://openbaton.github.io/documentation/nfvo-installation-src/

*Note: 
+ Nếu chỉ để thử nghiệm thì chỉ cần NFVO, Generic VNFM, VIM Driver (OpenStack và Test) và CLI.
+ Một số issue có thể xin xem phần issue.
# FIRST CONFIGURATION
 http://openbaton.github.io/documentation/nfvo-configuration/

# INTERGRATION TESTS 

Sau khi cấu hình xong, truy cập thử vào dashboard (http://[your-ip]:8000), thử thêm/xóa/sửa dummy các component (NSD/VNFD/Key-Pair/Vim-Instance). Check log tại /var/log/openbaton/ (mặc định, có thể thay đổi trong /etc/openbaton/openbaton-nfvo.properties).

Sau đó thực hiện bộ test tính tương thích của OpenBaton: https://github.com/openbaton/integration-tests
 
 *Note: Nên đọc kĩ mô tả của từng testcase và thực hiện từng testcase một. Thứ tự thực hiện nên bắt đầu từ các dummy-test (sử dụng dummy-vnfm, dummy-vim-instance) rồi mới tới generic vnfm, real-vim sử dụng hệ thống openstack thật. Release 3 của Openbaton mới nhận được Identify API 2.0 (Keystone của OpenStack), nên Keystone của OpenStack cần được ENABLE_IDENTITY_V2=True (trong stackrc của Devstack).
 
# LAUNCHING NETWORK SERVICE ROADMAP

1. Cài đặt VIM Driver. 

Openbaton có 2 loại VIM Driver: test, OpenStack và tự định nghĩa. Script cài 3.0 của OpenBaton đã cài giúp cả 2.

http://openbaton.github.io/documentation/vim-driver/

2. Đăng kí (register) một hoặc nhiều Point of Presences (Gọi tắt là PoPs, còn được gọi là VIM Instances.).

Đăng kí (hay kết nối) với các hạ tầng NFVI sẽ sử dụng. Xem chi tiết ở dưới.

http://openbaton.github.io/documentation/vim-instance/

3. Cài đặt một VNF Manager.

Cài đặt một VNF Manager để quản lý các VNF. Thực chất VNF Manager là cầu nối giữa MANO và EMS bên trong các VNF.
OpenBaton đã cài sẵn giùm Generic VNFM.

http://openbaton.github.io/documentation/vnfm-intro/

4. Tự build hoặc tải một hoặc vài gói VNF Packages.

Ngoài cách upload VNFD của từng VNF, các VNF còn được đóng gói hoàn chỉnh vào một bộ cài gọi là VNF Packages. Xem chi tiết ở dưới.

http://openbaton.github.io/documentation/vnf-package/

5. Chuẩn bị file Network Service Descriptor (NSD) rồi upload lên OpenBaton.

6. Khởi chạy Network Service.

# POINT OF PRESENT (OR VIM INSTANCE) REGISTRATION 

 Việc đăng kí có thể sử dụng CLI hoặc Dashboard. Log quá trình đăng kí trong /var/log/openbaton/openbaton.log và ./plugin-logs/plugin-[tên VIM types sử dụng].log

http://openbaton.github.io/documentation/vim-instance/

*Sample:

https://github.com/ttcong/Luan-van-NFV/blob/master/LAB/OpenBaton/Register-PoP.json

Tất cả các thông tin đều phụ thuộc vào Project(Tennant)/UserName-Pass/authUrl/SecurityGroup/Location(Region) của OpenStack.
KeyPair là keypair import từ Openstack. KeyPair không có thì phải để null tuy nhiên nên có.

# VNF PACKAGE
OpenBaton VNF Package tuân thủ chuẩn đóng gói CSAR. Ngoài ra, OpenBaton còn tự định nghĩa một VNF Package là một file nén có cấu trúc như sau:
 - Metadata.yaml      (File YAML chứa mô tả của cả gói VNF Package này)
 - vnfd.json          (VNFD của VNF)
 - scripts/           (Thư mục chứa các script thực thi các event trong vòng đời VNF)
    - 1_script.sh
    - 2_script.sh
 - image.img (not supported at OpenBaton 3.0, use image-link in VNFD.json!)   (Image cài đặt VM để host VNF)

*Sample:

