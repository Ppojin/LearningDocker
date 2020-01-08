#성능 개선?
# 방법1: BASE IMAGE 교체
FROM    node:alpine
#node:alpine

## 방법2: node 설치# FROM BaseImage
# FROM alpine:3.11
### curl으로 설치하기
## RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
### wget으로 설치하기
## RUN wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

WORKDIR /home/node
COPY ./package.json ./package.json
RUN npm install

COPY ./index.js ./index.js

CMD ["npm", "start"]