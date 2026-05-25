# 💱 Crypto Exchange — Backend

> Backend for a cryptocurrency exchange service with a website and Telegram Mini App.  
> The source code is closed — available upon request.

---

## 🧩 About the Project

A full-featured backend for a P2P crypto exchange platform. Users can submit exchange requests through both the main website and a Telegram Mini App. Operators manage orders, rates, and users via an admin panel. Live support is available through a built-in chat.

---

## ⚙️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| Database | PostgreSQL |
| Real-time | WebSockets |
| External API | Bybit API |
| Auth | JWT + Telegram Auth |

---

## 🏗️ Architecture

<img width="813" height="641" alt="image" src="https://github.com/user-attachments/assets/1e054d01-730c-4484-803b-bc8ec599ed0f" />

---

## 🔑 Key Features

### Exchange Core
- Exchange order creation and lifecycle management (pending → confirmed → completed)
- Real-time rates pulled from **Bybit API** with configurable markup
- Manual rate override via admin panel
- Support for multiple trading pairs

### Authentication
- **JWT tokens** for website users
- **Telegram OAuth** for Mini App users
- Role-based access: user / operator / admin

### Live Chat
- **WebSocket**-based real-time chat between user and operator
- Chat attached to a specific exchange order
- Message history stored in PostgreSQL

### Admin Panel
- Full order management (view, confirm, reject, complete)
- Manual rate adjustments per currency pair
- User management: view profiles, transaction history
- User blocking / unblocking
- Statistics and analytics dashboard

---

## 🔒 Source Code

The repository is private. If you're a recruiter or developer and would like to review the code, feel free to reach out — I can grant temporary access.

---

## 📬 Contact

**Telegram:** https://t.me/YuriGoryunov
