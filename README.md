# TPDevOps2

Description
Ce projet est destiné à créer une image Docker compatible avec les politiques de sécurité de l'industriel. Le Dockerfile et le script de démarrage (start.sh) ont été modifiés pour garantir que le conteneur ne s'exécute pas en tant que root et puisse fonctionner en mode lecture seule.

Modifications Apportées
Dockerfile
Ajout d'un utilisateur non-root:

Un utilisateur nommé "whoami" 
L'utilisateur "whoami" est utilisé pour exécuter le conteneur.

Update des paquets : apk update
Configuration du répertoire de travail et des permissions:

Le script start.sh a été copié dans /home/whoami/ et rendu exécutable.
Le répertoire de travail a été défini à la racine (/).
Exposition du port 4321:

Le port 4321 a été exposé.
Définition du point d'entrée et de la commande par défaut:

Le point d'entrée a été défini sur /home/whoami/start.sh.
La commande par défaut a été définie sur nc -l 4323.

start.sh : 
Modification pour éviter d'écrire dans un répertoire en lecture seule:
Les opérations d'écriture ont été redirigées vers le répertoire /tmp au lieu de /home/www.

Instructions d'Exécution
Cloner le repository:

git clone <URL_du_repository>
cd <nom_du_repository>

Rendre les scripts exécutables:

chmod +x validator.sh
chmod +x src/start.sh

Exécuter le script de validation:

./validator.sh

Ce script construira l'image Docker, vérifiera que l'utilisateur à l'intérieur du conteneur n'est pas root, et s'assurera que le conteneur peut fonctionner en mode lecture seule.
