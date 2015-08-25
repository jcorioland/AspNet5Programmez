# Utilisation de l'image de base aspnet 5 beta 6
FROM microsoft/aspnet:1.0.0-beta6

MAINTAINER Benjamin Talmard

# https://github.com/aspnet/dnx/issues/1590#issuecomment-126965429  
ENV MONO_THREADS_PER_CPU=2000

# On créé le dossier qui contiendra les sources de l'application
RUN mkdir -p /opt/src

# On se place dans le dossier /opt/src
WORKDIR /opt/src

# On ajoute le code de l'application au dossier courant
COPY ./AspNetDockerProgrammez /opt/src

# Exécution de la restauration des packages NuGet
RUN dnu restore

# Exposition du port 5004 utilisé par le serveur Kestrel (cf. project.json) en dehors du conteneur
EXPOSE 5004

# Démarrage de l'application en utilisant DNX et la commande Kestrel (cf. project.json)
ENTRYPOINT ["dnx", ".", "kestrel"]
