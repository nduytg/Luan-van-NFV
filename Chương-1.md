---
title: Chương 1
layout: post
author: nduytg
permalink: /Luận văn
source-id: 1_BrIrW6mQLABn7TvtB68C-YgTxgaHdGyXmGcrkAw4CE
published: true
---
Chương 1

*Giới thiệu sơ lược về NFV và thực trạng mạng hiện nay*

[[TOC]]

# Giới thiệu đề tài

Trong thời đại hiện nay, sự ra đời của các công nghệ mới như mạng di động 5G, Internet của vạn vật (Internet of Things), điện toán đám mây (Cloud Computing), thực tại ảo (Virtual Reality)… cũng như việc mở rộng hoạt động kinh doanh của các doanh nghiệp, đặc biệt là các doanh nghiệp Internet dẫn đến nhu cầu về đường truyền và quản lý luồng dữ liệu tăng lên theo cấp số nhân. Điều này đặt ra cho các nhà cung cấp dịch vụ (Service Provider) áp lực phải luôn không ngừng mở rộng qui mô cũng như nâng cao chất lượng dịch vụ truyền dẫn. Cách làm phổ biến hiện tại là ứng với mỗi một dịch vụ mới, các nhà cung cấp dịch vụ lại cần trang bị thêm những thiết bị phần cứng mới tương ứng.

*Vào thời điểm thực hiện luận văn này (nửa đầu năm 2017), Viettel cũng đã bắt đầu triển khai rộng rãi hệ thống mạng 4G tại Việt Nam.** Việc này đặt ra một bài toán phức tạp về việc xây dựng hạ tầng phần cứng mạng bên dưới để đáp ứng các dịch vụ mạng mới.*

Đa phần những hệ thống mạng hiện tại đều sử dụng thiết bị chuyên dụng của các hãng như Cisco hay Juniper,.. Tuy nhiên, những hệ thống này lại đang dần bộc lộ các khuyết điểm như: giá thành thiết bị đắt đỏ, khó quản lý tập trung, kém tương thích với các hệ thống của hãng khác khiến các doanh nghiệp phải phụ thuộc vào một số hãng phần cứng nhất định... Và quan trọng hơn thì việc khởi tạo một dịch vụ mạng hiện tại phải trải qua rất nhiều bước như: lắp đặt thiết bị mạng, đấu nối dây, cấu hình dịch vụ, kiểm thử và cuối cùng mới là đưa vào vận hành. Mỗi một dự án lại có các yêu cầu riêng, đòi hỏi những loại thiết bị chuyên dụng khác nhau. Với một quy trình dài dòng và nhiêu khê như vậy sẽ làm lãng phí rất nhiều thời gian và nhân lực cho mỗi dự án mới, khách hàng mới. Đặc biệt là có những dự án chỉ cần hoạt động vài tháng thì việc triển khai dịch vụ theo mô hình truyền thống là vô cùng lãng phí và tốn thời gian.

Đây là những khuyết điểm không thể chấp nhận trong môi trường công nghệ thông tin hiện nay bởi nhu cầu của từng khách hàng hiện tại là rất đa dạng và đặc thù. Mỗi một giây chậm trễ đều lãng phí tiền bạc và nguồn lực của công ty mà quan trọng hơn là đánh mất sự tín nhiệm của người dùng. Với những vấn đề tồn đọng trên thì hạ tầng mạng hiện có về lâu dài sẽ không thể đáp ứng nổi nhu cầu của các stakeholder (doanh nghiệp, nhà cung cấp dịch vụ, người dùng cuối).

![image alt text]({{ site.url }}/public/QoJjYCYO0CEhE5KKE7fQ_img_0.jpg)

*Nhu cầu của các stakeholders*

*Vậy thì liệu có cách nào để giải quyết được bài toán trên hay không?** *

Câu trả lời là có. Giải pháp ở đây chính là ứng dụngcông nghệ ảo hóa (Virtualization) vào hạ tầng mạng trong các Datacenter, các Network Node trên đường truyền và tại nhà của người dùng cuối bằng công nghệ Ảo hóa Chức năng Mạng (Network Function Virtualization - NFV).

