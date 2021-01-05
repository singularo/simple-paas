
# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 2020-01-05 - 1.0
### Changed
- use different path for each script
- quiet commands down but add error outputs
- renamed backup all command

### Added
- extra commands to sp
- syslog setup and logging
- restic pruning script
- restic prune all script
- restic prune parameters

### Fixed
- fixed invalid calls in sp

### Removed
- docker logins that were not required
