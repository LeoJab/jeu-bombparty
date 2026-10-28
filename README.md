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
| `mots.txt` | Dictionnaire français (~325 000 formes, sans accents, compressé par préfixes) |
| `syl.json` | Syllabes classées en 5 niveaux selon le nombre de mots courants qui les contiennent (minimum 10) |
| `communs.txt` | Mots courants (+ pop culture) : servent à noter la difficulté des syllabes et à proposer la solution après une explosion |
| `pop.txt` | Mots pop culture (jeux vidéo, mangas, séries, internet) — déclenchent l'effet 🎮 |
| `fonts/` | Polices Bungee et Nunito (licence OFL) |
| `chadgang.json`, `cover.png` | Fiche du jeu dans le hub |

## Tester en local
Le jeu charge le dictionnaire avec `fetch`, il faut donc un petit serveur :
```
python -m http.server 8000
```
puis ouvrir http://localhost:8000 (mode même écran / solo).

Dictionnaire : [an-array-of-french-words](https://github.com/words/an-array-of-french-words) (MIT) + [French-Wordlist](https://github.com/Taknok/French-Wordlist) (MIT).

## Ajouter des mots pop culture
Ajoute simplement une ligne par mot dans `pop.txt` (majuscules et accents acceptés, espaces ignorés : `One Piece` → `onepiece`), puis `git push`. Le mot est accepté en jeu et déclenche l'effet 🎮 POP CULTURE.
