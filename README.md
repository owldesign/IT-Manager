<p align="center">
  <img src="docs/images/app-icon.png" width="128" height="128" alt="IT Manager app icon">
</p>

<h1 align="center">IT Manager</h1>

<p align="center">
  <strong>Your IT operations, locked down.</strong><br>
  A native macOS encrypted vault for small-business IT management.<br>
  Store credentials, equipment, employees, and more — all protected by AES-256-GCM encryption.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/macOS-14%2B-blue?logo=apple&logoColor=white" alt="macOS 14+">
  <img src="https://img.shields.io/badge/Swift-5.9-orange?logo=swift&logoColor=white" alt="Swift 5.9">
  <img src="https://img.shields.io/badge/SwiftUI-blue?logo=swift&logoColor=white" alt="SwiftUI">
  <img src="https://img.shields.io/badge/GRDB-green?logo=swift&logoColor=white" alt="GRDB">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License">
</p>

<p align="center">
  <a href="https://github.com/owldesign/IT-Manager/releases">Download</a> · <a href="https://owldesign.github.io/IT-Manager/">Website</a>
</p>

---

## Features

- **8 entity types** — Companies, Employees, Equipment, Credentials, Subscriptions, Service Providers, Credit Cards, Secure Notes
- **Custom fields** — define your own fields per entity type, with optional field-level encryption for sensitive data
- **AES-256-GCM encryption** — two-key architecture with database-level DEK + field-level FEK
- **Touch ID unlock** — biometric authentication with Keychain integration
- **Guided onboarding** — set up your vault and first company in a seamless two-step flow
- **Global fuzzy search** — hit `Cmd+K` for a Spotlight-style overlay that searches everything
- **System-wide hotkey** — configurable global shortcut (default `⇧⌘Space`) to summon search from any app
- **Menu bar app** — lives in your menu bar for quick access; closing the window keeps the app running
- **TOTP code generation** — built-in authenticator with live countdown timer
- **Password generator** — cryptographic generation with configurable length and character sets
- **CSV/JSON import & export** — painless migrations for all entity types
- **Encrypted backups** — `.itmbackup` format with automatic scheduling and rotation
- **Auto-lock & secure clipboard** — vault locks on idle, clipboard clears after timeout
- **Renewal alerts** — upcoming expirations surfaced on the dashboard
- **Auto-updates** — built-in updates via Sparkle, always on the latest version
- **Keyboard-driven** — shortcuts for every major operation
- **Offline-first** — no accounts, no cloud, no tracking. All data stays on your Mac

## Security Architecture

IT Manager uses a layered encryption design:

1. **Master Password** is processed through PBKDF2 (600,000 iterations) to derive a **Master Key**
2. The Master Key is expanded via **HKDF** into two independent keys:
   - **DEK** (Database Encryption Key) — encrypts the entire SQLite database
   - **FEK** (Field Encryption Key) — additional AES-256-GCM encryption for sensitive fields
3. **HMAC-SHA256 verification** confirms the correct password before unlocking
4. **Keychain integration** with biometric access control for Touch ID unlock
5. **Secure Enclave key wrapping** on Apple Silicon for tamper-resistant key storage
6. **Memory zeroing** ensures sensitive data is cleared from RAM after use

## Installation

1. Download the latest DMG from [Releases](https://github.com/owldesign/IT-Manager/releases)
2. Open the DMG and drag **IT Manager** to your Applications folder
3. Right-click the app and select **Open**, then confirm (the app is not notarized)

Or remove the quarantine attribute:

```bash
xattr -cr "/Applications/IT Manager.app"
```

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `⇧⌘Space` | System-wide Spotlight search (configurable) |
| `⌘K` | In-app global search |
| `⌘N` | New record |
| `⌘0` | Dashboard |
| `⌘1` – `⌘7` | Navigate entity types |
| `⇧⌘E` | Export |
| `⇧⌘I` | Import |
| `⇧⌘L` | Lock vault |

## License

MIT — see [LICENSE](LICENSE) for details.

## Acknowledgments

- [GRDB.swift](https://github.com/groue/GRDB.swift) — SQLite toolkit for Swift
- [Sparkle](https://sparkle-project.org/) — software update framework for macOS
