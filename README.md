<!-- LOGO DU PROJET OU DE L'ORGANISME PUBLIQUE -->

<div>
    <img src="./images/mcn.png" />
</div>

<!-- PROJET -->
# Plateforme d'accueil du CEAI 
  La plateforme d' accueil Web du Centre d'Expertise Appliquée en Innovation du CQEN (CEAI) est un site statique développé en Ruby avec Jekyll, déployé sur AWS S3 et exposé avec AWS CloudFront.

## Site
- https://ceai.cqen.ca/

## Objectif
  La plate forme web du CEAI donne un apperçcu sur les activités ainsi que les services qu'offre l'équipe d'innovation dont:
   - Le laboratoire d'expérimentation sur ses plateformes AWS SEA , Keycloak et Openshift. Ceci est un concept représentant l’ensemble des ressources nécessaires à la réalisation d’une expérimentation, cela inclut les environnements de développements, les usagers, les environnements de déploiements, la documentation, etc. 
   - L'API d'administration unifiant la gestion des usagers et des ressources allouées aux laboratoires sur les trois produits mentionnés ci-haut : AWS SEA, Openshift et Keycloak.

##  prérequis
   - Avoir un poste Linux ou MacOs
   - Avoir visual studio code installé sur le poste

### Étapes pour héberger le site localement:
1. Cloner le projet.
2. Faire la commande `git submodule init` pour initialiser le submodule dans votre répertoire local, puis `git submodule update` pour pull la dernière version du submodule.
3. Avoir ruby v3.0.4 ou + installé sur votre poste et faire la commande ```gem install jekyll bundler``` [Suivre la procédure d'installation](./procedure.md)
4. Faire la commande ```bundle exec jekyll server``` à la racine du site.

### Explication des dossiers
- `_layouts` : fichiers html faisant office de template, un layout est le html qui englobe le contenu d'une page, plusieurs layouts peuvent être utilisés l'un dans l'autre
- `_include` : layouts imbriqués dans ceux plus généraux dans - `_layouts` :
- `_posts` : fichiers markdown contenant certains paramètres et son contenu, ce sont les articles qui seront utilisés et listés sur le site
- `_sass` : scss disponible du site et des thèmes
- `.github/workflow` : contient les paramètres de build pour github pages, notamment quel token utiliser
- `assets` : (à vérifier) contient les contenus multimédia du site ainsi que les feuilles de style utilisées, le css généré par le css se retrouvera dans ce dossier lors du build
- `_site` : (généré lors d'un push) site résultant du build

### Précision sur la création des pages avec Jekyll:
 Pour s'assurer que le liens hypertexte soit généré d'une manière compatible avec le service de site static S3, il faut:
  - Ajouter dans le fichier nom-de-la-page.markdown  qui se trouve dans le dossier _pages un permalink: /nom-de-la-page/index.html ce qui va générer automatiquement 
    un nouveau fichier nom-de-la-page/index.html dans le dossier _site.
 
### Pour mettre à jour le submodule (contenu du site): 
```bash
git submodule update --remote
``` 
### Pipeline de déploiement en production
Le pipeline fonctionne sur : 
-	AWS CodePipeline
Le pipeline est démarré par : 
-	Un Github Pull Request se faisant accepter sur la branche main OU tout autre push sur la branche main. I
Vous pourrez voir le processus en cours d'exécution et voir les détails de chaque étape d'exécution en cliquant sur le pipeline sur le console AWS.
Voici le [lien](https://github.com/CQEN-QDCE/ceai-cqen-deployments/tree/main/plateform_web)pour que vous puissiez voir les processus de provisionnement  de l'environnement sur AWS et tous les détails de l'architecture

### Références:
 - https://platoniq.github.io/decidim-install/decidim-focal/
 - https://jekyllrb.com/docs/installation/ubuntu/
 