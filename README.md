# Vibe-Za-Usiku 🇰🇪

<p align="center">
  <img src="./static/images/read.png" alt="OnlyFun Kenya Banner">
</p>

<p align="center">
  <strong>Premium creator monetization platform built for the Kenyan market.</strong>
</p>

<p align="center">
  Kenyan creators can monetize exclusive content through subscriptions, pay-per-view posts, private messaging, and seamless M-Pesa payments.
</p>

---

<div align="center">

![Django](https://img.shields.io/badge/Django-6.0-092E20?logo=django)
![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-17-4169E1?logo=postgresql)
![M-Pesa](https://img.shields.io/badge/M--Pesa-Daraja-00B300)
![Google OAuth](https://img.shields.io/badge/Google-OAuth-4285F4?logo=google)
![License](https://img.shields.io/badge/license-Proprietary-red)
![Status](https://img.shields.io/badge/status-Active-success)

</div>

---

# 🌍 Overview

OnlyFun Kenya is a modern creator subscription platform focused on the East African market.

Creators can:
- Upload premium content
- Sell subscriptions
- Offer pay-per-view posts
- Receive M-Pesa payouts
- Build communities with fans

Fans can:
- Subscribe to creators
- Purchase locked content
- Chat privately with creators
- Pay instantly using M-Pesa STK Push

The platform automatically handles:
- Revenue splitting
- Payment verification
- Secure media delivery
- Withdrawal processing
- Notifications
- Access control

---

# 🇰🇪 Why OnlyFun Kenya?

Most global creator platforms do not support African payment systems properly.

OnlyFun Kenya solves this problem with:
- Native M-Pesa integration
- Kenyan currency support (KES)
- Local creator payouts
- Mobile-first experience
- East African audience targeting

Built in Kenya, for Kenyan creators.

---

# 📸 Screenshots

## Homepage

![Homepage](./static/images/home.png)

---

## Creator Profile

![Creator Profile](./static/images/profile.png)

---

## Dashboard

![Dashboard](./static/images/dashboard.png)

---

# 🚀 Features

# 👩‍🎨 Creator Features

- Premium content uploads
- Photo, video, and text posts
- Monthly subscriptions
- Pay-per-view content
- Analytics dashboard
- Subscriber tracking
- Earnings overview
- Fan messaging
- M-Pesa withdrawals
- Creator verification system
- Content scheduling
- Draft posts
- Notification center

---

# 🧑‍💻 Fan Features

- Browse trending creators
- Search by category
- Follow creators
- Subscribe monthly
- Purchase locked posts
- Real-time notifications
- Private messaging
- Mobile-friendly experience
- Google Sign-In
- Instant M-Pesa payments

---

# 🛡️ Platform Features

- Automatic 20% commission system
- Atomic transaction handling
- Idempotent payment callbacks
- Fraud prevention logic
- Secure content access
- Rate limiting
- Audit-friendly payment records
- Admin moderation tools
- Creator approval workflow

---

# 🏗️ System Architecture

```text
┌─────────────────────────────────────────────────────────┐
│                     FAN (Browser)                      │
│  Browse → Subscribe → STK Push → Unlock Content       │
└───────────────────────┬────────────────────────────────┘
                        │
┌───────────────────────▼────────────────────────────────┐
│                   DJANGO BACKEND                       │
│                                                        │
│  ┌──────────┐ ┌──────────┐ ┌──────────────────────┐   │
│  │  Views   │ │  Models  │ │   Payment Gateway    │   │
│  │  Auth    │ │  Access  │ │   STK Push / B2C     │   │
│  │  Content │ │  Logic   │ │   Callback Handler   │   │
│  └──────────┘ └──────────┘ └──────────────────────┘   │
│                                                        │
└───────────────────────┬────────────────────────────────┘
                        │
┌───────────────────────▼────────────────────────────────┐
│                 SAFARICOM DARAJA API                  │
│                                                        │
│   STK Push → PIN → Callback → Verification → Done     │
│                                                        │
└────────────────────────────────────────────────────────┘
```

---

# 💰 Payment Flow

```text
Fan clicks "Subscribe" (KES 500)
        ↓
M-Pesa STK Push sent to fan phone
        ↓
Fan enters M-Pesa PIN
        ↓
Safaricom verifies payment
        ↓
Callback sent to Django backend
        ↓
Payment verified & recorded
        ↓
Automatic revenue split:
   • Platform → 20%
   • Creator → 80%
        ↓
Subscription activated
        ↓
Premium content unlocked
```

---

# 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Django 6.0 |
| Language | Python 3.12 |
| Database | PostgreSQL 17 |
| Authentication | Django AllAuth + Google OAuth |
| Payments | Safaricom Daraja API |
| Frontend | Django Templates + Vanilla JS |
| Styling | Custom CSS Design System |
| Icons | Font Awesome 6 |
| Email | Gmail SMTP |
| Tunneling | ngrok |
| Deployment | Gunicorn + Nginx |

---

# 📁 Project Structure

```text
onlyfun_list/
│
├── onlyfun/
│   ├── models.py
│   ├── views.py
│   ├── views_payments.py
│   ├── mpesa.py
│   ├── urls.py
│   ├── admin.py
│   ├── forms.py
│   ├── signals.py
│   ├── middleware.py
│   └── templates/onlyfun/
│
├── users/
│   ├── forms.py
│   ├── models.py
│   └── templates/users/
│
├── templates/
│   ├── base.html
│   ├── account/
│   ├── admin/
│   └── socialaccount/
│
├── static/
│   ├── css/
│   ├── js/
│   └── images/
│
├── media/
│
├── docs/
│   ├── banner.png
│   ├── homepage.png
│   ├── profile.png
│   └── dashboard.png
│
├── .env
├── manage.py
└── requirements.txt
```

---

# 🔐 Security

OnlyFun Kenya includes multiple production-grade security protections.

## Payment Security

- Idempotent M-Pesa callbacks
- Atomic database transactions
- Double-payment prevention
- Transaction verification
- Row-level locking using `select_for_update()`

## Platform Security

- CSRF protection
- Environment variable secret management
- Secure session handling
- Authentication middleware
- Login protection
- Rate limiting
- Permission-based content access

## Media Security

- Protected media endpoints
- Locked premium thumbnails
- Subscription access checks
- Pay-per-view validation
- Private file serving

---

# 📊 Database Models

| Model | Purpose |
|---|---|
| CreatorProfile | Creator profile and payout settings |
| FanProfile | Fan preferences and activity |
| Content | Creator posts and media |
| Subscription | Fan subscriptions |
| Payment | Transaction records |
| Withdrawal | Creator payout requests |
| ContentAccess | PPV purchase tracking |
| Message | Fan-creator chat |
| Notification | Real-time alerts |
| Category | Content organization |
| Like | Engagement tracking |
| Comment | User comments |
| Report | Moderation reports |

---

# 🔌 API Endpoints

| Endpoint | Purpose |
|---|---|
| `/api/mpesa/stk/` | Initiate STK Push |
| `/api/mpesa/callback/` | Daraja callback endpoint |
| `/api/content/<id>/unlock/` | Unlock paid content |
| `/api/subscription/create/` | Create subscriptions |
| `/api/withdrawals/request/` | Request creator payout |

---

# 🚦 Getting Started

# Prerequisites

- Python 3.12+
- PostgreSQL
- Safaricom Daraja credentials
- Google OAuth credentials

---

# Installation

```bash
# Clone repository
git clone https://github.com/yourusername/onlyfun-kenya.git

# Enter project
cd onlyfun-kenya

# Create virtual environment
python -m venv venv

# Activate virtual environment
source venv/bin/activate

# Windows
# venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env

# Run migrations
python manage.py migrate

# Create admin user
python manage.py createsuperuser

# Load categories
python manage.py add_categories

# Start server
python manage.py runserver
```

---

# ⚙️ Environment Variables

```env
# Django
SECRET_KEY=your-secret-key
DEBUG=True

# Database
DB_NAME=onlyfun
DB_USER=postgres
DB_PASSWORD=password
DB_HOST=localhost
DB_PORT=5432

# Google OAuth
GOOGLE_CLIENT_ID=your-client-id
GOOGLE_CLIENT_SECRET=your-client-secret

# Daraja API
DARAJA_CONSUMER_KEY=your-key
DARAJA_CONSUMER_SECRET=your-secret
DARAJA_PASSKEY=your-passkey
BUSINESS_SHORTCODE=174379

# URLs
CALLBACK_URL=https://your-domain.com/api/mpesa/callback/
SITE_URL=https://your-domain.com

# Email
GMAIL_USER=your-email@gmail.com
GMAIL_APP_PASSWORD=your-password
```

---

# 🧪 M-Pesa Sandbox Testing

```bash
# Start local server
python manage.py runserver

# Expose localhost
ngrok http 8000
```

Update `.env`:

```env
CALLBACK_URL=https://your-ngrok-url.ngrok.io/api/mpesa/callback/
SITE_URL=https://your-ngrok-url.ngrok.io
```

---

# 🔧 Management Commands

```bash
# Add content categories
python manage.py add_categories

# Release creator funds
python manage.py release_funds

# Auto-process payouts
python manage.py auto_payout

# Generate fake data
python manage.py seed_data
```

---

# 🚀 Deployment

| Service | Technology |
|---|---|
| OS | Ubuntu Server |
| Web Server | Nginx |
| WSGI | Gunicorn |
| Database | PostgreSQL |
| SSL | Let's Encrypt |
| Process Manager | systemd |
| Media Storage | Local / S3 Compatible |

---

# 📈 Future Improvements

- Redis caching
- Celery background workers
- WebSocket notifications
- AI content moderation
- Video transcoding pipeline
- Creator live streaming
- Mobile applications
- Recommendation engine
- Subscription bundles
- Multi-currency support

---

# 📝 License

Proprietary Software — All Rights Reserved.

This source code may not be copied, redistributed, modified, or used commercially without permission from the author.

---

# 👨‍💻 Author

## Kenneth Mburu

Full-stack developer focused on scalable web platforms, payment systems, and creator economy infrastructure.

---

# 🙏 Acknowledgments

- Safaricom Daraja API
- Django
- Django AllAuth
- PostgreSQL
- Font Awesome
- Google Fonts

---

<div align="center">

## 🇰🇪 Built in Kenya, for Kenyan creators 🇰🇪

</div>
