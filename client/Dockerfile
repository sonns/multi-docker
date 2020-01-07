FROM node:alpine as builder
WORKDIR /app
COPY package.json /app/package.json
RUN npm install
COPY . .
RUN npm run build
RUN ls -al ./src
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html