# TP1 Python — Partie 1

**Étudiant :** Omar GHILAN  
**Module :** Architecture Web — Master AI — Systèmes Distribués Agentiques

---

## 📁 Structure du dépôt

- `TP1python_partie1.ipynb` → Notebook Python contenant tous les exercices résolus.
- `README.md` → Ce document (réponses + explications).
- `screenshots/` → Captures d'écran prouvant l'exécution des exercices.

---

## Exercice 1 : Système de notation pondérée

**Conversions utilisées :**
- `input()` renvoie toujours une chaîne (`str`).
- Les notes sont converties immédiatement en `float` avec `float()` car elles peuvent contenir une partie décimale.
- Les coefficients sont convertis en `int` avec `int()` car ce sont des entiers.
- Le résultat final est reconverti en `str` avec `str()` pour être concaténé avec le texte de la phrase d'affichage.

**Formule appliquée :**
moyenne = (note_projet × coeff_projet + note_ecrit × coeff_ecrit) / (coeff_projet + coeff_ecrit)

**Résultat observé :** le programme affiche correctement la moyenne pondérée sur 20 avec l'identifiant de l'étudiant.

---

## Exercice 2 : Analyse d'une équation ax² + bx + c = 0

**Structure utilisée :**
1. **Tests imbriqués** : on vérifie d'abord `a == 0`, puis à l'intérieur on teste `b == 0`.
   - Si `a == 0` et `b == 0` → équation dégénérée.
   - Si `a == 0` et `b != 0` → équation du premier degré.
   - Sinon → équation du second degré (`est_second_degre = True`).

2. **Structure conditionnelle séparée** (et non imbriquée) : elle s'exécute uniquement si `est_second_degre` est vrai. On y calcule le discriminant Δ = b² − 4ac, puis on affiche le nombre de solutions selon le signe :
   - Δ > 0 → 2 solutions réelles.
   - Δ = 0 → 1 solution réelle (double).
   - Δ < 0 → aucune solution réelle.

**Résultat observé :** le programme distingue correctement les 3 cas possibles.

---

## Exercice 3 : Contrôle de saisie et boucle d'affichage

**Boucle `while` (validation) :**
Elle permet de **répéter la demande de saisie** tant que l'utilisateur n'a pas fourni un entier impair valide. On utilise `try / except ValueError` pour gérer les saisies non numériques, et `valeur != int(valeur)` pour détecter les décimaux. La boucle ne s'arrête que lorsque la condition est remplie (`valide = True`).

**Boucle `for` + `range()` :**
Une fois la saisie validée, on affiche tous les entiers de `0` à `nombre` inclus grâce à `range(nombre + 1)`.

**Résultat observé :** conforme à l'exemple du sujet — les erreurs s'affichent, puis la séquence correcte est imprimée.

---

## Exercice 4 : Traitement des notes

**1. Paramètre par défaut & immuabilité :**
- La fonction `ajouter_bonus(note, bonus=2)` utilise un **paramètre par défaut** (`bonus=2`).
- On déclare `x = 10`, on appelle `ajouter_bonus(x)`, puis on affiche `x` → il reste à `10`.
- **Preuve d'immuabilité :** les types de base (`int`, `float`, `str`...) sont immuables en Python. La fonction crée un **nouvel objet local**, la variable externe n'est donc pas modifiée.

**2. `map()` :**
`map(ajouter_bonus, notes)` applique la fonction à chaque élément de la liste `notes` et retourne un itérateur, qu'on convertit en liste avec `list()`.

**3. `zip()` :**
`zip(etudiants, notes_bonus)` regroupe les deux listes en paires (étudiant, note), ce qui permet de les parcourir simultanément dans une boucle `for`.

**Résultat observé :**
```
Ali : 14.0
Sara : 17.5
```

---

## Exercice 5 : Saisie ordonnée et calcul de la médiane

**Démarche :**
1. On demande d'abord le nombre total de notes `n`.
2. On utilise une boucle `for` pour saisir chaque note, et à l'intérieur une boucle `while` pour **forcer l'ordre croissant** : si la nouvelle note est inférieure à la précédente, on redemande la saisie.
3. On teste la parité de `n` avec `n % 2 == 0`.
4. Calcul de la médiane (liste déjà triée) :
   - **n impair** : élément du milieu → `notes[n // 2]`.
   - **n pair** : moyenne des deux éléments du milieu → `(notes[n//2 - 1] + notes[n//2]) / 2`.

**Résultat observé :** la médiane est correcte dans les deux cas (pair et impair).

---

## Exercice 6 : Configuration d'un système multi-agents

**Structure utilisée :**
- **Dictionnaire `config_ia`** : structure principale (clé → valeur).
- **Dictionnaire imbriqué `agent_recherche`** : stocke les paramètres de l'agent (modèle, température, outils).
- **Liste `outils`** : contient des **tuples** `(nom, version)`.
- **Tuple** : immuable, idéal pour lier un nom d'outil à sa version.

**Modification de la température :**
Accès direct via `config_ia["agent_recherche"]["temperature"] = 0.5` — pas besoin de redéclarer le dictionnaire (car les dictionnaires sont **mutables**).

**Extraction du nom "Calculatrice" :**
```python
config_ia["agent_recherche"]["outils"][1][0]
```

Chemin : dict → dict → liste → tuple → élément d'indice 0 (le nom).

**Résultat observé :** `Calculatrice` est bien affiché sans sa version.

---

## ✅ Conclusion

Tous les exercices du TP1 ont été traités et testés avec succès. Les captures d'écran correspondantes se trouvent dans le dossier `screenshots/`.



