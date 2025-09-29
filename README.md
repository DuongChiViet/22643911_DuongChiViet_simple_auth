🔐 Authentication Examples with Node.js & Express
Minh họa hai phương pháp xác thực cơ bản trong Node.js:

- Basic Auth
- Cookie-based Auth

📑 Mục lục
🟦 Simple Basic Auth Example
1️⃣ Chạy server
2️⃣ Thông tin đăng nhập
3️⃣ Các route
4️⃣ Kiểm thử với Postman
🟩 Simple Cookie Auth Example
1️⃣ Chạy server
2️⃣ Thông tin đăng nhập
3️⃣ Các route
4️⃣ Hướng dẫn kiểm thử
5️⃣ Kiểm tra MongoDB

---

🟦 Simple Basic Auth Example
Xác thực Basic Auth với Node.js và Express.

**1️⃣ Chạy server**
Chạy lệnh sau trong thư mục chứa file:

```bash
node basic_auth.js
```

Server sẽ chạy tại: http://localhost:3000

**2️⃣ Thông tin đăng nhập**
Username: admin
Password: 12345

**3️⃣ Các route**

| Route   | Yêu cầu xác thực | Nội dung trả về                        |
| ------- | -------------------- | ----------------------------------------- |
| /       | Không               | Welcome! Visit first public resource.     |
| /public | Không               | Welcome! Visit second public resource.    |
| /secure | Có                  | You have accessed a protected resource 🎉 |

**4️⃣ Kiểm thử các trường hợp với Postman**

- Trường hợp GET `/` → Welcome! Visit first public resource.

  ![1759140881442](image/README/1759140881442.png)
- Trường hợp GET `/public` → Welcome! Visit second public resource.

  ![1759140893493](image/README/1759140893493.png)
- Trường hợp GET `/secure` chưa đăng nhập → Báo lỗi xác thực.

  ![1759140907965](image/README/1759140907965.png)
- Trường hợp GET `/secure` đúng tài khoản → Truy cập thành công.

  ![1759140919505](image/README/1759140919505.png)
- Trường hợp GET `/secure` sai tài khoản → Báo lỗi xác thực.

  ![1759140929640](image/README/1759140929640.png)

---

🟩 Simple Cookie Auth Example
Xác thực Cookie-based Auth với Node.js và Express.

**1️⃣ Chạy server**

```bash
node cookie_auth.js
```

Server sẽ chạy tại: http://localhost:3001

**2️⃣ Thông tin đăng nhập**
Username: admin
Password: 12345

**3️⃣ Các route**

| Route    | Yêu cầu xác thực | Nội dung trả về                                     |
| -------- | -------------------- | ------------------------------------------------------ |
| /login   | Không               | Đăng nhập, nhận cookie nếu đúng tài khoản     |
| /logout  | Không               | Đăng xuất, xóa cookie                              |
| /profile | Có                  | Truy cập tài nguyên bảo vệ nếu đã đăng nhập |

**4️⃣ Hướng dẫn kiểm thử**

- Trường hợp GET `/profile` chưa đăng nhập → No cookie found.

  ![1759140963775](image/README/1759140963775.png)
- Trường hợp POST `/login` → Logged in, trả về cookie.

  ![1759140974773](image/README/1759140974773.png)

  ![1759141012259](image/README/1759141012259.png)
- Trường hợp GET `/profile` sau khi đăng nhập → cookie được gửi kèm, truy cập thành công.

  ![1759140997127](image/README/1759140997127.png)

**5️⃣ Kiểm tra trong MongoDB (Thông tin session)**
Ví dụ minh họa dữ liệu session lưu trong MongoDB:

```json
{
	"_id": "6516c1f8e4b0a2a1f8c12345",
	"username": "admin",
	"cookie_token": "a1b2c3d4e5f6g7h8",
	"createdAt": "2025-09-29T15:00:00.000Z"
}
```
