# Changelog

All notable changes to IT Manager will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-10

### Added
- Encrypted vault creation with master password
- Two-key encryption system (DEK for database, FEK for field-level AES-256-GCM)
- Touch ID / biometric authentication
- 8 entity types: Companies, Employees, Equipment, Credentials, Subscriptions, Service Providers, Credit Cards, Secure Notes
- Full CRUD operations for all entity types
- Global fuzzy search (Command-K) with Spotlight-style overlay
- Dashboard with aggregate statistics
- Per-company dashboard with stats and details
- CSV and JSON import & export
- Encrypted backup & restore (.itmbackup format)
- Automatic backup scheduling with rotation
- TOTP code generation with live countdown
- Cryptographic password generator
- Secure clipboard with auto-clear
- Renewal alert notifications on dashboard
- Auto-lock on window close
- Keyboard shortcuts for all operations
- Dark mode support
- Structured logging via OSLog
- Audit trail (created/modified timestamps) on all records
