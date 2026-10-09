# PdfCraft RU Edition

This is the personal Russian-language customization of PdfCraft. The original `main` branch is kept unchanged; changes are developed on `feature/ru-ui-polish-and-releases` and reviewed into `feature/ru-edition`.

## Changes

- Localized Russian UI and improved bookmark-search accessibility labels.
- Compact responsive home tool cards with more room for longer Cyrillic titles.
- Updated UI typography and spacing; bundled open-font fallbacks are kept.
- Translation verification helper in **Add a stamp → Translation verification statement**. Enter source language, organization, director/signatory name, role and date, then **Copy statement and select text tool**. Click a PDF page, paste the statement, place it and save a copy. Sign using the separate signature tools. This helper does **not** create a digital signature or a notarial certification.
- Existing tools provide custom PDF/image stamps, Fill & Sign and certificate-based digital signing; these are distinct actions.

## Development builds

GitHub Actions produces artifacts from the working branch:
- `PdfCraft RU Windows build` → ZIP with Windows x64 EXE
- `PdfCraft RU macOS (Apple Silicon)` → ZIP with a macOS M1-compatible DMG

The DMG uses ad-hoc signing and is **not** Apple-notarized. On a trusted Mac, attempting to open the app may prompt Gatekeeper; review the source and use System Settings → Privacy & Security → Open Anyway when appropriate.

## Checks

- `cargo fmt --all -- --check`
- `cargo clippy --workspace --all-targets -- -D warnings`
- `cargo test --workspace`
- `cargo build --release -p pdfcraft`

Automated Rust formatting is enabled only on the RU development branch.

## Draft releases

The `ru-release.yml` workflow responds to version tags matching `ru-v*`. It builds Windows ZIP + macOS Apple Silicon DMG, computes SHA-256 hashes and creates a **draft**, not a published release. Review on real machines before publishing. Upstream's normal release process is independent.
