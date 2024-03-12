---
title : "Security Group"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---
#### Security Group

Một số đặc điểm cơ bản của Security group:

* Chỉ có thể thêm vào các Allow rule, mà không thể bổ sung Deny rule.
* Có thể chỉ định các rule riêng biệt cho lưu lượng truy cập đi ra hoặc đi vào.
* Một Security group mới được tạo ra không có sẵn Inbound rules. 
  Do đó, tại thời điểm ban đầu Instance sẽ không cho phép bất cứ lưu lượng truy cập nào được phép đi vào, đòi hỏi ta phải bổ sung Inbound rule để cấp phép truy cập.
* Mặc định, Security group có sẵn Outbound rule cho phép mọi lưu lượng được phép đi ra khỏi Instance. 
Rule này có thể được chỉnh sửa (xóa) và bổ sung các Outbound rule cụ thể, chỉ rõ lưu lượng nào xuất phát từ Instance được phép đi ra ngoài.
Nếu SG không có Outbound rule thì không một lưu lượng nào được phép đi ra khỏi Instance. 
* Security groups là một dịch vụ Stateful - nghĩa là nếu lưu lượng đi vào Instance đã được cấp phép thì lưu lượng cũng có thể đi ra ngoài Instance, và ngược lại, bất kể Outbound rule như thế nào.
* Các Instance chỉ có thể giao tiếp được với nhau khi và chỉ khi chúng được liên kết với Security group cho phép kết nối, hoặc Security group mà Instance có liên kết chứa Rule cho phép lưu lượng try cập (ngoại trừ Security group mặc định với có các rule  mặc định cho phép toàn bộ lưu lượng được truy cập).
* Security group được liên kết với các network interface. 
Sau khi Instance đã được khởi tạo, ta vẫn có thể thay đổi Security group đã được gán với Instance, điều này cũng thay đổi security group đang được gán với primary network interface tương ứng. 

#### Security group Rule

Rule được sinh ra để cấp quyền truy cập cho lưu lượng đi vào hoặc đi ra khỏi Instance. Quyền truy cập này có thể được áp dụng cho một CIDR cụ thể hoặc cho một Security group nằm trong cùng một VPC hoặc nằm trong một VPC khác nhưng có kết nối peering đã được khởi tạo. 

Các thành phần cơ bản của Security group rule:
* (Chỉ đối với Inbound rules) gồm điểm xuất phát (nguồn) của lưu lượng truy cập và port đích hoặc dải port.
Nguồn có thể là một security group khác, là một dải IPv4 hoặc IPv6 CIDR hoặc đơn thuẩn là một địa chỉ IPv4 hoặc IPv6.
* (Chỉ đối với Outbound rules) gồm đích đến của lưu lượng và port đích hay dải port đích.
Đích đến có thể là một security group khác, là một dải IPv4 hoặc IPv6 CIDR hoặc đơn thuẩn là một địa chỉ IPv4 hoặc IPv6 hoặc là một dịch vụ bắt đầu bằng một tiền tố (ví dụ: igw_xxx) nằm trong danh sách prefix ID(một dịch vụ được xác định bởi prefix ID - tên và ID của dịch vụ khả dụng trong region).
* Mọi giao thức đều có một số giao thức chuẩn. Ví dụ: SSH là 22,..
