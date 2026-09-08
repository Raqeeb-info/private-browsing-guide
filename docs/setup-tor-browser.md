# Setting up Tor Browser

*Verified against Tor Browser 15.0.21, September 2026.*

## 1. Download

Official source — **only** this one: <https://www.torproject.org/download/>

- **Windows:** portable .exe
- **macOS:** .dmg
- **Linux:** .tar.xz
- **Android:** from the Tor Project site, Google Play, or F-Droid

There is **no official Tor Browser for iOS.** Apple requires all browsers to use WebKit, so a
real port is not possible. The Tor Project points iOS users to **Onion Browser**, which is
maintained independently and is not equivalent. Treat iOS as a weaker platform for this.

**If torproject.org is blocked where you are**, use an official mirror:

- GetTor by email: send a mail to gettor@torproject.org with your OS name in the body
- Official mirrors: <https://tor.eff.org/> or <https://lacebolla.net/>
- GetTor Telegram bot: <https://t.me/gettor_bot>

Never download Tor Browser from a third-party site, an unfamiliar app store, or a link in a
video description that is not torproject.org. Backdoored Tor Browser builds are a real,
documented attack.

Verify the signature — see [verify-downloads.md](verify-downloads.md). For Tor Browser this
matters more than for anything else you will install.

## 2. First launch

You get a connection screen with two options:

- **Connect** — normal. Use this if Tor is not blocked on your network.
- **Configure connection** — for censored networks. Use bridges, below.

**"Always connect automatically"** is convenient but means Tor starts before you have decided
you want it running. Fine at home; think twice on a monitored network.

## 3. Bridges, if Tor is blocked

If your ISP, country, or network blocks Tor, you need a bridge: an unlisted entry point.

In **Settings → Connection → Bridges**, pick a built-in bridge:

- **obfs4** — makes Tor traffic look like random noise. Good general choice.
- **snowflake** — routes through volunteer browsers over WebRTC. Very effective against
  sophisticated blocking, because the volunteer pool changes constantly.
- **meek-azure** — domain-fronts through a major CDN. Slow, but very hard to block without
  breaking a lot of other things.

If built-in bridges are also blocked, request private ones at
<https://bridges.torproject.org/> or email bridges@torproject.org from a Gmail or Riseup
address.

## 4. The security level slider

Shield icon in the toolbar, or Settings → Privacy and Security.

- **Standard** — all features on. Least protected. Low-risk browsing only.
- **Safer** — JavaScript off on non-HTTPS sites, media click-to-play, JIT disabled.
- **Safest** — JavaScript off everywhere, no media, no non-essential fonts or icons.

**Recommendation:** if you are using Tor Browser at all, you probably have a reason. Run at
**Safer** minimum. Use **Safest** for anything genuinely sensitive — most browser exploits
historically used against Tor users went through JavaScript.

## 5. Circuits and identity

- **New Identity** (hamburger menu, or Ctrl+Shift+U) — closes everything, clears all state,
  builds fresh circuits. Use this between separate activities. It is a full reset.
- **New Circuit for this Site** (Ctrl+Shift+L) — new route for the current site only. Use
  when an exit node is blocked or slow.
- The **circuit display** (click the padlock) shows your three relays and their countries.
  Worth showing on camera — it makes the three-hop concept concrete.

## 6. Onion services

Addresses ending in .onion only resolve inside Tor. They never leave the Tor network, so
there is no exit node and no exit-node risk.

- **Onion-Location** — some sites advertise an onion version, and Tor Browser shows a purple
  ".onion available" button. Use it.
- Legitimate onion services you can demo: DuckDuckGo, ProPublica, the BBC, the New York
  Times, Debian, and the Tor Project itself all run them.

Onion addresses are long random strings by design (v3 addresses are 56 characters). There is
no DNS, so you have to get the address from a source you trust. Onion phishing with
near-identical addresses is common.

## 7. Rules

1. **Do not install extensions.** Same reason as Mullvad Browser, more so.
2. **Do not maximize the window.** Tor Browser opens at a deliberately common size.
3. **Do not log into personal accounts.** This is the number one deanonymization mistake.
4. **Do not open downloaded files while online.** A PDF or DOC can phone home outside Tor and
   reveal your real IP. Open them offline, or in a VM.
5. **Do not enable JavaScript on a site just to make it work** if the site matters.
6. **Do not torrent over Tor.** BitTorrent clients leak your real IP regardless of proxy
   settings, and it wrecks the network for everyone else.
7. **Do not use Tor Browser for your normal logged-in life** and expect anonymity elsewhere.

## 8. Verify

- <https://check.torproject.org/> — confirms you are routing through Tor
- Click the padlock to see the circuit
- <https://coveryourtracks.eff.org/> — fingerprint check
