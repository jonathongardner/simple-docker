# Base image
FROM alpine
RUN echo $(node --version) > tmp/test1
RUN apk add --update nodejs-current=15.10.0-r0
RUN echo $(node --version) > tmp/test2
RUN apk del nodejs-current
RUN echo $(node --version) > tmp/test3
RUN apk add --update nodejs=14.16.1-r1
RUN echo $(node --version) > tmp/test4
CMD [ "/bin/sh" ]
