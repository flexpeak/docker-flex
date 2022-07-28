FROM debian:stable-slim

RUN apt update && apt install -y curl
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt-get update && apt-get install -y nodejs && apt-get install -y nano cron && apt-get clean

RUN rm -rf /var/www/html

WORKDIR /var/www

RUN npm install pm2 -g

COPY ./ecosystem.config.js /home/flexdock/ecosystem.config.js

CMD ["pm2-runtime", "/home/flexdock/ecosystem.config.js"]
