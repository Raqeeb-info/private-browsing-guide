# Mullvad VPN + Mullvad Browser

A complete private browsing setup using two tools that solve two different problems:

| Layer | Tool | Hides |
|---|---|---|
| **1. Network** | **Mullvad VPN** | Your **IP address** — from websites, and your browsing from your ISP |
| **2. Browser** | **Mullvad Browser** | Your **fingerprint** — the signals that identify you even without an IP |

Neither one is enough alone. Together they cover both halves of how you get tracked online.

> **Scope:** this is about privacy from tracking, profiling and surveillance — advertisers,
> data brokers, your ISP, and casual network observers. No tool here makes you anonymous
> from a determined, well-resourced adversary, and none of it is a shield for illegal activity.

---

## Why two tools

Most privacy advice stops at "get a VPN." That solves exactly one of the two ways you are
identified online.

### Problem 1: the network knows who you are

Your ISP sees every domain you visit and is allowed to sell that in many countries. Every
site you load sees your IP address, which maps to your city and your account with your ISP.

**Mullvad VPN fixes this.** Your traffic goes to Mullvad first, encrypted. Your ISP sees only
that you talked to Mullvad. Websites see a Mullvad IP shared with many other users.

### Problem 2: the browser tells on you anyway

Here is the part the VPN does nothing about. Every site you visit can read: your screen
resolution, your timezone, your fonts, your GPU model, your language, your installed
extensions, how your browser renders a hidden image. Combined, that is usually **unique** —
a fingerprint that follows you across IP addresses, across incognito windows, across cleared
cookies.

A VPN with a normal browser is like wearing a mask while keeping your name tag on.

**Mullvad Browser fixes this.** It makes you look identical to every other Mullvad Browser
user: spoofed timezone, standardized screen metrics, blocked canvas and WebGL fingerprinting,
no telemetry, nothing written to disk.

### Together

- **VPN alone** — sites can't see your IP, but they still recognize *you* by fingerprint
- **Browser alone** — sites can't fingerprint you, but they see your real IP and ISP
- **Both** — no IP, no fingerprint, no ISP visibility

---

## Contents

| Doc | What's in it |
|---|---|
| [docs/how-it-works.md](docs/how-it-works.md) | The two layers explained properly — read this first |
| [docs/threat-model.md](docs/threat-model.md) | What this setup does and does not defend against |
| [docs/1-mullvad-vpn.md](docs/1-mullvad-vpn.md) | **Layer 1** — installing and configuring the VPN |
| [docs/2-mullvad-browser.md](docs/2-mullvad-browser.md) | **Layer 2** — installing and configuring the browser |
| [docs/verify-downloads.md](docs/verify-downloads.md) | Checking signatures so you don't install a backdoored build |
| [docs/common-mistakes.md](docs/common-mistakes.md) | The things that undo all of it |
| [docs/going-further.md](docs/going-further.md) | DNS, search, email, and where this setup stops |
| [LINKS.md](LINKS.md) | Every official link in one place |
| [VIDEO-OUTLINE.md](VIDEO-OUTLINE.md) | A video structure built on the two-layer framing |

---

## Quick start

1. Read [docs/how-it-works.md](docs/how-it-works.md) — five minutes, makes the rest obvious
2. Create a Mullvad account at <https://mullvad.net/en/account/create> — no email, no name,
   just a generated number. **Write the number down.**
3. Install and configure the VPN: [docs/1-mullvad-vpn.md](docs/1-mullvad-vpn.md)
4. Install and configure the browser: [docs/2-mullvad-browser.md](docs/2-mullvad-browser.md)
5. Verify both signatures: [docs/verify-downloads.md](docs/verify-downloads.md)
6. Test it works:
   - IP → <https://mullvad.net/check>
   - Fingerprint → <https://coveryourtracks.eff.org/>
7. Read [docs/common-mistakes.md](docs/common-mistakes.md) before you rely on any of it

---

## Why Mullvad for both

- **No account, no email, no name.** You press one button and get a 16-digit number — that
  number *is* your account. There is no personal data to leak, subpoena, or breach, because
  you were never asked for any.
- **Proven, not promised.** In April 2023 Swedish police arrived with a search warrant for
  customer data and left without searching and without taking anything — the data did not
  exist. [The full story](docs/1-mullvad-vpn.md#proof-not-promises--the-april-2023-raid).
- **Flat €5/month**, whether you buy one month or ten years. No countdown timers, no
  "83% off" pricing games.
- **Cash accepted.** Literally mail an envelope of banknotes with a one-time payment token —
  no financial institution involved at any point. Also Monero and Bitcoin (10% off), plus
  normal cards. And it isn't a subscription: nothing auto-renews, no card on file, you just
  top up time.
- **Repeatedly audited** by third parties, publicly, with the reports published.
- **RAM-only servers** — no disks to seize or forensically recover.
- **Open source clients**, all on GitHub.
- **No affiliate program and no influencer sponsorships**, by policy. Nobody is paid to
  recommend Mullvad, which is part of why it keeps showing up in honest recommendations.
- **The browser is co-developed with the Tor Project** — it is built on the same
  fingerprint-resistance engineering as Tor Browser, minus the Tor network.

---

## Be accurate about what this does

Worth saying plainly, especially if you're explaining it to other people:

**Mullvad still receives your traffic.** They have to, in order to route it. What you have
done is swap trusting your ISP — a company that sells browsing data as a line of business —
for trusting one whose entire model depends on not knowing who you are, backed by audits and
diskless infrastructure. That is a real, significant upgrade. It is not the same as being
anonymous.

Accurate claim: *"My ISP can't see my browsing, websites can't see my IP, and nothing can
fingerprint me across sites."*

Not accurate: *"I'm anonymous."*

If you need the version where **no single party** can link you to your traffic, that is Tor's
three-relay design, and it is a different tool with different costs — see
[docs/going-further.md](docs/going-further.md).

---

## License

Documentation released under [CC BY 4.0](LICENSE).
