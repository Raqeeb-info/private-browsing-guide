# The mistakes that undo everything

You can have a perfect VPN and a perfectly hardened browser and still be identified in about
four seconds. These are the ways it happens, roughly in order of how often they do.

---

## 1. Logging into an account tied to your real name

**The mistake:** opening Gmail, Facebook, Instagram, Amazon, or anything else with your real
identity inside your private browser.

**Why it kills you:** the site now has a session cookie linked to *you*. Your IP and
fingerprint are irrelevant — you told them who you are. Worse, that session can be correlated
with every other page you visit while logged in, and with the ad and analytics networks
embedded in those pages.

**Fix:** hard separation. One browser for anonymous browsing, a different browser for your
logged-in life. Never cross the streams. If you slip, close the browser, clear everything,
and treat that session as burned.

---

## 2. Free VPNs

**The mistake:** using a free VPN, or a heavily discounted one from a YouTube sponsor read.

**Why it kills you:** running VPN infrastructure costs real money. If you are not paying,
your data is the revenue. Multiple free VPNs have been caught logging, injecting ads,
selling bandwidth, or shipping outright malware. Several are quietly owned by companies whose
main business is advertising analytics.

**Fix:** pay for a provider with a published, audited no-logs policy. Mullvad, IVPN, and
Proton VPN are the usual reputable picks. €5/month is the real price.

---

## 3. Installing extensions in a hardened browser

**The mistake:** adding your favourite password manager, dark mode extension, or a second
ad blocker to Mullvad Browser or Tor Browser.

**Why it kills you:** fingerprint resistance works by making everyone look identical. Every
extension you add makes you *different*. Extensions are detectable from a web page — through
injected DOM elements, resources they expose, or timing. Two or three unusual extensions is
often enough to be globally unique.

**Fix:** use what ships with the browser. uBlock Origin is already there. If you need a
password manager, keep it in your other browser.

---

## 4. Maximizing the window

**The mistake:** hitting the maximize button out of habit.

**Why it kills you:** your window's inner dimensions are readable by JavaScript. Maximized
means your exact screen resolution, minus your exact taskbar height and browser chrome. That
is a strong identifier, and it persists across IP changes.

**Fix:** leave the default window size. Letterboxing mitigates it by rounding dimensions to
common values, but the default is still the safest.

---

## 5. Trusting the VPN too much

**The mistake:** thinking "no logs" means "nobody can ever know."

**Why it matters:** Mullvad receives your packets. They must, in order to route them. Their
protection is a policy backed by audits, RAM-only servers, and a business model that does not
need your identity. That is genuinely strong. It is not the same as *cryptographic*
impossibility, which is what Tor gives you.

**Fix:** be accurate about what you have. Say "my ISP cannot see my browsing and websites
cannot see my IP" — not "I am anonymous."

---

## 6. DNS leaks

**The mistake:** setting a custom DNS server, or using a VPN client that does not route DNS.

**Why it kills you:** DNS queries reveal every domain you visit. If they go outside the
tunnel, your ISP has your full browsing history regardless of the VPN.

**Fix:** leave Mullvad's DNS settings alone, and test at <https://browserleaks.com/dns>. Do not
"improve" it by pointing at Google DNS — that hands your history to an ad company.

---

## 7. Opening downloaded files while connected

**The mistake:** downloading a PDF or DOCX in Tor Browser and double-clicking it.

**Why it kills you:** these formats can fetch remote resources. Your PDF reader or Word is
not routed through Tor, so it connects directly — revealing your real IP to whoever made the
document. This is a known, actively used technique.

**Fix:** disconnect from the internet before opening, or open in a VM, or use Tails which
handles this for you.

---

## 8. Torrenting over Tor or a leaky VPN

**The mistake:** running BitTorrent through Tor.

**Why it kills you:** BitTorrent clients frequently send your real IP inside the protocol
itself, regardless of proxy settings. It also consumes enormous amounts of volunteer-donated
Tor bandwidth, degrading the network for people who need it.

**Fix:** do not torrent over Tor. If you torrent, use a VPN that supports it, with a kill
switch, and bind the client to the VPN interface.

---

## 9. Your writing and your habits

**The mistake:** assuming technical anonymity is the whole problem.

**Why it kills you:** stylometry is real and effective. So is reusing a username, mentioning
your city, posting at consistent local hours, referencing a job, or uploading a photo with
EXIF data. Technical identifiers get all the attention; behavioral ones do most of the work.

**Fix:** if it genuinely matters, do not reuse usernames, strip metadata from files, watch
what you disclose, and be aware that your writing style is itself an identifier.

---

## 10. Believing a single tool is enough

**The mistake:** "I have a VPN, I am private."

**Why it kills you:** a VPN changes one variable. Your browser fingerprint, your cookies,
your logins, your DNS, your behavior, and your OS all still identify you. Privacy is a stack,
and it fails at the weakest layer.

**Fix:** VPN plus hardened browser plus discipline about accounts. All three, or none of them
matter much.

---

## The one-sentence version

**Technical tools protect you from the network. Nothing protects you from yourself.**
