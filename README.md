# IT Manager

**A secure, encrypted vault for small-business IT management**

![macOS 14+](https://img.shields.io/badge/macOS-14%2B-blue)
![Swift 5.9+](https://img.shields.io/badge/Swift-5.9%2B-orange)
![License MIT](https://img.shields.io/badge/License-MIT-green)

<!-- Screenshot: docs/screenshots/app-overview.png -->

## Overview

IT Manager is an offline-first encrypted vault built for IT professionals who manage infrastructure across multiple companies. It provides a single, secure workspace to organize employees, equipment, credentials, subscriptions, service providers, credit cards, and secure notes -- all protected by AES-256-GCM encryption with a two-key architecture.

Every piece of data is encrypted at rest using a master password that never leaves your machine. The database itself is encrypted with a dedicated Database Encryption Key (DEK), while sensitive fields like passwords, API keys, and card numbers receive an additional layer of field-level encryption via a separate Field Encryption Key (FEK). Touch ID unlock, auto-lock on idle, and secure clipboard with auto-clear keep your data protected even when you step away.

IT Manager runs entirely on your Mac with no cloud dependency. Global fuzzy search (Command-K) lets you find any record instantly, CSV/JSON import and export make migrations painless, and encrypted backups with automatic scheduling ensure you never lose data.

## Key Features

- **AES-256-GCM encryption** with two-key system (database-level DEK + field-level FEK)
- **8 entity types**: Companies, Employees, Equipment, Credentials, Subscriptions, Service Providers, Credit Cards, Secure Notes
- **Touch ID / biometric unlock** with Keychain integration
- **Global fuzzy search** (Command-K) with Spotlight-style overlay
- **CSV/JSON import & export** for all entity types
- **Encrypted backup & restore** (.itmbackup format) with automatic scheduling and rotation
- **TOTP code generation** with live countdown timer
- **Cryptographic password generator** with configurable length and character sets
- **Auto-lock & secure clipboard** with automatic clearing after configurable timeout
- **Renewal alert notifications** surfaced on the dashboard
- **Dark mode support** with system appearance detection
- **Keyboard shortcuts** for all major operations

## Security Architecture

IT Manager uses a layered encryption design to protect your data:

1. **Master Password** is processed through PBKDF2 to derive a **Master Key**
2. The Master Key is expanded via **HKDF** into two independent keys:
   - **DEK** (Database Encryption Key) -- encrypts the entire SQLite database
   - **FEK** (Field Encryption Key) -- provides additional AES-256-GCM encryption for sensitive fields (passwords, API keys, card numbers)
3. **Keychain integration** with biometric access control stores the wrapped master key for Touch ID unlock
4. **Secure Enclave key wrapping** on Apple Silicon hardware for tamper-resistant key storage
5. **Memory zeroing** ensures sensitive data is cleared from RAM after use

## Installation

1. Download the latest DMG from [Releases](https://github.com/owldesign/IT-Manager/releases)
2. Open the DMG and drag **IT Manager** to your Applications folder
3. On first launch, since the app is not notarized, right-click the app and select **Open**, then confirm in the dialog

Alternatively, remove the quarantine attribute from the terminal:

```bash
xattr -cr "/Applications/IT Manager.app"
```

## Auto-Updates

IT Manager includes built-in auto-updates via Sparkle. To check for updates manually, go to **IT Manager > Check for Updates** in the menu bar.

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Command-K | Open global search |
| Command-N | New record |
| Command-0 | Dashboard |
| Command-1 | Companies |
| Command-2 | Employees |
| Command-3 | Equipment |
| Command-4 | Credentials |
| Command-5 | Subscriptions |
| Command-6 | Service Providers |
| Command-7 | Credit Cards |
| Shift-Command-E | Export |
| Shift-Command-I | Import |
| Shift-Command-L | Lock vault |

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgments

- [GRDB.swift](https://github.com/groue/GRDB.swift) -- SQLite toolkit for Swift
- [Sparkle](https://sparkle-project.org/) -- software update framework for macOS
