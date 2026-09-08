# Start here: what are you actually defending against?

Every privacy decision downstream of this depends on the answer. Building for the wrong
threat model means you either waste effort or leave the real hole open.

Ask three questions.

## 1. Who is the adversary?

| Adversary | What they can do | What stops them |
|---|---|---|
| **Advertisers / data brokers** | Fingerprint your browser, correlate across sites, buy your data | Fingerprint-resistant browser. VPN helps. |
| **Your ISP** | See every domain you visit, sell that data, hand it to authorities | VPN or Tor. Encrypted DNS helps but isn't enough alone. |
| **Websites you visit** | Log your IP, fingerprint, behavior; link accounts | VPN/Tor + fingerprint resistance + not logging in |
| **Public Wi-Fi snoop** | Intercept unencrypted traffic, spoof DNS | VPN (or just HTTPS, mostly) |
| **Your employer / school / family network** | Monitor the network, install monitoring software | VPN. If they control the *device*, nothing browser-level helps. |
| **A national censor** | Block Tor and VPN protocols, monitor who connects | Tor bridges (obfs4/Snowflake), VPN obfuscation |
| **A targeted, well-resourced adversary** | Traffic correlation, legal pressure, malware, device seizure | Tails/Whonix + operational discipline. Browser choice is a small part. |

Most people making a "browse privately" setup are defending against rows 1–4. That's the
Mullvad Browser + Mullvad VPN sweet spot.

## 2. What is the cost of failure?

- **Annoying** (targeted ads, price discrimination) → VPN + hardened browser is plenty
- **Embarrassing** (browsing history exposed) → same, plus discipline about accounts
- **Professionally damaging** (source burned, research exposed) → Tor Browser
- **Physically dangerous** (activist under a hostile government) → Tails, and read the real
  operational security literature, not a YouTube video

## 3. What are you willing to live with?

Privacy has real costs. Being honest about them upfront means you actually stick with the setup:

- Tor Browser is slow and breaks sites. You will not use it for everything.
- Fingerprint-resistant browsers block things. Some sites will misbehave.
- Not logging into accounts is the single most effective step and the hardest one to keep.
- A VPN costs money — and free VPNs monetize you, which defeats the entire purpose.

A setup you abandon after a week protects nobody. Pick the level you'll actually maintain.

---

## Common mismatches

**Over-building:** Running Tails on a burner laptop to avoid targeted ads. You needed uBlock
Origin and a VPN.

**Under-building:** Using a VPN with regular Chrome, logged into Google, and believing you're
anonymous. Your fingerprint and your Google session identify you completely — the VPN changed
one variable out of thirty.

**The classic:** Using Tor Browser perfectly, then logging into a personal email account
inside it. Everything upstream is now pointless. This is the single most common way people
deanonymize themselves.

---

## Threat model → setup

```
Advertisers, trackers, ISP snooping
  → Mullvad VPN + Mullvad Browser
  → uBlock Origin (already included), no logins to real accounts

Above, plus you want anonymity for specific sessions
  → Same, plus Tor Browser for those sessions
  → Keep the two lives strictly separate

Journalist / researcher / source protection
  → Tor Browser as the default, not the exception
  → Consider Tails on a USB stick for sensitive work

Serious targeted risk
  → Tails or Whonix, amnesic by design
  → Compartmentalized identities, separate hardware
  → Read the primary sources; a guide like this one isn't enough
```

Once you know which row you're in, go to [browser-comparison.md](browser-comparison.md).
