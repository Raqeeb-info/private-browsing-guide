# Verifying downloads

*Fingerprints verified against the official documentation, September 2026.*

Skipping this step is the most common way a "privacy setup" turns into a compromised
machine. A backdoored Tor Browser build is a documented, real-world attack — attackers have
distributed modified copies through fake mirrors and search ads. Signature verification is
how you know the file came from the people who wrote it.

It takes about three minutes. Do it.

---

## Install GnuPG

- **Windows:** <https://gpg4win.org/> (or `winget install GnuPG.Gpg4win`)
- **macOS:** <https://gpgtools.org/> or `brew install gnupg`
- **Linux:** usually preinstalled, otherwise `apt install gnupg` / `dnf install gnupg2`

---

## Verifying Tor Browser

Note: **Mullvad Browser is signed with the same key**, because it is built by the Tor
Project. One key covers both browsers.

**Key fingerprint:**

```
EF6E 286D DA85 EA2A 4BA7 DE68 4E2C 6E87 9329 8290
```

Subkey (the one that actually signs releases):

```
CAAE 408A EBE2 288E 96FC 5D5E 1574 32CF 78A6 5729
```

### Steps

1. Download the installer **and** the matching `.asc` signature file from the same page.
   Put both in the same folder.

2. Fetch the signing key:

```bash
gpg --auto-key-locate nodefault,wkd --locate-keys torbrowser@torproject.org
```

3. Check the fingerprint you just imported matches the one printed above — read it
   character by character:

```bash
gpg --fingerprint --fingerprint torbrowser@torproject.org
```

Passing `--fingerprint` twice also shows the subkey fingerprint.

4. Verify the file:

```bash
gpg --verify tor-browser-windows-x86_64-portable-15.0.21.exe.asc
```

Substitute your actual filename.

---

## Verifying Mullvad Browser

Identical process, same key. The signature link is on the download page, or on the GitHub
release next to the installer.

```bash
gpg --verify mullvad-browser-windows-x86_64-15.0.21.exe.asc
```

---

## Verifying the Mullvad VPN app

Different key — this one is Mullvad's own.

**Key fingerprint:**

```
A119 8702 FC3E 0A09 A9AE 5B75 D5A1 D4F2 66DE 8DDF
```

1. Download the app and its `.asc` signature from
   <https://mullvad.net/en/download/vpn/> (each platform page has a signature link).

2. Import the key:

```bash
gpg --keyserver hkps://keys.openpgp.org --recv-keys A1198702FC3E0A09A9AE5B75D5A1D4F266DE8DDF
```

3. Verify:

```bash
gpg --verify MullvadVPN-2026.4.exe.asc
```

---

## Reading the output

**Good:**

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

Delete the file. Do not run it. Re-download from the official site, and consider that
something on your network or machine may be interfering.

---

## The fingerprint problem

There is a bootstrapping issue worth naming honestly, especially in a video: you are reading
the fingerprint from the same website you downloaded the file from. If an attacker fully
controls that site, they control both.

In practice this is still a large improvement, because it forces the attacker to compromise
the website's TLS *and* the distribution *and* keep the two consistent — rather than just
seeding a fake mirror or buying a search ad.

To do better, cross-check the fingerprint against an independent source: the Tor Project's
GitLab, the Mullvad GitHub repository, an archived copy of the page from a different date,
or a copy someone else published years ago. If several independent sources agree, the key is
almost certainly real.
