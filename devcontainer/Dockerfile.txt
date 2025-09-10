FROM node:20.19-alpine

LABEL devcontainer.metadata="{\"customizations\":{\"vscode\":{\"settings\":{\
\"extensions.allowed\":{\"angular.ng-template\":[\"20.0.1\"],\"dbaeumer.vscode-eslint\":[\"3.0.10\"],\
\"esbenp.prettier-vscode\":[\"11.0.0\"],\"eamodio.gitlens\":[\"17.2.0\"],\"ms-vscode-remote.remote-containers\":\
[\"0.417.0\"]}},\"extensions\":[\"angular.ng-template\",\"eamodio.gitlens\",\"esbenp.prettier-vscode\",\
\"ms-vscode-remote.remote-containers\"]}},\"remoteUser\":\"nodeuser\"}"

RUN apk add git

RUN npm install -g npm@10.8.2

RUN npm install -g @angular/cli@19.2.0

RUN addgroup appgroup

RUN adduser nodeuser  -D

RUN mkdir -p /usr/src/app && chown -R nodeuser:appgroup /usr/src/app

WORKDIR /usr/src/app

USER nodeuser