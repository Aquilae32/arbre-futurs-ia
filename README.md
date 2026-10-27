# Arbre des futurs de l'IA

Ce dépôt contient les fichiers d'authenticité de l'*Arbre des futurs de l'IA*. C'est un outil interactif qui décompose en un arbre de probabilités à sept nœuds les futurs possibles de l'IA avancée d'ici 2100 : seize issues, selon qu'une superintelligence existe ou non et que les humains continuent ou non de l'orienter.

- **Version de référence :** https://claude.ai/artifact/QgcA1YRtSX1Q72bMrUiLMj
- **Page de présentation :** https://juwain.net/arbre/
- **Auteurs :** Louis (commande, orientation et décisions éditoriales) et Claude, d'Anthropic (rédaction, calculs, estimations initiales)

## Édition 2.1 (26 octobre 2026)

| Fichier | Rôle |
|---|---|
| `declaration-arbre-2.1.txt.asc` | Déclaration d'authenticité signée par Louis (OpenPGP) |
| `declaration-arbre-2.1-complement.txt.asc` | Déclaration complémentaire signée, qui décrit la copie autonome |
| `*.asc.ots` | Preuves d'horodatage des déclarations (OpenTimestamps, ancrées dans Bitcoin) |
| `arbre-futurs-ia-2.1-autonome.html` | Copie d'archive autonome, à ouvrir sans connexion |
| `arbre-futurs-ia-2.1.html` | Copie d'archive d'origine, identique octet pour octet au fichier publié |
| `verification-arbre-2.1.md` | Mode d'emploi de vérification |
| `verification-arbre-2.1.en.md` | Verification guide (English) |

- **Empreinte du contenu (SHA-256) :** `8d11a1fc385eafdf066504f576518c86efc32895dcde6b2d8751157251a28d8e`
- **Empreinte de la copie autonome :** `36c34b207b4de5e4a2d6d4142c281bbe7aba38c9a4110cb36a06d2cc32436dfe`
- **Empreinte de la copie d'origine :** `617147d4abf8bf9891e9b918025328dbb8915456e781ec8ca17de0e0fe1b0d30`

## Clé de Louis

- **Adresse :** `jenkins@juwain.net`
- **Empreinte :** `7279 D3DC 2A9B 89AB D8AF  45E0 9641 7ABA 7B36 F5B6`
- **Où l'obtenir :** par Web Key Directory (`gpg --locate-keys jenkins@juwain.net`) ou sur keys.openpgp.org.

Les commits et les étiquettes de ce dépôt sont signés avec cette clé. Vérifiez par exemple l'étiquette de l'édition avec `git verify-tag v2.1`.

Pour la vérification complète, suivez `verification-arbre-2.1.md`. Comparez toujours l'empreinte de la clé avec celle que Louis affiche sur ses profils publics, indépendamment de ce dépôt.

## Historique des éditions

- **2.1, 26 octobre 2026 :** édition actuelle.
- **2.0, 26 octobre 2026 :** remplacée. Empreinte du contenu : `a5de6ab17b165d448fd2b81a7ae7c4b98429a4a6e13dd74ddffa48c6338dc4e0`.

---

**English.** This repository holds the authenticity files of the *Arbre des futurs de l'IA* (AI Futures Tree), an interactive tool in French about the possible futures of advanced AI up to 2100. Edition 2.1 is described by two signed statements (`declaration-arbre-2.1.txt.asc` and its supplement), timestamped in Bitcoin (`.ots`). See `verification-arbre-2.1.en.md` to verify it. Louis's OpenPGP key: `jenkins@juwain.net`, fingerprint `7279 D3DC 2A9B 89AB D8AF  45E0 9641 7ABA 7B36 F5B6`.
