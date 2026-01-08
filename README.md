SETUP Promox làm vPC mô hình standalone

Bước 1: Chuẩn bị Proxmox

- Cài Proxmox
- Setup network
  + Nếu port dưới Switch là trunk thì cấu hình network theo file: **trunk-interfaces**
  + Nếu port dưới Switch là access vlan thì cấu hình network theo file: **access-interfaces**
- Chuẩn bị ISO theo file **pre.md**

Bước 2: Setup vFW bằng pfSense

Cài theo hướng dẫn ở file: **pfsense-install.md**

Bước 3: Cài VPN

Cài theo hướng dẫn ở file: **pritunl-install.md**

Bước 4: Cài các VM cần thiết theo nhu cầu

Kết nối VPN Pritunl, sau đó cài VM và đặt IP LAN, quản lý traffic qua vFW pfSense
