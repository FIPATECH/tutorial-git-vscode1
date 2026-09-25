## Étape 4 : comprendre le remote puis ouvrir une pull request

Tes commits locaux sont maintenant publiés sur GitHub. Avant d'ouvrir la pull request, prends deux minutes pour comprendre ce que Git suit réellement.

### Branche locale et branche distante

Affiche les remotes :

```bash
git remote -v
```

Puis les branches et leurs upstreams :

```bash
git branch -vv
```

Tu devrais voir que `feature/robot-status` suit une branche distante du type :

```text
origin/feature/robot-status
```

Attention : `origin/feature/robot-status` n'est pas une deuxième branche que tu édites directement. C'est une **remote-tracking branch**, une référence locale représentant l'état du remote connu par ton Git.

### `fetch`, `pull` et `push`

Mets à jour ta connaissance du remote sans modifier tes fichiers :

```bash
git fetch origin
```

Puis regarde le graphe :

```bash
git log --oneline --graph --decorate --all
```

À retenir :

- `git fetch` récupère les nouveaux objets et met à jour les références distantes ;
- `git pull` récupère puis intègre les changements dans ta branche courante ;
- `git push` envoie tes commits locaux vers le remote.

### Vérifier avant la PR

Exécute encore :

```bash
git status
```

Ton working tree doit être propre et ta branche doit être à jour avec son upstream.

### Ouvrir la pull request

Tu connais déjà les PR grâce au tutoriel GitHub Basics. Ici, la différence est que **tout le travail a été produit localement**, puis publié avec `git push`.

[**Créer ma pull request →**](../../compare/main...feature/robot-status?expand=1)

Choisis :

- **base** : `main`
- **compare** : `feature/robot-status`

Utilise un titre clair, par exemple :

```text
Update robot configuration
```

Ajoute une vraie description qui résume ce que tu as fait et pourquoi.

Le bot vérifiera également que la PR contient bien les deux fichiers attendus :

- `robot/config.yaml`
- `.gitignore`

Une fois la PR valide, **reste dans sa Conversation** : comme dans le premier tutoriel, la suite viendra directement à toi.
