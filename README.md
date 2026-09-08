# Cleaning Management System

A booking and operations platform for a cleaning services business — customers book and pay for services online, staff manage jobs and invoices, and admins track revenue, refunds, and feedback from a dashboard.

*Group project (university coursework).* My contribution covered the **payment module**, **invoicing system**, and **notification module** — see [My Contribution](#my-contribution) below.

## Tech Stack

**Backend** — Node.js, Express 5, MongoDB (Mongoose), JWT authentication, Socket.IO (real-time updates), node-cron (scheduled reminders), Nodemailer, PayHere payment gateway integration.

**Frontend** — React 18, TypeScript, Vite, Radix UI, Tailwind CSS, React Router, Socket.IO client, jsPDF (PDF export).

**Testing** — Jest on both backend (with `mongodb-memory-server` for isolated DB tests) and frontend (with Testing Library).

## Features

- **Bookings** — service booking flow, rescheduling, job completion, staff job dashboard.
- **Payments** — advance + balance reservations, cash-on-delivery, pay-after-completion, PayHere checkout integration with success/failure/cancel pages, auto-generated payment links.
- **Invoicing** — auto-filled customer/booking details, timestamped invoice generation, QR-coded booking verification, PDF export for staff and customers.
- **Refunds** — refund workflow branching between instant online refunds (PayHere) and manual COD processing, with an admin refund manager.
- **Notifications** — order confirmations, live status alerts, and automated reminders (balance-payment and pre-cleaning) via a scheduled cron job, plus a notification template manager.
- **Feedback** — post-completion feedback and complaint workflow.
- **Admin dashboard** — financial dashboard, revenue charts, booking management, refund management, feedback review.
- **AI invoice assistant** — an Anthropic-powered assistant integrated into the invoicing flow.
- **Analytics** — booking and payment analytics endpoints.

## My Contribution

As a group project, I designed and built:

- **Payment module** — advance-plus-balance reservations, cash-on-delivery, and pay-after-completion flows, with auto-generated payment links.
- **Refund flow** — branching between instant online refunds (via PayHere) and manual cash-on-delivery processing.
- **Invoicing system** — auto-filled customer/booking details, timestamped generation, QR-coded booking verification, and PDF export for staff.
- **Notification module** — order-confirmation and live-status alerts, plus automated balance-payment and pre-cleaning reminders.

## Setup

### Prerequisites

- Node.js
- A MongoDB connection string (e.g. a free MongoDB Atlas cluster)
- (Optional) A PayHere sandbox merchant account for payment testing
- (Optional) An Anthropic API key for the AI invoice assistant

### Backend

```bash
cd backend
npm install
cp .env.example .env   # fill in MONGODB_URI, JWT_SECRET, and any optional keys
npm start               # runs on http://localhost:4000 by default
```

### Frontend

```bash
cd frontend
npm install
cp .env.example .env   # set VITE_API_URL to the backend URL above
npm run dev              # Vite dev server
```

### Environment variables

See `backend/.env.example` and `frontend/.env.example` for the full list. At minimum the backend needs `MONGODB_URI` and `JWT_SECRET` to start; PayHere, email, and AI assistant credentials are only required to exercise those specific features.

## Testing

```bash
cd backend && npm test    # Jest, using mongodb-memory-server (no real DB needed)
cd frontend && npm test   # Jest + Testing Library
```
