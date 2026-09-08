# Private Browsing Setup Guide

A practical guide to browsing the internet privately: choosing between **Tor Browser** and
**Mullvad Browser**, setting up **Mullvad VPN**, and avoiding the mistakes that undo all of it.

> **Scope:** this is about *privacy from surveillance, tracking and profiling* — advertisers,
> data brokers, your ISP, and casual network observers. It is not a guide to evading law
> enforcement, and no tool listed here will do that for you.

---

## The one-paragraph answer

**Use Mullvad Browser + Mullvad VPN for everyday private browsing.** It is fast enough to
actually live in, it kills browser fingerprinting, and the VPN hides your IP from the sites
you visit. **Use Tor Browser when you need real anonymity** — when it matters that *nobody*,
including your VPN provider, can link the traffic back to you. They solve different problems.
Pick based on your threat model, not on which one sounds more hardcore.

---

## Contents

| Doc | What's in it |
|---|---|
| [docs/threat-model.md](docs/threat-model.md) | Decide what you're actually defending against — read this first |
| [docs/browser-comparison.md](docs/browser-comparison.md) | Tor Browser vs Mullvad Browser, in detail |
| [docs/setup-mullvad-vpn.md](docs/setup-mullvad-vpn.md) | Installing and configuring Mullvad VPN |
| [docs/setup-mullvad-browser.md](docs/setup-mullvad-browser.md) | Installing and configuring Mullvad Browser |
| [docs/setup-tor-browser.md](docs/setup-tor-browser.md) | Installing and configuring Tor Browser |
| [docs/verify-downloads.md](docs/verify-downloads.md) | Verifying signatures so you don't install a backdoored build |
| [docs/common-mistakes.md](docs/common-mistakes.md) | The things that leak your identity anyway |
| [docs/going-further.md](docs/going-further.md) | Tails, Whonix, Qubes, DNS, search, email |
| [LINKS.md](LINKS.md) | Every official link in one place |
| [VIDEO-OUTLINE.md](VIDEO-OUTLINE.md) | A structure for the video, with the framing that keeps it accurate |

---

## Quick start

1. Read [docs/threat-model.md](docs/threat-model.md) — 5 minutes, saves you from over- or under-building.
2. Sign up for Mullvad VPN at <https://mullvad.net/> — no email, no name. Save the account number.
3. Install the VPN: [docs/setup-mullvad-vpn.md](docs/setup-mullvad-vpn.md)
4. Install a browser:
   - Everyday privacy → [Mullvad Browser](docs/setup-mullvad-browser.md)
   - Real anonymity → [Tor Browser](docs/setup-tor-browser.md)
5. Verify what you downloaded: [docs/verify-downloads.md](docs/verify-downloads.md)
6. Read [docs/common-mistakes.md](docs/common-mistakes.md) before you start using it.

---

## The two problems, kept separate

Privacy online is really two independent problems. Most people conflate them, and that's
where bad setups come from.

**Problem 1 — the network sees who you are.** Your ISP sees every domain you visit. Every
site you load sees your IP address, which maps to your rough location and your account with
your ISP. *Fixed by:* a VPN (shifts trust to the VPN provider) or Tor (removes the need to
trust anyone single party).

**Problem 2 — the browser tells sites who you are.** Even with a perfect IP hiding, your
browser leaks a fingerprint: screen size, fonts, GPU, timezone, language, extensions.
Combined, that's often unique enough to track you across sites and across IP changes.
*Fixed by:* a fingerprint-resistant browser (Mullvad Browser or Tor Browser).

**You need both.** A VPN with Chrome is barely private. Tor Browser on your normal machine
still needs care. This guide covers both halves.

---

## What none of this protects you from

Be honest about this in your own head, and on camera if you're making a video:

- **Logging into accounts.** The moment you sign into Google, Facebook, or anything tied to
  your real name, that session is deanonymized. No browser fixes it.
- **What you type.** Writing style, usernames you reuse, personal details you mention.
- **Malware on your machine.** If your OS is compromised, the browser doesn't matter.
- **Global adversaries.** A well-resourced actor watching both ends of a Tor circuit can, in
  theory, correlate timing. This is a real, studied limitation.
- **Doing illegal things.** These are privacy tools, not immunity.

---

## License

Documentation released under [CC BY 4.0](LICENSE). Do what you like with it, credit appreciated.
