# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **Scoop bucket** for distributing the Senzing SDK on Windows. It contains a Scoop package manifest (`bucket/senzingsdk.json`) that downloads the Senzing SDK from the `senzing-production-win` S3 bucket.

## Key Files

- **bucket/senzingsdk.json**: Scoop package manifest. Defines the download URL, SHA-256 hash, EULA acceptance flow, environment variable setup (`SENZING_DIR`, `PATH`), and `checkver`/`autoupdate` blocks for Scoop's built-in update tooling.
- **.github/workflows/update-to-new-release.yaml**: Manually dispatched workflow that runs Scoop's own `checkver.ps1 -Update` (from a pinned checkout of ScoopInstaller/Scoop) against the manifest. Scoop's `checkver` block finds the latest version in the S3 bucket and its `autoupdate` block rewrites the version, URL, and hash. If the version changed, the workflow opens a PR with a signed commit.

## Important Conventions

- Update logic lives in the manifest's `checkver`/`autoupdate` blocks, not in the workflow. Don't hand-edit manifest fields from the workflow.
- The `checkver` script sorts S3 keys by `[version]` because the S3 listing is lexical (it would rank 4.4 above 4.10).
- The manifest uses Scoop's canonical formatting (4-space indentation, as written by Scoop's `ConvertToPrettyJson`) so automated updates produce minimal diffs. The workflow converts Scoop's CRLF output to LF.
- YAML files must pass Prettier formatting (`prettier --check`).

## CI/CD and Automation

GitHub Actions workflows use reusable workflows from [senzing-factory/build-resources](https://github.com/senzing-factory/build-resources):

- **update-to-new-release.yaml**: On dispatch, runs Scoop `checkver -Update` and opens a PR if a new SDK version is available
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
