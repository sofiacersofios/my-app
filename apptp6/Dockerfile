# Etapa de build
FROM node:13.12.0-alpine as build
WORKDIR /app
# Copia los archivos de package.json y package-lock.json para gestionar las dependencias
COPY /package*.json ./
# Instala las dependencias
RUN npm install
# Copia el resto de los archivos de la aplicación
COPY . . 

# Etapa de producción
FROM node:13.12.0-alpine
WORKDIR /app
# Copia los archivos de la etapa de construcción (incluyendo "my-app")
COPY --from=build /app ./
# Exponer el puerto 3000
EXPOSE 3000
# Comando para iniciar la aplicación
CMD ["npm", "start"]
