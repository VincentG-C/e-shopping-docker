FROM node:25.8.1-alpine3.22 AS base
WORKDIR /web
COPY package.json .
RUN npm install
COPY . .

FROM base AS dev
RUN adduser -D -g '' elf
RUN chown -R elf /web/src
RUN chown elf /web /web/node_modules
USER elf
CMD ["npm", "run", "dev"]

FROM base AS build
RUN npm run build

FROM nginx:1.29.6-alpine-slim AS prod
WORKDIR /usr/share/nginx/html
COPY --from=build /web/dist .
COPY nginx.conf /etc/nginx/conf.d/default.conf
