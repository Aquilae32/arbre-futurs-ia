# Verifying the authenticity of the AI Futures Tree, edition 2.2

This guide lets you check that edition 2.2 of the *Arbre des futurs de l'IA* (AI Futures Tree; Louis and Claude, by Anthropic, 1 November 2026) has not been altered, that Louis published it, and when.

## The files

| File | Purpose |
|---|---|
| `declaration-arbre-2.2.txt.asc` | Authenticity statement for the edition, signed by Louis (OpenPGP) |
| `declaration-arbre-2.2.txt.asc.ots` | Timestamp proof of the statement (OpenTimestamps, anchored in Bitcoin) |
| `arbre-futurs-ia-2.2-autonome.html` | Standalone archive copy of the page, which opens offline in any browser |
| `arbre-futurs-ia-2.2.html` | Original archive copy, byte-for-byte identical to the published file (in the Git repository) |

You need **GnuPG**: GPG Suite on macOS, Gpg4win on Windows, the `gnupg` package on Linux. For step 5 you also need opentimestamps.org or the `ots` client.

## 1. Get Louis's key and check its fingerprint

Fetch the key from Louis's domain (Web Key Directory):

```
gpg --auto-key-locate clear,nodefault,wkd --locate-keys jenkins@juwain.net
```

or from the keyserver:

```
gpg --keyserver hkps://keys.openpgp.org --recv-keys 7279D3DC2A9B89ABD8AF45E096417ABA7B36F5B6
```

The key fingerprint must be:

```
7279 D3DC 2A9B 89AB D8AF  45E0 9641 7ABA 7B36 F5B6
```

Don't rely on this document alone for the comparison: anyone who forged the files could have changed this guide as well. Compare the fingerprint with the one Louis shows elsewhere, on his public profiles (Nostr, Mastodon, Bluesky, X). The key obtained from the juwain.net domain is itself an independent source.

## 2. Verify the statement's signature

```
gpg --verify declaration-arbre-2.2.txt.asc
```

The expected result is "Good signature from "Dupont Louis <jenkins@juwain.net>"", made with key `7279D3DC2A9B89ABD8AF45E096417ABA7B36F5B6`.

A warning such as "This key is not certified with a trusted signature" is **normal**. It only means you have not certified this key yourself; the fingerprint check in step 1 takes its place.

The statement is in plain text inside the `.asc` file; it is in French. It gives the fingerprints used in steps 3 and 4.

## 3. Verify the archive copy

Compute the file's SHA-256 fingerprint:

| System | Command |
|---|---|
| macOS | `shasum -a 256 arbre-futurs-ia-2.2-autonome.html` |
| Linux | `sha256sum arbre-futurs-ia-2.2-autonome.html` |
| Windows (PowerShell) | `Get-FileHash arbre-futurs-ia-2.2-autonome.html -Algorithm SHA256` |

For the standalone copy, it must be:

```
a88f4eba9dabd601fc0ba56427d514383310edc06f4fc4257ebe8609bc5e5bc7
```

For the original copy, `arbre-futurs-ia-2.2.html`, it must be:

```
f836078f66f198706b660e665537fbba7430262463803d6c61132fa07b783003
```

## 4. Verify the page's content

Open the standalone copy or the online page and go to the **Authenticité** (authenticity) section. The page shows the content fingerprint it has just recomputed. It must match the one in the statement:

```
fbe54bead5a456fb20a38cb66506d09abe10efeeb27149e1783ed2dc86efd902
```

Always compare with the **signed statement**, not with the "Conforme" (compliant) status shown by the page: a forged page could display a false status. For this step, use the standalone copy rather than the original: without a document header, the original copy may show garbled accents and wrongly report modified content.

## 5. Verify the date

**On opentimestamps.org:** drop the `.ots` file, then the `.asc` statement when the site asks for it. The site shows the Bitcoin block that attests the statement's existence, and its date.

**On the command line:**

```
ots info declaration-arbre-2.2.txt.asc.ots
ots verify declaration-arbre-2.2.txt.asc.ots
```

`ots verify` checks the proof directly against the Bitcoin blockchain; it needs access to a Bitcoin Core node.

## What these checks prove, and what they don't

- **Steps 1 and 2.** The statement was signed by the holder of the key published under the juwain.net domain, that is, Louis.
- **Steps 3 and 4.** The archive copies and the page match exactly the edition described. The content fingerprint covers the tree's structure, the texts, the data and the sources, but not the interface code; an archive file's fingerprint covers everything.
- **Step 5.** The signed statement existed no later than the date of the Bitcoin block shown.
- **What they don't prove: that the content is correct.** They attest the work's origin and integrity, not the quality of its analyses.

If a check fails, the copy you have is not edition 2.2 as published by Louis. You can report it to jenkins@juwain.net.

Edition 2.1 (26 October 2026), now superseded, is verified with its own guide, `verification-arbre-2.1.en.md`.
