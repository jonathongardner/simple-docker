# Base image
FROM alpine
RUN echo $(node --version) > /tmp/test1
COPY bin/* /bin/
RUN echo $(node --version) > /tmp/test3
CMD [ "/bin/sh" ]
