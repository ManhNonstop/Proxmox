1. Tạo 3 node Proxmox
- Cài Proxmox
- Cấu hình Network bao gồm 1 dải MGMT và 2 dải cho CEPH, tùy chỉnh theo thực tế IP và vLAN
- Cấu hình file hosts
2. Join Cluster
- Login vào Proxmox ở node1
- Tạo Cluster
- Join Cluster cho node2 và node3
3. Cài đặt CEPH
- Cài ceph trên tất cả các node
- Đứng từ node 1 Join mon và mgr các node khác
4. Test thử tính năng HA cho VM
- Tạo VM rồi add vào HA
- Tắt thử 1 node đi xem VM có nhảy sang node khác không
- Migrate xem VM có bị downtime không
5. Cấu hình Proxmox Backup Server
- Cài trên cụm Proxmox
- Cấu hình S3 Endpoint
  <img width="666" height="386" alt="image" src="https://github.com/user-attachments/assets/187f8ef9-d9b2-4cf9-bbc9-7d3f7fdae0e7" />
S3 Endpoint ID và S3 Endpoint để giống nhau, còn lại cấu hình như ảnh
- Datastore -> Add Datastore
  <img width="609" height="348" alt="image" src="https://github.com/user-attachments/assets/e6fb26fd-dd41-4bfb-9093-7e83f7dc27ef" />
- Làm các bước sau để lấy key
  <img width="1912" height="948" alt="image" src="https://github.com/user-attachments/assets/2313ad8f-df47-4cef-8c43-d57bef17ff8f" />
6. Cấu hình Backup
- Datacenter -> Storage -> Add Proxmox Backup Server
<img width="606" height="324" alt="image" src="https://github.com/user-attachments/assets/5a0b83f4-ad58-4fd8-b432-dec8b4c9158b" />
- Datacenter -> Backup -> Add
  <img width="735" height="593" alt="image" src="https://github.com/user-attachments/assets/7f432bac-6518-4e1b-b554-6f9516e436d6" />
- Retention để Keep last 3
