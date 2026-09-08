# Video outline

A structure for the video, built around the accurate framing rather than the usual
"VPN = invisible" script. Roughly 12–15 minutes at a normal pace.

---

## Cold open (0:00–0:30)

Show a site fingerprinting you in real time — <https://coveryourtracks.eff.org/> in a normal
browser. Point at the result: "This is you. Not your IP — you. Change your IP, use incognito,
clear your cookies: this stays the same."

Hook: "Everyone tells you to get a VPN. A VPN fixes about a third of this. Here is the rest."

---

## Part 1 — The two problems (0:30–3:00)

The framing that makes everything else make sense:

1. **The network knows who you are.** ISP sees every domain. Sites see your IP.
2. **The browser tells on you.** Fingerprint: screen size, fonts, GPU, timezone, extensions.

Most guides only solve #1 and call it privacy. Show incognito mode failing the fingerprint
test to make the point.

---

## Part 2 — Fixing the network half (3:00–6:00)

Mullvad VPN. Cover:

- Signup with no email, no name — just a generated number. **Show this on screen**, it is
  genuinely surprising to people.
- €5/month flat, no fake discounts
- Cash and Monero accepted
- Audits, RAM-only servers
- Settings that matter: kill switch, auto-connect, DAITA, quantum-resistant tunnel

**The honest bit that will set your video apart:** "Mullvad still receives your traffic.
They have to, to route it. What you have done is swap trusting your ISP — which sells data
as a business — for trusting a company whose entire model depends on not knowing who you
are. That is a real upgrade. It is not the same as being anonymous."

---

## Part 3 — Fixing the browser half (6:00–9:00)

Mullvad Browser. Cover:

- Made by Mullvad **and the Tor Project** together
- It is literally Tor Browser with the Tor part removed — show that both ship the same
  version number
- What it does out of the box: resistFingerprinting, letterboxing, uBlock, no telemetry,
  nothing written to disk
- The security slider — recommend Safer

Then re-run the fingerprint test. Show the difference. This is your payoff shot.

---

## Part 4 — Tor Browser, and when you actually need it (9:00–12:00)

The three-hop explanation, using the circuit display in the browser as your visual:

- Guard knows your IP, not your destination
- Middle knows neither
- Exit knows the destination, not your IP

"With a VPN, one company could theoretically know both halves. With Tor, no single relay
can. That is the difference, and that is what you are paying for with the slowness."

Cover: security slider, New Identity, onion services, bridges for censored networks.

**The correction most videos get wrong:** do not chain Tor Browser through your VPN by
default. The Tor Project advises against it, it is unnecessary, and configured backwards it
makes things worse. Mullvad Browser is the one designed for VPN use. If your problem is that
your ISP can see you use Tor, the built-in bridges are the actual solution.

---

## Part 5 — The mistakes (12:00–14:00)

Fast-paced list. This is the most useful section for your viewers:

1. Logging into a real account inside your private browser — kills everything instantly
2. Free VPNs — you are the product
3. Installing extensions — you just became unique
4. Maximizing the window — leaks your exact screen size
5. Opening downloaded PDFs while online — they phone home outside the tunnel
6. Torrenting over Tor — leaks your real IP anyway, and wrecks the network

---

## Close (14:00–15:00)

The two-browser habit as the actual takeaway:

- Hardened browser for private browsing, nothing logged in
- Normal browser for your real life

"Mullvad Browser plus a VPN makes you unremarkable. Tor makes you anonymous. Most people
need the first one every day and the second one occasionally. And no tool on earth protects
you from logging into your own email."

Point at this repo in the description.

---

## Things to get right on camera

- Verify a signature on screen, even briefly. Almost nobody shows this and it is the step
  that stops people installing backdoored builds.
- Do not claim a VPN makes you anonymous.
- Do not claim Tor is unbreakable — mention traffic correlation by a global adversary.
- Mention that Mullvad refuses affiliate and sponsorship deals, so nobody is paid to
  recommend it. It explains why it keeps coming up in honest recommendations, and it
  pre-empts "this is sponsored" comments.
