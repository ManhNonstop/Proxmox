Bước 1: Cài Pritunl

Tạo VM để cài Pritunl, OS mình chọn là Ubuntu 24, sau đó paste lệnh bên dưới để cài đặt Pritunl

============

sudo tee /etc/apt/sources.list.d/mongodb-org.list << EOF
deb [ signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu noble/mongodb-org/8.0 multiverse
EOF

sudo tee /etc/apt/sources.list.d/openvpn.list << EOF
deb [ signed-by=/usr/share/keyrings/openvpn-repo.gpg ] https://build.openvpn.net/debian/openvpn/stable noble main
EOF

sudo tee /etc/apt/sources.list.d/pritunl.list << EOF
deb [ signed-by=/usr/share/keyrings/pritunl.gpg ] https://repo.pritunl.com/stable/apt noble main
EOF

sudo apt --assume-yes install gnupg

curl -fsSL https://www.mongodb.org/static/pgp/server-8.0.asc | sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg --dearmor --yes

curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg | sudo gpg -o /usr/share/keyrings/openvpn-repo.gpg --dearmor --yes

curl -fsSL https://raw.githubusercontent.com/pritunl/pgp/master/pritunl_repo_pub.asc | sudo gpg -o /usr/share/keyrings/pritunl.gpg --dearmor --yes

sudo apt update

sudo apt --assume-yes install pritunl openvpn mongodb-org wireguard wireguard-tools

sudo ufw disable

sudo systemctl start pritunl mongod

sudo systemctl enable pritunl mongod

============

Bước 2: Cấu hình Pritunl

Mở port SSH và HTTPS trên Firewall để truy cập và cài đặt Pritunl

<img width="1685" height="890" alt="image" src="https://github.com/user-attachments/assets/f55b1fef-72f5-49b6-8e8b-5358c05893a1" />

Cài đặt Pritunl

<img width="1686" height="937" alt="image" src="https://github.com/user-attachments/assets/7e3f735a-e271-4f09-b978-8fedab296b07" />

<img width="801" height="284" alt="image" src="https://github.com/user-attachments/assets/8efe46fe-d74e-42ed-b406-63fca670fd1e" />

Sau khi cài đặt xong, Pritunl active là có thể sang bước cấu hình

Cấu hình Pritunl

<img width="1685" height="890" alt="image" src="https://github.com/user-attachments/assets/07d2e250-6fab-4cc4-94ff-242f58da132d" />

Nhập lệnh **sudo pritunl setup-key** để lấy key kết nối với mongodb, sau đó nhấn Next

<img width="1685" height="892" alt="image" src="https://github.com/user-attachments/assets/71f2678e-b94d-4934-9e3d-02135f7bd747" />

Sau đó nhập tiếp lệnh **sudo pritunl default-password** để lấy thông tin đăng nhập Pritunl, sau đó login vào

<img width="1685" height="888" alt="image" src="https://github.com/user-attachments/assets/937e6cf4-bd10-45cb-8729-3e48cc0bf477" />

Ở bước này, chúng ta có thể đổi username và password, port access hoặc set domain để cài SSL. Mình chỉ đổi port access sang 8443, còn lại giữ nguyên và chọn Save. Lúc này cần quay lại pfSense và đổi lại port 443 sang 8443 ở mục NAT để có thể truy cập với port mới.

<img width="1672" height="896" alt="image" src="https://github.com/user-attachments/assets/e762fc47-7d48-4db4-8b87-b6c41208dd09" />

Bước đầu tiên setup là tạo Organization, bấm Add Organization

<img width="1670" height="893" alt="image" src="https://github.com/user-attachments/assets/6db642d0-4e8c-4916-b848-01a993e1fbd9" />

Nhập tên tùy ý và chọn Add, sau khi xong sẽ như ảnh

<img width="1681" height="896" alt="image" src="https://github.com/user-attachments/assets/acc8da54-baee-4479-a84b-2559371878d5" />

Ở bước này, mình add User manhhc, có thể nhập mã pin để thêm bảo mật

<img width="1685" height="895" alt="image" src="https://github.com/user-attachments/assets/189e8334-1660-4cc8-8748-6def8b6eb4c5" />

Tiếp theo cần tạo Server để kết nối, chọn Add Server

<img width="1683" height="894" alt="image" src="https://github.com/user-attachments/assets/042929f6-bb82-433b-9ad3-3f1fcbb4a5c4" />

Nhập tên cho server, đổi Port từ UDP sang TCP

<img width="1680" height="893" alt="image" src="https://github.com/user-attachments/assets/55154e0f-c568-455b-a098-b618a0338fd2" />

Tiếp tục Attach Organization vừa tạo vào Server

<img width="1671" height="896" alt="image" src="https://github.com/user-attachments/assets/b9508696-152a-4982-a56d-c08eb2dc27c3" />

Sau đó Start Server và hiển thị như ảnh là được

<img width="1671" height="893" alt="image" src="https://github.com/user-attachments/assets/27c480e9-d540-44ff-ad73-37ea86ed4d17" />

Quay lại pfSense để mở port TCP cho Server

<img width="1686" height="896" alt="image" src="https://github.com/user-attachments/assets/aa075a8f-9eb2-4bb2-a0df-ba21a10e9fe8" />

Stop Server, sau đó add route cho dải LAN để khi VPN có thể kết nối được các IP trong dải

<img width="1664" height="892" alt="image" src="https://github.com/user-attachments/assets/78fd27dd-def0-46c2-ae03-a95288e6036c" />

Sau khi hoàn thành các bước, tải Pritunl client về và kết nối
















