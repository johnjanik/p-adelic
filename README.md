# p-adelic for Android

A calculator for the **adelic strip** of a global field — see every
local completion of a number side-by-side: ℝ at infinity plus a column
per prime `p` showing its `p`-adic expansion. Type `1/14`, `√2`,
`exp(1)`, `klzeta(7, -1)`, or 60 other library examples, and watch the
number reveal itself at every place at once.

Native port of the iOS [p-adelic](https://apps.apple.com/app/p-adelic/id6753321456)
app. Pure Kotlin / Jetpack Compose; no Google Play account, no
telemetry, no cloud sync. **2 MB**.

## Requirements

- Android 8.0 (Oreo) or newer.
- ~10 MB free storage (the APK is ~2 MB; Android allocates a bit
  more for install overhead).

## Download

Tap **`app-release.apk`** in the file list above and choose
**Download** (or "Save link as…" on desktop, then transfer to your
phone).

Verify the APK is the real thing (optional but recommended) — the
build is signed by `CN=practicallyzen.com, O=PracticallyZen, C=US`
with fingerprint:

```
SHA-256: 91:5A:D6:D2:F7:44:7F:0D:8D:B2:F8:95:5E:10:38:CD:
        B7:62:8D:61:D9:1A:DE:53:6E:61:CB:C8:21:83:9A:B9
SHA-1:   CC:B6:C6:BA:DD:6F:44:A7:6C:06:FB:9C:77:A9:B7:24:
        89:33:BA:D0
```

Every future update will be signed by the **same** identity. If
Android refuses to install an update because the signature changed,
**don't proceed — it's not me.** You can inspect what's already
installed via *Settings → Apps → p-adelic → App info → App details
in store / Open by default → Advanced* (the path varies per OEM), or
with `adb shell pm list packages -f | grep padelic`.

## Install

p-adelic isn't on the Google Play Store, so you'll install it as a
"sideloaded" APK. Modern Android makes this painless but asks for
explicit per-source permission the first time.

1. **Tap the downloaded APK** in your browser's downloads or in your
   file manager.
2. Android will say **"For your security, your phone is not allowed
   to install unknown apps from this source."** Tap **Settings**.
3. Toggle **Allow from this source** on, then tap your back button.
4. The install prompt reappears. Tap **Install**, then **Open**.
5. The app appears in your launcher as **p-adelic**. The first launch
   shows the empty calculator strip — type `1/14` in the input bar
   and hit go to see your first adelic point.

If you don't see the "Settings" link in step 2, the permission lives
under:

> **Settings → Apps → Special access → Install unknown apps →
> [your browser or file manager] → Allow**

## Updates

Just download the new APK and tap to install — Android upgrades the
existing copy in place and **your history persists**. No data wipe.

If you ever see *"App not installed because the package conflicts
with an existing package"*, the new APK is signed with a different
identity than the one you have. That should never happen for
legitimate updates — double-check the source.

## What it does

Three tabs along the bottom:

- **Calculator.** Type a number; see its decimal expansion at ∞ and
  its `p`-adic expansion at every prime. Tap a column to focus it.
  Long-press a column for the deep-dive panel: full digit row, nested
  balls (pinch to drill), Bruhat–Tits tree, Berkovich line.
- **History.** Every commit is auto-saved. Tap to restore.
- **Library.** 60 curated examples across 7 chapters (Foundations,
  Square roots & Hensel, Adelic, Cyclotomic, Algebraic numbers,
  Special functions, Newton polygons). Tap a tile, jump to the
  Calculator tab with everything pre-configured.

The bottom bar also has a **mod** chip — long-press to engage modular
view, where each column becomes a lifted integer in `ℤ/pᵃ`.

What you can type:

- Rationals: `7/12`, `-1`, `1.5`, `(1+2)*3`
- Radicals: `sqrt(2)`, `√7`, `sqrt(-1)`
- Cyclotomic: `zeta_5`, `ζ_3`
- Polynomials: `poly(x^4 - 10x^2 + 1)`
- Algebraic: `algebraic(x^3 - 2)` (cube root of 2)
- Special functions: `exp(6)`, `log(7)`, `artinHasse(2)`, `gammaP(7)`,
  `klzeta(5, -1)` (Kubota–Leopoldt zeta)
- Modular: `modinv(7, 12)`, `modpow(2, 10, 17)`, `crt(2, 3, 3, 5)`,
  `phi(360)`, `lambda(32)`, `mulord(2, 13)`, `disclog(2, 8, 13)`,
  `primroot(13)`, `gcd(48, 18)`, `bezout(240, 46)`
- Hilbert pairs: `hilbert(2, 3)`
- Tate / adelic Fourier: `tate`

## Privacy

- No analytics. No crash reporting. No accounts.
- History stays on-device, in a local database. Uninstalling deletes
  it.
- Settings stay on-device, in DataStore.
- The app makes **zero** network calls in normal use. The only
  outbound action is the **Send feedback** button in Settings, which
  composes a `mailto:` to the developer through your installed mail
  app — and only if you tap Send.

## Feedback

In-app: ⚙ Settings → Send feedback. Composes a mail to
`john@practicallyzen.com` through whichever mail client you use.

Source code is held privately by the developer; happy to discuss the
math, the engine design, or specific behavior — just write.
