FROM nginx:latest  
# il est fortement recommandé de toujours spécifier des versions lorsque nous travaillons sur des environnements autre le développement.

WORKDIR /usr/share/nginx/html  
# change le répertoire de travail à la racine de l'hôte web nginx  
# il est préférable d'utiliser WORKDIR plutôt que 'RUN cd /un/chemin'

COPY index.html index.html  

# je n'ai pas besoin de spécifier EXPOSE ou CMD car ils sont déjà présents dans mon FROM
