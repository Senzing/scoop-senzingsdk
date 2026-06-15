# Changelog

All notable changes to this project will be documented in this file.

The changelog format is based on [Keep a Changelog] and [CommonMark].
This project adheres to [Semantic Versioning].

## [Unreleased]

### Fixed

- Issue- and PR-tracking workflows now add to the senzing organization project board instead of referencing the undefined `SENZING_PROJECT_GARAGE` variable (which resolved to an empty project).

## [1.0.0] - 2026-05-29

### Changed

- Installing from the MSI now.
- Corrected the EULA URL.

### Added

- `'true'` is now an accepted response at the interactive EULA prompt (alongside `yes`, `y`, `1`, and `I_ACCEPT_THE_SENZING_EULA`).

### Fixed

- Partial install files are now cleaned up when the EULA is rejected at the prompt.

[CommonMark]: https://commonmark.org/
[Keep a Changelog]: https://keepachangelog.com/
[Semantic Versioning]: https://semver.org/
