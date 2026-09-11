# Layer 1 — Mullvad VPN (IP protection)

*Verified against Mullvad app version 2026.4, September 2026.*

**What this layer does:** hides your IP address from every website you visit, and hides your
browsing from your ISP.

**What it does not do:** stop browser fingerprinting. That is
[Layer 2](2-mullvad-browser.md), and you need both.

## Why Mullvad specifically

- **No account, no email, no name.** You click a button and get a 16-digit account number.
  That number *is* your identity. There is nothing else to leak.
- **Flat €5/month**, regardless of whether you pay for one month or ten years. No
  "3 years for $1.99!" pricing games, which are usually a sign the provider monetizes you
  some other way.
- **Cash accepted.** You can literally mail an envelope of banknotes with a one-time payment
  token. Also Monero and Bitcoin (10% discount), plus normal cards, PayPal, bank transfer,
  Swish, iDEAL and others.
- **Repeatedly audited**, publicly, by third parties, with reports published.
- **Diskless, RAM-only infrastructure** — servers run from RAM, so there is no disk to seize.
- **Open source clients**, on GitHub.
- **WireGuard by default**, with OpenVPN available.

If a VPN is free, you are the product. That is not a slogan — it's the business model.

## 1. Get an account — there is nothing to give them

This is the part that surprises people, and it is worth dwelling on. **Mullvad does not ask
you for anything.** Not an email address. Not a username. Not a password. Not a name.

You go to <https://mullvad.net/en/account/create>, press one button, and the site generates a
**16-digit account number**. That number *is* your account. It is the only credential that
exists, and it is the only thing Mullvad knows about you.

Think about what that means for a moment. There is no email to subpoena. No name to breach.
No password to reuse. No "forgot password" flow leaking your address. No support ticket
history tying an identity to an IP. The privacy isn't a policy sitting on top of a database —
**there is no database row with your name on it, because you were never asked.**

> **Write the number down before you do anything else.** There is no password reset, no email
> recovery, no support ticket that can restore it. If you lose the number, the account and any
> time left on it are gone. Treat it like cash. A password manager or a piece of paper both work.

### It is not a subscription

Mullvad removed the option to create new subscriptions. Nothing auto-renews and nothing has
your card on file. You **top up time** on the numbered account, like a prepaid phone. Pay for
one month, walk away for a year, come back and top it up again.

It is a flat **€5 / month** no matter how much you buy at once. No "3 years for $1.99",
no countdown timers, no fake discounts. When a provider does use those, it's usually because
they monetize you some other way.

### Paying without attaching your name

The account is anonymous the moment it is created. Payment is the one step that can attach an
identity back to it, so Mullvad supports a ladder of options — pick the rung that matches your
threat model:

| Method | Privacy | Notes |
|---|---|---|
| **Cash by post** | **Highest** | Generate a payment token on the site, put it in an envelope with banknotes, and mail it. No financial institution is involved at any point. Accepted in EUR, USD, GBP, SEK, NOK, CHF, CAD, AUD and NZD. |
| **Monero (XMR)** | Very high | Private by design — amounts and parties are not publicly visible. **10% discount** on all crypto. |
| **Bitcoin / Bitcoin Cash** | Good | Also 10% off, but the blockchain is public. Only as private as how you obtained the coins. |
| **Card, PayPal, Swish, bank transfer, iDEAL** | Normal | Perfectly fine for most people. |

**Cash is the interesting one**, and it's worth showing on camera because almost nobody
believes it until they see it. You are not mailing your account number — you generate a
one-time **payment token**, and that token is what goes in the envelope with the money. The
result is an account with no name, no email, and no payment trail whatsoever.

**For most people, a card is fine.** Be clear-eyed about the tradeoff rather than paranoid
about it: your card issuer learns that you paid Mullvad €5. It learns nothing about what you
browse, and Mullvad still has no idea who you are — the payment processor and the numbered
account are not linked on their side. Cash and Monero close even that gap, which matters if
*the fact that you use a VPN at all* is something you need to keep private.

### Proof, not promises — the April 2023 raid

Every VPN on earth claims "no logs." It is the single most abused phrase in the industry, and
it is almost always just a sentence on a marketing page. Mullvad's claim is one of the very
few that has been **tested in the real world, by police, and survived.**

On **18 April 2023**, at least six officers from the Swedish police **National Operations
Department (NOA)** arrived at Mullvad's office in Gothenburg with a **search warrant**. They
came to seize computers containing customer data. It was the first such visit in the company's
fourteen-year history, and a letter received nine days later revealed the search had been
carried out at **Germany's request**, for an investigation there.

Mullvad's staff and lawyers walked them through how the service actually works: the customer
data they were looking for **does not exist**. There are no logs of activity, no names, no
email addresses — just numbered accounts. The prosecutor was consulted. The officers
**left without conducting the search and without taking a single thing.**

Mullvad's own summary of the visit is the sharpest line in this whole guide:

> *"If they had taken something that would not have given them access to any customer
> information."*

That is the whole argument for building a service this way. A company's promise not to hand
over your data is only as strong as its ability to refuse — and no company can refuse a lawful
warrant indefinitely. What a company *can* do is make sure there was never anything to hand
over in the first place. **You cannot seize what was never collected.**

That is the difference between a VPN that *says* no logs and one that has *proven* it.

**Sources** — Mullvad's own account: [Mullvad VPN was subject to a search warrant](https://mullvad.net/en/blog/2023/4/20/mullvad-vpn-was-subject-to-a-search-warrant-customer-data-not-compromised).
Independent reporting: [Gizmodo](https://gizmodo.com/vpn-mullvad-search-warrant-data-it-doesnt-collect-1850358717)
· [TechRadar](https://www.techradar.com/news/mullvads-no-log-policy-proven-after-police-raid)
· [Techdirt](https://www.techdirt.com/2023/05/01/cops-raid-swedish-vpn-provider-only-to-find-out-theres-no-there-there/).
Cite the independent coverage, not just the company blog — it pre-empts the obvious objection.

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
- Stop browser fingerprinting — that is entirely [Layer 2's](2-mullvad-browser.md) job, and
  without it you are still recognizable on every site you visit
- Protect you if you log into accounts tied to your real identity
- Stop malware, phishing, or anything on your own machine

It is one layer. A good one. Now go install [Layer 2](2-mullvad-browser.md).
