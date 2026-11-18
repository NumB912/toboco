# 🚀 Project Name

Đây là hệ thống được xây dựng theo kiến trúc **multi-service**, bao gồm Frontend, Backend và các service chuyên biệt cho Email, File và Notification.

## 🏗️ Architecture

<p align="center">
  <img src="images/architecture.png" width="800">
</p>

### Các service trong hệ thống

| Service | Vai trò |
|---|---|
| 🎨 Frontend | Giao diện người dùng và giao tiếp với Backend |
| ⚙️ Backend | Xử lý business logic, authentication và API |
| 📧 Email Service | Gửi và quản lý email |
| 📁 File Service | Upload, lưu trữ và quản lý file |
| 🔔 Notification Service | Xử lý và gửi notification đến người dùng |

---

## 🎨 Frontend

Frontend chịu trách nhiệm xây dựng giao diện và tương tác với người dùng.

**Nhiệm vụ chính:**

- Hiển thị UI
- Quản lý state
- Gọi API đến Backend
- Hiển thị notification
- Upload/download file
- Authentication

```text
User
  │
  ▼
Frontend
  │
  ▼
Backend API
```

---

## ⚙️ Backend

Backend là service chính chịu trách nhiệm xử lý business logic của hệ thống.

**Nhiệm vụ chính:**

- Authentication / Authorization
- Xử lý business logic
- Quản lý database
- Cung cấp REST API
- Giao tiếp với các service khác

```text
Frontend
    │
    ▼
 Backend
   ├── Database
   ├── Email Service
   ├── File Service
   └── Notification Service
```

---

## 📧 Email Service

Email Service chịu trách nhiệm xử lý việc gửi email.

Ví dụ:

- Email xác thực tài khoản
- Reset password
- Email thông báo
- Email xác nhận hành động
- Email system

Backend không cần trực tiếp xử lý quá trình gửi email mà có thể gửi request/message đến Email Service.

```text
Backend
   │
   │ Send Email Request
   ▼
Email Service
   │
   ▼
SMTP / Email Provider
   │
   ▼
User Email
```

---

## 📁 File Service

File Service chịu trách nhiệm quản lý các file được upload lên hệ thống.

**Nhiệm vụ chính:**

- Upload file
- Download file
- Delete file
- Quản lý metadata
- Kiểm tra file
- Lưu trữ file

```text
Frontend
    │
    ▼
 Backend
    │
    ▼
File Service
    │
    ▼
File Storage
```

---

## 🔔 Notification Service

Notification Service chịu trách nhiệm xử lý notification của hệ thống.

Ví dụ:

- Notification khi có message mới
- Notification khi có request
- Notification khi một action hoàn thành
- Real-time notification

```text
Backend
    │
    ▼
Notification Service
    │
    ├── Database
    │
    └── WebSocket / SSE
             │
             ▼
          Frontend
```

---

## 🔄 Overall Flow

Một flow tổng quát của hệ thống:

```text
                    ┌──────────────┐
                    │   Frontend   │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    Backend   │
                    └──────┬───────┘
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
      ┌────────────┐ ┌────────────┐ ┌──────────────┐
      │    Email   │ │    File    │ │ Notification │
      │   Service  │ │   Service  │ │    Service   │
      └────────────┘ └────────────┘ └──────────────┘
```

## 🎯 Design Goals

Hệ thống được chia thành nhiều service nhằm:

- Tách biệt trách nhiệm giữa các thành phần.
- Dễ phát triển và bảo trì.
- Có thể scale từng service độc lập.
- Giảm coupling giữa các module.
- Cho phép các service được triển khai độc lập.
- Dễ dàng thay thế hoặc mở rộng từng service trong tương lai.
