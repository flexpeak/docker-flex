FROM alpine:latest

ARG USER_UID
ARG USER_GID

RUN groupadd -g ${USER_GID} flexdock && \
useradd -u ${USER_UID} -g flexdock -m flexdock && \
usermod -p "*" flexdock

RUN ldconfig

RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt-get update && apt-get install -y nodejs && apt-get install -y nano cron && apt-get clean

RUN rm -rf /var/www/html

WORKDIR /var/www

COPY ./ecosystem.config.js /home/flexdock

CMD ["pm2-runtime", "/home/flexdock/ecosystem.config.js"]
