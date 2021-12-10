+++
title = "Git delouse"
description = "Splitting commits into pieces"
draft = false
date = 2021-12-09T13:49:54+00:00
updated = 2021-12-09T13:49:54+00:00
template = "blog/page.html"

[taxonomies]
authors = ["Pierre Baconnier"]
+++

## Git delouse, kezako ?

Pourquoi diviser un commit ? 

Par exemple, supposons que vous ajoutez une correction de bogue mais que vous renommez également une variable pour lui donner une signification plus claire. 
Lorsque vous soumettez le code pour révision, vous réalisez que le renommage de la variable ajoute beaucoup de bruit à la modification réelle.
Vous pouvez alors décider que c'est une bonne idée de diviser ce commit en deux parties: une qui change atomiquement le nom de la variable partout, et une qui corrige le bug. Vous pouvez alors pointer vers le commit de correction de bogue lorsque vous effectuerez une pull request.

Comment ça marche ?

```bash
git commit -m 'fix: bugfix for login screen'
# Error, I should've split this one up. Let's start over!

git delouse
git add -p    # Just pick the bugfix bits
git fixup
git add -p    # Add changes of indexing zone
git commit -m 'refacto: rename variable name to be clearer'
```