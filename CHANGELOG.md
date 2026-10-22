# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

<!-- markdownlint-disable MD024 -->

## [Unreleased]

## [0.3.0] - 2026-10-22

### Changed

- The direct-submission shortcut now defaults to `Ctrl+Enter`, and the
  reviewed-submission shortcut now defaults to `Ctrl+Shift+Enter`.
- Follow-ups now use `Alt+Enter` to queue without review and `Alt+Shift+Enter`
  to submit for review.

## [0.2.0] - 2026-10-15

### Added

- Review support for follow-up messages submitted with `Alt+Enter`.
- A configurable `submitFollowUpWithoutReview` shortcut, defaulting to
  `Alt+Shift+Enter`.

### Changed

- Accidental-submission prevention is enabled by default and now controls only
  whether Enter submits or inserts a new line.
- The reviewed-submission shortcut is always active and defaults to
  `Ctrl+Enter`.
- The direct-submission shortcut now defaults to `Ctrl+Shift+Enter`.

### Fixed

- Slash commands and `!` shortcuts submitted through a no-review keybinding now
  use Pi's interactive command path instead of being sent to the language model.

## [0.1.7] - 2026-10-11

### Added

- Optional accidental-submission prevention that makes Enter insert a new line.
- Configurable shortcuts for reviewed and unreviewed prompt submission.
- Example configuration in `examples/prompt-reviewer.json`.

### Changed

- Prompt-review help, status, notifications, and documentation now describe the
  active submission behavior and keybindings.

[Unreleased]: https://github.com/surfdude75/pi-prompt-reviewer/compare/v0.3.0...HEAD
[0.3.0]: https://github.com/surfdude75/pi-prompt-reviewer/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/surfdude75/pi-prompt-reviewer/compare/v0.1.7...v0.2.0
[0.1.7]: https://github.com/surfdude75/pi-prompt-reviewer/compare/v0.1.6...v0.1.7
