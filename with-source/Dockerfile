# Base image
FROM alpine
RUN echo $(node --version) > /tmp/test1
RUN apk add --update nodejs=14.16.1-r1 npm
RUN echo $(node --version) > /tmp/test2
RUN mkdir -p /var/www/js
WORKDIR /var/www/js
COPY package*.json ./
RUN npm install
RUN echo $(node --version) > /tmp/test3
CMD [ "/bin/sh" ]
