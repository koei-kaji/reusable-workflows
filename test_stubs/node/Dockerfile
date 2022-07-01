# https://firebase.google.com/docs/emulator-suite/install_and_configure
FROM node:16.15.1-alpine3.16
ARG NPM_VERSION=8.13.2
ENV USERNAME=hello
WORKDIR /usr/src/app
RUN npm install --location=global npm@${NPM_VERSION} \
    && rm -rf /var/cache/apk/* \
    && npm cache clean --force \
    && addgroup -S ${USERNAME} && adduser -S ${USERNAME} -G ${USERNAME} \
    && chown -R ${USERNAME}:${USERNAME} .
USER ${USERNAME}:${USERNAME}
COPY . ./
RUN npm ci
CMD [ "node", "src/hello.js" ]