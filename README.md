# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421

Lớp: 58KTPM

**Bài tập 03:**  

# SỬ DỤNG WORDPRESS ĐỂ TẠO WEB SITE
## deadline : 23h59 ngày 12 tháng 5 năm 2026.

1. CẤU HÌNH DOCKER TRÊN UBUNTU:
- Tạo thư mục chứa dự án: mkdir ~/wordpress_project && cd ~/wordpress_project
  <img width="649" height="38" alt="image" src="https://github.com/user-attachments/assets/95505d34-8e80-44f9-b2a6-8c1860a77784" />

- Cấu hình file docker-compose.yml: sudo nano docker-compose.yml
  <img width="1096" height="623" alt="image" src="https://github.com/user-attachments/assets/6d56a22d-b39a-4ffc-a5ca-a8a96573c75f" />

- Chạy lệnh sau để Docker tải image và khởi động các container: docker compose up -d
==> Kết quả:
  <img width="1410" height="658" alt="image" src="https://github.com/user-attachments/assets/6366e765-6cc4-479d-83c9-d9a6f88aa63a" />
<img width="1668" height="931" alt="image" src="https://github.com/user-attachments/assets/ff6b9694-a819-41a7-9cb7-c7fdc0c6f12f" />
- Sử dụng cloudflare tunnel để public web wordpress lên sub-domain wp.nguyentuanem.io.vn:
  + Xóa file chứng chỉ từ dự án trước đó: rm /home/tuanem/.cloudflared/cert.pem
  + cloudflared tunnel login
    <img width="1743" height="752" alt="image" src="https://github.com/user-attachments/assets/ea2c3f9d-6162-4078-98ad-fd949364d893" />
  + cloudflared tunnel create wp-tunnel
  + cloudflared tunnel route dns wp-tunnel wp.nguyentuanem.io.vn
  + cloudflared tunnel run --url http://localhost:8001 wp-tunnel
- Cấu hình WordPress để nhận diện HTTPS
  + sudo nano ~/wordpress_project/wp_data/wp-config.php
    <img width="1105" height="619" alt="image" src="https://github.com/user-attachments/assets/252a26de-76ea-4770-ad25-598bf05c995f" />

==> Kết quả: 
<img width="1877" height="953" alt="image" src="https://github.com/user-attachments/assets/28c39014-0c46-4be6-842b-7b0dc45841a8" />

- Tạo bài viết giới thiệu bản thân:
  <img width="1103" height="888" alt="image" src="https://github.com/user-attachments/assets/09185d97-4c9e-4bac-8352-f82bfb90bb29" />
- Tạo 1 bài viết trong wordpress giới thiệu về ngành học mà em yêu thích trong trường TNUT:
  <img width="1847" height="997" alt="image" src="https://github.com/user-attachments/assets/bff913e2-6440-41a9-8c79-8202a49623c4" />
- Bài học rút ra: Việc sử dụng mã nguồn mở WordPress để tạo website là một giải pháp cân bằng giữa tính linh hoạt và sự tiện dụng. Về công sức, người dùng cần đầu tư thời gian cho các bước thiết lập ban đầu như cấu hình Docker, quản lý cơ sở dữ liệu MariaDB và kết nối tên miền qua các công cụ như Cloudflare Tunnel. WordPress rất dễ dùng đối với người mới nhờ giao diện quản trị trực quan, cho phép soạn thảo nội dung đa phương tiện và tùy chỉnh giao diện (Theme) mà không cần can thiệp sâu vào code. Tuy nhiên, về mặt tài nguyên máy chủ, WordPress đòi hỏi mức tiêu thụ RAM và CPU nhất định để vận hành mượt mà các container như PHP và cơ sở dữ liệu, đặc biệt là khi cài đặt nhiều plugin hoặc xử lý lượng truy cập lớn. Ngoài ra, việc quản lý qua SSH yêu cầu người dùng phải nắm vững các kỹ năng về Linux và Docker để xử lý các vấn đề về phân quyền thư mục hoặc cấu hình hệ thống.
