ARG VERSION

#Dev
FROM nginx:${VERSION}-alpine as dev

#Copy config
COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf

#Prod
From dev as prod

COPY ./assets /app/public