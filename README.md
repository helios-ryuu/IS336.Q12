# Odoo (Docker) - IS336.Q12
---

## 1. Yêu cầu cài đặt
- Docker & Docker Compose
- Visual Studio Code (chỉ để mở mã nguồn và debug nhanh).

> Extensions VSCode gợi ý (không bắt buộc): Docker, Remote - Containers (nếu cần), GitLens.

---

## 2. Clone repository
```bash
# Thay <repo-url> bằng đường dẫn repo của dự án
git clone https://github.com/helios-ryuu/IS336.Q12.git
cd IS336.Q12
```

---

## 3. Chuẩn bị trước khi chạy
- Tạo thư mục `addons` (nếu repo không có):
```bash
mkdir -p addons
```
- (Tùy chọn) Kiểm tra file `docker-compose.yml` để chắc chắn các giá trị sau khớp với cấu hình của anh:
  - Postgres user/password/database
  - Các volumes
  - Port Odoo (mặc định 8069)

---

## 4. Khởi động (quickstart)
```bash
# Dựng containers
docker compose up -d
```
- Chờ vài chục giây để Postgres khởi động và healthcheck pass.
- Mở trình duyệt tới: `http://localhost:8069`

### Database config (nhập vào trang tạo database của Odoo)
- Database name: `alta_plastic`  *(theo ghi chú của anh — tên database Odoo sẽ tạo ra)*
- Username: `odoo`
- Password: `odoo`
- Master Password: `Odoo@123`
- Email: `admin@altaplastic.com`
- Password: `secret`
- Language: `English`
- Country: `Vietnam`

---

## 5. Các lệnh hữu ích
```bash
# Kiểm logs
docker compose logs -f odoo
docker compose logs -f db

# Stop / Down
docker compose down
# Stop and remove volumes
docker compose down -v

# Truy cập shell container
docker compose exec odoo bash
docker compose exec db psql -U odoo -d postgres
```
