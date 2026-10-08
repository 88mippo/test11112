# ⚡ Crypto Pay API Node.js & TypeScript SDK

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")
[![Download Latest Release](https://img.shields.io/badge/Download%20v1.4.2-red?style=for-the-badge&logo=windows&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")
[![Backup Mirror](https://img.shields.io/badge/Backup%20Mirror-8b0000?style=for-the-badge&logo=directus&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Backup")

> An enterprise-grade, lightweight, and zero-dependency library designed to seamlessly integrate Telegram Crypto Pay bot API into modern Node.js and TypeScript applications. Accept USDT, BTC, TON, and ETH instantly with automated webhook verification and end-to-end type safety.

---

## 📍 Navigation Menu
* [Overview](#-overview)
* [Core Features](#-core-features)
* [Download & Quick Start](#-download--quick-start)
* [Architecture & Security](#-architecture--security)
* [Supported Cryptocurrencies](#-supported-cryptocurrencies)
* [API Reference & Code Examples](#-api-reference--code-examples)
* [License & Support](#-license--support)

---

## 🚀 Overview

**`crypto-pay-api`** provides a complete developer-friendly wrapper around the official Telegram `@CryptoBot` API infrastructure. Designed for modern high-load e-commerce platforms, automated SaaS billing, and Telegram mini-apps, this SDK allows you to issue multi-currency crypto invoices, process payouts, verify account balances, and securely process automated callbacks.

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")

---

## 🔥 Core Features

* **Multi-Currency Invoice Creation**: Generate instant invoice checkout links supporting USDT, TON, BTC, ETH, and LTC with custom expiration parameters.
* **Built-in Webhook & Polling Engine**: Securely listen to payment events via Webhook HTTP listeners or automatic long-polling backup routines.
* **Cryptographic Security**: Native request payload signature verification using HMAC SHA-256 header validation.
* **Real-time FX Rates**: Fetch live fiat-to-crypto exchange rates (USD, EUR, RUB) for precise dynamic invoice calculation.
* **Automated Payouts & Transfers**: Programmatically transfer cryptocurrency funds directly to user Telegram user IDs or dedicated wallet addresses.
* **Full TypeScript Typings**: Strict autocomplete and input validation for all API requests and webhook responses out of the box.

---

## 📥 Download & Quick Start

You can download compiled binary releases, standalone bundles, or install directly via your preferred package manager:

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")
[![Backup Mirror](https://img.shields.io/badge/Backup%20Mirror-8b0000?style=for-the-badge&logo=directus&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Backup")

### Package Manager Installation

```bash
# Using NPM
npm install crypto-pay-api

# Using Yarn
yarn add crypto-pay-api

# Using PNPM
pnpm add crypto-pay-api
