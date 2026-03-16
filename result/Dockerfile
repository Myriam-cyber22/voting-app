# Image de base Node.js version 18 (légère avec Alpine)
FROM node:18-alpine

# Dossier de travail dans le conteneur
WORKDIR /app

# Copier d'abord les fichiers de dépendances séparément
# (optimisation du cache Docker : npm install ne se relance que si package.json change)
COPY package*.json ./

# Installer les dépendances
RUN npm install --production

# Copier le reste du code source
COPY . .

# Exposer le port de l'application
EXPOSE 8081

# Commande de démarrage
CMD ["node", "server.js"]
