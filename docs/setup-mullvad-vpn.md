# Setting up Mullvad VPN

*Verified against Mullvad app version 2026.4, September 2026.*

## Why Mullvad specifically

- **No account, no email, no name.** You click a button and get a 16-digit account number.
  That number *is* your identity. There is nothing else to leak.
- **Flat €5/month**, regardless of whether you pay for one month or ten years. No
  "3 years for $1.99!" pricing games, which are usually a sign the provider monetizes you
  some other way.
- **Cash accepted.** You can literally mail an envelope with your account number and banknotes.
  Also Monero and Bitcoin (10% discount), plus normal cards, PayPal, bank transfer, Swish,
  iDEAL, and others.
- **Repeatedly audited**, publicly, by third parties, with reports published.
- **Diskless, RAM-only infrastructure** — servers run from RAM, so there is no disk to seize.
- **Open source clients**, on GitHub.
- **WireGuard by default**, with OpenVPN available.

If a VPN is free, you are the product. That is not a slogan — it's the business model.

## 1. Get an account

1. Go to <https://mullvad.net/en/account/create>
2. Click to generate an account number
3. **Write the number down somewhere safe.** There is no password reset, no email recovery,
   no support ticket that can restore it. Lose it and you lose the account.
4. Add time with your chosen payment method

For maximum privacy, pay with cash or Monero. For normal use, a card is fine — Mullvad's
payment processor knows you paid Mullvad, but not what you browse.

## 2. Install the app

**Windows:** <https://mullvad.net/en/download/vpn/windows>
**macOS:** <https://mullvad.net/en/download/vpn/macos>
**Linux:** <https://mullvad.net/en/download/vpn/linux>
**Android:** <https://mullvad.net/en/download/vpn/android> (also on Google Play and F-Droid)
**iOS:** App Store

Verify the signature before installing — see [verify-downloads.md](verify-downloads.md).

Log in with your account number. No username, no password.

## 3. Configure it properly

These are the settings that matter. Defaults are good, but check them.

### Essential

- **Kill switch** — on. Mullvad calls this "Lockdown mode" in some versions. If the VPN
  drops, your traffic stops rather than falling back to your real IP. Non-negotiable.
- **Auto-connect** — on. Connects before anything else can talk to the network.
- **Launch app on start-up** — on.
- **DNS** — leave Mullvad's DNS on. Don't point it at Google or Cloudflare; that hands your
  full browsing history to a company whose business is data.

### Strongly recommended

- **WireGuard** — keep it as the tunnel protocol. Faster and more modern than OpenVPN.
- **DAITA** (Defense Against AI-guided Traffic Analysis) — on, if your device can spare the
  bandwidth. It pads and reshapes traffic so packet-size and timing patterns can't be used to
  guess which websites you're visiting. Costs some bandwidth; worth it.
- **Quantum-resistant tunnel** — on. Post-quantum key exchange, guards against
  "harvest now, decrypt later."

### Situational

- **Multihop** — routes through two Mullvad servers in different countries. Protects against
  a single server being compromised or monitored. Slower. Worth it if you're in the higher
  tiers of the threat model.
- **Server selection** — a nearby server is fastest. A server in a different legal
  jurisdiction is marginally better for privacy. Avoid picking a country where your unusual
  choice is itself notable.
- **Split tunneling** — lets specific apps bypass the VPN. Convenient for things like game
  clients or banking apps that block VPNs. Understand that anything you exclude is exposed.
- **Obfuscation (Shadowsocks / UDP-over-TCP)** — only if a network blocks WireGuard.

## 4. Verify it's actually working

Do this once after setup, and again any time you change settings.

1. **IP check** — <https://mullvad.net/check> — should show "You are connected" and a Mullvad IP
2. **DNS leak test** — <https://browserleaks.com/dns> — every server listed should belong to Mullvad,
   not your ISP
3. **WebRTC leak** — <https://browserleaks.com/webrtc> — should not show your real local or
   public IP. Mullvad Browser and Tor Browser both block this already.
4. **Kill switch test** — disconnect the VPN while a download is running. The download should
   stop dead, not continue.

If any of these fail, fix it before you rely on the setup.

## Realistic expectations

Mullvad hides your IP from websites and hides your browsing from your ISP. It does **not**:

- Make you anonymous (Mullvad receives your traffic; you're trusting their no-logs policy)
- Stop browser fingerprinting (that's the browser's job — see the browser setup docs)
- Protect you if you log into accounts tied to your real identity
- Stop malware, phishing, or anything on your own machine

It's one layer. A good one. Not the whole stack.
