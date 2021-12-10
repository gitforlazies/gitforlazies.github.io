+++
title = "Git fixup"
description = "Fixing up the last commit"
draft = false
date = 2021-12-09T13:49:54+00:00
updated = 2021-12-09T13:49:54+00:00
template = "blog/page.html"

[taxonomies]
authors = ["Pierre Baconnier"]
+++

## Git fixup, kezako ?

Vous êtes probablement familier avec `git commit --amend` pour incorporer les changements en cours dans le dernier commit(*lastcommit*), réécrivant le dernier commit et en générant un nouveau, d'un digest différent. 
La toolbox git offre une commande similaire appelée `git fixup`, qui fera la même chose, mais sans demander le message du commit.

Il s'agit donc d'une version plus rapide de `commit --amend`.

*n.b: Cette action est aussi accessible depuis l'éditeur de rebase:*
```bash
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
```

Comment ça marche ?

```bash
git add -p    # Pick bits to commit
git commit
git add -p    # Add changes of indexing zone
git fixup     # Add those to the last commit
```