FROM node:25.8.1-alpine3.22 AS base
WORKDIR /web
COPY package.json .
RUN npm install
COPY . .
RUN adduser -D -g '' elf
RUN chown -R elf /web/src
USER elf

FROM base AS dev
CMD ["npm", "run", "dev"]

FROM base AS prod
CMD ["npm", "start"]