
#  Exercices sur les Volumes 

Bienvenue dans cette série d'exercices sur l'utilisation des volumes Docker. Ces exercices sont conçus pour initier les débutants aux concepts de persistance de données dans Docker.

---

## Exercice 1 : Création et Inspection de Volume

**Objectif :** Créer un volume Docker et inspecter ses détails.

1. **Créer un volume nommé**  
   ```bash
   docker volume create mon_volume
   ```

2. **Lister les volumes existants**  
   ```bash
   docker volume ls
   ```

3. **Inspecter le volume pour en voir les détails**  
   ```bash
   docker volume inspect mon_volume
   ```

4. **Question** : Que remarquez-vous dans les détails affichés par `docker volume inspect` ? Quels éléments indiquent l’emplacement et le type de volume ?

---

## Exercice 2 : Utilisation de Volume avec un Conteneur

**Objectif :** Utiliser un volume pour stocker des données dans un conteneur, afin qu'elles persistent après la suppression du conteneur.

1. **Lancer un conteneur avec un volume monté sur `/data`**  
   ```bash
   docker run -d --name conteneur_test -v mon_volume:/data nginx
   ```

2. **Créer un fichier dans le volume monté**  
   ```bash
   docker exec conteneur_test sh -c "echo 'Bienvenue dans le volume Docker' > /data/bonjour.txt"
   ```

3. **Arrêter et supprimer le conteneur**  
   ```bash
   docker rm -f conteneur_test
   ```

4. **Relancer un nouveau conteneur avec le même volume et vérifier le fichier**  
   ```bash
   docker run --rm -v mon_volume:/data nginx cat /data/bonjour.txt
   ```

5. **Question** : Le fichier est-il toujours présent ? Pourquoi ?

---

## Exercice 3 : Nettoyage des Volumes Inutilisés

**Objectif :** Apprendre à nettoyer les volumes non utilisés pour libérer de l’espace disque.

1. **Créer plusieurs volumes de test**  
   ```bash
   docker volume create volume_test1
   docker volume create volume_test2
   ```

2. **Lister tous les volumes**  
   ```bash
   docker volume ls
   ```

3. **Supprimer les volumes inutilisés**  
   ```bash
   docker volume prune
   ```

4. **Question** : Pourquoi est-il important de supprimer les volumes non utilisés dans un environnement Docker ?

---

## Exercice 4 : Modification de Données dans un Volume depuis l’Hôte

**Objectif :** Apprendre à modifier des données directement dans le volume depuis le système de fichiers hôte.

1. **Localiser le volume sur l’hôte avec `docker volume inspect`**  
   ```bash
   docker volume inspect mon_volume
   ```

2. **Naviguer jusqu’au répertoire du volume sur votre système de fichiers**  

3. **Créer un fichier dans le volume depuis l’hôte**  
   ```bash
   echo "Fichier ajouté depuis l'hôte" > /var/lib/docker/volumes/mon_volume/_data/fichier_hote.txt
   ```

4. **Vérifier le fichier depuis le conteneur**  
   ```bash
   docker run --rm -v mon_volume:/data nginx ls /data
   ```

5. **Question** : Que constatez-vous concernant l'accès aux données du volume depuis l'hôte et le conteneur ?

---

## Exercice 5 : Supprimer un Volume et Observer l'Impact sur les Données

**Objectif :** Observer ce qu'il se passe lorsqu'un volume est supprimé après l’utilisation avec un conteneur.

1. **Lancer un conteneur avec un volume monté**  
   ```bash
   docker run -d --name conteneur_demo -v mon_volume:/data nginx
   ```

2. **Créer un fichier dans le conteneur**  
   ```bash
   docker exec conteneur_demo sh -c "echo 'Test de persistance' > /data/persistance.txt"
   ```

3. **Supprimer le conteneur**  
   ```bash
   docker rm -f conteneur_demo
   ```

4. **Supprimer le volume**  
   ```bash
   docker volume rm mon_volume
   ```

5. **Question** : Qu’arrive-t-il aux données stockées dans le volume après sa suppression ? Pourquoi est-il important de comprendre cette opération ?

---

## Exercice 6 : Utilisation des Bind Mounts

**Objectif :** Savoir utiliser Bind Mounts

1. **Naviguer dans le répertoire du Dockerfile `dockerfile-exemple2`** 

2. **Exécuter un conteneur Nginx avec un Bind Mount**  

3. **Lancez un conteneur Nginx en montant un répertoire de votre hôte dans le conteneur pour servir du contenu personnalisé.**  
   ```bash
   docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx
   ```

4. **Exécuter un deuxième conteneur Nginx sans Bind Mount**  
5. **Lancez un autre conteneur Nginx sans Bind Mount pour observer les différences..**  
   ```bash
   docker container run -d --name nginx2 -p 8080:80 nginx
   ```

6. **Accéder à l'intérieur d'un conteneur Nginx**  
5. **Entrez dans le shell d'un conteneur Nginx en cours d'exécution pour explorer le système de fichiers.**  
   ```bash
   docker container exec -it nginx bash
   ```

---



Ces exercices vous aideront à mieux comprendre la gestion des volumes dans Docker. Prenez le temps de tester et d'explorer chaque commande pour renforcer votre compréhension.

