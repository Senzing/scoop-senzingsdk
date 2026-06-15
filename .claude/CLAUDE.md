# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **Scoop bucket** for distributing the Senzing SDK on Windows. It contains a Scoop package manifest (`bucket/senzingsdk.json`) that downloads the Senzing SDK from the `senzing-production-win` S3 bucket.

## Key Files

- **bucket/senzingsdk.json**: Scoop package manifest. Defines the download URL, SHA-256 hash, EULA acceptance flow, environment variable setup (`SENZING_DIR`, `PATH`), and `checkver`/`autoupdate` blocks for Scoop's built-in update tooling.
- **.github/workflows/update-to-new-release.yaml**: Automated workflow that runs hourly to check the S3 bucket for new SDK versions. When a new version is found, it downloads the zip, computes the SHA-256 hash, updates the manifest via in-place string replacement (to preserve formatting), and pushes to main.

## Important Conventions

- The S3 bucket URL (`https://senzing-production-win.s3.amazonaws.com/`) is set once in the workflow's "Set S3 URL" step and referenced via `$env:S3_URL` elsewhere. Do not hardcode it in multiple places.
- The manifest uses 2-space JSON indentation. The workflow updates fields via regex replacement on the raw file to avoid reformatting.
- YAML files must pass Prettier formatting (`prettier --check`).

## CI/CD and Automation

GitHub Actions workflows use reusable workflows from [senzing-factory/build-resources](https://github.com/senzing-factory/build-resources):

- **update-to-new-release.yaml**: Checks S3 for new SDK versions on dispatch, updates manifest, and pushes to main
- **lint-workflows.yaml**: Runs super-linter on pushes to non-main branches and PRs to main
- **spellcheck.yaml**: Runs cspell on PRs to main
- **claude-pr-review.yaml**: Automated Claude PR review on opened/synchronized PRs
- **dependabot-approve-and-merge.yaml**: Auto-approves and merges dependabot PRs
- **add-labels-standardized.yaml**: Adds labels to new issues
- **add-to-project-senzing.yaml**: Adds issues to the senzing organization project board

## CHANGELOG Convention

CHANGELOG.md follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format with [Semantic Versioning](https://semver.org/). Changes are manually curated (not auto-generated) to describe user-facing impacts.

## Claude Slash Commands

- `/senzing` - Runs steps from the centralized senzing command
