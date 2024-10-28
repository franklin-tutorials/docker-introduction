# Instructions pour l'exercice : Créer un fichier Compose pour une application multi-conteneurs

> Objectif : Créer une configuration Compose pour un site web Drupal CMS local

- Créez un fichier docker-compose.yml dans ce répertoire vide.
- Utilisez l'image `drupal:10-apache` avec l'image `postgres:16`.
- Utilisez `ports` pour exposer Drupal sur le port 8081 (ou votre port préféré).
- Définissez la variable d'environnement POSTGRES_PASSWORD pour le service postgres.
- Notez également que l'image officielle de PostgreSQL utilise par défaut user: postgres et database: postgres.
- Configurez Drupal dans le navigateur via `http://localhost:8081`
- Astuce : dans les paramètres avancés de Drupal, remplacez "localhost" par le nom du service Docker de postgres pour la connexion à la base de données.
- Utilisez la documentation Docker Hub pour configurer correctement les variables d'environnement et les volumes.
- Utilisez des volumes pour stocker les données uniques de Drupal.
