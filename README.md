# KaziPay – Secure Escrow for Kenya’s Gig Economy

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Built with Django](https://img.shields.io/badge/Built%20with-Django-092E20?logo=django)](https://www.djangoproject.com/)
[![React](https://img.shields.io/badge/Frontend-React-61DAFB?logo=react)](https://reactjs.org/)
[![M‑Pesa](https://img.shields.io/badge/Powered%20by-M‑Pesa-00A859?logo=safaricom)](https://developer.safaricom.co.ke/)

**KaziPay** is an escrow platform that connects clients and gig workers in Kenya. Clients pay via M‑Pesa, funds are held securely, and workers receive payment only after the client confirms job completion – eliminating the trust gap in informal work.

## 🌟 Key Features

- 🔐 **Secure Authentication** – Phone‑based OTP or email/password login with JWT.
- 💰 **M‑Pesa Escrow** – Clients pay via STK Push; funds held until job is confirmed.
- ✅ **Milestone‑Based Release** – Payment released instantly to worker via M‑Pesa B2C after client confirmation.
- 📱 **Dual‑Role Dashboards** – Separate views for clients and workers.
- 📨 **Real‑time SMS Notifications** – Africa’s Talking keeps both parties informed at every step.
- ⏱️ **Auto‑Release** – If client doesn’t confirm within 48 hours, the system automatically pays the worker.
- 🧾 **Transaction History** – Full audit trail for all jobs and payments.

## 🛠️ Technology Stack

| Technology         | Purpose                                    |
|--------------------|--------------------------------------------|
| **React**          | Frontend UI framework (Vite, Tailwind CSS) |
| **Django**         | Backend API server (REST Framework, JWT)   |
| **PostgreSQL**     | Relational database                        |
| **M‑Pesa Daraja**  | Payment processing (STK Push, B2C, callbacks) |
| **Africa’s Talking** | SMS notifications                        |
| **Railway / Netlify** | Backend / frontend hosting               |
| **Claude / ChatGPT** | AI assistance for vibe coding             |

## 🏗️ Project Structure
kazipay/

├── backend/ # Django project
│ ├── Kazi_Pay/ # Project settings
│ ├── kazipay_app/ # Main app (models, views, utils)
│ │ ├── migrations/
│ │ ├── management/commands/ # Auto‑release cron
│ │ ├── models.py
│ │ ├── views.py
│ │ └── utils/
│ │ ├── mpesa.py
│ │ └── sms.py
│ ├── requirements.txt
│ └── manage.py
├── frontend/ # React + Vite
│ ├── src/
│ │ ├── components/
│ │ ├── pages/
│ │ ├── services/
│ │ └── App.jsx
│ └── package.json
├── README.md
├── LICENSE
└── .gitignore


## 🔐 Authentication & Roles

- Users register/login with **phone number** (OTP via Africa’s Talking) or **email/password**.
- JWT tokens secure API requests.
- Roles: `client`, `worker`, or `both`.

**Test accounts (for demo):**
- Client: `254708374149` (phone) / `client@example.com` / `test123`
- Worker: `254712345678` (phone) / `worker@example.com` / `test123`

## 💸 How It Works

1. **Client posts a job** – description, amount, worker’s phone.
2. **Client pays** – M‑Pesa STK Push prompt; funds held in escrow.
3. **Worker accepts** – sees the job in dashboard and accepts.
4. **Client confirms** – after work is done, client clicks “Confirm”.
5. **Worker gets paid** – money instantly transferred via M‑Pesa B2C.

SMS notifications at every step.

## ⚙️ Setup & Installation

### Prerequisites
- Python 3.10+, Node.js 16+
- PostgreSQL
- Safaricom Daraja sandbox credentials
- Africa’s Talking sandbox credentials

### Backend (Django)
`
cd backend
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
cp .env.example .env
# Edit .env with your credentials
python manage.py migrate
python manage.py runserver
Frontend (React)
bash
cd frontend
npm install
npm run dev
Environment Variables (.env.example)
Backend:

ini
SECRET_KEY=your-secret-key
DEBUG=True
DATABASE_URL=postgresql://user:password@localhost:5432/kazipay

MPESA_CONSUMER_KEY=your_key
MPESA_CONSUMER_SECRET=your_secret
MPESA_SHORTCODE=174379
MPESA_PASSKEY=your_passkey
MPESA_CALLBACK_URL=https://your-backend-url/api/mpesa/callback

AFRICA_TALKING_USERNAME=sandbox
AFRICA_TALKING_API_KEY=your_api_key
Frontend:

ini
VITE_API_BASE_URL=http://localhost:8000/api
🧠 Smart Features
Auto‑Release Mechanism
A Django management command runs hourly, finds jobs in_progress older than 48 hours, and automatically pays the worker – protecting workers from unresponsive clients.

Transaction Logging
Every deposit and payout is recorded in a Transaction model for full transparency.

🌍 Use Cases
Freelance marketplaces

Domestic services (plumbing, cleaning, repairs)

Creative work (design, writing, media)

Cross‑border work (future)

👥 Team
Name	Role
Joseph Omondi	Backend
Wendy Okoth	Backend
Susan Awori	Frontend
John Chiwai	M‑Pesa Integration
Gavin Chesebe	Documentation & Presentation
🤝 Contributing
We welcome contributions! Please open an issue or pull request.

Fork the repository

Create a feature branch (git checkout -b feature/amazing)

Commit your changes (git commit -m 'Add amazing feature')

Push to the branch (git push origin feature/amazing)

Open a Pull Request

📄 License
MIT License – see LICENSE file.

🔗 Links
Live Demo: (add your live demo link here)

Backend API: (add deployed backend URL)

Frontend: (add deployed frontend URL)

Issues: GitHub Issues

🏆 Acknowledgments
Safaricom for M‑Pesa Daraja API

Africa’s Talking for SMS

Django and React communities

GOMYCODE Kenya for the hackathon

⭐ Star this repo if KaziPay inspires you!
💬 Questions? Open an issue.

Built for the M‑Pesa Africa x GOMYCODE Hackathon 2026 – Money in Motion
