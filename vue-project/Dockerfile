FROM node:18-alpine as builder

RUN npm install -g http-server

WORKDIR /app

RUN npm install -g corepack && corepack enable
RUN corepack prepare pnpm@latest --activate

COPY package.json ./

RUN pnpm fetch --prod
ADD . ./

RUN pnpm install 
RUN pnpm build

EXPOSE 8080

CMD ["http-server", "dist"]