# Video outline

Structured around the two-layer framing, which is both accurate and a better story than the
usual "get a VPN and you're invisible" script. Roughly 12–14 minutes at a normal pace.

The spine of the video: **two problems, two tools, one demo each.**

---

## Cold open (0:00–0:45)

Open <https://coveryourtracks.eff.org/> in your normal browser. Show the result.

Then do the thing that sells it: **turn on your VPN and reload.** The IP changes. The
fingerprint does not. Same result, same unique ID.

> "Everyone tells you to get a VPN. Watch what a VPN actually does to this — nothing. Your IP
> changed and the site still knows exactly which browser I am. There are two ways you get
> tracked online, and a VPN only fixes one of them."

That single demo is your whole video in fifteen seconds.

---

## Part 1 — The two problems (0:45–3:00)

Lay out the frame you will follow for the rest of the video.

**Problem 1 — the network knows who you are.** Your ISP sees every domain you visit, even
over HTTPS. Every site sees your IP: your city, your ISP, a stable identifier.

**Problem 2 — the browser tells on you anyway.** Screen size, timezone, fonts, GPU, canvas
rendering, extensions. Combined, usually unique among hundreds of millions of browsers.

The key point, said plainly:

> "Your fingerprint survives changing your IP. It survives incognito mode. It survives
> clearing cookies. It survives switching to your phone's hotspot. That's why the VPN alone
> did nothing."

Analogy that lands: **a VPN is a mask; a fingerprint is your name tag.** Most people are
wearing the mask with the name tag still on.

---

## Part 2 — Layer 1: Mullvad VPN (3:00–6:30)

Fixes Problem 1.

Show the signup, because it genuinely surprises people:

- No email. No name. Click a button, get a 16-digit number. **Film this.**
- €5/month flat, whether you buy a month or ten years. No countdown timers, no fake discounts.
- Cash in an envelope is an accepted payment method. So is Monero.
- Audited, RAM-only servers, open source clients.
- In April 2023 Swedish police showed up with a search warrant and left with nothing, because
  the data does not exist. That is a better trust argument than any marketing page.

Settings that matter, on screen: **kill switch**, auto-connect, **DAITA**,
quantum-resistant tunnel.

Then verify: <https://mullvad.net/check> and <https://browserleaks.com/dns>.

**The honest bit that will set your video apart:**

> "Mullvad still receives your traffic. They have to — that's how routing works. What you've
> done is swap trusting your ISP, a company that sells browsing data as a business, for
> trusting one whose whole model depends on not knowing who you are. That's a real upgrade.
> It's not the same as being anonymous, and anyone telling you otherwise is selling something."

---

## Part 3 — Layer 2: Mullvad Browser (6:30–10:00)

Fixes Problem 2. This is the half most videos skip entirely, so make it the centrepiece.

- Co-developed by **Mullvad and the Tor Project** — it is Tor Browser's fingerprint hardening
  with the Tor network removed, because it assumes a VPN instead. Show that both ship the
  same version number. Good detail, nobody knows it.
- What it does out of the box: spoofed timezone and screen metrics, letterboxing, blocked
  canvas and WebGL, bundled fonts, uBlock Origin, no telemetry, nothing written to disk.

The idea worth explaining slowly, because it is counterintuitive:

> "It doesn't hide your fingerprint. It gives you the *same* fingerprint as everyone else
> using it. The protection isn't in the browser — it's in the crowd. Which is exactly why
> you don't customize it."

Then the payoff: **re-run Cover Your Tracks in Mullvad Browser** and put it side by side with
the cold open. This is your money shot — same machine, same network, different verdict.

Cover the security slider and recommend **Safer**.

---

## Part 4 — The rules (10:00–12:30)

Fast-paced. The most genuinely useful section for viewers.

1. **Don't log into real accounts in it.** One Gmail login and both layers are pointless.
   This is number one for a reason.
2. **Don't install extensions.** You just made yourself unique inside the browser that exists
   to make you identical.
3. **Don't maximize the window.** Leaks your exact screen resolution.
4. **Don't use a free VPN.** You're not paying, so you're the product — several are owned by
   ad companies.
5. **Don't change settings to fix a broken site.** Open that site in your other browser.
6. **Don't skip signature verification.** Show yourself running `gpg --verify` on screen,
   even briefly. Almost nobody demonstrates this and it is what stops people installing
   backdoored builds.

---

## Close (12:30–14:00)

The two-browser habit as the real takeaway:

- **Mullvad Browser + Mullvad VPN** — private browsing, nothing logged in
- **A normal browser** — email, banking, shopping, your actual logged-in life

> "Two problems, two tools. The VPN hides your IP. The browser hides your fingerprint. You
> need both, because either one alone leaves the other door wide open. And no tool on earth
> protects you from logging into your own email."

Point at the repo in the description.

---

## Things to get right on camera

- **Do** show the fingerprint test before and after — it is the entire argument, visually.
- **Do** say a VPN moves trust rather than eliminating it.
- **Don't** say "anonymous." Say "untrackable across sites," which is true.
- **Don't** chain Tor Browser through the VPN if you mention Tor. The Tor Project advises
  against it. Mullvad Browser is the one built for VPN use — that distinction is the whole
  reason both browsers exist.
- **Do** mention that Mullvad refuses affiliate programs and influencer sponsorships. It
  explains why it keeps appearing in honest recommendations, and it pre-empts every
  "this is sponsored" comment before it is written.
