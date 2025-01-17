# Stage 1: Build React app
FROM node:18 AS build

WORKDIR /app

COPY package*.json .

COPY . .

RUN npm install --production

RUN npm run build

# Stage 2: Serve with NGINX
FROM nginx:1.23

#  take local folder directory /app/build which is create in this command npm run build above  and copy to nginx folder /usr/share/nginx/html
# the default folder for nginx is /usr/share/nginx/html because nginx require the static files to run the app. when i try to npm run build it create stic files in build folder and we copy that build folder to nginx folder
COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
