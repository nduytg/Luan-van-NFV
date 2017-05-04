# Tìm hiểu về OpenDayLight

## 1.Giới thiệu về OpenDayLight
OpenDayLight (ODL) là một dự án SDN mã nguồn mở ra đời vào năm 2013 do tổ chức cùng tên OpenDayLight Foundation quản lý.

Vì muốn thúc đẩy việc ứng dụng công nghệ SDN và NFV vào hạ tầng mạng, tổ chức Linux Foundation đã thành lập nên dự án này cùng với những đại gia về công nghệ khác bao gồm: Arista Networks, Big Switch Networks, Brocade, Cisco, Citrix, Ericsson, HP, IBM, Juniper Networks, Microsoft, NEC, Nuage Networks, PLUMgrid, Red Hat và VMware.

## 2.ODL SDN Controller
OpenDayLight là một phần mềm cho phép người dùng điểu khiển các thiết bị mạng một cách tập trung thông qua giao thức OpenFlow (nguồn mở). ODL được viết bằng ngôn ngữ Java chạy trên các máy ảo JVM.

Ngoài ra, ODL còn cung cấp khả năng lập trình điều khiển các thiết bị và theo dõi hệ thống khi cần thiết, điều này làm tăng tính tùy biến và linh hoạt của hệ thống mạng. Một ưu điểm vượt trội so với các thiết bị mạng cổ điển trước đây.

Như ta có thể thấy, ODL phân tách rạch ròi giữa control plane và data plane, việc này giúp ODL có thể quản trị được các network services trên thiết bị phần cứng của nhiều hãng khác nhau.
Kiến trúc

## 3.Tổng quan kiến trúc của OpenDayLight
### Microservice
OpenDayLight là một phần mềm theo kiến trúc microservice (module/plugin). Vì thế, ODL có thể hoạt động tốt trên nhiều nền tảng thiết bị với nhiều quy mô khác nhau, dễ dàng mở rộng hoặc thay đổi mã nguồn của các module khi cần thiết. ODL tập trung vào việc mô tả mô hình mạng, các chức năng được thực thi trên nó và trạng thái, kết quả đạt được.

Bằng việc chia sẻ và lưu trữ các kiểu dữ liệu có cấu trúc theo dạng YANG, ODL cho phép người quản trị quản lý chặt chẽ các dịch vụ, khởi tạo từng dịch vụ và kết hợp chúng lại với nhau để giải quyết nhiều bài toán phức tạp hơn. Trong ODL Model Driven Service Abstraction Layer (MD-SAL), bất kỳ ứng dụng hay chức năng nào cũng có thể được đóng gói thành 1 service và chạy trên controller. Các service này có thể được cấu hình và kết nối lại với nhau theo vô số cách để đáp ứng nhu cầu thay đổi liên tục trong hệ thống mạng.

Một số đặc điểm trong kiến trúc microservice của OpenDayLight
Có thể cài đặt bất cứ giao thức hay dịch vụ nào bạn cần.
Có khả năng kết hợp nhiều dịch vụ và giao thức lại với nhau để giải quyết các bài toán khó.
Kiến trúc theo dạng module cho phép người quản trị có thê dùng bất kỳ ứng dụng nào được người khác tạo ra và chia sẻ trong hệ sinh thái của OpenDayLight

### Hỗ trợ nhiều giao thức mạng
ODL là phần mềm hỗ trợ nhiều giao thức mạng nhất trong tất cả các giải pháp về SDN. OpenDayLight hỗ trợ giao thức OpenFlow và các extension của nó nhưu Table Type Pattern cũng như các giao thức mạng truyền thống là: NETCONF, BGP/PCEP và CAPWAP. Ngoài ra ODL còn có thể tương tác với OpenStack và Open vSwitch qua dự án OVSDB Integration Project.
SDN và NFV
Hiện nay, các nhà cung cấp dịch vụ truyền thông - Communication Service Provider (CSP) đang thực hiện một loạt các PoC (Proof of Concept) (ETSI NFV Proof of Concepts) dựa trên OpenDayLight và trong tương lai là triển khai NFV trên SDN.

NFV PoC #19 của ETSI đã cho thấy việc ứng dụng ODL làm SDN chó thể quản lý việc triển khai các VNF, service chainning và điều phối VNF bởi OpenSrack. PoC này được tài trợ bởi AT&T và sử dụng các switch, phần mềm của nhiều hãng khác nhau.

OpenDayLight còn được chọn làm một trong những công nghệ nền tảng cho dự án Open Platform for NFV (OPNFV) một dự án của Linux Foundation. ODL được OPNFV chọn vì những lý do sau:
Nền tảng mở, không phụ thuộc vào bất kỳ hãng nào.
Northbound interface có thể tương thích với nhiều hệ thống quản lý khác nhau.
Hỗ trợ kết nối giữa nhiều domain khác nhau.
Có sẵn tính năng ảo hóa mạng và service function chainning
Hỗ trợ nhiều loại thiết bị và công nghệ
Hỗ trợ quản lý policy

## 4.Thực hành
http://docs.opendaylight.org/en/stable-boron/getting-started-guide/index.html

http://docs.opendaylight.org/en/stable-boron/getting-started-guide/common-features/dlux.html
Dev
http://sdnhub.org/tutorials/opendaylight/

## 5.Tham khảo
ODL Overview
https://www.opendaylight.org/platform-overview/

ODL and NFV
https://www.opendaylight.org/cloud-and-nfv

ODL Getting Started Guide
http://docs.opendaylight.org/en/stable-boron/getting-started-guide/index.html

