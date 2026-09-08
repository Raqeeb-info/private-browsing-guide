# Setting up Mullvad Browser

*Verified against Mullvad Browser 15.0.21, September 2026.*

Mullvad Browser is free and does **not** require a Mullvad VPN subscription — though it is
designed assuming you have some VPN in front of it.

Detail worth mentioning on camera: Mullvad Browser and Tor Browser ship the **same version
numbers** (both 15.0.21 as of writing) because they are built from the same codebase by the
same people. Mullvad Browser is Tor Browser with the Tor client removed.

## 1. Download

- **Windows:** <https://mullvad.net/en/download/browser/windows>
- **macOS:** <https://mullvad.net/en/download/browser/macos>
- **Linux:** <https://mullvad.net/en/download/browser/linux>

Or from the official GitHub releases: <https://github.com/mullvad/mullvad-browser/releases>

Verify the signature first — see [verify-downloads.md](verify-downloads.md).

There is **no Android or iOS version.** On mobile, use Tor Browser for Android, or Firefox
with strict tracking protection plus the Mullvad VPN app.

## 2. Install

Standard installer. On Windows it requires Windows 10 or later, 64-bit only.

## 3. What is already configured for you

Do not undo these. They are the entire point of the browser.

| Setting | State |
|---|---|
| Telemetry, crash reports, studies | Off |
| uBlock Origin | Installed and enabled |
| Cookies and history | Cleared on close (permanent private-mode behavior) |
| privacy.resistFingerprinting | On |
| Letterboxing | On |
| Canvas / WebGL / audio fingerprinting | Blocked or standardized |
| First-party isolation | On |
| Search engine | Non-tracking default |
| Password manager | Disabled by default |

## 4. The security level slider

Same three-tier system as Tor Browser. Find it in the shield or settings menu.

- **Standard** — everything on. Fastest, most compatible, least protected.
- **Safer** — disables JavaScript on non-HTTPS sites, blocks some fonts and media, disables
  JIT. **This is a good default for most people.**
- **Safest** — JavaScript off everywhere. Maximum protection; many sites will not work.

Start at Safer. Drop to Standard for specific sites you trust that break.

## 5. Rules for keeping the protection intact

This is where people undo everything, so it is worth stating plainly.

1. **Do not install extensions.** Every extension you add is a fingerprint signal. You just
   became one of the very few people with that exact extension set. uBlock Origin is already
   there and everyone else has it too — that is why it is safe.
2. **Do not resize or maximize the window** more than you have to. Window dimensions are a
   strong fingerprint. Letterboxing helps, but the default size is the safest size.
3. **Do not log into accounts tied to your real identity.** Not "not usually." Not at all, in
   this browser. If you need Gmail, use a different browser for that.
4. **Do not change privacy settings** to fix a broken site. Use a different browser for that
   site instead.
5. **Keep it updated.** Fingerprinting research moves, and the browser tracks Firefox ESR
   security updates.

## 6. Verify it is working

- **Fingerprint:** <https://coveryourtracks.eff.org/> — run the full test. Note that a
  "unique" verdict from this specific tool can be misleading for fingerprint-resistant
  browsers: what matters is that you look like *other Mullvad Browser users*, which the tool
  cannot measure.
- **Detailed signals:** <https://browserleaks.com/> — check canvas, WebGL, fonts, WebRTC.
- **IP:** <https://mullvad.net/check> — confirms the VPN half is working.

## 7. The two-browser habit

The setup that actually works long-term:

- **Mullvad Browser** — your private browsing. No logins, no accounts.
- **A separate normal browser** (Firefox, Brave, whatever) — your logged-in life. Email,
  banking, shopping, social media.

Keeping them strictly separate is more effective than any single setting, because it stops
the one thing no browser hardening can prevent: linking your anonymous browsing to your real
identity through a session cookie.

Never mix. If you catch yourself logging into something in Mullvad Browser, close it, clear
it, and move that activity to the other browser.
