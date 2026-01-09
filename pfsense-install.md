Bước 1: Tạo VM với ISO của pfSense


  <img width="1686" height="888" alt="image" src="https://github.com/user-attachments/assets/0d38f59a-003a-4bd1-acf3-7a283ad495e9" />

  Mục General đặt tên cho máy ảo pfSense, sau đó Next

  <img width="1685" height="895" alt="image" src="https://github.com/user-attachments/assets/93e5cba0-19e4-48ae-9dd0-9f23cf970e1a" />

  Mục OS chọn ISO cài pfSense, sau đó Next

  <img width="1683" height="889" alt="image" src="https://github.com/user-attachments/assets/8f1afd0a-7d38-4af7-b598-59e957df1e65" />

  Next tiếp sang mục Disks

  <img width="1687" height="893" alt="image" src="https://github.com/user-attachments/assets/c0be8f9b-b92a-4ebd-9650-865309513595" />

  Nên đặt khoảng 40-100G cho máy ảo pfsense, còn lại giữ nguyên và Next

  <img width="1684" height="893" alt="image" src="https://github.com/user-attachments/assets/f8bb9400-a821-4e9e-a50d-2c8660550302" />

  Mục CPU ưu tiên nhiều Core, sau dó Next

  <img width="1690" height="898" alt="image" src="https://github.com/user-attachments/assets/870e7c27-7bbe-496e-9144-424fd5342df1" />

  RAM nếu có điều kiện thì nâng cao lên khoảng 8-16G, sau đó Next

  <img width="1684" height="896" alt="image" src="https://github.com/user-attachments/assets/76f1e85e-f4e5-4599-ac9c-0147b2bf053f" />

  Bridge chọn vmbr0, VLAN tag chính là ID VLAN, tùy theo thực tế đặt, sau đó Next

  <img width="1685" height="897" alt="image" src="https://github.com/user-attachments/assets/447c80f2-c326-42ba-9a5c-a1e353365bc7" />

  Ở mục Confirm, xem lại 1 lượt nếu ổn thì chọn Start after created và bấm Finish

  <img width="1668" height="690" alt="image" src="https://github.com/user-attachments/assets/14b4aba8-6399-48b5-a94b-f496b0a0ef57" />

  Tạo thêm 1 port làm LAN cho pfsense, ở mục VLAN Tag để tùy ý theo nhu cầu

