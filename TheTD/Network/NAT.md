# **NAT**

## **1. NAT là gì**
**NAT** là viết tắt của **Network Address Translation** có nghĩa là biên dịch địa chỉ mạng. Thông thường, NAT được dùng phổ biến trong mạng LAN sử dụng địa chỉ cục bộ khi cần truy cập ra mạng Internet công cộng và ngược lại. Vị trí NAT là router biên kết nối giữa hai mạng.

![NAT](img/NAT(1).png)

**Địa chỉ Private**: Được định nghĩa trong RFC 1918
- 10.0.0.0 - 10.255.255.255
- 172.16.0.0 - 172.31.255.255
- 192.168.0.0 - 192.168.255.255

**Địa chỉ Public**L Là các địa chỉ còn lại, được cung cấp bởi các tổ chức có thẩm quyền

## **2. Ưu điểm và nhược điểm của NAT**
**Ưu điểm**
- Tiết kiệm địa chỉ IPv4
- Che giấu IP bên trong mạng LAN
- Chia sẻ kết nối Internet cho nhiều máy tính chỉ với IP public duy nhất trong mạng LAN
- Giúp nhà quản trị mạng lọc được các gói tin đến và xét duyệt quyền truy cập của IP public đến một port bất kỳ

**Nhược điểm**
- Tốn thời gian chuyển đổi giữa IP Private <-> IP Public, tăng độ chễ trong quá trình Switching
- Vì nó giấu IP nên sẽ khó khắn khi truy vết gói tin gốc

## **3. Các thuật ngữ liên quan**
![NAT](img/NAT(2).png)

- **Địa chỉ inside local**: Địa chỉ được đặt ở Local, nó không được cung cấp bởi NIC
- **Địa chỉ inside global**: Địa chỉ IP đã được đăng ký tại NIC
- **Địa chỉ outside local**: Địa chỉ IP nằm ở thiết bị mạng bên ngoài. Các thiết bị bên trong sẽ tìm thấy thiết bị mạng bên ngoài thông qua địa chỉ này. Địa chỉ outside local không nhất thiết phải đăng ký bởi NIC. Nó có thể là một địa chỉ private
- **Địa chỉ outside global**: Địa chỉ IP đặt cho  thiết bị ở mạng bên ngoài. Địa chỉ này là một IP hợp lệ trên mạng Internet.

## **4. Cơ chế hoạt động**
![NAT](img/NAT(3).png)
- Giai đoạn gói tin được truyền từ Host ra mạng Internet, NAT dịch hay thay đổi một hoặc cả hai địa chỉ bên trong gói tin đó đi qua một Router hay một số thiết bị khác. Thông thường nó chỉ thay đổi địa chỉ Private của một kết nối mạng thành địa chỉ Public.
- Giai đoạn gói tin truyền từ mạng Internet (Public) quay trở lại NAT, NAT sẽ thực hiện nhiệm vụ thay đổi địa chỉ đích đến thành địa chỉ IP trong hệ thống mạng cục bộ và chuyển đi

## **5. Phân loại NAT**
### **Static NAT**
Static NAT (NAT tĩnh) là phương thức NAT một đổi một. Một IP Private sẽ được map với một IP Public.

![NAT](img/NAT(4).png)

***Cấu hình NAT Static***
> Router(config)#ip nat inside source static [inside local address] [inside global address]

**Ví dụ:**
```sh
R(config)#ip nat inside source statice 192.168.32.10 213.18.123.110 

(Địa chỉ 192.168.32.10 sẽ được chuyển thành 213.18.123.110 khi đi ra khỏi Router)
Sau khi cấu hình xong phải áp dụng vào cổng in và cổng out, trong ví dụ dưới đây, cổng
Ethernet là cổng in, còn cổng Serial là cổng out

Router(config)#interface ethernet 0
Router(config-if)#ip nat inside
Router(config)#interface serial 0
Router(config-if)#ip nat outside
```
### **Dynamic NAT**
Một địa chỉ IP Private sẽ được map với một địa chỉ IP Public trong nhóm địa chỉ IP Public.

![NAT](img/NAT(5).png)

```sh
Router(config)#ip nat pool [ tên pool] [A.B.C.D A1.B1.C1.D1] netmask [mặt nạ]
Router(config)#ip nat inside source list [số hiệu ACL] pool [tên pool]
Router(config)#access-list [số hiệu ACL] permit [A.B.C.D wildcard masks]

Ví dụ:

R(config)#ip nat pool nat-pool 1 213.18.123.110 213.18.123.120 netmask 255.255.255.0
R(config)#ip nat inside source list 1 pool nat-pool1
R(config)#access-list 1 permit 192.168.32.0 0.0.0.255
Sau đó áp vào cổng In và Out như Static NAT
Note: Dải địa chỉ inside local address và inside global address phải nằm trong dải cho phép của ACL
```

### **NAT Overload (PAT: Port Address Translation)**
NAT Overloading là một dạng thức của NAT động (Dynamic Overload). Nhiều địa chỉ IP Private sẽ được map với một địa chỉ IP Public qua các Port (cổng) khác nhau.

Cũng giống như PAT (Port Address Translation), một địa chỉ NAT hoặc Port sẽ có nhiều mức độ NAT khác nhau.

![NAT](img/NAT(6).png)

```sh
- Cấu hình overload với 1 địa chỉ IP cụ thể:
Router(config)#access-list [số hiệu] permit [địa chỉ] [wildcard mask]
Router(config)#ip nat inside source list [tên số hiệu ACL] pool [tên pool] overload

Ví dụ:
R(config)#access-list 2 permit 10.0.0.0 0.0.0.255
R(config)#ip nat inside source list 2 pool nat-pool2 overload

- Cấu hình overload dùng địa chỉ của cổng ra.(Thường xuyên được dung hơn là trường
hợp trên)
Router(config)#ip nat inside source list [tên số hiệu ACL] interface [cổng ra] overload
Router(config)#access-list [số hiệu] permit [địa chỉ] [windcard mask]
Ví dụ:
R(config)#ip nat inside source list 3 interface serial 0/0 overload
R(config)#access-list 3 permit 10.0.0.0 0.0.0.255
```

Trong Overload NAT, mỗi máy tính trong mạng nội bộ (Private Network) được Router biên dịch đến cùng một địa chỉ IP 213.18.123.100 nhưng trên các cổng giao tiếp khác nhau.


# **Tài liệu tham khảo**
1. https://wikimaytinh.com/nat-la-gi-nat-hoat-dong-nhu-the-nao-trong-mang.html
2. https://quantrimang.com/cong-nghe/network-address-translation-nat-hoat-dong-nhu-the-nao-phan-1-118495
3. https://bizflycloud.vn/tin-tuc/nat-la-gi-network-address-translation-cach-cau-hinh-va-gioi-thieu-cac-ky-thuat-pho-bien-20210329113205944.htm