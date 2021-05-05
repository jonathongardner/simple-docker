# Base image
FROM alpine
RUN echo $(node --version) > tmp/test1
RUN apk add --update nodejs-current=15.10.0-r0
RUN echo $(node --version) > tmp/test2
CMD [ "/bin/sh" ]
