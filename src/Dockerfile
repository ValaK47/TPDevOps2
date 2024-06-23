# Dockerfile for creating a Docker image with net-tools and a custom start script.

# Use the donch/net-tools image as the base image.
FROM donch/net-tools

# Ajouter un utilisateur non-root
RUN addgroup -S group1 && adduser -S whoami -G group1

# Installer les dépendances nécessaires
RUN apk update && apk add --no-cache bash

# Définir l'utilisateur non-root pour les prochaines instructions
USER whoami
WORKDIR /

# Copier le script start.sh et lui donner les permissions d'exécution
COPY start.sh /home/whoami/start.sh

USER root
RUN chmod +x /home/whoami/start.sh

USER whoami
WORKDIR /

# Expose port 4321 in the container.
EXPOSE 4321

# Set /home/whoami/start.sh as the entrypoint of the image.
ENTRYPOINT ["/home/whoami/start.sh"]

# Set "nc -l 4323" as the default command of the image.
CMD ["nc", "-l", "4323"]