Công nghệ NFV cho phép ta tách biệt các hàm chức năng mạng (Network Function) như: NAT, Firewall, Intrusion Detection, DNS, Caching,... khỏi các thiết bị vật lý chuyên biệt và triển khai dưới hình thức phần mềm có thể chạy trong môi trường ảo hóa trên các thiết bị vật lý phổ thông hơn. Các thiết bị vật lý lúc này có thể là các high-volume servers, switches và storages được sản xuất theo các tiêu chuẩn công nghiệp chung. Việc này sẽ giúp ta giảm chi phí đầu tư và sự phụ thuộc vào các thiết bị phần cứng chuyên biệt của từng hãng phần cứng như trước đây. Đồng thời, các nhà mạng có thể khởi tạo, điều phối và di dời các hàm chức năng mạng, các dịch vụ mạng một cách linh hoạt hơn từ đó tận dụng tốt hơn hạ tầng phần cứng đã đầu tư. Không chỉ chi phí đầu tư mà cả chi phí vận hành, bảo dưỡng và nâng cấp thiết bị sau này cũng sẽ được cắt giảm đáng kể.

*Một trong những nhà mạng lớn ở Mỹ hiện nay là AT&T đã tuyên bố rằng hãng sẽ ảo hóa 75% hạ tầng mạng của mình vào năm 2020 bằng cách ứng dụng công nghệ NFV và SDN (Software-defined Networking).*

# Lịch sử NFV

Định nghĩa về NFV bắt nguồn từ các nhà cung cấp dịch vụ - những người đang tìm kiếm giải phát để thúc đẩy nhanh hơn việc triển khai các dịch vụ mạng mới cũng như thu về lợi nhuận cao hơn. Những hạn chế của các thiết bị phần cứng đòi hỏi họ phải áp dụng các công nghệ ảo hóa vào hệ thống mạng của họ. Vì chung mục đích như vậy, nhiều nhà cung cấp dịch vụ đã hợp tác với nhau và thành lập nên nhóm ETSI ISG NFV (ETSI Industry Specification Group for Network Functions Virtualization) thuộc Viện Tiêu chuẩn Viễn thông Châu Âu (European Telecommunications Standards Institute - ETSI). Đây là là nhóm có nhiệm vụ phát triển các yêu cầu và kiến trúc để áp dụng ảo hóa cho nhiều chức năng trong hệ thống mạng viễn thông. Ban đầu, ETSI ISG NFV gồm 7 nhà mạng viễn thông hàng đầu là: AT&T, BT, Deutsche Telekom, Orange, Telecom Italia, Telefonica và Verizon. Ngoài ra còn có sự tham gia của 52 nhà mạng, các nhà cung cấp thiết bị viễn thông, hãng sản xuất phần cứng khác. Không lâu sau đó, cộng đồng ETSI ISG NFV mở rộng với 230 công ty, bao gồm nhiều nhà cung cấp dịch vụ toàn cầu.

*Tháng 10-2012, tại hội nghị SDN and OpenFlow World Congress diễn ra tại Darmstadt (Đức), ETSI ISG NFV đã công bố sách trắng đầu tiên về NFV. **Từ đó đến nay**, nhóm nghiên cứu của ETSI đã tiếp tục cho ra đời những tài liệu đặc tả chuyên sâu hơn về NFV, bao gồm các định nghĩa về thuật ngữ tiêu chuẩn, các ứng dụng, mô hình kiến trúc tổng quát,... Chúng đã trở thành những tài liệu tham khảo chuẩn về một mô hình NFV cho cả các nhà phát triển và nhà cung cấp dịch vụ ứng dụng NFV.*

