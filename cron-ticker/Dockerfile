# /app /usr /lib
# FROM --platform=linux/amd64 node:19.2.0-alpine3.17 
# https://docs.docker.com/build/building/multi-platform/#getting-started
# FROM --platform=$BUILDPLATFORM node:19.2.0-alpine3.17 
FROM node:19.2.0-alpine3.17 

# cd app
WORKDIR /app

COPY package.json ./

# Instalar todas las dependencias
RUN npm install

# copia todo lo del path the docker y lo pega en el working dir (/app) excluyendo dockerignore
COPY . .

# Realizar testing
RUN npm run test

# Eliminar archivos y directorios no necesarios
RUN rm -rf tests && rm -rf node_modules 

# Unicamente las dependencias de produccion
RUN npm install --prod

# comando run de la imagen
# se ejecuta cuando se monta la imagen del contenedor
# Inicia la aplicacion 
CMD ["node", "app.js"]
