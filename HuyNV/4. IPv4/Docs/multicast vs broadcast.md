# Multicast

Địa chỉ multicast là một gói dữ liệu IP duy nhất đại diện cho một nhóm máy chủ mạng. Địa chỉ multicast có sẵn để xử lý datagram hoặc khung dự định là multicast cho một dịch vụ mạng được chỉ định.

Multicast: Các gói được gửi từ một địa chỉ nguồn đến một nhóm các máy tính. Địa chỉ đích tượng trưng cho các máy trạm muốn nhận lưu lượng này. Mặc định, một router hoặc một switch lớp 3 sẽ không chuyển các gói tin này trừ khi phải cấu hình định tuyến Multicast. Một thiết bị switch lớp 2 không thể nhận biết được vị trí của địa chỉ Multicast đích. Tất cả các gói sẽ được phát tán ra tất cả các cổng ở chế độ mặc định.

Một địa chỉ multicast nằm trong khoảng từ 224.0.0.0 đến 239.255.255.255.

Cơ chế dùng Unicast thì dữ liệu sẽ đi từ máy trạm đến máy trạm; Broadcast thì lưu lượng sẽ đi đến tất cả các máy trạm trên phân đoạn mạng đó. Cơ chế Multicast sẽ nằm giữa hai thái cực này, trong đó máy nguồn chỉ gửi những gói tin từ một máy trạm đến các người dùng muốn nhận loại lưu lượng đó đó. Nhóm này gọi là nhóm Multicast. Các máy nhận lưu lượng Multicast có thể nằm ở bất cứ nơi nào chứ không chỉ trên phân đoạn mạng cục bộ.

Các lưu lượng dạng Multicast thường là một chiều (unidirectional). Do có nhiều máy trạm nhận cùng một dữ liệu, nên thông thường các gói tin không được phép gửi ngược về máy nguồn trên cơ chế Multicast. Một máy trạm đích sẽ trả lưu lượng ngược về nguồn theo cơ chế Unicast. Cơ chế Multicast cũng sẽ được truyền theo kiểu không kết nối (connectionless). Multicast dùng UDP chứ không dùng TCP.

Các máy trạm muốn nhận dữ liệu từ nguồn Multicast có thể tham ra hoặc rời khỏi một nhóm multicast bất kỳ thời điểm nào. Hơn nữa, một máy trạm sẽ quyết định có trở thành thành viên của một hay nhiều nhóm multicast hay không. 

Có 3 yêu cầu cơ bản để có thể triển khai multicast trên mạng:

- Phải có một tập hợp các địa chỉ dành cho các nhóm multicast.
- Phải có một cơ chế trong đó các máy trạm có thể tham gia và rời khỏi nhóm.
- Phải có một giao thức định tuyến cho phép các router phân phối các lưu lượng multicast tới các thành viên của nhóm mà không làm quá tải tài nguyên mạng. 

# Broadcast

Một địa chỉ Broadcast sẽ đại diện cho tất cả các thiết bị kết nối cùng mạng. Do đó, khi một gói tin được gửi đến địa chỉ Broadcast, toàn bộ các thiết bị trong mạng đều nhận được.

Địa chỉ broadcast gồm 2 loại:

- Direct broadcast: 192.168.12.255
- Local broadcast: 255.255.255.255

Broadcast được sử dụng trong một mạng máy tính, trong số những thứ khác, khi địa chỉ IP của máy nhận vẫn chưa được biết tới. Kỹ thuật này được sử dụng trong mô hình OSI ở tầng mạng. Ví dụ như các [giao thức ARP](https://wikimaytinh.com/giao-thuc-arp-la-gi-nguyen-ly-hoat-dong-cua-arp.html), [DHCP](https://wikimaytinh.com/dhcp-la-gi-cach-kiem-tra-dhcp.html), và Wake on LAN.


