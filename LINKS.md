# All links

Every official link used in this guide, in one place. Safe to paste into a video description.

*Checked September 2026.*

---

## Layer 1 — Mullvad VPN (IP protection)

| What | Link |
|---|---|
| Homepage | <https://mullvad.net/> |
| Create an account | <https://mullvad.net/en/account/create> |
| Pricing | <https://mullvad.net/en/pricing> |
| Download — all platforms | <https://mullvad.net/en/download/vpn/> |
| Download — Windows | <https://mullvad.net/en/download/vpn/windows> |
| Download — macOS | <https://mullvad.net/en/download/vpn/macos> |
| Download — Linux | <https://mullvad.net/en/download/vpn/linux> |
| Download — Android | <https://mullvad.net/en/download/vpn/android> |
| Verify app signature | <https://mullvad.net/en/help/verifying-signatures> |
| Connection check | <https://mullvad.net/check> |
| Encrypted DNS | <https://mullvad.net/en/help/dns-over-https-and-dns-over-tls> |

## Layer 2 — Mullvad Browser (fingerprint protection)

| What | Link |
|---|---|
| Download — all platforms | <https://mullvad.net/en/download/browser/> |
| Download — Windows | <https://mullvad.net/en/download/browser/windows> |
| Download — macOS | <https://mullvad.net/en/download/browser/macos> |
| Download — Linux | <https://mullvad.net/en/download/browser/linux> |
| GitHub releases | <https://github.com/mullvad/mullvad-browser/releases> |
| Source code | <https://github.com/mullvad/mullvad-browser> |
| Verify browser signature | <https://mullvad.net/en/help/verifying-mullvad-browser-signature> |

## Mullvad, generally

| What | Link |
|---|---|
| Help centre | <https://mullvad.net/en/help> |
| Blog | <https://mullvad.net/en/blog> |
| All source code | <https://github.com/mullvad> |
| The 2023 police search, no data seized | <https://mullvad.net/en/blog/2023/4/20/mullvad-vpn-was-subject-to-a-search-warrant-customer-data-not-compromised> |

---

## Testing your setup

| What | Tests | Link |
|---|---|---|
| IP and connection check | Layer 1 | <https://mullvad.net/check> |
| DNS leak | Layer 1 | <https://browserleaks.com/dns> |
| WebRTC leak | Layer 1 | <https://browserleaks.com/webrtc> |
| Browser fingerprint | Layer 2 | <https://coveryourtracks.eff.org/> |
| Detailed browser signals | Layer 2 | <https://browserleaks.com/> |

## Verification tools

| What | Link |
|---|---|
| Gpg4win (Windows) | <https://gpg4win.org/> |
| GPG Suite (macOS) | <https://gpgtools.org/> |

---

## Beyond this setup

| What | Link |
|---|---|
| Tor Browser | <https://www.torproject.org/download/> |
| Tor support portal | <https://support.torproject.org/> |
| Tails | <https://tails.net/> |
| Whonix | <https://www.whonix.org/> |
| Qubes OS | <https://www.qubes-os.org/> |
| GrapheneOS | <https://grapheneos.org/> |
| F-Droid | <https://f-droid.org/> |

## Search engines

| What | Link |
|---|---|
| DuckDuckGo | <https://duckduckgo.com/> |
| Startpage | <https://www.startpage.com/> |
| Brave Search | <https://search.brave.com/> |
| SearXNG instances | <https://searx.space/> |

## Email and aliasing

| What | Link |
|---|---|
| Proton Mail | <https://proton.me/mail> |
| Tuta | <https://tuta.com/> |
| SimpleLogin | <https://simplelogin.io/> |
| addy.io | <https://addy.io/> |

## Encrypted DNS

| What | Link |
|---|---|
| Mullvad DNS | <https://mullvad.net/en/help/dns-over-https-and-dns-over-tls> |
| Quad9 | <https://www.quad9.net/> |
| NextDNS | <https://nextdns.io/> |

## Learning more

| What | Link |
|---|---|
| EFF Surveillance Self-Defense | <https://ssd.eff.org/> |
| Privacy Guides | <https://www.privacyguides.org/> |
| Whonix documentation | <https://www.whonix.org/wiki/Documentation> |

---

## Key fingerprints

**Mullvad (code signing)** — signs the Mullvad VPN app:

```
A119 8702 FC3E 0A09 A9AE 5B75 D5A1 D4F2 66DE 8DDF
```

**Tor Browser Developers** — signs Mullvad Browser, because the Tor Project co-develops it:

```
EF6E 286D DA85 EA2A 4BA7 DE68 4E2C 6E87 9329 8290
```

Always cross-check these against the official sites before trusting them. See
[docs/verify-downloads.md](docs/verify-downloads.md).
