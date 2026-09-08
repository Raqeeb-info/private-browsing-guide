# The mistakes that undo both layers

You can have Layer 1 and Layer 2 set up perfectly and still be identified in about four
seconds. These are the ways it happens, roughly in order of how often they do.

---

## 1. Logging into an account tied to your real name

**Breaks:** both layers, instantly.

**The mistake:** opening Gmail, Facebook, Instagram, Amazon, or anything with your real
identity inside Mullvad Browser.

**Why it kills you:** the site now has a session cookie linked to *you*. Your IP and your
fingerprint are irrelevant — you told them who you are. Worse, that session can be correlated
with every other page you visit while logged in, and with the ad and analytics networks
embedded in those pages.

**Fix:** hard separation. Mullvad Browser for private browsing, a completely different
browser for your logged-in life. Never cross the streams. If you slip, close the browser,
clear everything, and treat that session as burned.

---

## 2. Using a free VPN instead of Layer 1

**Breaks:** Layer 1, and worse than having no VPN at all.

**Why it kills you:** running VPN infrastructure costs real money. If you are not paying,
your data is the revenue. Multiple free VPNs have been caught logging, injecting ads, selling
users' bandwidth, or shipping outright malware. Several are quietly owned by companies whose
main business is advertising analytics — so you routed *all* your traffic through an ad
company on purpose.

**Fix:** €5/month is the real price. Pay it.

---

## 3. Installing extensions in Mullvad Browser

**Breaks:** Layer 2, comprehensively.

**Why it kills you:** fingerprint resistance works by making everyone look identical. Every
extension you add makes you *different*. Extensions are detectable from a web page — through
injected DOM elements, resources they expose, or timing. Two or three unusual extensions is
often enough to be globally unique, which means you have defeated the entire point of the
browser.

**Fix:** use what ships with it. uBlock Origin is already installed, and everyone else has
it too, which is exactly why it is safe. If you need a password manager, keep it in your
other browser.

---

## 4. Maximizing the window

**Breaks:** Layer 2.

**Why it kills you:** your window's inner dimensions are readable by JavaScript. Maximized
means your exact screen resolution, minus your exact taskbar height and browser chrome. That
is a strong identifier and it persists across IP changes, so it defeats Layer 1 too.

**Fix:** leave the default window size. Letterboxing mitigates it by rounding dimensions to
common values, but the default size is still the safest.

---

## 5. Running one layer and thinking you are done

**Breaks:** whichever half you skipped.

**The mistake:** "I have a VPN, I'm private." Or: "I use a hardened browser, I'm fine."

**Why it kills you:** a VPN with a normal browser leaves you fully fingerprintable — sites
recognize you across every IP you ever use. A hardened browser with no VPN leaves your real
IP and your ISP's full view of your browsing intact.

**Fix:** both. That is the whole premise of this repo.

---

## 6. Trusting Layer 1 too much

**Breaks:** your understanding, which eventually breaks your behavior.

**The mistake:** thinking "no logs" means "nobody can ever know."

**Why it matters:** Mullvad receives your packets. They must, in order to route them. Their
protection is a policy backed by audits, RAM-only servers, and a business model that does not
need your identity — and it has survived a real police search. That is genuinely strong. It
is not the same as *cryptographic* impossibility.

**Fix:** be accurate about what you have. "My ISP can't see my browsing and websites can't
see my IP" — not "I'm anonymous."

---

## 7. DNS leaks

**Breaks:** Layer 1, silently.

**The mistake:** setting a custom DNS server, or using a VPN client that does not route DNS
through the tunnel.

**Why it kills you:** DNS queries reveal every domain you visit. If they go outside the
tunnel, your ISP has your full browsing history regardless of the VPN, and you will never
notice.

**Fix:** leave Mullvad's DNS settings alone and test at <https://browserleaks.com/dns>. Do
not "improve" it by pointing at Google DNS — that hands your history to an ad company.

---

## 8. Opening downloaded files while connected

**Breaks:** both layers, from outside the browser.

**The mistake:** downloading a PDF or DOCX and double-clicking it.

**Why it kills you:** these formats can fetch remote resources. Your PDF reader or Word is a
separate application — it is covered by the VPN, but it is not covered by the browser's
protections, and if the VPN ever drops it connects directly. Documents that phone home are an
actively used tracking technique.

**Fix:** make sure the kill switch is on. For anything sensitive, disconnect from the
internet before opening, or open it in a VM.

---

## 9. Turning off protections to fix a broken site

**Breaks:** Layer 2.

**The mistake:** a site misbehaves, so you drop the security level, allow scripts, or change
a privacy setting — and then leave it that way.

**Why it kills you:** every setting you change moves you further from the default
configuration everyone else has. Your customized browser is a fingerprint.

**Fix:** open that one site in your other browser instead. Never customize the private one.

---

## 10. Your writing and your habits

**Breaks:** everything, without touching the technology.

**Why it kills you:** stylometry is real and effective. So is reusing a username, mentioning
your city, posting at consistent local hours, referencing your job, or uploading a photo with
EXIF data intact.

**Fix:** if it genuinely matters, do not reuse usernames, strip metadata from files, and be
aware that your writing style is itself an identifier.

---

## The one-sentence version

**Layer 1 protects you from the network. Layer 2 protects you from the browser. Nothing
protects you from yourself.**
