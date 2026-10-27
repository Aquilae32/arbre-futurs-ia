# Verifying the authenticity of the AI Futures Tree, edition 2.1

This guide lets you check that edition 2.1 of the *Arbre des futurs de l'IA* (AI Futures Tree; Louis and Claude, by Anthropic, 26 October 2026) has not been altered, that Louis published it, and when.

## The files

| File | Purpose |
|---|---|
| `declaration-arbre-2.1.txt.asc` | Authenticity statement for the edition, signed by Louis (OpenPGP) |
| `declaration-arbre-2.1-complement.txt.asc` | Signed supplementary statement describing the standalone archive copy |
| `….asc.ots` | Timestamp proof of each statement (OpenTimestamps, anchored in Bitcoin) |
| `arbre-futurs-ia-2.1-autonome.html` | Standalone archive copy of the page, which opens offline in any browser |
| `arbre-futurs-ia-2.1.html` | Original archive copy, byte-for-byte identical to the published file (in the Git repository) |

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

## 2. Verify the signatures of both statements

```
gpg --verify declaration-arbre-2.1.txt.asc
gpg --verify declaration-arbre-2.1-complement.txt.asc
```

The expected result for each is "Good signature from "Dupont Louis <jenkins@juwain.net>"", made with key `7279D3DC2A9B89ABD8AF45E096417ABA7B36F5B6`.

A warning such as "This key is not certified with a trusted signature" is **normal**. It only means you have not certified this key yourself; the fingerprint check in step 1 takes its place.

The supplementary statement gives the fingerprint of the main statement. Check that they match:

```
shasum -a 256 declaration-arbre-2.1.txt.asc
```

Both statements are in plain text inside the `.asc` files; they are in French. They give the fingerprints used in steps 3 and 4.

## 3. Verify the archive copy

Compute the file's SHA-256 fingerprint:

| System | Command |
|---|---|
| macOS | `shasum -a 256 arbre-futurs-ia-2.1-autonome.html` |
| Linux | `sha256sum arbre-futurs-ia-2.1-autonome.html` |
| Windows (PowerShell) | `Get-FileHash arbre-futurs-ia-2.1-autonome.html -Algorithm SHA256` |

For the standalone copy, it must match the supplementary statement:

```
36c34b207b4de5e4a2d6d4142c281bbe7aba38c9a4110cb36a06d2cc32436dfe
```

For the original copy, `arbre-futurs-ia-2.1.html`, it must match the main statement:

```
617147d4abf8bf9891e9b918025328dbb8915456e781ec8ca17de0e0fe1b0d30
```

## 4. Verify the page's content

Open the standalone copy or the online page and go to the **Authenticité** (authenticity) section. The page shows the content fingerprint it has just recomputed. It must match the one in both statements:

```
8d11a1fc385eafdf066504f576518c86efc32895dcde6b2d8751157251a28d8e
```

Always compare with the **signed statements**, not with the "Conforme" (compliant) status shown by the page: a forged page could display a false status. For this step, use the standalone copy rather than the original: without a document header, the original copy may show garbled accents and wrongly report modified content.

## 5. Verify the dates

**On opentimestamps.org:** drop a `.ots` file, then the matching `.asc` statement when the site asks for it. The site shows the Bitcoin block that attests the statement's existence, and its date.

**On the command line:**

```
ots info declaration-arbre-2.1.txt.asc.ots
ots verify declaration-arbre-2.1.txt.asc.ots
ots verify declaration-arbre-2.1-complement.txt.asc.ots
```

`ots verify` checks the proof directly against the Bitcoin blockchain; it needs access to a Bitcoin Core node.

## What these checks prove, and what they don't

- **Steps 1 and 2.** Both statements were signed by the holder of the key published under the juwain.net domain, that is, Louis.
- **Steps 3 and 4.** The archive copies and the page match exactly the edition described. The content fingerprint covers the tree's structure, the texts, the data and the sources, but not the interface code; an archive file's fingerprint covers everything.
- **Step 5.** Each signed statement existed no later than the date of the Bitcoin block shown.
- **What they don't prove: that the content is correct.** They attest the work's origin and integrity, not the quality of its analyses.

If a check fails, the copy you have is not edition 2.1 as published by Louis. You can report it to jenkins@juwain.net.
