# Changelog

All notable changes to this project will be documented in this file.

The changelog format is based on [Keep a Changelog] and [CommonMark].
This project adheres to [Semantic Versioning].

## [Unreleased]

### Changed

- The "Update to new release" workflow now uses Scoop's built-in `checkver`/`autoupdate` to find the latest version and update the manifest, instead of custom download-and-regex logic. It no longer takes a version input.
- The manifest is now in Scoop's canonical 4-space JSON format.
- The manifest's `checkver` now selects the highest version in the S3 bucket. Previously its regex matched the first (oldest) key in the listing.

### Fixed

- Issue- and PR-tracking workflows now add to the senzing organization project board instead of referencing the undefined `SENZING_PROJECT_GARAGE` variable (which resolved to an empty project).
- The "Update to new release" workflow now creates signed (verified) commits via the GitHub API instead of unsigned local commits.

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
