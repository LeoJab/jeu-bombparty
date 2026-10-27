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
| `syl.json` | Syllabes de 2–3 lettres et leur nombre de mots (sert aux niveaux de difficulté) |
| `communs.txt` | Mots courants, utilisés pour la solution affichée après une explosion |
| `fonts/` | Polices Bungee et Nunito (licence OFL) |
| `chadgang.json`, `cover.png` | Fiche du jeu dans le hub |

## Tester en local
Le jeu charge le dictionnaire avec `fetch`, il faut donc un petit serveur :
```
python -m http.server 8000
```
puis ouvrir http://localhost:8000 (mode même écran / solo).

Dictionnaire : [an-array-of-french-words](https://github.com/words/an-array-of-french-words) (MIT) + [French-Wordlist](https://github.com/Taknok/French-Wordlist) (MIT).