Bước 2: Cài đặt và cấu hình pfSense

  <img width="1225" height="567" alt="image" src="https://github.com/user-attachments/assets/83d40697-6b89-4057-abd8-a4398124e6ee" />

  Chọn Accept để bắt đầu cài

  <img width="1227" height="565" alt="image" src="https://github.com/user-attachments/assets/c4257f82-9e3b-43fd-a23a-d2b084de0506" />

  Mục Install chọn OK

  <img width="1229" height="567" alt="image" src="https://github.com/user-attachments/assets/c31d8cc2-dd81-499d-90af-a5a975a9e672" />

  Chọn OK để hệ thống tự chia Disk

  <img width="1224" height="566" alt="image" src="https://github.com/user-attachments/assets/a3bc7b15-adfa-485a-be37-aea18c115812" />

  Chọn Select để bắt đầu quá trình phân vùng ổ cứng

  <img width="1227" height="568" alt="image" src="https://github.com/user-attachments/assets/23562256-b259-4d65-8746-501c43539c48" />

  Chọn OK theo mặc định

  <img width="1228" height="566" alt="image" src="https://github.com/user-attachments/assets/ef678e19-9592-4a02-9933-e3f816b0e540" />

  Bấm nút Space để chọn ổ cứng cần cài đặt, sau đó chọn OK

  <img width="1231" height="567" alt="image" src="https://github.com/user-attachments/assets/143b3506-c440-4479-8e5c-82ab3cf70a11" />

  Xác nhận lại lần nữa và chọn YES

  <img width="1228" height="567" alt="image" src="https://github.com/user-attachments/assets/3150c77a-8a10-49ba-b386-fefed22b43b7" />

  Bắt đầu quá trình cài đặt pfSense

  <img width="1227" height="564" alt="image" src="https://github.com/user-attachments/assets/36eba909-3970-4d5c-935a-52572ce0536a" />

  Sau khi cài đặt xong, chọn Reboot để hệ thống khởi động lại

  <img width="1225" height="565" alt="image" src="https://github.com/user-attachments/assets/02f81e1f-8174-4084-9a40-2513f6c14ca3" />

  Chọn Interface làm WAN cho pfSense, ở đây theo thứ tự add card WAN trước và add LAN sau nên chọn vtnet0 làm WAN

  <img width="1227" height="565" alt="image" src="https://github.com/user-attachments/assets/c79f505a-b0e3-43e5-b746-55d0e8eca9e5" />

  Tiếp theo chọn Interface làm LAN cho pfSense, chọn vtnet1

  <img width="1226" height="567" alt="image" src="https://github.com/user-attachments/assets/615c870d-d2aa-42c4-9b93-26050ac00856" />

  Xác nhận, nếu đúng thì chọn y

  <img width="1228" height="566" alt="image" src="https://github.com/user-attachments/assets/a1b665e5-9c05-4978-9e19-6bd691fb8e34" />

  Sau khi setup xong Interface, hệ thống về màn hình mặc định, tuy nhiên IP chưa set cho WAN và LAN nên cần set thủ công, chọn 2

  <img width="1228" height="572" alt="image" src="https://github.com/user-attachments/assets/98db62f5-1a59-4e22-89ef-12b9ce82a567" />

  <img width="1227" height="567" alt="image" src="https://github.com/user-attachments/assets/ef4e4d05-f526-43b9-a778-8599baed230e" />

  <img width="1226" height="566" alt="image" src="https://github.com/user-attachments/assets/df6b07fe-39d1-44bd-aebf-baba0b8107f2" />

  <img width="1225" height="565" alt="image" src="https://github.com/user-attachments/assets/a5b50dbc-a7eb-4958-a139-4dd13d24d1d2" />

  <img width="1228" height="568" alt="image" src="https://github.com/user-attachments/assets/65209e79-7bda-4f3a-94d1-c9687578acc9" />

  <img width="1230" height="571" alt="image" src="https://github.com/user-attachments/assets/ffd354eb-c778-4c84-92c7-56a307988a65" />

  <img width="1226" height="565" alt="image" src="https://github.com/user-attachments/assets/a4173c0d-60f2-443e-a6ff-0d7acbbbfbaf" />

  <img width="1229" height="571" alt="image" src="https://github.com/user-attachments/assets/4521d88e-a590-4e1c-9591-1b274b116157" />

  <img width="1681" height="891" alt="image" src="https://github.com/user-attachments/assets/623d776a-17c4-466f-ade1-097b4c8d1c8d" />

  <img width="1684" height="895" alt="image" src="https://github.com/user-attachments/assets/eff71c95-42dc-446c-b8bb-790998b6eef0" />

  <img width="1684" height="888" alt="image" src="https://github.com/user-attachments/assets/4f1cf01c-994f-421c-be7c-6d882942c961" />

  <img width="1680" height="898" alt="image" src="https://github.com/user-attachments/assets/2252d8b2-f016-41e1-93d1-99cee8bea2ef" />

  <img width="1686" height="896" alt="image" src="https://github.com/user-attachments/assets/e930ccd5-da4d-4841-91d6-578028e1db7d" />

  <img width="1685" height="898" alt="image" src="https://github.com/user-attachments/assets/1e25e733-1179-4c8d-bf7a-6d02b50b981f" />

  <img width="1685" height="893" alt="image" src="https://github.com/user-attachments/assets/edfeac1f-17b6-46b8-a608-037259ded59b" />

  <img width="1685" height="899" alt="image" src="https://github.com/user-attachments/assets/8575f067-4f72-45dc-80a0-01039f95cc3a" />
