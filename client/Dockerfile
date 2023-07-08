# Step 1 : Build image
FROM node:16-alpine as builder

ARG NPMRC_FILE

# Needed by node-gyp module
RUN apk add --no-cache --virtual .gyp python3 make g++

# Define working directory and copy source
WORKDIR /home/node/app

# Copy all, execpt files in .dockerignore (ex. 'node_modules')
COPY . .

# Create .npmrc file from Base64 encode build arg
RUN echo $NPMRC_FILE | base64 -d > .npmrc

# Install modules and build
RUN npm ci --prefer-offline --no-audit

RUN \
    npm run build && \
    npm prune --production
# adding NODE_ICU_DATA to environment
ENV NODE_ICU_DATA=/home/node/app/node_modules/full-icu

# Step 2 : Run image
FROM node:16-alpine
ENV NODE_ENV=production
WORKDIR /home/node/app

# Copy builded source from the upper builder stage
COPY --from=builder /home/node/app/ .

# Set user
USER node

# Start the app
CMD ["npm","run","start"]
