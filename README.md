<p align="center">
  <a href="https://github.com/ghostfolio/ghostfolio">
    <img src="assets/logo.png" alt="Ghostfolio Logo" width="130" />
  </a>
</p>

<h1 align="center">Ghostfolio — Open Source Wealth Management & Portfolio Tracker</h1>

<p align="center">
  <strong>The Ultimate Privacy-First Personal Finance Dashboard for Stocks, ETFs, Crypto, and Net Worth Analytics</strong>
</p>

<p align="center">
  <a href="https://github.com/ghostfolio/ghostfolio/releases"><img src="https://img.shields.io/badge/Download-Latest_Release-blue?style=for-the-badge&logo=github" alt="Download Release"></a>
  <a href="https://github.com/ghostfolio/ghostfolio/actions"><img src="https://img.shields.io/badge/Status-Active_Build-success?style=for-the-badge" alt="Build Status"></a>
  <a href="https://github.com/ghostfolio/ghostfolio/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-AGPL--3.0-orange?style=for-the-badge" alt="License"></a>
</p>

<p align="center">
  <a href="#-about-ghostfolio">About</a> •
  <a href="#-key-features">Key Features</a> •
  <a href="#-system-requirements">Requirements</a> •
  <a href="#-installation--deployment">Installation</a> •
  <a href="#-frequently-asked-questions">FAQ</a>
</p>

---

## 📖 About Ghostfolio

**Ghostfolio** is a modern, privacy-focused, open-source personal finance and wealth management application. It empowers individuals to track their financial portfolio, monitor asset allocation, calculate investment returns, and analyze net worth over time without compromising sensitive personal data.

<p align="center">
  <img src="assets/banner.jpg" alt="Ghostfolio Banner" width="100%" />
</p>

---

## ✨ Key Features & Capabilities

### 📈 Multi-Asset Investment Tracking
* **Global Stocks & ETFs:** Support for global exchanges, market indices, and mutual funds with automated live market data fetching.
* **Cryptocurrency Integration:** Track Bitcoin, Ethereum, and thousands of altcoins via integrated crypto market feeds.
* **Cash & Commodities:** Keep track of fiat currency balances, physical gold, silver, and alternative assets in one place.

### 📊 Advanced Portfolio Analytics & Insights
* **Performance Metrics:** Calculate precise Return on Investment (ROI), Return on Average Investment (ROAI), and Dividend Yield across multiple timeframes.
* **Asset Allocation Breakdown:** Dynamic visualization of portfolio diversification by asset class, market sector, currency, and geographic location.
* **Dividend Calendar:** Monitor incoming payouts and analyze dividend growth trends over time.

---

## 🖥️ System Requirements

* **Operating System:** Windows 10/11, macOS 11+, Linux, or Docker Host
* **Node.js:** v18.x or v20.x LTS
* **Database:** PostgreSQL 14+ and Redis 6+

---

## 🚀 Quick Start with Docker

```bash
# 1. Clone the repository
git clone [https://github.com/ghostfolio/ghostfolio.git](https://github.com/ghostfolio/ghostfolio.git)

# 2. Navigate to project root
cd ghostfolio

# 3. Create environment configuration
cp .env.example .env

# 4. Launch containers
docker compose up -d
