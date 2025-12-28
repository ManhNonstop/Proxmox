1. Tạo 3 node Proxmox
- Cài Proxmox
- Cấu hình Network như file interfaces, tùy chỉnh theo thực tế IP và vLAN
- Cấu hình Chrony
- Cấu hình file hosts
- Chia disk
  + lvcreate -L 280G -n ceph-osd-0 pve
2. Join Cluster
- Login vào Proxmox ở node1
- Tạo Cluster
- Join Cluster cho node2 và node3
3. Cài đặt CEPH
- Cài ceph
- Join mon và mgr
5. Test thử tính năng HA cho VM
