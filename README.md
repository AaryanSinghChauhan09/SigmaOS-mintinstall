# SigmaOS Mintinstall

Rust model for a software-center catalog, package metadata, category filtering,
search, and installation-state display, inspired by Linux Mint MintInstall.

## Current behavior and limits

The current `install`, `remove`, and `update` methods change in-memory package
state; they do not invoke a package manager, download an artifact, or modify
the host. `check_updates()` does not query a repository. A state of `Installed`
therefore does not establish that software is present on the system.

Installation actions must be explicit, verifiable, and recoverable; do not hide
package or privilege changes behind presentation-layer defaults. A real
backend needs artifact provenance and signature checks, a transaction preview,
privilege boundaries, and clear rollback behavior.

## Development

The crate depends on `SigmaOS-kernel` through a sibling path dependency. CI
resolves SigmaOS path dependencies and runs `cargo test --all-targets --locked`.
