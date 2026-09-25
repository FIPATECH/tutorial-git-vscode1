## Étape 3 : lire l'historique, annuler une modification et utiliser Source Control

Tu viens de créer puis pousser un commit. Avant d'en faire un deuxième, apprends à regarder l'historique et à corriger une erreur locale sans paniquer.

### 1. Explorer l'historique

Dans le terminal :

```bash
git log --oneline --graph --decorate --all
```

Tu dois voir au minimum :

- `main` ;
- `feature/robot-status` ;
- ton commit récent ;
- des références comme `origin/main` ou `origin/feature/robot-status`.

Affiche le dernier commit en détail :

```bash
git show HEAD
```

`HEAD` désigne ta position actuelle dans l'historique, généralement le dernier commit de la branche sur laquelle tu te trouves.

Dans VS Code, ouvre **Source Control** puis la vue **Graph** si elle est disponible. Tu observes le même historique, mais visuellement.

### 2. Annuler une modification non commitée

Ouvre `robot/mission.md` et ajoute temporairement une ligne quelconque, par exemple :

```text
TEST TEMPORAIRE
```

Enregistre puis regarde :

```bash
git status
git diff robot/mission.md
```

Décide finalement de jeter cette modification :

```bash
git restore robot/mission.md
```

Puis :

```bash
git status
```

La modification a disparu.

> [!WARNING]
> `git restore` sur un fichier modifié remplace son contenu local par la version enregistrée dans Git. Vérifie toujours ce que tu jettes avant de l'utiliser.

### 3. Comprendre `.gitignore`

Les projets robotiques génèrent souvent beaucoup de fichiers qu'on ne veut **pas** versionner : builds, caches Python, environnements virtuels, logs, etc.

Ouvre `.gitignore` dans VS Code et ajoute :

```gitignore
build/
install/
log/
__pycache__/
.venv/
```

Dans **Source Control**, ouvre le diff de `.gitignore` et relis-le.

Cette fois, stage le fichier depuis VS Code avec le bouton **+** à côté du fichier. Vérifie ensuite dans le terminal que VS Code a bien exécuté l'équivalent d'un `git add` :

```bash
git status
git diff --staged
```

### 4. Committer depuis VS Code

Dans **Source Control** :

1. saisis un message clair, par exemple `Ignore generated files` ;
2. clique sur **Commit**.

Puis vérifie le résultat dans le terminal :

```bash
git log -2 --oneline
git status
```

Tu viens d'utiliser deux interfaces différentes sur **le même Git** : le terminal et VS Code.

Publie le deuxième commit :

```bash
git push
```

Mona vérifiera le contenu de `.gitignore` et que ta branche contient désormais plusieurs commits.
