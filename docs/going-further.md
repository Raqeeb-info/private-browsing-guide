# Going further

Mullvad VPN + Mullvad Browser covers the two big holes. These are the smaller ones, plus an
honest note on where this setup stops.

---

## Search engines

Your search history is the single most revealing dataset about you, and it sits outside both
layers — you can be perfectly unfingerprintable and still hand a search engine a complete
profile of your interests.

Options that do not build one:

- **DuckDuckGo** — <https://duckduckgo.com/> — the sensible default
- **Startpage** — <https://www.startpage.com/> — Google results, proxied
- **Brave Search** — <https://search.brave.com/> — independent index
- **SearXNG** — <https://searx.space/> — self-hostable metasearch; public instances vary in
  quality, so pick a reputable one or run your own

Mullvad used to run a search proxy called **Leta**, and you will still see it recommended in
older guides and videos. Mullvad shut it down in November 2025. Do not include it.

---

## Encrypted DNS

While the VPN is connected, Mullvad's DNS already covers you and you should leave it alone.
This is for when you are off the VPN — a phone on mobile data, a device that can't run the
app:

- **Mullvad DNS** — <https://mullvad.net/en/help/dns-over-https-and-dns-over-tls> — free,
  works without an account, includes ad and tracker blocking variants
- **Quad9** — <https://www.quad9.net/> — non-profit, blocks known malicious domains
- **NextDNS** — <https://nextdns.io/> — configurable filtering, free tier

Avoid Google (8.8.8.8) and Cloudflare (1.1.1.1) if privacy is the point. They are fast and
they are not obviously abusing it, but you are handing a full browsing history to a large
advertising or CDN company for no reason.

---

## Email and aliases

A private browsing setup with a Gmail account attached to it is not a private setup. Email is
the most common thread linking your accounts together.

- **Proton Mail** — <https://proton.me/mail> — end-to-end encrypted, Swiss, free tier
- **Tuta** — <https://tuta.com/> — end-to-end encrypted, German, free tier
- **SimpleLogin** — <https://simplelogin.io/> — email aliasing
- **addy.io** — <https://addy.io/> — email aliasing

Aliasing is the highest value-per-effort item on this page. Every service gets a different
address, so a breach at one cannot be correlated with your accounts anywhere else.

---

## Mobile

Layer 1 works fine on mobile — the Mullvad VPN app covers Android and iOS on the same
account. Layer 2 does not: **there is no Mullvad Browser for mobile.**

Best available:

- **Mullvad VPN app** — Android and iOS, also on F-Droid
- **Firefox for Android** with strict tracking protection and uBlock Origin
- **GrapheneOS** — <https://grapheneos.org/> — hardened Android, Pixel devices only. The
  serious option if mobile privacy actually matters to you.
- **F-Droid** — <https://f-droid.org/> — open source app repository

Be realistic: mobile privacy is structurally worse than desktop. The OS, the baseband, and
the app stores all see more than you would like, and no browser fixes that.

---

## Where this setup stops

Two limits are worth naming, because they are the reason other tools exist.

### You still trust one company

Mullvad receives your traffic. Their no-logs policy is audited, their servers are diskless,
their business model never asks who you are, and a Swedish police search in 2023 came away
with nothing. That is about as good as trust gets — but it is trust.

**Tor** removes it. Traffic passes through three independent relays: the first knows your IP
but not your destination, the last knows your destination but not your IP, and no single
operator has both halves. That is a categorically different guarantee, and the price is that
it is slow and many sites block it.

If you need it, use **Tor Browser** from <https://www.torproject.org/download/> — and use it
on its own, not chained through your VPN. The Tor Project advises against combining the two:
it buys you very little, and configured backwards it actively weakens Tor. Mullvad Browser is
the one designed to sit behind a VPN.

A reasonable pattern is both, kept separate: Mullvad Browser + VPN as your everyday setup,
Tor Browser opened for the specific sessions that need real anonymity.

### The device itself still knows

Both layers operate on the network and in the browser. If your operating system is
compromised, or someone gets the machine, neither helps.

- **Tails** — <https://tails.net/> — a live Linux USB that routes everything through Tor and
  writes nothing to disk. Power it off and the session is gone.
- **Whonix** — <https://www.whonix.org/> — two VMs, where the workstation physically cannot
  reach the network except through a Tor gateway. Malware on it still cannot learn your real
  IP.
- **Qubes OS** — <https://www.qubes-os.org/> — every activity in its own isolated VM. The
  strongest option and the steepest learning curve by a wide margin.

These are for people who are actually targeted. If you are here to stop advertisers and your
ISP, you do not need them.

---

## Reading the primary sources

Do not take any single guide's word for it, including this one:

- **EFF Surveillance Self-Defense** — <https://ssd.eff.org/> — the best free introduction to
  threat modeling anywhere
- **Privacy Guides** — <https://www.privacyguides.org/> — community-maintained, careful,
  takes no affiliate money
- **Mullvad's blog** — <https://mullvad.net/en/blog> — unusually honest about what a VPN
  does not do
- **Mullvad help centre** — <https://mullvad.net/en/help>
- **Tor support portal** — <https://support.torproject.org/>

Be careful with VPN recommendations generally: the market pays large affiliate commissions
and a great deal of "best VPN" content is bought. Mullvad publicly refuses to run affiliate
programs or sponsor influencers, which is part of why it keeps appearing in recommendations
that nobody was paid to make.
