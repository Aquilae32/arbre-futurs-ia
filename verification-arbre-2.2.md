# Vérifier l'authenticité de l'Arbre des futurs de l'IA, édition 2.2

Ce mode d'emploi permet de vérifier trois choses sur l'édition 2.2 de l'*Arbre des futurs de l'IA* (Louis ; Claude, d'Anthropic, 1er novembre 2026) : qu'elle n'a pas été modifiée, qu'elle a bien été publiée par Louis, et à quelle date.

## Les fichiers

| Fichier | Rôle |
|---|---|
| `declaration-arbre-2.2.txt.asc` | Déclaration d'authenticité de l'édition, signée par Louis (OpenPGP) |
| `declaration-arbre-2.2.txt.asc.ots` | Preuve d'horodatage de la déclaration (OpenTimestamps, ancrée dans Bitcoin) |
| `arbre-futurs-ia-2.2-autonome.html` | Copie d'archive autonome de la page, à ouvrir sans connexion dans n'importe quel navigateur |
| `arbre-futurs-ia-2.2.html` | Copie d'archive d'origine, identique octet pour octet au fichier publié (dans le dépôt Git) |

Il vous faut **GnuPG** : GPG Suite sous macOS, Gpg4win sous Windows, le paquet `gnupg` sous Linux. Pour l'étape 5, il vous faut aussi le site opentimestamps.org ou le client `ots`.

## 1. Obtenir la clé de Louis et contrôler son empreinte

Récupérez la clé sur le domaine de Louis (Web Key Directory) :

```
gpg --auto-key-locate clear,nodefault,wkd --locate-keys jenkins@juwain.net
```

ou sur le serveur de clés :

```
gpg --keyserver hkps://keys.openpgp.org --recv-keys 7279D3DC2A9B89ABD8AF45E096417ABA7B36F5B6
```

L'empreinte de la clé doit être :

```
7279 D3DC 2A9B 89AB D8AF  45E0 9641 7ABA 7B36 F5B6
```

Ne vous fiez pas à ce seul document pour la comparaison : quelqu'un qui aurait falsifié les fichiers aurait pu modifier aussi ce mode d'emploi. Comparez l'empreinte avec celle que Louis affiche ailleurs, sur ses profils publics (Nostr, Mastodon, Bluesky, X). La clé obtenue par le domaine juwain.net constitue déjà en elle-même une source indépendante.

## 2. Vérifier la signature de la déclaration

```
gpg --verify declaration-arbre-2.2.txt.asc
```

Le résultat attendu est « Bonne signature de « Dupont Louis <jenkins@juwain.net> » » (« Good signature » en anglais), avec la clé `7279D3DC2A9B89ABD8AF45E096417ABA7B36F5B6`.

Un avertissement du type « cette clef n'est pas certifiée avec une signature de confiance » est **normal**. Il signifie seulement que vous n'avez pas certifié vous-même cette clé ; la comparaison de l'empreinte à l'étape 1 en tient lieu.

Le texte de la déclaration se lit en clair dans le fichier `.asc`. Il donne les empreintes utilisées aux étapes 3 et 4.

## 3. Vérifier la copie d'archive

Calculez l'empreinte SHA-256 du fichier :

| Système | Commande |
|---|---|
| macOS | `shasum -a 256 arbre-futurs-ia-2.2-autonome.html` |
| Linux | `sha256sum arbre-futurs-ia-2.2-autonome.html` |
| Windows (PowerShell) | `Get-FileHash arbre-futurs-ia-2.2-autonome.html -Algorithm SHA256` |

Pour la copie autonome, l'empreinte doit être :

```
a88f4eba9dabd601fc0ba56427d514383310edc06f4fc4257ebe8609bc5e5bc7
```

Pour la copie d'origine, `arbre-futurs-ia-2.2.html`, elle doit être :

```
f836078f66f198706b660e665537fbba7430262463803d6c61132fa07b783003
```

## 4. Vérifier le contenu de la page

Ouvrez la copie autonome ou la page en ligne, puis allez à la section **Authenticité**. La page y affiche l'empreinte du contenu qu'elle a recalculée. Celle-ci doit être identique à celle de la déclaration :

```
fbe54bead5a456fb20a38cb66506d09abe10efeeb27149e1783ed2dc86efd902
```

Comparez toujours avec la **déclaration signée**, et non avec le statut « Conforme » affiché par la page : une page falsifiée pourrait afficher un faux statut. Pour cette étape, utilisez la copie autonome plutôt que la copie d'origine. Sans en-tête de document, la copie d'origine peut afficher des accents illisibles et signaler à tort un contenu modifié.

## 5. Vérifier la date

**Sur le site opentimestamps.org :** déposez le fichier `.ots`, puis la déclaration `.asc` quand le site le demande. Le site indique le bloc Bitcoin qui atteste l'existence de la déclaration, et sa date.

**En ligne de commande :**

```
ots info declaration-arbre-2.2.txt.asc.ots
ots verify declaration-arbre-2.2.txt.asc.ots
```

`ots verify` vérifie la preuve directement contre la chaîne Bitcoin ; il demande l'accès à un nœud Bitcoin Core.

## Ce que prouvent ces vérifications, et ce qu'elles ne prouvent pas

- **Étapes 1 et 2.** La déclaration a été signée par le détenteur de la clé publiée sous le domaine juwain.net, c'est-à-dire Louis.
- **Étapes 3 et 4.** Les copies d'archive et la page correspondent exactement à l'édition décrite. L'empreinte du contenu couvre la structure de l'arbre, les textes, les données et les sources, mais pas le code de l'interface ; l'empreinte d'un fichier d'archive couvre tout.
- **Étape 5.** La déclaration signée existait au plus tard à la date du bloc Bitcoin indiqué.
- **Ce qu'elles ne prouvent pas : que le contenu est juste.** Elles attestent l'origine et l'intégrité de l'œuvre, non la qualité de ses analyses.

Si une vérification échoue, la copie que vous avez n'est pas l'édition 2.2 publiée par Louis. Vous pouvez le signaler à jenkins@juwain.net.

L'édition 2.1 (26 octobre 2026), remplacée, se vérifie avec son propre mode d'emploi, `verification-arbre-2.1.md`.
