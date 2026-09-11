# How the two layers work

The whole setup makes sense once you separate the two ways you get identified online. They
are genuinely independent problems, and each tool solves exactly one of them.

---

## Layer 1 — Mullvad VPN hides your IP

### What your IP address gives away

Every request your computer makes carries your IP address. From it, a website gets:

- Your approximate location — usually city-level, sometimes better
- Your ISP, and therefore an account with your real name behind a legal request
- A stable identifier that links every site you visit from that connection
- Enough for a data broker to join your activity across services

Separately, your **ISP sees every domain you connect to**, even over HTTPS. HTTPS encrypts
the *contents* of a page, not the fact that you asked for it. In many countries that history
is legally sellable, and in most it is retainable.

### What the VPN does

```
Without VPN:
  You ──────────────────────────────► Website
       ISP sees every domain          Site sees your real IP

With Mullvad VPN:
  You ══encrypted══► Mullvad ────────► Website
       ISP sees only                   Site sees a Mullvad IP,
       "traffic to Mullvad"            shared with many users
```

Your ISP now sees an encrypted tunnel to one address and nothing about what is inside it.
Websites see an IP belonging to a Mullvad server, used by many people at once.

### What it does not do

**It does not make you anonymous.** Mullvad receives your packets — that is how routing
works. Their protection is a no-logs *policy*, backed by third-party audits, RAM-only
servers with no disks to seize, and a business model that never asks who you are. That is
strong. It is trust, not mathematics.

**It does nothing about fingerprinting.** This is the important part, and it is why Layer 2
exists.

---

## Layer 2 — Mullvad Browser hides your fingerprint

### The thing most people don't know

Load a page and JavaScript can read, without asking permission:

| Signal | Example |
|---|---|
| Screen and window size | 2560x1440, window 1920x937 |
| Timezone | UTC+2 |
| Language and locale | en-GB, sv-SE |
| Installed fonts | your exact list, often hundreds |
| GPU model and driver | via WebGL |
| Canvas rendering | how your machine draws a hidden image, pixel for pixel |
| Audio stack | how your machine processes a generated tone |
| CPU cores, RAM | navigator.hardwareConcurrency |
| Extensions | detectable from injected elements and exposed resources |
| Battery, sensors, media devices | on some platforms |

Individually these are unremarkable. Combined, they are usually **unique among hundreds of
millions of browsers**. That combination is your fingerprint.

### Why it beats every other privacy measure

Your fingerprint survives:

- **Changing your IP** — a VPN changes one signal out of thirty
- **Incognito / private mode** — same hardware, same fonts, same GPU, same everything
- **Clearing cookies** — the fingerprint was never stored on your machine
- **Switching networks** — home, phone tethering, coffee shop: same fingerprint

This is precisely why a VPN alone is not private browsing. You changed your address; you did
not change your face.

### What the browser does

Mullvad Browser is built on Firefox ESR by **Mullvad together with the Tor Project**. It is
Tor Browser's fingerprint-resistance engineering with the Tor network removed, because it
assumes you have a VPN instead. It ships the same version numbers as Tor Browser because it
comes from the same codebase.

The strategy is **uniformity, not concealment.** You cannot hide that you have a screen size.
You *can* make sure your screen size is the same value everyone else reports.

| Technique | What it does |
|---|---|
| privacy.resistFingerprinting | Spoofs or standardizes timezone, locale, screen metrics, hardware details |
| Letterboxing | Rounds window dimensions to common values so resizing reveals nothing |
| Canvas / WebGL / audio blocking | Returns standardized or blocked results instead of hardware-specific ones |
| Bundled font list | Everyone reports the same fonts |
| uBlock Origin preinstalled | Everyone has the same extension, so it isn't a distinguishing signal |
| No telemetry, studies or crash reports | Nothing phones home |
| First-party isolation | Cookies and storage can't follow you between sites |
| No disk persistence | History and cookies gone on close |

### The counterintuitive part

**Fingerprint resistance works better the more people share your fingerprint.** This is why
"don't customize it" is the single most important rule in the browser doc. Install two
extensions and change your font size, and you have made yourself unique again — inside a
browser whose entire purpose was making you identical.

The protection is not in the browser. It is in the *crowd*. Do not leave the crowd.

---

## The pizza order

If you only remember one thing from this page, make it this.

You call the same pizza place every Friday. **You never give them your name.** You just order:

> Large. Thin crust. Half pepperoni, half mushroom. Extra garlic dip. No oregano.
> Cut into squares.

Every single one of those is ordinary. Hundreds of people order large. Hundreds order thin
crust. Extra garlic dip is on the menu for a reason.

But *that exact combination*? **You are the only person in the city who orders that.**

So the shop doesn't need your name. They have something better: they have the
square-cut-half-and-half-extra-garlic guy. You are a regular, and you never once told them who
you were. **That is your browser fingerprint.** Screen size, timezone, fonts, GPU, language —
each one boring, the combination unique.

### Now move house

New address. New phone number. You call and order the same thing.

*"Oh — it's you again."*

Your address changed. **Your order didn't.** That is exactly what a VPN does and does not do:
it changes where the delivery goes, not what you asked for. A new IP with the same fingerprint
is a new address with the same order, and the shop knows you the second you start talking.

Call from a blocked number if you like — that's incognito mode. Same order. Same guy.

### The only thing that actually works

You stop ordering *your* pizza. You order what everybody else orders: **plain medium cheese,
cut into normal slices.** Now you are one of four hundred identical orders that night, and
nobody can pick you out of them.

That is Mullvad Browser. It doesn't hide your order — it gives you *everyone else's order.*

And notice the cost, because it is the real one: **no extra garlic dip.** The protection only
works while your order is boring. The moment you ask for one custom thing, you are the garlic
guy again.

That is precisely why the rule in [Layer 2](2-mullvad-browser.md) is *don't install extensions
and don't resize the window.* Every tweak is another topping, and every topping puts you back
on the list.

---

## Why you need both

| Setup | IP hidden | Fingerprint hidden | Result |
|---|---|---|---|
| Normal browser, no VPN | No | No | Fully tracked |
| Normal browser + VPN | Yes | **No** | Recognized by fingerprint anyway |
| Mullvad Browser, no VPN | **No** | Yes | Can't be fingerprinted, but they have your IP |
| **Mullvad Browser + Mullvad VPN** | Yes | Yes | **The setup this repo describes** |

The second row is what most people actually have, and it is why they are surprised to learn
they are still tracked.

---

## What neither layer can fix

Both tools work at the technical level. Neither can help with:

- **Logging into an account with your real name.** You told the site who you are; the IP and
  fingerprint are now irrelevant. This is the number one way people undo the whole setup.
- **What you type** — usernames you reuse, personal details, writing style, posting hours.
- **Malware on your machine.** If the OS is compromised, browser hardening is decoration.
- **A global adversary** who can watch large parts of the internet at once.

See [common-mistakes.md](common-mistakes.md) for the full list.

---

Next: [Layer 1 — Mullvad VPN](1-mullvad-vpn.md), then [Layer 2 — Mullvad Browser](2-mullvad-browser.md)
