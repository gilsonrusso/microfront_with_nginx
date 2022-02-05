FROM node:14-alpine as build

WORKDIR /app

COPY . .

RUN npm ci --silent

RUN npm run build -- --deploy-url /angular/

FROM nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/dist/angular-app /usr/share/nginx/html