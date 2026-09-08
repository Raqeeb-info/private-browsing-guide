# What this setup defends against

Mullvad VPN + Mullvad Browser is a strong, practical, everyday privacy setup. It is not
universal armour. Knowing exactly where the line sits keeps you from either over-building or
trusting it further than it goes.

---

## Covered well

| Adversary | What they want | Why this setup stops them |
|---|---|---|
| **Advertisers and data brokers** | Fingerprint you, correlate across sites, sell the profile | Layer 2 makes you identical to other Mullvad Browser users; Layer 1 removes the IP as a join key |
| **Your ISP** | Log and sell your browsing history | Layer 1 encrypts everything; they see one tunnel to Mullvad |
| **Websites you visit** | Your IP, location, and a stable identifier | Layer 1 gives a shared Mullvad IP; Layer 2 gives a generic fingerprint |
| **Ad and analytics networks embedded in pages** | Follow you site to site | First-party isolation, no persistent storage, uBlock Origin |
| **Public Wi-Fi snooping** | Intercept traffic, spoof DNS | Layer 1 encrypts the whole connection including DNS |
| **Casual network monitoring** at work, school, or home | See which sites you visit | Layer 1, provided they do not control the device itself |

If your concern is on this list — and for most people it is all of it — this setup is
genuinely sufficient. Install it, follow the rules, stop worrying.

---

## Partly covered

**Legal requests to Mullvad.** Mullvad's defence is that there is nothing to hand over: no
account identity, no logs, RAM-only servers. This has been tested in practice: on 18 April
2023, officers from the Swedish police National Operations Department arrived at Mullvad's
office with a search warrant for customer data, and left with nothing after Mullvad
demonstrated that the data does not exist
([Mullvad's account](https://mullvad.net/en/blog/2023/4/20/mullvad-vpn-was-subject-to-a-search-warrant-customer-data-not-compromised)).
Strong evidence — but it is an architecture and a policy, not a mathematical guarantee.

**A single well-positioned observer.** Someone who can watch both your connection to Mullvad
and Mullvad's connection to a website could in principle correlate the timing. Mullvad's
DAITA feature (Defense Against AI-guided Traffic Analysis) pads and reshapes traffic
specifically to make this harder. Turn it on.

**Someone who controls your device.** Employer-managed laptops, school machines, or anything
with monitoring software installed. Nothing at the browser or network level helps here,
because the observation happens before encryption.

---

## Not covered

**You logging into your own accounts.** Open Gmail in Mullvad Browser and Google knows
exactly who you are. Both layers become irrelevant in that instant. This is by far the most
common failure, and no tool can prevent it.

**Anything you type.** Reused usernames, your city, your job, your posting hours, your
writing style. Stylometry works. Technical identifiers get the attention; behavioral ones do
most of the real deanonymization.

**Malware or a compromised OS.** Keyloggers and infostealers see everything before the
browser encrypts it.

**A targeted, well-resourced adversary.** A state actor specifically interested in you is a
different threat model requiring different tools and, more importantly, different habits.

**Illegal activity.** These are privacy tools, not immunity. Nothing here is designed for or
adequate to that purpose.

---

## Deciding how far to go

Ask what the cost of failure actually is:

- **Annoying** — targeted ads, price discrimination, a creepy recommendation feed
  → **This setup is exactly right.**
- **Embarrassing** — someone seeing your browsing history
  → **This setup, plus real discipline about not logging in.**
- **Professionally damaging** — a source exposed, research attributed to you
  → **You need Tor's guarantee**, where no single party can link you to your traffic. See
  [going-further.md](going-further.md).
- **Physically dangerous** — activist or journalist under a hostile government
  → **Tails or Whonix**, and read the primary operational security literature rather than any
  single guide, including this one.

---

## Two ways people get this wrong

**Under-building:** a VPN with normal Chrome, logged into Google, believing it is private.
The VPN changed one signal out of thirty. The fingerprint and the Google session identify
you completely. This is the most common setup in the world and it barely helps.

**Over-building:** running Tails on a burner laptop to avoid targeted advertising. You needed
uBlock Origin and a VPN, and the extra effort you will abandon in a week protects nobody.

A setup you actually maintain beats a stricter one you give up on. Pick the level that
matches the real risk.
