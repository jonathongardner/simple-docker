# Base image
FROM alpine
RUN echo $(ruby --version) > /tmp/test2
COPY Gemfile* ./
RUN echo $(ruby --version) > /tmp/test3
CMD [ "/bin/sh" ]
