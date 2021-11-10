FROM node:16-alpine as builder
WORKDIR '/usr/app'
COPY package*.json ./
RUN yarn
COPY . .
RUN yarn

FROM nginx
EXPOSE 3000
COPY --from=builder /usr/app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
