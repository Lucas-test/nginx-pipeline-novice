# Projet Nginx avec pipeline CI

## Objectif

Ce projet a pour objectif de créer un serveur Nginx simple et de mettre en place une pipeline CI avec GitHub Actions.

La pipeline permet de vérifier automatiquement que le projet est correct avant de le valider.

## Structure du projet

```text
.
├── index.html
├── nginx.conf
├── Dockerfile
├── README.md
└── .github/
    └── workflows/
        └── build.yml



## Niveau 2 - Engineer

Pour améliorer la pipeline, j'ai ajouté un déclenchement automatique sur `push` vers la branche `main`.

La pipeline peut aussi être lancée manuellement avec `workflow_dispatch`.

La pipeline effectue maintenant les étapes suivantes :

```text
Push sur main
        ↓
Récupération du code
        ↓
Vérification des fichiers essentiels
        ↓
Construction de l'image Docker
        ↓
Test de la configuration Nginx
        ↓
Lancement du conteneur
        ↓
Test HTTP du service
        ↓
Test de l'endpoint /health
        ↓
Nettoyage du conteneur
```

Un endpoint `/health` a été ajouté dans la configuration Nginx.

Il retourne une réponse HTTP 200 avec le texte `OK`.

La pipeline utilise la commande suivante pour vérifier que le service répond en HTTP :

```bash
curl -f http://localhost:8080
```

Elle utilise aussi cette commande pour vérifier l'endpoint `/health` :

```bash
curl -f http://localhost:8080/health
```

## Qualité et sécurité

Aucun secret n'est stocké dans le code source.

Le projet ne contient pas :

- de mot de passe ;
- de clé API ;
- de token ;
- de variable sensible.

La pipeline n'affiche aucun secret dans les logs. Elle exécute uniquement des commandes de vérification, de build Docker et de test HTTP.