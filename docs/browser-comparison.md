# Tor Browser vs Mullvad Browser

Both browsers come from the same engineering work. Mullvad Browser is a **joint project
between Mullvad VPN and the Tor Project**, released in April 2023. It is, roughly,
"Tor Browser with the Tor network removed and a VPN assumed in its place."

That single sentence explains almost every difference below.

---

## Side by side

| | **Mullvad Browser** | **Tor Browser** |
|---|---|---|
| Base | Firefox ESR | Firefox ESR |
| Network routing | **None built in** — uses whatever connection you give it (a VPN, ideally) | **Tor**, 3 relays, built in and mandatory |
| Fingerprint resistance | Yes — same hardening as Tor Browser | Yes |
| Speed | Normal browsing speed | Noticeably slower; video is painful |
| Blocked by websites | Rarely | Often — many sites block or CAPTCHA Tor exit nodes |
| Anonymity set | Everyone using Mullvad Browser (smaller) | Everyone using Tor Browser (larger) |
| Who can see your real IP | Your VPN provider | Your ISP sees you use Tor; nobody sees IP + destination together |
| Onion sites (.onion) | No | Yes |
| Cost | Free (VPN is separate, paid) | Free |
| Multi-account / circuit isolation | Per-site state isolation | Per-site circuit isolation ("New Circuit for this Site") |
| Best for | Everyday private browsing, at usable speed | Anonymity, censorship circumvention, onion services |

---

## What they share

Because Mullvad Browser inherits Tor Browser's hardening, both give you:

- **`privacy.resistFingerprinting`** — spoofs or standardizes timezone, locale, screen
  metrics, and dozens of other signals so you look like every other user of that browser.
- **Letterboxing** — window dimensions get rounded to common sizes, so resizing your window
  doesn't create a unique measurement.
- **uBlock Origin preinstalled**, no telemetry, no crash reporters, no studies.
- **State isolation by first party** — cookies and storage can't follow you between sites.
- **No disk persistence by default** — history and cookies are gone when you close it
  (Mullvad Browser runs in a permanent private-browsing-like mode).
- **Canvas, WebGL, audio and font fingerprinting** blocked or standardized.

The hardening is the valuable part, and you get it either way.

---

## The real distinction: who you have to trust

This is the point worth making clearly in a video, because it's the thing most guides skip.

**With a VPN**, you have moved trust, not eliminated it. Your ISP no longer sees your
traffic — Mullvad does. Mullvad's real IP address knowledge is unavoidable: they receive
your packets. Their protection is a *policy* (no logs), backed by audits, a diskless
RAM-only infrastructure, and a business model that doesn't need your identity. That is a
genuinely strong setup. It is still trust.

**With Tor**, no single party has both halves of the picture:

- The **guard** relay knows your IP but not your destination.
- The **middle** relay knows neither.
- The **exit** relay knows the destination but not your IP.

No trust in any one operator required. That is a categorically different guarantee — and
it's why "Tor is slower" is a price, not a flaw.

**The tradeoff:** Tor's protection weakens against an adversary who can watch large parts of
the internet at once and correlate traffic timing at both ends. Mullvad's DAITA feature
(Defense Against AI-guided Traffic Analysis, added 2024) pads traffic to resist a related
class of attack on the VPN side.

---

## The anonymity-set nuance

A common counterintuitive point: **fingerprint resistance works better the more people share
your fingerprint.** Tor Browser has more users than Mullvad Browser, so "I am a Tor Browser
user" narrows you down less than "I am a Mullvad Browser user."

But this cuts both ways. With Mullvad Browser you are one of a smaller browser population —
while with Tor you are visibly *using Tor*, which is itself a signal some networks flag.
Neither is strictly better; it depends on whether standing out as a Tor user is a problem
where you are.

---

## Should you run Tor Browser *through* a VPN?

Short answer: **no, not by default.**

The Tor Project's own guidance is that combining Tor with a VPN is unnecessary for most
people and can *hurt* if you configure it wrong. Reasons:

- Tor Browser is tuned as a complete system. Adding a VPN changes its assumptions.
- "VPN → Tor" means Mullvad sees you connect to Tor (they already can't see more than that)
  and Tor's guarantees are unchanged. You gained very little.
- "Tor → VPN" is worse: it gives the VPN a persistent identifier tied to your Tor traffic and
  breaks Tor's exit diversity. Don't.

The one legitimate use of VPN→Tor is **hiding from your ISP that you use Tor at all** — in a
country where Tor use is itself dangerous. Even then, Tor's own **bridges** (especially
obfs4 or Snowflake) are the purpose-built solution and are usually the better choice.

**Mullvad Browser, on the other hand, is explicitly designed to be used with a VPN.** That
combination is the intended configuration, not a hack.

---

## Decision guide

**Use Mullvad Browser + Mullvad VPN if:**
- You want to stop being tracked, profiled and advertised at
- You want your ISP out of your browsing history
- You need speed — video, large downloads, normal web apps
- Sites blocking you would be a dealbreaker
- You are comfortable trusting one audited company

**Use Tor Browser if:**
- You are a journalist, researcher, activist, or source
- You need `.onion` services
- You are in a country that censors the internet
- The consequence of being identified is serious
- It genuinely matters that *no single party* can link you to your traffic

**Use both:** honestly, this is the right answer for most people. Mullvad Browser is your
daily driver; Tor Browser is the one you open when it matters. They install side by side and
don't conflict.

**Go further** — Tails or Whonix — if your threat model includes a targeted adversary with
resources. See [going-further.md](going-further.md).

---

## For the video: the honest framing

If you want one line that's accurate and doesn't oversell:

> "Mullvad VPN plus Mullvad Browser makes you *unremarkable* — hard to track, hard to
> profile, boring to advertisers. Tor Browser makes you *anonymous* — nobody can connect the
> traffic to you at all. The first one you can use all day. The second one you use when it
> matters."

And the correction worth making, because most videos get it wrong:

> "A VPN doesn't delete your IP address. Mullvad still receives your traffic — they just
> don't keep records of it. You've swapped trusting your ISP for trusting Mullvad. That's a
> real upgrade, but it's a trade, not magic. Tor is the version where you don't have to
> trust anyone."
