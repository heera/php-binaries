# PHP Binaries Mirror

Pre-built static PHP binaries for [Fluent Studio](https://github.com/heera/fluent-studio), mirrored from upstream sources with SHA256 verification.

## Structure

| Release Tag | Contents |
|-------------|----------|
| `php-7.4` | PHP 7.4.33 binaries (final release, built from source) |
| `php-8.1` | Latest PHP 8.1.x binaries for all platforms |
| `php-8.2` | Latest PHP 8.2.x binaries for all platforms |
| `php-8.3` | Latest PHP 8.3.x binaries for all platforms |
| `php-8.4` | Latest PHP 8.4.x binaries for all platforms |
| `manifest` | `manifest.json` — version index with download URLs and SHA256 checksums |

## Platforms

- macOS ARM64 (`macos-aarch64`)
- macOS x86_64 (`macos-x86_64`)
- Linux ARM64 (`linux-aarch64`)
- Linux x86_64 (`linux-x86_64`)
- Windows x86_64 (`windows-x86_64`)

## Variants

Each Unix platform has two variants:
- `cli` — command-line interpreter
- `fpm` — FastCGI process manager

Windows builds include both CLI and FPM in a single archive.

## Sources

- Unix builds: [static-php-cli](https://dl.static-php.dev/static-php-cli/bulk/)
- Windows builds: [windows.php.net](https://windows.php.net/downloads/releases/)

## Automation

Two workflows handle binary management:

- **Mirror** (`mirror.yml`): Runs weekly (Monday 06:00 UTC). Discovers the latest patch for each 8.x minor series, downloads all platform/variant combinations, generates SHA256 checksums, and publishes GitHub Releases.
- **Build Legacy** (`build-legacy.yml`): Manual trigger. Compiles PHP 7.4.33 from source on native runners (macOS ARM/x86, Linux ARM/x86). Only needs to run once since 7.4.33 is the final release.
