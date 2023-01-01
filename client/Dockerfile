FROM node:16-alpine AS build
WORKDIR /app
COPY ./package.json .
RUN npm install --production
COPY . .
RUN npm run build

# If no serverside rendering is done, pass static files to nginx server
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/build /usr/share/nginx/html

