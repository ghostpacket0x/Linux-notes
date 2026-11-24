# Changelog

All notable changes to these notes are recorded here, newest first. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and the project uses [semantic versioning](https://semver.org/).

## [Unreleased]

## [1.0.0] - 2026-11-24

### Added
- Writing your own systemd service, with a sample unit file and a lab (section 10, services).
- Learning paths for beginners, help desk, system administration, defensive security, and developers ([LEARNING-PATHS.md](LEARNING-PATHS.md)).
- Reading manuals and docs, with a lab ([section 28](sections/28-reading-manuals-and-docs.md)).
- Disks and mounts, with a lab ([section 27](sections/27-disks-and-mounts.md)).
- Docker basics, with a lab ([section 26](sections/26-docker-basics.md)).
- Git basics, with a lab ([section 25](sections/25-git-basics.md)).
- Environment variables, PATH, and shell customisation, with a lab ([section 23](sections/23-environment-variables-and-path.md)).
- Backups and recovery, with a lab ([section 24](sections/24-backups-and-recovery.md)).
- Finding interesting files, with a lab ([section 22](sections/22-finding-interesting-files.md)).
- Bash scripting basics, with a lab ([section 21](sections/21-bash-scripting.md)).
- Firewall basics, SSH keys, and cron, each with a lab ([sections 18 to 20](sections/18-ssh-keys-and-config.md)).
- Logs and monitoring, and permissions and ownership, each with a lab ([sections 16 and 17](sections/16-permissions-and-ownership.md)).
- Redirection and pipes, with a lab ([section 2](sections/02-text-and-viewing.md)).
- Games and challenges, linked from the Labs index ([Labs](Labs/README.md)).
- Glossary, contributing guide, and MIT license.

### Changed
- Networking commands use `ip` instead of the older `ifconfig`, `ifup`, and `ifdown`. The older tools are explained in a short note.
- The practice folder is named `Labs` and is linked from every section.
- The main README includes a table of contents, a "Start here" section, and an environment note.

### Fixed
- Practice links in sections 18 to 20 were missing and have been added.
- Escaped pipe characters in tables, so they display correctly on GitHub.
- Section 2 redirection examples and the order explanation.
- Lab 25 works whether or not `~/bin` is already in PATH.
- Lab 27 expected results match what Git actually does.
- Labs index now lists every lab and links to its section, with corrected filenames for labs 16 to 26.

## How to update this file

Add each change under **Unreleased** as you make it, using the headings above. When you tag a release, rename **Unreleased** to the version number and today's date, then start a new **Unreleased** section.
