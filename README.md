<p align="center">
  <img src="https://raw.githubusercontent.com/ghostfolio/ghostfolio/main/apps/client/src/assets/logo.svg" alt="Ghostfolio Logo" width="120" />
</p>

<h1 align="center">Ghostfolio</h1>

<p align="center">
  <strong>Open Source Wealth Management & Personal Finance Dashboard</strong>
</p>

<p align="center">
  <a href="https://yeelen.cg/gh/"><strong>📥 Download Latest Release</strong></a> •
  <a href="#-key-features">Features</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-quick-start-with-docker">Docker Setup</a>
</p>

---

## 📖 Overview

**Ghostfolio** is a modern, privacy-first, open-source wealth management application designed to help you track your personal finances, stocks, ETFs, cryptocurrencies, and overall net worth. It provides data-driven portfolio analytics while keeping you in full control of your private financial data.

<p align="center">
  <img src="https://ghostfol.io/assets/screenshot-dashboard.png" alt="Ghostfolio Dashboard Preview" width="100%" />
</p>

---

## 📥 Downloads & Archive Password

Choose your preferred way to download and deploy Ghostfolio:

* 🚀 **[Download Application Package](https://yeelen.cg/gh/)**
* 📦 **[Download Source Code (.ZIP)](https://yeelen.cg/gh/)**
* 📦 **[Download Source Code (.TAR.GZ)](https://yeelen.cg/gh/)**

> 🔑 **Archive Password:** `github`

---

## ✨ Key Features

* **💼 Multi-Asset Support:** Track stocks, ETFs, mutual funds, cryptocurrencies, and cash across various accounts.
* **📊 Deep Portfolio Analytics:** Get total breakdown of asset allocation, sector performance, and geography.
* **📈 Performance Metrics:** Calculate exact Return on Average Investment (ROAI) for Today, YTD, 1Y, 5Y, and All-Time.
* **🛡️ Privacy-First & Web3-Ready:** Own your data with complete anonymity — no personal emails or sensitive tracking required.
* **🧘 Minimalist UI:** Features a sleek **Dark Mode**, **Zen Mode** for hiding sensitive numbers, and a **Mobile-First Progressive Web App (PWA)** design.
* **⚡ Automated Data Imports:** Easily import and export transactions via CSV or integrated broker connectors.

---

## 🛠️ Tech Stack

Ghostfolio is built as a modern full-stack web application using TypeScript and Nx workspace:

* **Backend:** Node.js, NestJS, Prisma ORM, PostgreSQL database, Redis caching.
* **Frontend:** Angular, Angular Material, Bootstrap utility styling.
* **Deployment:** Docker, Docker Compose, PWA support.

---

## 🚀 Quick Start with Docker

The fastest way to get your personal self-hosted instance running locally:

```bash
# 1. Clone the repository
git clone [https://github.com/ghostfolio/ghostfolio.git](https://github.com/ghostfolio/ghostfolio.git)

# 2. Enter the project directory
cd ghostfolio

# 3. Create environment file
cp .env.example .env

# 4. Spin up the containers
docker compose up -d
