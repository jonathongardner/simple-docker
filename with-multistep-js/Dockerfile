FROM node:lts-alpine as build-stage
# make the 'app' folder the current working directory
ENV ROOT /var/www/ui
RUN mkdir -p $ROOT
WORKDIR $ROOT
# copy both 'package.json' and 'package-lock.json' (if available)
COPY ui/package*.json ./
# install project dependencies
RUN npm install
# copy project files and folders to the current working directory
COPY ui ./
# build static/minified javascript
RUN npm run build

FROM nginx
COPY --from=build-stage /var/www/ui/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
