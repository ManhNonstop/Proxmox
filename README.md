SETUP Promox làm vPC mô hình standalone

Bước 1: Chuẩn bị Proxmox

- Cài Proxmox
- Setup network
  + Nếu port dưới Switch là trunk thì cấu hình network theo file: **trunk-interfaces**
  + Nếu port dưới Switch là access vlan thì cấu hình network theo file: **access-interfaces**
- Chuẩn bị ISO theo file **pre.md**

Bước 2: Setup vFW bằng pfSense

Bước 3: Cài VPN

Bước 4: Cài các VM cần thiết theo nhu cầu
