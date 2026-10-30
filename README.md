# 💣 BombParty — ChadGangGames

Jeu de mots explosif pour le hub ChadGangGames : une syllabe s'affiche sur la bombe, tape un mot qui la contient avant qu'elle t'explose dans les mains.

## Modes
- **En ligne** (via le SDK du hub) : jusqu'à 8 joueurs, salles à code, invitations `?room=CODE`, classement « victoires ».
- **Survie solo** : classement séparé `solo` (score = nombre de mots).
- **Même écran** : quand le jeu est ouvert hors du hub (pas de SDK).

## Fichiers
| Fichier | Rôle |
|---|---|
| `index.html` | Tout le jeu (HTML/CSS/JS) |
| `mots.txt` | Dictionnaire français complet (~497 000 formes : an-array-of-french-words + Wiktionnaire + Hunspell/Grammalecte développé), sans accents, compressé par préfixes |
| `syl.json` | Syllabes classées en 5 niveaux selon le nombre de mots courants qui les contiennent (minimum 10) |
| `communs.txt` | Mots courants (+ pop culture) : servent à noter la difficulté des syllabes et à proposer la solution après une explosion |
| `extras.txt` | Mots bonus par catégorie (sections `#lol`, `#marque`, `#ville`, `#prenom`, `#anglais`, codés par préfixe) : ~134 000 entrées |
| `pop.txt` | Mots pop culture (jeux vidéo, mangas, séries, internet) — déclenchent l'effet 🎮 |
| `fonts/` | Polices Bungee et Nunito (licence OFL) |
| `chadgang.json`, `cover.png` | Fiche du jeu dans le hub |

## Tester en local
Le jeu charge le dictionnaire avec `fetch`, il faut donc un petit serveur :
```
python -m http.server 8000
```
puis ouvrir http://localhost:8000 (mode même écran / solo).

Sources : prénoms [INSEE via ThinkR-open/prenoms](https://github.com/ThinkR-open/prenoms), communes [Communes-France-JSON](https://github.com/high54/Communes-France-JSON), villes du monde [datasets/world-cities](https://github.com/datasets/world-cities) (GeoNames, CC-BY), marques [simple-icons](https://github.com/simple-icons/simple-icons) + [knockoff](https://github.com/Shpigford/knockoff) + liste manuelle, anglais [google-10000-english](https://github.com/first20hours/google-10000-english).

Dictionnaire : [an-array-of-french-words](https://github.com/words/an-array-of-french-words) (MIT) + [French-Wordlist](https://github.com/Taknok/French-Wordlist) (MIT).

## Ajouter des mots pop culture
Ajoute simplement une ligne par mot dans `pop.txt` (majuscules et accents acceptés, espaces ignorés : `One Piece` → `onepiece`), puis `git push`. Le mot est accepté en jeu et déclenche l'effet 🎮 POP CULTURE.

## Mots perso (ajoutés par les joueurs)
Bouton **✍️ Mots perso** (accueil, salon, en jeu) et bouton « ➕ Proposer ce mot » quand un mot est refusé.
Les mots sont stockés **dans le hub** (`ChadGang.liste('mots')`, voir la fiche du hub) :
- un membre propose → en attente ; un **modo ou un admin** valide ou refuse (une alerte part dans le salon Discord admin) ;
- un modo/admin qui ajoute un mot l'ajoute directement ;
- les modos/admins peuvent **retirer** un mot ajouté ; chacun peut annuler sa propre proposition.
Les mots validés sont jouables tout de suite (le jeu relit la liste au lancement d'une partie et quand quelqu'un modifie la liste).
