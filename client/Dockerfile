FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build
# do tego momentu tworzymy obraz ktory bedzie wziety do stworzenia tego poniżej 
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html 
# w drugim copy /app/build jest domyślnym folderem w którym generuje się obraz