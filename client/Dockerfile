#Using node-18 as a base image
FROM node:18-alpine


#Setting the work dirictory
WORKDIR /app


#Copying the package.json file to the container
COPY package*.json ./


#Running npm install to install the project dependencies in the node_modules/ directory
RUN npm install


#Copying the project files to the container
COPY . .


#Running "npm run build" to build the application
RUN npm run build


#Exposing port 3000 from the container 
EXPOSE 3000


#starting the application
CMD ["npm", "run", "serve"]

