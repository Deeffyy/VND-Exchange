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
| Language | Python (FastAPI) |
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

## 📡 API Reference

> 🔒 Endpoints marked with **Auth** require `Authorization` header with a JWT token.

### Authentication

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/auth/` | — | Authenticate via Telegram InitData, returns JWT access + refresh tokens |
| `POST` | `/auth-manager/` | — | Authenticate as operator/manager |
| `POST` | `/kyc-confirm` | ✅ | Submit phone number for KYC verification |

### Exchange

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/submit-application/` | ✅ | Create a new exchange request |
| `POST` | `/confirm/{application_id}/` | — | Confirm payment for an exchange application |
| `POST` | `/method-details/` | ✅ | Save draft with payment method details before submission |
| `POST` | `/change-status/` | ✅ | Update status of an exchange request (admin/operator) |
| `GET` | `/exchange-requests` | ✅ | List all exchange requests (admin) |

### Rates & Methods

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/rates/` | — | Get current exchange rates (optional `key` filter) |
| `GET` | `/methods` | — | Get available payment methods with supported currencies |
| `GET` | `/targets` | — | Get available target (receive) methods with supported currencies |
| `POST` | `/validate_address/` | — | Validate a crypto wallet address for a given network |

### User

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/user/` | ✅ | Get current user profile, saved payment & recipient details, KYC/ToS status |
| `GET` | `/history/` | ✅ | Get paginated exchange history (cursor-based) |
| `POST` | `/history/` | ✅ | Add a history record manually |

### Chat & Messages

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/messages/` | ✅ | Get all messages (paginated, limit/offset) |
| `GET` | `/request-messages/` | ✅ | Get messages for a specific exchange request |
| `GET` | `/user-messages/` | ✅ | Get all messages for a specific user (admin) |

### Files

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/upload/` | ✅ | Upload a file (multipart), returns file UUID |
| `GET` | `/file/` | ✅ | Download a file by UUID |
| `GET` | `/get-file-path/` | ✅ | Get file path/metadata by UUID |
| `POST` | `/files/` | ✅ | List all files uploaded by current user |

### System

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/webhook` | — | Incoming webhook handler (payment provider callbacks) |
| `GET` | `/healthz` | — | Health check |
| `GET` | `/` | — | Root / ping |

---

### Key Data Models

<details>
<summary>Exchange Request</summary>

```json
{
  "amount": { "value": 1000, "currency": "RUB" },
  "returns": { "value": 0, "currency": "USDT" },
  "source": "card_rub",
  "target": "crypto_usdt_trc20",
  "geolocation": "optional"
}
```
</details>

<details>
<summary>Auth Response</summary>

```json
{
  "access_token": "...",
  "refresh_token": "...",
  "token_type": "bearer"
}
```
</details>

<details>
<summary>Message (Chat)</summary>

```json
{
  "id": "uuid",
  "from": "user_id",
  "to": "operator_id",
  "text": "Hello",
  "fileId": null,
  "timestamp": 1716000000
}
```
</details>

---


## 🔒 Source Code

The repository is private. If you're a recruiter or developer and would like to review the code, feel free to reach out — I can grant temporary access.

---

## 📬 Contact

**Telegram:** https://t.me/YuriGoryunov
