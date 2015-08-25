# Utilisation de l'image de base aspnet 5 beta 5
FROM microsoft/aspnet:1.0.0-beta6

MAINTAINER Julien CORIOLAND

# On créé le dossier qui contiendra les sources de l'application
RUN mkdir -p /opt/src

# On se place dans le dossier /opt/src
WORKDIR /opt/src

# On ajoute le code de l'application au dossier courant
COPY ./AspNetDockerProgrammez /opt/src

ENV MONO_THREADS_PER_CPU=2000

# Exécution de la restauration des packages NuGet
RUN dnu restore

# Exposition du port 5004 utilisé par le serveur Kestrel (cf. project.json) en dehors du conteneur
EXPOSE 5004

# Démarrage de l'application en utilisant DNX et la commande Kestrel (cf. project.json)
ENTRYPOINT ["dnx", ".", "kestrel"]