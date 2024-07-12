# Dockerize-NextJS
Install yarn on Ubuntu

curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -

echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt-get update && sudo apt-get install yarn

vim Dockerfile

FROM node:latest

WORKDIR /app

COPY package.json .

RUN yarn

COPY . .

RUN yarn build

CMD ["yarn", "start"]

docker build -t nextjs .

docker run -p 3001:3000 nextapp