<table>
  <tr>
    <td>Tiêu chí so sánh</td>
    <td>Hạ tầng mạng truyền thống</td>
    <td>Ứng dụng NFV</td>
  </tr>
  <tr>
    <td>Chi phí phần cứng</td>
    <td>Chi phí cao hơn do phải mua cả giải pháp của từng hãng phần cứng chuyên biệt.</td>
    <td>Chi phí thấp hơn do chỉ sử dụng phần cứng phổ thông còn phần mềm hoàn toàn chủ động được, đồng thời tận dụng được tối đa hiệu suất phần cứng.</td>
  </tr>
  <tr>
    <td>Khả năng điều khiển luồng traffic</td>
    <td>Khó, phức tạp.</td>
    <td>Dễ dàng, linh động hơn, đặc biệt là nếu được kết hợp với công nghệ Software-defined Network.</td>
  </tr>
  <tr>
    <td>Khả năng tùy biến, mở rộng, thay thế.</td>
    <td>Khó khăn do phụ thuộc hoàn toàn vào hãng phần cứng. Khi cần thay thế thì phải thay thế toàn bộ.</td>
    <td>Dễ dàng do tất cả đều được thiết kế theo dạng module.</td>
  </tr>
  <tr>
    <td>Khả năng nâng cấp</td>
    <td>Thấp. Tốc độ cập nhật phần mềm trên các thiết bị phần cứng thường chậm và phụ thuộc nhiều vào hãng sản xuất.</td>
    <td>Cao. Tốc độ cập nhật phần mềm nhanh, do cơ chế nguồn mở và có nhiều hãng cung cấp phần mềm điều khiển.</td>
  </tr>
  <tr>
    <td>Hệ sinh thái</td>
    <td>Nhỏ, bó buộc theo giải pháp của từng hãng.</td>
    <td>Rộng, dễ dàng tương tác với các thành phần của các hãng khác thông qua các chuẩn giao tiếp chung được ETSI đặt ra.</td>
  </tr>
  <tr>
    <td>Độ ổn định</td>
    <td>Cao</td>
    <td>Thấp (nhưng sẽ tăng dần trong tương lai)</td>
  </tr>
  <tr>
    <td>Khả năng tự động mở rộng khi lưu lượng truy cập tăng</td>
    <td>Không</td>
    <td>Có</td>
  </tr>
  <tr>
    <td>Yêu cầu về trình độ nhân sự</td>
    <td>Vừa phải</td>
    <td>Đòi hỏi nhân sự có chuyên môn cao</td>
  </tr>
</table>


*Bảng so sánh giữa NFV và hạ tầng mạng truyền thống*

# Lợi ích của NFV

Ta hãy cùng điểm qua một số lợi ích mà NFV mang lại:

* **Triển khai các dịch vụ mạng một cách nhanh chóng: **Đây là một trong những ưu điểm quan trọng nhất của NFV. Nhờ tận dụng công nghệ ảo hóa và điện toán đám mây, các kỹ sư có thể triển khai các dịch vụ mạng (Network Service) chỉ trong vòng vài giờ so với nhiều ngày như hiện nay. Điều này đồng nghĩa với việc ta có thể giảm thời gian đưa sản phẩm/dịch vụ mới ra thị trường, tăng tính cạnh tranh cho doanh nghiệp.

* **Tận dụng tối đa hạ tầng phần cứng:**** **Nhờ tận dụng công nghệ ảo hóa, một hạ tầng mạng vật lý có thể chứa nhiều hạ tầng mạng ảo trên nó. Từ đó, ta có thể phục vụ được nhiều khách hàng khác nhau cũng như tiết kiệm được đáng kể chi phí đầu tư và duy trì hoạt động. Bên cạnh đó, đội ngũ quản trị còn có thể tạo nên những môi trường thử nghiệm để huấn luyện nhân viên song song với các môi trường dịch vụ thật đang hoạt động.

* **Đơn giản hóa việc quản trị:** Thông qua các hàm API, quản trị viên hệ thống có thể kiểm soát luồng dữ liệu, tài nguyên hệ thống một cách dễ dàng, linh động và tập trung.

* **Linh hoạt trong việc đáp ứng lưu lượng băng thông: **Hệ thống có thể tự động khởi tạo thêm các chức năng mạng để khi lưu lượng băng thông tăng đột biến, đáp ứng được nhu cầu người dùng. Ngược lại, hệ thống cũng có thể dễ dàng thu hẹp các chức năng mạng lại khi lượng tải thấp, giúp tiết kiệm tài nguyên và điện năng tiêu thụ.

Từ những lợi ích trên, ETSI đã đề xuất ra một số use-case cụ thể như sau: 

