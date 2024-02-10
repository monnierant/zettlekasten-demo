---
type: conclusion
topic: devops 
---

- Topic : #VeilleIT/devops 
- Tags : #gitlab #git #gitflow 

# Idea

A flow based partially on [[🌐Git Flow]]  and partially on [[📺What Is GitLab Workflow - GitLab Flow]]

![[Z. Assets/0d3be0fc9015e9b87c7206775d0ee5e4_MD5.png]]


# Exemple

## Principe

Ce repo contient dans le dossier `thesaurus` l'ensemble des thésaurus qui peuvent être mis à jour par medtra sans sortir une nouvelle version.

Actuellement, chaque fichier dans un dossier de thésaurus `<ThesaurusName>` sera copier dans le zip de destination sous le format `<ThesaurusName>-table_name.json` à la racine du zip final.

### Chiffrage du zip

Le zip est chiffré avec une clé

Cette clé est défini dans la variable CICD de gitlab `ZIP_PASSWORD`

- Options: Masked
- Environements: All (default)

## Obtenir la dernière version

https://gitlab.ows.fr/ass1/deploiement/thesaurus-presance/-/releases/permalink/latest

https://gitlab.ows.fr/ass1/deploiement/thesaurus-presance/-/releases/permalink/latest/downloads/:filepath

## Usage

### Prérequis Développement

[Installing git flow on Windows](https://github.com/petervanderdoes/gitflow-avh/wiki/Installing-on-Windows)

### Démaré une nouvelle version

Initialisation de la branch feature/presance

```Bash
git checkout develop
git pull origin develop
git flow feature start presance
```

C'est le moment de faire toutes les modifications nécessaires sur les thésaurus

### Publier les modifications

```Bash
git status
git add .
git commit -m "Feature - Message de changement"
git flow feature publish presance
```

> [!tip] 
> Utiliser `git add -p .` pour faire un ajout partielle et avoir un commit message par aspect rajouter 

Il faut ensuite se rendre sur le site de gitlab du projet pour lancer une merge requeste de :

- la branche `feature/presance` vers la branch `develop`

Un test automatique va être lancé pour confirmer la validité des JSONs du projet.

### Corriger un souci si les tests ne passent pas

On corrige le code pour valider le test de la merge request

```Bash
git status
git add .
git commit -m "Feature - Message de changement"
git flow feature publish presance
```

Le `publish` va remettre à jour la merge request et automatiquement relancer les tests.

### Execution de la merge request

Si les tests sont bon et que vous avez approuver la revue de code, alors vous pouvez merger la request.

Une fois la request mergée, il faut faire du menage sur votre poste.

```Bash
git checkout develop
git pull origin develop
git flow feature delete presance
```

### Publication d'une nouvelle version

1. Lancer une merge request depuis la branch `develop` vers la branche `main`
2. Une fois le merge terminé, créer un tag avec le numéro de version `exemple: V2023`

Cette procédure va rendre la branch main à jour avec la dernière version.

Cela va aussi créer un tag de la version et réaliser automatiquement une publication dans le repository general du zip.

Enfin une release avec le numéro de version sera créé, attaché au tag et pointant vers le zip publier sur le repo général.



# Links

Sources :

## West : Similar

## East : Opposite

## North : Theme / Question

- [[How to use gitlab for CI-CD]]
- [[How to make the perfect CICD Pipeline to build a simple docker helper container]]

## South : What does it lead to

