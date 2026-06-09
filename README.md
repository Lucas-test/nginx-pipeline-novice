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