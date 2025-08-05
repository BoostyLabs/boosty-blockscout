FROM node:lts-alpine3.20 AS build

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY block_scout_web/package*.json ./block_scout_web

RUN cd block_scout_web && npm install

# Bundle app source
COPY . .

# Final stage
FROM node:lts-alpine3.20
WORKDIR /usr/src/app

COPY --chown=node:node --from=build /usr/src/app/ ./

CMD mix phx.server