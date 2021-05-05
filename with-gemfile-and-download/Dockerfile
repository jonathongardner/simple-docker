# Base image
FROM ruby:2.6.0
RUN echo $(ruby --version) > /tmp/test1
COPY Gemfile* ./
RUN echo $(ruby --version) > /tmp/test2
RUN bundle install
RUN echo $(ruby --version) > /tmp/test3
CMD [ "/bin/sh" ]
