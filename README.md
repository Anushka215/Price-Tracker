# E-commerce Price Tracker

A full-stack app that tracks product prices on Amazon and Flipkart and emails you when a price drops below your target.

## Features

- Track products by pasting an Amazon or Flipkart URL
- Price history charts for every tracked product
- Wishlist with per-product target prices
- Automatic background price checks (every 6 hours by default)
- Email alerts on price drops
- JWT-based authentication

## Tech Stack

- **Frontend:** React, React Router, Recharts, Axios
- **Backend:** Node.js, Express, MongoDB (Mongoose)
- **Scraping:** Puppeteer
- **Scheduling / Email:** node-cron, Nodemailer

## Getting Started

### Prerequisites

- Node.js 14+
- MongoDB (local or Atlas)
- A Gmail app password (for email alerts)

### Setup

```bash
# Install dependencies
npm install
npm install --prefix client

# Configure environment
cp .env.example .env   # then fill in your values
```

### Run

```bash
npm run dev:full       # backend on :5000, frontend on :3000
```

Or run them separately with `npm run dev` and `npm run client`.

## API Overview

| Method | Endpoint                         | Description             |
| ------ | -------------------------------- | ----------------------- |
| POST   | `/api/auth/register`             | Create an account       |
| POST   | `/api/auth/login`                | Log in                  |
| GET    | `/api/auth/me`                   | Current user            |
| POST   | `/api/products/track`            | Start tracking a URL    |
| GET    | `/api/products`                  | List tracked products   |
| GET    | `/api/products/:id`              | Product details         |
| PUT    | `/api/products/:id/refresh`      | Re-scrape price now     |
| DELETE | `/api/products/:id`              | Stop tracking           |
| GET    | `/api/wishlist`                  | List wishlist           |
| POST   | `/api/wishlist`                  | Add to wishlist         |
| PUT    | `/api/wishlist/:productId`       | Update target price     |
| DELETE | `/api/wishlist/:productId`       | Remove from wishlist    |
| PUT    | `/api/user/settings`             | Update user settings    |
| GET    | `/api/health`                    | Health check            |
