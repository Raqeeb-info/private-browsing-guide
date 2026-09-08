# Going further

Once the VPN and browser are set up, these are the next layers — roughly in order of
effort-to-benefit.

---

## Search engines

Your search history is the single most revealing dataset about you. Options that do not
build a profile:

- **DuckDuckGo** — <https://duckduckgo.com/> — default in Tor Browser, has an onion service
- **Startpage** — <https://www.startpage.com/> — Google results, proxied
- **Brave Search** — <https://search.brave.com/> — independent index
- **SearXNG** — <https://searx.space/> — self-hostable metasearch; public instances vary in
  quality, so pick a reputable one or run your own

Mullvad used to run a search proxy called **Leta**, and you will still see it recommended in
older guides and videos. Mullvad shut it down in November 2025. Do not include it.

---

## Encrypted DNS

If you are on a VPN, its DNS already covers you. Off the VPN, encrypted DNS stops your ISP
reading your queries in plaintext:

- **Mullvad DNS** — <https://mullvad.net/en/help/dns-over-https-and-dns-over-tls> — free,
  no account needed, includes ad and tracker blocking variants
- **Quad9** — <https://www.quad9.net/> — non-profit, blocks known malicious domains
- **NextDNS** — <https://nextdns.io/> — configurable filtering, free tier

Avoid using Google (8.8.8.8) or Cloudflare (1.1.1.1) if privacy is the goal. They are fast
and they are not selling your DNS data, but you are still handing a full browsing history to
a large advertising or CDN company.

---

## Email

A privacy setup with a Gmail account attached to it is not a privacy setup.

- **Proton Mail** — <https://proton.me/mail> — end-to-end encrypted, Swiss, free tier
- **Tuta** — <https://tuta.com/> — end-to-end encrypted, German, free tier
- **SimpleLogin** / **addy.io** / **Proton Pass aliases** — email aliasing, so every service
  gets a different address and none of them can correlate you

Aliasing is underrated and very high value for low effort.

---

## Amnesic operating systems

This is the step above browser-level privacy: the whole OS forgets.

### Tails

<https://tails.net/>

A live Linux system you boot from a USB stick. Everything routes through Tor. Nothing is
written to disk. Power it off and every trace is gone.

**Use when:** you need strong anonymity on a machine you do not fully trust, or you need to
leave no forensic trace on the hardware. This is the tool used by journalists and sources.

**Cost:** you reboot into it, and you lose all convenience.

### Whonix

<https://www.whonix.org/>

Two virtual machines: a gateway that runs Tor, and a workstation that has *no way* to reach
the network except through the gateway. Even if the workstation is compromised by malware, it
cannot discover your real IP — it does not have one.

**Use when:** you want Tails-grade isolation but need persistence, and you want to run it
alongside your normal desktop.

### Qubes OS

<https://www.qubes-os.org/>

Security through compartmentalization: every activity runs in its own isolated VM. Can run
Whonix inside it. The strongest of the three, and the steepest learning curve by a wide
margin.

**Use when:** you are genuinely a target, and you are willing to change how you use a
computer.

---

## Mobile

Mobile privacy is structurally worse than desktop. The OS, the baseband, and the app stores
all see more than you would like.

- **Tor Browser for Android** — official, works well
- **Mullvad VPN app** — Android and iOS, same account
- **GrapheneOS** — <https://grapheneos.org/> — hardened Android, Pixel devices only. The
  serious option.
- **F-Droid** — <https://f-droid.org/> — open source app repository

There is no Mullvad Browser for mobile.

---

## Reading the primary sources

Do not take a guide's word for it, including this one. These are the sources worth reading:

- **Tor Project support portal** — <https://support.torproject.org/>
- **EFF Surveillance Self-Defense** — <https://ssd.eff.org/> — the best introduction to
  threat modeling anywhere, and it is free
- **Privacy Guides** — <https://www.privacyguides.org/> — community-maintained, careful,
  no affiliate links
- **Mullvad's blog and help pages** — <https://mullvad.net/en/blog> — unusually honest about
  what a VPN does not do
- **Whonix documentation** — <https://www.whonix.org/wiki/Documentation> — deep, technical,
  applies well beyond Whonix itself

Be careful with YouTube and blog recommendations generally — the VPN market pays large
affiliate commissions, and a great deal of "best VPN" content is bought. Prefer sources that
take no affiliate money, and note that Mullvad publicly refuses to run affiliate programs or
sponsor influencers, which is part of why it comes up so often in non-sponsored
recommendations.
