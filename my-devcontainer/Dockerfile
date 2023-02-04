FROM node:16-alpine

RUN apk add --no-cache curl \
    && curl -qL https://www.npmjs.com/install.sh | sh \
    && npm install -g @angular/cli

WORKDIR /app

# COPY package.json package.json

EXPOSE 4000 4200

CMD ["npm", "run", "start"]