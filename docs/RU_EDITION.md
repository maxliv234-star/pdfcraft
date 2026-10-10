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
- `PdfCraft RU Windows build` → Windows x64 EXE build artifact (GitHub downloads it as a ZIP)
- `PdfCraft RU macOS (Apple Silicon)` → ZIP with a macOS M1-compatible DMG

The DMG uses ad-hoc signing and is **not** Apple-notarized. On a trusted Mac, attempting to open the app may prompt Gatekeeper; review the source and use System Settings → Privacy & Security → Open Anyway when appropriate.

## Checks

- `cargo fmt --all -- --check`
- `cargo clippy --workspace --all-targets --locked -- -D warnings`
- `cargo test --workspace --locked`
- `cargo build --release --locked -p pdfcraft`

Formatting is validated in CI; the workflow never pushes formatting changes into PR branches. Windows and macOS artifact builds also run the UI library tests.

## Draft releases

The `ru-release.yml` workflow responds to version tags matching `ru-v*` only when the tag points to the current `feature/ru-edition` branch tip. Tag only after green CI and manual QA. It builds Windows ZIP + macOS Apple Silicon DMG, computes SHA-256 hashes and creates a **draft**, not a published release. Review on real machines before publishing. Upstream's normal release process is independent.
