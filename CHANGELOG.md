# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [2.0.0]

### Added

- Procedure for auto-selecting craclib dictionary
- Procedure for checking dependencies
- Common branch is also loaded from _init.defaultBranch_

### Changed

- Changed modifier `--master` to `-c` for the enter command.
- Git setting _realm.common-branch_ reworded to _realm.commonBranch_

### Fixed

- New realm names no longer contains special characters like `'`, `.`, `&` or `+`
- Muted unwanted git error message when not in repo

## [1.3.0] - 2022-07-18

### Added

- Configuration through Git config

### Fixed

- Missing support of uppercase letters in realm names

## [1.2.0] - 2022-06-08

### Added

- In-script configurable separator and common branch

### Changed

- Reworked script logic
- Update of Bash if blocks and varbiable writing style

## [1.1.0] - 2021-02-07

### Added

- "reword" sub-command
- Ability to enter existing realm
- Support for realm custom names

### Changed

- Use sed for realm listing
- Rewrite --help contents
- Get realm name using a function

## [1.0.1] - 2020-10-19

### Changed

- Use older Git commands for better compatibility

## [1.0.0] - 2020-09-17

### Added

- Realm entering logic
- Realm leaving logic
- Realm disposal
- Realm listing
- Ability to enter new realm from common branch

[Unreleased]: https://github.com/dehahost/git-realm/compare/v2.0.0...HEAD
[2.0.0]: https://github.com/dehahost/git-realm/compare/v1.3.0...v2.0.0
[1.3.0]: https://github.com/dehahost/git-realm/compare/v1.2.0...v1.3.0
[1.2.0]: https://github.com/dehahost/git-realm/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/dehahost/git-realm/compare/v1.0.1...v1.1.0
[1.0.1]: https://github.com/dehahost/git-realm/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/dehahost/git-realm/releases/tag/v1.0.0
