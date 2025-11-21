## Contexte rapide

Ce dépôt est un petit site statique (page unique) : la source principale est `mon site.html` à la racine et les ressources images sont dans le dossier `image/`.

Résumé architecture : page HTML autonome, styles en ligne dans `<style>` et pas de build/tooling détecté.

## Objectif pour un agent IA

Rendre des modifications ciblées sur la page statique sans casser le marquage HTML existant. Proposer des corrections simples (balises mal utilisées, attributs manquants) et améliorer l'accessibilité des images et la structure minimale.

## Règles pratiques (actionables)

- Toujours travailler sur `c:\Users\Utilisateur\OneDrive\Desktop\mon site de formation\mon site.html` (le nom contient des espaces ; ne pas renommer sans l'accord du mainteneur).
- Le site n'a pas de système de build — valider les changements en ouvrant le fichier dans un navigateur ou en lançant un serveur statique local (ex. `python -m http.server 8000`).
- Respecter le style existant : les styles sont majoritairement en ligne dans `<style>` ; pour de petites corrections, ajoutez/modifiez ces règles plutôt que d'introduire une nouvelle feuille externe.

## Patterns et problèmes observés (exemples concrets)

- Image mal formée : l'élément `<img>` dans `mon site.html` utilise `href=""` au lieu de `src`. Corriger en `src="image/ton-image.ext"` et ajouter `alt="..."`.
  - Exemple à corriger :
    - actuel : `<img href="">`
    - souhaité : `<img src="image/monimage.jpg" alt="description">`
- Classes et éléments : la page utilise une classe `rouge` pour un container et une classe `button` sur un lien. Conserver ces noms de classes lors de modifications pour éviter de casser le style.
- Styles globaux : le `<style>` contient `body{ margin:100px; }` — gardez ce réglage en tête si vous modifiez la mise en page.

## Flux de travail pour modifications

1. Lire `mon site.html` et identifier la ligne à changer.
2. Faire un petit patch (modification minimale). Exemple : corriger l'attribut `img` et ajouter `alt`.
3. Valider localement : ouvrir `mon site.html` dans un navigateur ou démarrer un serveur local.

Commande utile (PowerShell) pour servir le dossier et tester dans un navigateur :

```powershell
cd "C:\Users\Utilisateur\OneDrive\Desktop\mon site de formation"; python -m http.server 8000
```

Puis ouvrir http://localhost:8000/mon%20site.html

## Ce qu'il ne faut pas faire

- Ne pas introduire de frameworks ou outils de build (npm, webpack, etc.) sans explication — le dépôt est intentionnellement minimal.
- Ne pas renommer `mon site.html` sans coordination (chemin et espaces présents dans les référencements locaux).

## Fichiers/clés à consulter

- `mon site.html` — source primaire de la page.
- `image/` — dossier d'assets (vérifier noms de fichiers et extensions avant d'insérer dans `src`).

## Exemple de petite correction acceptable

- Remplacement simple pour corriger l'image : changer `<img href="">` par `<img src="image/placeholder.jpg" alt="illustration">`.

---
Si vous voulez que j'intègre des validations HTML automatiques ou un mini-serveur de développement (ex: Live Server), dites-moi et je l'ajouterai comme section de workflow avec les commandes concrètes.
