## Build
FROM node:10-alpine as builder
## Build
# FROM beevelop/ionic:latest AS ionic
# Create app directory
RUN node -v
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

RUN npm i -g ionic cordova

ENTRYPOINT [“ionic”]
# Install app dependencies
RUN npm install

# Bundle app source
COPY . .

RUN node -v
# Build Ionic app
RUN ionic build

## Run 
FROM nginx:alpine

# Copy built files from the previous stage
COPY --from=builder /usr/src/app/www /usr/share/nginx/html
