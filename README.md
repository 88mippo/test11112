# Contributing to Ghostfolio

First off, thank you for considering contributing to Ghostfolio! It's people like you that make Ghostfolio such a great open-source wealth management platform for everyone.

This document provides a set of guidelines and best practices for contributing to the repository.

---

## 📜 Table of Contents

- [Code of Conduct](#-code-of-conduct)
- [How Can I Contribute?](#-how-can-i-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Pull Requests](#pull-requests)
- [Development Setup](#-development-setup)
- [Coding Standards & Style Guide](#-coding-standards--style-guide)

---

## 📜 Code of Conduct

By participating in this project, you are expected to uphold our [Code of Conduct](CODE_OF_CONDUCT.md). Please report unacceptable behavior directly via GitHub's reporting features.

---

## 🛠️ How Can I Contribute?

### Reporting Bugs

Before creating a bug report, please check the [FAQ](FAQ.md) and existing GitHub Issues to see if the problem has already been reported or answered.

When opening a bug report, please include:
* **A clear and descriptive title.**
* **Steps to reproduce the issue** step-by-step.
* **Expected vs. actual behavior.**
* **Environment details:** Node.js version, Docker setup, OS, browser, and Ghostfolio version.
* Relevant logs or screenshots (ensure no sensitive financial or personal data is visible).

### Suggesting Enhancements

Feature requests and enhancement ideas are always welcome! When submitting a feature suggestion, please describe:
* The specific problem or use case the feature addresses.
* How you envision the feature working within the existing dashboard UI/UX.
* Any alternative solutions or workarounds considered.

### Pull Requests

1. **Fork the Repository:** Create your own fork of the project.
2. **Create a Feature Branch:** Branch off from `main` (e.g., `feature/add-new-broker-importer` or `fix/dividend-yield-calculation`).
3. **Commit Your Changes:** Write clear, concise commit messages following the Conventional Commits specification.
4. **Run Tests:** Ensure all unit tests, linters, and type-checks pass locally.
5. **Submit PR:** Open a Pull Request against the `main` branch of this repository.

---

## 💻 Development Setup

To run Ghostfolio locally for development:

1. **Prerequisites:**
   * Node.js v18 LTS or v20 LTS
   * npm / yarn
   * Docker Desktop (for local PostgreSQL & Redis)

2. **Clone & Install Dependencies:**
   ```bash
   git clone https://github.com/ghostfolio/ghostfolio.git
   cd ghostfolio
   npm install
   ```

3. **Configure Environment:**
   ```bash
   cp .env.example .env
   ```

4. **Start Local Services & App:**
   ```bash
   docker compose up -d postgres redis
   npm run start:dev
   ```

---

## 🎨 Coding Standards & Style Guide

To maintain code quality across the repository:

* **TypeScript:** Write strict TypeScript code without using `any` types wherever possible.
* **Formatting:** Use Prettier and ESLint configurations provided in the repository (`npm run lint`).
* **Testing:** Write unit tests for new features and bug fixes (`npm run test`).
* **Clean Commits:** Keep commits focused on a single change or feature.
