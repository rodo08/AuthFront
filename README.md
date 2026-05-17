# MERN Auth — Frontend

**Live demo:** https://stupendous-auth.netlify.app/login

React client for the MERN authentication system. Handles signup, login, email verification, and password reset, communicating with the [backend API](https://github.com/rodo08/AuthBack) via HTTP-only cookie sessions.

## Stack

- **React 19** + **Vite**
- **Zustand** — global auth state
- **React Router DOM v7** — client-side routing
- **Axios** — API requests (cookies included by default)
- **Tailwind CSS v4** — styling
- **Framer Motion** — page/component animations
- **React Hot Toast** — notifications

## Features

- Sign up with email verification (7-digit OTP)
- Login / Logout
- Protected routes (authenticated + verified users only)
- Forgot password / Reset password via email link (powered by Mailgun)
- Password strength meter on signup
- Handles backend cold start gracefully (5s timeout + user feedback)

## Project Structure

```
src/
├── components/
│   ├── FloatingShape.jsx       # Background decoration
│   ├── Input.jsx               # Reusable input with icon
│   ├── LoadingSpinner.jsx      # Full-screen loader
│   └── PasswordStrengthMeter.jsx
├── pages/
│   ├── SignUpPage.jsx
│   ├── LoginPage.jsx
│   ├── EmailVerificationPage.jsx
│   ├── ForgotPasswordPage.jsx
│   ├── ResetPasswordPage.jsx
│   └── DashboardPage.jsx
├── store/
│   └── authStore.js            # Zustand store — all auth actions
└── utils/
    └── date.js                 # Date formatter
```

## Environment Variables

Create a `.env` file in this directory:

```env
VITE_API_URL=http://localhost:3000
```

For production, set `VITE_API_URL` to your deployed backend URL.

## Getting Started

```bash
bun install
bun run dev
```

## Routes

| Path | Access | Description |
|------|--------|-------------|
| `/` | Protected | Dashboard |
| `/signup` | Public | Create account |
| `/login` | Public | Sign in |
| `/verify-email` | Public | OTP verification |
| `/forgot-password` | Public | Request reset link |
| `/reset-password/:token` | Public | Set new password |
