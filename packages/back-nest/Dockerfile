FROM node:20-alpine

# Install build dependencies for native modules
RUN apk add --no-cache python3 make g++

# Create app directory
RUN mkdir -p /app
WORKDIR /app

# Install app dependencies
COPY package.json ./
RUN yarn install --network-timeout 1000000

# Bundle app source
COPY . /app
RUN yarn build

EXPOSE 80

CMD [ "node", "dist/main.js" ]
