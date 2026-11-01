# Arbre des futurs de l'IA

Ce dépôt contient les fichiers d'authenticité de l'*Arbre des futurs de l'IA*. C'est un outil interactif qui décompose en un arbre de probabilités à sept nœuds les futurs possibles de l'IA avancée d'ici 2100 : seize issues, selon qu'une superintelligence existe ou non et que les humains continuent ou non de l'orienter.

- **Version de référence (édition 2.2) :** https://claude.ai/artifact/XKeWgyP9oN6eDMwQjGvy75
- **Page de présentation :** https://juwain.net/arbre/
- **Auteurs :** Louis (commande, orientation et décisions éditoriales) et Claude, d'Anthropic (rédaction, calculs, estimations initiales)

## Édition 2.2 (1er novembre 2026)

| Fichier | Rôle |
|---|---|
| `declaration-arbre-2.2.txt.asc` | Déclaration d'authenticité signée par Louis (OpenPGP) |
| `declaration-arbre-2.2.txt.asc.ots` | Preuve d'horodatage de la déclaration (OpenTimestamps, ancrée dans Bitcoin) |
| `arbre-futurs-ia-2.2-autonome.html` | Copie d'archive autonome, à ouvrir sans connexion |
| `arbre-futurs-ia-2.2.html` | Copie d'archive d'origine, identique octet pour octet au fichier publié |
| `verification-arbre-2.2.md` | Mode d'emploi de vérification |
| `verification-arbre-2.2.en.md` | Verification guide (English) |

- **Empreinte du contenu (SHA-256) :** `fbe54bead5a456fb20a38cb66506d09abe10efeeb27149e1783ed2dc86efd902`
- **Empreinte de la copie autonome :** `a88f4eba9dabd601fc0ba56427d514383310edc06f4fc4257ebe8609bc5e5bc7`
- **Empreinte de la copie d'origine :** `f836078f66f198706b660e665537fbba7430262463803d6c61132fa07b783003`

## Clé de Louis

- **Adresse :** `jenkins@juwain.net`
- **Empreinte :** `7279 D3DC 2A9B 89AB D8AF  45E0 9641 7ABA 7B36 F5B6`
- **Où l'obtenir :** par Web Key Directory (`gpg --locate-keys jenkins@juwain.net`) ou sur keys.openpgp.org.

Les commits et les étiquettes de ce dépôt sont signés avec cette clé. Vérifiez par exemple l'étiquette de l'édition avec `git verify-tag v2.2`.

Pour la vérification complète, suivez `verification-arbre-2.2.md`. Comparez toujours l'empreinte de la clé avec celle que Louis affiche sur ses profils publics, indépendamment de ce dépôt.

## Historique des éditions

- **2.2, 1er novembre 2026 :** édition actuelle.
- **2.1, 26 octobre 2026 :** remplacée. Empreinte du contenu : `8d11a1fc385eafdf066504f576518c86efc32895dcde6b2d8751157251a28d8e`. Ses fichiers restent dans ce dépôt (`declaration-arbre-2.1*.asc`, `arbre-futurs-ia-2.1*.html`, `verification-arbre-2.1*.md`), avec l'étiquette `v2.1`. Version de référence : https://claude.ai/artifact/QgcA1YRtSX1Q72bMrUiLMj
- **2.0, 26 octobre 2026 :** remplacée. Empreinte du contenu : `a5de6ab17b165d448fd2b81a7ae7c4b98429a4a6e13dd74ddffa48c6338dc4e0`.

---

**English.** This repository holds the authenticity files of the *Arbre des futurs de l'IA* (AI Futures Tree), an interactive tool in French about the possible futures of advanced AI up to 2100. Edition 2.2 (1 November 2026) is described by a signed statement (`declaration-arbre-2.2.txt.asc`), timestamped in Bitcoin (`.ots`). See `verification-arbre-2.2.en.md` to verify it. Edition 2.1 remains verifiable with its own files. Louis's OpenPGP key: `jenkins@juwain.net`, fingerprint `7279 D3DC 2A9B 89AB D8AF  45E0 9641 7ABA 7B36 F5B6`.