![image alt text]({{ site.url }}/public/QoJjYCYO0CEhE5KKE7fQ_img_1.png)

*Một số usecase tiêu biểu của NFV*

1. NFVI as a Service: các Service Provider cung cấp hạ tầng ảo hóa chức năng mạng  (NFV Infrastructure) của mình cho các Service Provider khác sử dụng lại như một dịch vụ điện toán đám mây theo mô hình IaaS (Infrastructure as a Service).

2. VNF as a Service: các Service Provider sẽ cung cấp các chức năng mạng dưới dạng điện toán đám mây theo mô hình SaaS (Software as a Service) cho các doanh nghiệp. Điều này giúp các doanh nghiệp thay thế cắt giảm chi phí đầu tư, vận hành, bảo dưỡng các thiết bị mạng như Router, Firewall, IPS,... cho hệ thống nội bộ của mình.

3. Virtual Network Platform as a Service: Service Provider cung cấp hạ tầng và các ứng dụng theo mô điện toán đám mây PaaS (Platform as a Service) để doanh nghiệp tự triển khai ứng dụng mạng cho riêng mình.

4. VNF Forwarding Graphs: Service Provider kết nối các VNFs thông qua các kết nối luận lí giữa các VNFs, các kết nối vật lý giữa các máy vật lý host các VNFs và kết nối VNFs với các PNFs (Physical Network Function) để tạo thành một dịch vụ mạng (Network Service) hoàn chỉnh.

5. Virtualisation of Mobile Core Network, IMS and Mobile Base Station:: Cho phép các nhà mạng viễn thông/di động ảo hóa hạ tầng của mình, từ đó giảm chi phí, tăng hiệu suất, tăng tính sẵn sàng, linh hoạt cho hệ thống.

6. Virtualisation of Home Enviroment: Nhà cung cấp dịch vụ có thể ảo hóa một phần hoặc toàn bộ các thiết bị thu nhận/giải mã tín hiệu  (Residental Gateway như Router hay Setup Box như đầu thu truyền hình Internet) tại nhà của người sử dụng. Người sử dụng cuối không còn cần phải quan tâm đến các bước cấu hình phức tạp cũng như quan tâm bảo dưỡng các thiết bị thu nhận/giải mã tín hiệu của các dịch vụ như Internet, Thoại, Truyền hình Internet,...

7. Virtualisation of Content Delivery Networks: giúp các nhà cung cấp dịch vụ ảo hóa toàn bộ các thành phần của một hệ thống CDN (CDN controller và các cache nodes) và điều chỉnh luồng dữ liệu thích hợp.

![image alt text]({{ site.url }}/public/QoJjYCYO0CEhE5KKE7fQ_img_2.png)

8. Fixed Access Network Functions Virtualisation: việc ứng dụng NFV sẽ tối ưu tài nguyên kết nối đường truyển bằng cách tăng hiệu năng, giảm tiêu thụ năng lượng tại các Network Node trên đường truyền. Đồng thời, việc ứng dụng NFV còn mở ra khả năng chia sẻ tài nguyên này giữa các nhà cung cấp dịch vụ với nhau giúp giảm chi phí và tăng khả năng tận dụng tài nguyên.

Trong môi trường thực tế tại Việt Nam, nhóm nghiên cứu nhận thấy việc ứng dụng NFV vào thực tiễn có thể giải quyết các bài toán cụ thể sau đây:

* Đối với các **nhà cung cấp dịch vụ Internet và viễn thông** như Viettel, VNPT, FPT, CMC,...

    * Ảo hóa hạ tầng mạng Mobile Core Network, IMS và Mobile Base Station kết hợp với công nghệ SDN: triển khai, quản lý các dịch vụ di động/ di động viễn thông dễ dàng, nhanh chóng, linh hoạt và tối ưu hơn trên hạ tầng mạng viễn thông/di động trên nền phần cứng COTS (Commercial off the Shell).

    * Fixed Access Network Functions Virtualisation: Tối ưu hóa việc truyển dẫn cũng như cắt giảm chi phí nếu có thể chia sẻ tài nguyên về hạ tầng kết nối với nhau.

    * Virtualisation of Home Enviroment: quản lý tốt hơn dịch vụ Internet, Thoại, Truyền hình Internet đến người dùng. Cắt giảm chi phí triển khai, bảo trì, sửa chữa, đào tạo con người cho các thiết bị ở tại nhà khách hàng.

