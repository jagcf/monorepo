FROM node:10-alpine
#test 3.2 users_build true 

# ENV WAIT_VERSION 2.7.3
# ADD https://github.com/ufoscout/docker-compose-wait/releases/download/$WAIT_VERSION/wait /wait
# RUN chmod +x /wait

RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app

WORKDIR /home/node/app

COPY package.json ./package.json


COPY index.js ./


RUN ls -ltr
RUN cat package.json
#RUN cat .env

USER node

RUN npm install

COPY --chown=node:node . .




#EXPOSE 3000

CMD [ "node", "index.js" ]