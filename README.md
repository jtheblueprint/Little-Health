# Little Health

**A privacy-first child medical records tracker that runs entirely in your browser.**

No servers. No accounts. No telemetry. Your data never leaves your device.

---

## What It Does

Little Health tracks 17 categories of child health and medical records across 4 tabs:

| Tab | Categories |
|-----|-----------|
| **Health** | Immunizations, Illnesses, Medications, Symptoms & Treatments, Allergies, Lab Results |
| **Growth** | Growth Measurements, Milestones, Feeding & Food, Sleep Logs |
| **Records** | Appointments, Doctor Visits, Specialist Referrals, Recommendations, Insurance, Medical Bills, Emergency Info |
| **Settings** | Child Profile, Theme, Security, Backup & Sync |

### Key Features

- **Customizable dashboard** — Choose which 4 stats appear on the hero card + configurable widget (Days Well, Next Appointment, Active Meds, Latest Growth, Last Feeding, Last Sleep)
- **Natural language entry** — Type "fever 101 gave Tylenol yesterday" and it auto-categorizes into the right fields
- **Health timeline chart** — Gantt-style visualization of illnesses, medications, and symptoms over 6 months
- **Growth curves** — Smooth bezier charts for weight, height, and head circumference with toggle controls
- **Dark mode** — Auto (follows system), Light, or Dark with full theme-color status bar support
- **PIN lock + encryption** — Optional 4-digit PIN with AES-256-GCM encryption of all localStorage data via Web Crypto API
- **App Switcher privacy screen** — Covers content when backgrounding the app
- **Backup reminder** — Amber banner after 7+ days without export
- **Formatted Excel export** — Color-coded medical records document with no gridlines, alternating rows, section headers
- **JSON import/export** — Deduplicating merge sync between devices via AirDrop
- **Swipe-back navigation** — Right-edge swipe closes sheets or navigates back
- **Calendar view** — Month calendar with dot indicators for entries
- **Doctor auto-complete** — Learns provider names from your entries
- **Baby photo** — Tap the hero avatar to upload, resized and stored locally
- **Read-only entry view** — Tap entries to view, must press Edit to modify

## Install

### iPhone / iPad
1. Open this page in **Safari**
2. Tap **Share (↑)** → **"Add to Home Screen"**
3. Name it "Little Health" → **Add**
4. Launch from Home Screen — runs full-screen with no browser chrome

### Mac
1. Open in **Safari**
2. **File** → **"Add to Dock"** (macOS Sonoma+)

## Sync Between Devices

1. **Export** a JSON backup from device A (Settings → Backup → JSON)
2. **AirDrop** the file to device B
3. **Import** on device B (Settings → Backup → Import)
4. Only new entries are added — nothing is overwritten or duplicated

## Privacy & Security

- **Zero network calls** from the app (only Google Fonts on first load)
- **localStorage only** — data never transmitted anywhere
- **Optional AES-256-GCM encryption** when PIN is enabled (PBKDF2 key derivation, 100k iterations)
- **App Switcher blur** — hides content via opacity overlay on `visibilitychange`, `blur`, and `pagehide` events
- **Auto-lock** after 5 minutes of inactivity
- **No analytics, no tracking, no cookies**
- Fully inspectable single-file source code

## Technical Details

- Single HTML file (~140KB), zero dependencies, zero build step
- Vanilla JavaScript — no frameworks
- CSS custom properties for theming with `[data-theme]` attribute
- Inline SVG icons using CSS variables for automatic dark mode adaptation
- `apple-touch-icon` generated dynamically via canvas
- `meta theme-color` updated dynamically on theme switch
- `black-translucent` status bar for transparent PWA status area
- `env(safe-area-inset-*)` for Dynamic Island and home indicator spacing
- `font-size: 16px` on inputs to prevent iOS auto-zoom
- UTF-8 BOM on exports for Excel compatibility
- `Date.now()` entry IDs for millisecond-precision deduplication during import
- `today()` uses local time (not UTC) — fixes timezone filename bug from v1

## License

MIT