* Các công ty kinh doanh nội dung số đa phương tiện như: VNG, FilmPlus, K+,...

    * CDN: tối ưu việc xây dựng hạ tầng CDN cho dịch vụ của mình.

    * Sử dụng VNF as a Service như: Load balance, Firewall của các nhà cung cấp dịch vụ khác.

* Đối với các công ty cung cấp **hosting/public cloud **như: Vinahost, Vinadata, CMC, vHost,….

    * NFVIaaS hoặc Virtual Network Platform as a Service cho các nhà cung cấp dịch vụ sử dụng để tự xây dựng dịch vụ mạng của riêng mình.

    * VNF as a Service cung cấp dịch vụ mạng như: Load balance, Firewall,... cho các doanh nghiệp khác.

# Xu thế trong tương lai gần

Theo hãng phân tích IHS Infonetics, thị trường (NFV) sẽ tăng trưởng từ $2.3 tỉ trong năm 2015 lên đến $11.6 tỉ vào năm 2019. Nhận thức được những vấn đề tồn đọng cũng như những lợi ích mà NFV mang lại, hiện đã và đang có rất nhiều hãng công nghệ, viện nghiên cứu, trường đại học lớn đầu tư vào các giải pháp NFV:

* Về hướng nghiên cứu các tiêu chuẩn, đặc tả: Viện Tiêu chuẩn Viễn thông Châu Âu (European Telecommunications Standards Institute - ETSI), 3GPP,... đã đưa ra các sách trắng và tài liệu đặc tả nhằm tạo nên bộ khung để các công ty, cộng đồng nguồn mở xây dựng các dự án của riêng mình và có thể liên kết chúng với nhau.

* Về hướng phát triển các sản phẩm, giải pháp NFV:

    * Các dự án nguồn mở như: OPNFV, OpenSMano, OpenBaton,... 

    * Các sản phẩm thương mại như: Red Hat, Mirantis, VMWare NSX,...

* Về hướng ứng dụng trong hoạt động kinh doanh (một số use case tiêu biểu): 

    * Việc triển khai hệ thống 5G của SK Telecom (Hàn Quốc)

    * Quá trình chuyển đổi hạ tầng mạng của AT&T (Mỹ)

# Bố cục luận văn

(Đã giấu)

Ngoài ra, do hạn hẹp về thời gian nên nhóm chưa thể tìm hiểu chuyên sâu tất cả các vấn đề, còn một số vấn đề về việc tối ưu hóa hệ thống, ứng dụng containter, monitor và logging… (đoạn này sẽ cho vô khúc cuối cùng của luận văn).

# Tham khảo

* NFV Whitepaper 2012, 2013, 2014 - ETSI

* Bài phỏng vấn của Openstack.org với đại diện của SK Telecom 2/2016 [http://superuser.openstack.org/articles/how-openstack-is-helping-sk-telecom-roll-out-the-next-5g-lte-network](http://superuser.openstack.org/articles/how-openstack-is-helping-sk-telecom-roll-out-the-next-5g-lte-network)

* Viettel đang gấp rút triển khai mạng 5G trên cả nước [http://vneconomy.vn/cuoc-song-so/viettel-dang-gap-rut-trien-khai-mang-4g-tren-ca-nuoc-20170224024715453.htm](http://vneconomy.vn/cuoc-song-so/viettel-dang-gap-rut-trien-khai-mang-4g-tren-ca-nuoc-20170224024715453.htm)

* A network build in software - AT&T 

[http://about.att.com/innovation/sdn](http://about.att.com/innovation/sdn)

* NFV and SDN spend set to hit $157B by 2020 [http://www.rcrwireless.com/20150917/telecom-software/nfv-and-sdn-spend-set-to-hit-157b-by-2020-tag2](http://www.rcrwireless.com/20150917/telecom-software/nfv-and-sdn-spend-set-to-hit-157b-by-2020-tag2)

