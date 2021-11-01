# Site: 
- https://cqen-qdce.github.io/ceai-cqen-web-platform/

### Pour héberger le site localement:
1. Cloner le projet.
2. Faire la commande `git submodule init` pour initialiser le submodule dans votre répertoire local, puis `git submodule update` pour pull la dernière version du submodule.
3. Avoir ruby v2.4.0 ou + installé sur votre poste et faire la commande ```gem install jekyll bundler```.
4. Faire la commande ```bundle exec jekyll server``` à la racine du site.

### Pour mettre à jour le submodule (contenu du site): 
```bash
git submodule update --remote
``` 

### Explication des dossiers
- `_layouts` : fichiers html faisant office de template, un layout est le html qui englobe le contenu d'une page, plusieurs layouts peuvent être utilisés l'un dans l'autre
- `_include` : layouts imbriqués dans ceux plus généraux dans - `_layouts` :
- `_posts` : fichiers markdown contenant certains paramètres et son contenu, ce sont les articles qui seront utilisés et listés sur le site
- `_sass` : scss disponible du site et des thèmes
- `.github/workflow` : contient les paramètres de build pour github pages, notamment quel token utiliser
- `assets` : (à vérifier) contient les contenus multimédia du site ainsi que les feuilles de style utilisées, le css généré par le css se retrouvera dans ce dossier lors du build
- `_site` : (généré lors d'un push) site résultant du build
