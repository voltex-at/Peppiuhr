# Peppiuhr OTA — implementation plan

Status: planned, not yet implemented or published. This document is not an update manifest.

## User experience

The clock and local web panel will offer Check for updates, display the available version and release notes, and install only after explicit user confirmation. All messages will support German, Polish and English. Checking or connecting to Wi-Fi must never start an installation automatically.

## Delivery

Public releases in voltex-at/Peppiuhr will distribute the ESP32-S3 ES3C28P application image (`firmware.bin`). The merged USB image must never be used as an OTA payload. Release metadata must identify the hardware target, version, application size and SHA-256. HTTPS certificate verification is required. A SHA-256 checksum detects corruption but is not a publisher signature.

The implementation must validate target and partition size, reject incomplete or invalid downloads, preserve settings, and report errors without marking an unsuccessful update as installed. Automatic rollback requires bootloader support and must not be advertised before it has been configured and tested.

## First installation

The initial OTA-enabled firmware must be installed using USB. A running older firmware without an OTA client cannot acquire the new feature by itself.

## Storage and packaging

Existing v1.18 partition design: two 7 MiB OTA application slots on 16 MiB flash. Confirm the physical device matches this layout before testing.

Keep source code and USB/OTA binaries separate from unchanged SD artwork. SD artwork updates are a separate future feature and must not be implied by a firmware-only update.

## Release gate

Recover the complete v1.18 source, implement the client and UI, compile, test version/target validation and download failures, and clearly state hardware test coverage in release notes. Do not publish a placeholder binary or a manifest referencing an unavailable image.
