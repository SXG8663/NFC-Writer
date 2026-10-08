forked from https://github.com/SouumG/NFC-Writer
-


NFC Writer is a production-grade, highly optimized Progressive Web Application (PWA) designed for scanning, programming, formatting, and analyzing Near Field Communication (NFC) RFID transponders operating under the High-Frequency (HF) 13.56 MHz band.

Built entirely client-side using **React 18**, **Vite**, and **Tailwind CSS v4**, the suite delivers near-instantaneous offline operations, responsive telemetry, and precise NDEF record compilation without transmitting user data to external servers.

---

## Comprehensive Feature Set (11-Point Matrix)

NFC Writer implements and documents the maximum bounds of web-accessible RFID capabilities:

1. **Read NFC Tags (NDEF Parsing):** High-fidelity, real-time reader parses physical NDEF records and extracts plain text, web URLs, phone directory sequences (`tel:`), email structures, SMS drafts, Wi-Fi configurations, and raw JSON payloads.
2. **Write NFC Tags (NDEF Encoding):** Custom programmer compiles inputs into standardized NDEF byte streams, writing them directly to the contactless chip.
3. **Overwrite NFC Tags:** Allows modifying or completely replacing old NDEF structures on physical tags, provided the sector blocks have not been set to permanent read-only status.
4. **Erase NFC Tags:** Simulates and executes standard tag clearing by overwriting active memory sectors with a clean, empty text record to safely wipe old data blocks.
5. **Format NFC Tags:** Establishes a clean, initialized NDEF container registry on raw, unformatted, or corrupted transponders to prepare them for future writes.
6. **Lock NFC Tags (Read-Only):** Explains hardware locking constraints. Permanent, irreversible write-protection is highly hardware-dependent and generally managed via native OS-level toolsets.
7. **Multi-Record Tag Support:** Allows reading, writing, and parsing multiple distinct payloads (e.g., a Wi-Fi setup, a GPS coordinate, and a vCard business card) on a single physical tag.
8. **NFC Trigger Actions:** Automatically triggers native smartphone actions on contact (e.g., instantly dialing a number, launching maps coordinates, or opening a website).
9. **Secure Sandbox Protection:** Fully adheres to W3C privacy guidelines, requiring active browser tab visibility and deliberate user gestures (buttons/modals) to arm the transceiver.
10. **Device Matrix Compatibility:** Evaluates device specifications and provides helpful notifications and fallback instructions for incompatible browser engines.
11. **Strict Hardware Controls (What You Cannot Do):** Explicitly outlines standard OS security restrictions. No web browser can toggle device Wi-Fi/Bluetooth adapters, control hardware features like the camera flash, or bypass manufacturer-locked chip UIDs.

---

## Technical Architecture & Project Structure

The codebase is engineered with high modularity and clean separation of concerns:

- `/src/main.tsx`: Application entry point. Registers the Progressive Web App (PWA) Service Worker, setting up automated background updates.
- `/src/components/ReadView.tsx`: Real-time Web NFC scanner, complete with Hex dumps, record parsing, and telemetry diagnostics.
- `/src/components/WriteView.tsx`: Core NDEF programmer offering 11 distinct input types and preset template loading.
- `/src/components/ToolsView.tsx`: Advanced utility toolkit for developers, including SSID encryption generators, vCard builders, and URL shorteners.
- `/src/components/DocumentationView.tsx`: Centralized developer guide outlining chip architectures, protocol limits, and Web NFC specifications.
- `/src/data.ts`: Shared constants, utility string generators, and the 20 precompiled NFC templates.
- `/public/sw.js`: Custom Service Worker configured with a robust **Network-First offline-fallback pipeline** to ensure live assets are prioritized while maintaining 100% offline functionality.
