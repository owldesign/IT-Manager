# Changelog

All notable changes to IT Manager will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.4] - 2026-02-12

### Fixed
- "Quit IT Manager" from the menu bar now reliably exits the app
- Sparkle auto-update signatures now validate correctly (fixed EdDSA extraction on macOS)

## [1.0.3] - 2026-02-12

### Added
- System-wide global hotkey (default `⇧⌘Space`) to summon Spotlight search from any app
- Configurable shortcut recorder in Settings to customize the global hotkey
- Menu bar status item with quick access to search, lock vault, and quit
- App stays running in the menu bar when the window is closed (`⌘Q` hides, menu bar "Quit" exits)
- Spotlight search results now open the main window and navigate to the selected record

### Fixed
- Global hotkey now works reliably system-wide using CGEvent tap with automatic fallback
- Shortcut recorder no longer freezes the Settings window
- Menu bar icon no longer duplicates or disappears on window close/reopen cycle
- Search result double-click now correctly opens the app even when the main window is hidden
- Spotlight search panel no longer drifts upward on repeated open/close

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
