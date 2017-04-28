# ABOUT OPENBATON
 https://docs.google.com/document/d/1zMxk0c28_A-juBQ0a_Am9Q857-p7bAXFR02FYRgCvd0

# INSTALLATION
OpenBaton release 3.0 có 2 phiên bản: 
+ Stable: http://openbaton.github.io/documentation/nfvo-installation-deb/ (recommended)
+ For Dev: http://openbaton.github.io/documentation/nfvo-installation-src/

*Note: Nếu chỉ để thử nghiệm thì chỉ cần NFVO, Generic VNFM, VIM Driver (OpenStack và Test) và CLI.

# FIRST CONFIGURATION
 http://openbaton.github.io/documentation/nfvo-configuration/

# INTERGRATION TESTS 

Sau khi cấu hình xong, truy cập thử vào dashboard (http://[your-ip]:8000), thử thêm/xóa/sửa dummy các component (NSD/VNFD/Key-Pair/Vim-Instance). Check log tại /var/log/openbaton/ (mặc định, có thể thay đổi trong /etc/openbaton/openbaton-nfvo.properties).

Sau đó thực hiện bộ test tính tương thích của OpenBaton: https://github.com/openbaton/integration-tests
 
 *Note: Nên đọc kĩ mô tả của từng testcase và thực hiện từng testcase một. Thứ tự thực hiện nên bắt đầu từ các dummy-test (sử dụng dummy-vnfm, dummy-vim-instance) rồi mới tới generic vnfm, real-vim sử dụng hệ thống openstack thật. Release 3 của Openbaton mới nhận được Identify API 2.0 (Keystone của OpenStack), nên Keystone của OpenStack cần được ENABLE_IDENTITY_V2=True (trong stackrc của Devstack).

# VIM INSTANCE (Or Point of Presence) REGISTRATION 

Đăng kí (hay kết nối) với các hạ tầng NFVI sẽ sử dụng. Việc đăng kí có thể sử dụng CLI hoặc Dashboard. Log quá trình đăng kí trong /var/log/openbaton/openbaton.log và ./plugin-logs/plugin-[tên VIM types sử dụng].log

http://openbaton.github.io/documentation/vim-instance/

*Sample: 
https://github.com/ttcong/Luan-van-NFV/LAB/OpenBaton/Register-PoP.json

Tất cả các thông tin đều phụ thuộc vào Project(Tennant)/UserName-Pass/authUrl/SecurityGroup/Location(Region) của OpenStack.
KeyPair là keypair import từ Openstack. KeyPair không có thì phải để null tuy nhiên nên có.
