# Utiliser l'image de base node:lts-alpine
FROM node:lts-alpine

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Copier les fichiers package*.json
COPY package*.json ./

# Installer les dépendances avec npm install
RUN npm install

# Copier le reste des fichiers du client
COPY . .

# Construire l'application React
RUN npm run build

# Installer un serveur HTTP léger
RUN npm install -g serve

# Exposer le port 3000
EXPOSE 3000

# Servir les fichiers de build (Vite génère le dossier dist)
CMD ["serve", "-s", "dist", "-l", "3000"]