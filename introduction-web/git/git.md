# GIT

## création et modification d'un repository

création d'un répository (attention 1 seul max)

```bash
git init
```

ajout d'un fichier ou dossier à l'index

```bash
git add nom_du_ficher.extention
git add nom_du_dossier
```

vérification des changements

```bash
git status
```

ajout d'un fichier ou dossier à la branche (aprés un git add)

```bash
git commit
# Cela va ouvrir un éditeur de texte pour pouvoir entrer le detail des modif
```

```bash
git commit -m "description de la modification"
```

création d'une branche (ne jamais travailler directement sur le main)

```bash
git branch nom_de_la_branche
```

vérification des branches (liste)

```bash
git branch --list
```

changement de branches

```bash
git checkout nom_de_la_branche
# git branch --list (* montre la branche sur laquel on se situe)
```

fusion d'une branche vers la branche main

```bash
git merge
```
