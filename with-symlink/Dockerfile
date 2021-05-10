# Base image
FROM alpine
RUN mkdir -p /tmp/test/
RUN echo "cool" > /tmp/test/test1 && ln -s /tmp/test/test1 /tmp/test/test1-sym
RUN echo "coolo" >> /tmp/test/test1
CMD [ "/bin/sh" ]
