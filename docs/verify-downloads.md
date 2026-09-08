# Verifying downloads

*Fingerprints verified against the official documentation, September 2026.*

Skipping this step is the most common way a "privacy setup" turns into a compromised machine.
Attackers distribute modified builds of privacy software through fake mirrors and search ads,
and the modified copy looks and works exactly like the real one. Signature verification is
how you know the file came from the people who wrote it.

It takes about three minutes per file. Do it for both layers.

---

## Install GnuPG

- **Windows:** <https://gpg4win.org/> (or `winget install GnuPG.Gpg4win`)
- **macOS:** <https://gpgtools.org/> or `brew install gnupg`
- **Linux:** usually preinstalled, otherwise `apt install gnupg` / `dnf install gnupg2`

---

## Layer 1 — verifying the Mullvad VPN app

**Key fingerprint** — Mullvad's own code signing key:

```
A119 8702 FC3E 0A09 A9AE 5B75 D5A1 D4F2 66DE 8DDF
```

1. Download the app **and** its `.asc` signature from
   <https://mullvad.net/en/download/vpn/> — each platform page has a signature link next to
   the installer. Put both files in the same folder.

2. Import the key:

```bash
gpg --keyserver hkps://keys.openpgp.org --recv-keys A1198702FC3E0A09A9AE5B75D5A1D4F266DE8DDF
```

3. Check the fingerprint you imported matches the one above, character by character:

```bash
gpg --fingerprint admin@mullvad.net
```

4. Verify:

```bash
gpg --verify MullvadVPN-2026.4.exe.asc
```

Substitute your actual filename. You want `Good signature from "Mullvad (code signing)"`.

---

## Layer 2 — verifying Mullvad Browser

**Different key.** Mullvad Browser is signed by the **Tor Browser Developers** key, because
the Tor Project co-develops and builds it. This surprises people, and it is correct — if you
see this key, you have the right file.

**Key fingerprint:**

```
EF6E 286D DA85 EA2A 4BA7 DE68 4E2C 6E87 9329 8290
```

Subkey (the one that actually signs releases):

```
CAAE 408A EBE2 288E 96FC 5D5E 1574 32CF 78A6 5729
```

1. Download the installer **and** its `.asc` signature from
   <https://mullvad.net/en/download/browser/> or from the
   [GitHub release](https://github.com/mullvad/mullvad-browser/releases). Same folder.

2. Fetch the signing key:

```bash
gpg --auto-key-locate nodefault,wkd --locate-keys torbrowser@torproject.org
```

3. Check the fingerprint against the values above. Passing `--fingerprint` twice also shows
   the subkey:

```bash
gpg --fingerprint --fingerprint torbrowser@torproject.org
```

4. Verify:

```bash
gpg --verify mullvad-browser-windows-x86_64-15.0.21.exe.asc
```

---

## Reading the output

**Good:**

```
gpg: Good signature from "Mullvad (code signing) <admin@mullvad.net>"
```

```
gpg: Good signature from "Tor Browser Developers (signing key) <torbrowser@torproject.org>"
```

**This warning is normal and fine:**

```
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
```

It only means you have not personally marked the key as trusted in your keyring. The
signature itself is valid. What matters is that you compared the fingerprint against the
official documentation.

**Stop immediately if you see:**

```
gpg: BAD signature from ...
```

Delete the file. Do not run it. Re-download from the official site, and treat it as a sign
that something on your network or machine may be interfering.

---

## The fingerprint problem

Worth naming honestly, especially if you are explaining this to other people: you are reading
the fingerprint from the same website you downloaded the file from. If an attacker fully
controls that site, they control both.

In practice this is still a large improvement, because it forces an attacker to compromise
the website's TLS *and* the distribution *and* keep the two consistent — rather than simply
seeding a fake mirror or buying a search ad, which is what actually happens in the wild.

To do better, cross-check each fingerprint against an independent source: the
[Mullvad GitHub org](https://github.com/mullvad), the Tor Project's GitLab, an archived copy
of the page from a different date, or a copy someone published years ago. If several
independent sources agree, the key is almost certainly real.
